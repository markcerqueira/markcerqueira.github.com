---
layout: post
title: "Tips for Android JSON Parsing Using Jackson"
description: ""
category: 
tags: [android]
---

At Smule, we use the [Jackson library](http://wiki.fasterxml.com/JacksonHome) for our JSON parsing. Marshaling JSON into corresponding model objects is elegant and easy with Jackson and makes code much more readable. Here are some tips for those considering using Jackson for their marshaling.

<!--break-->

**Update:** This post applies to Jackson 1.9. If you're using Jackson 2.0, please see [my post on upgrading from Jackson 1.9 to 2.0](/2013/07/07/upgrading-to-jackson-20/). 

To parse JSON, you can **use Jackson's treeToValue method**. This method throws some exceptions so it's **recommended you create a helper method that catches these exceptions instead of having try-catches everywhere** you are parsing (our JSON helpers are in a class called JsonUtils). [Jackson best practices](http://wiki.fasterxml.com/JacksonBestPracticesPerformance) recommends one **re-use object mappers since creation of the mapper is an expensive operation** - so our JSON helper class has a defaultMapper() method.

{% highlight java %}
// newsFeedItemJsonNode is a JsonNode containing the JSON to be parsed
// the second parameter specifies the class of the object you want back
JsonUtils.parseJson(newsFeedItemJsonNode, NewsFeedItem.class);

// this helper method can be used to make JSON parsing a one-line operation
public static <T> T parseJson(JsonNode node, Class<T> class) {
    try {
        return JsonUtils.defaultMapper().treeToValue(node, class);
    } catch (IOException e) {
        Log.e(TAG, "Failed to parse JSON entity " + class.getSimpleName(), e);
        throw new RuntimeException(e);
    }
}

// re-use a single ObjectMapper so we're not creating multiple object mappers
private static ObjectMapper sObjectMapper = new ObjectMapper();
public static ObjectMapper defaultMapper() {
    return sObjectMapper;
}
{% endhighlight %}

<hr class="separator"/>

Model classes should usually **ignore unknown JSON properties**. If a server API later adds new fields or we just don't care about some fields, the parser won't throw exceptions if they are ignored. Jackson also **requires a defined default constructor**, otherwise an exception will be thrown on parsing.

{% highlight java %}
// if ignoreUnknown is false, Jackson would throw an exception if we don't parse all fields
@JsonIgnoreProperties(ignoreUnknown = true)
public class NewsFeedItem {
	public NewsFeedItem() {
		// Jackson requires a default constructor
	} 
}
{% endhighlight %}

<hr class="separator"/>

Model classes can **annotate variables to automatically parse JSON fields**. This works automatically for primitive types and Strings, but it **can even parse other classes** if those classes are set up for Jackson parsing.

{% highlight java %}
public class NewsFeedItem {
	// will parse "type" out of our JSON and store it in the type variable
	 @JsonProperty("type") public String type;
	
	 // FeedIcon is one of our classes set up to parse JSON
	 // here we parse a list of FeedIcon objects that are referenced by "feedIcons"
	 @JsonProperty("feedIcons") public List<FeedIcon> feedIcons;
}
{% endhighlight %}

<hr class="separator"/>

If you have data nested in an array or hash and want to get at the data in it, you have to **override the setter Jackson creates and get the data yourself**. Consider this JSON that has some data we'd like to store as two integers instead of a hash in our mode class:

{% highlight json %}
{
    "social": {
        "numFollowers": 40,
        "numFollowees": 10
    }
} 
{% endhighlight %}

To extract the two integers out of "social" and store them as integers in our class, we override how Jackson parses the "social" JSON element:

{% highlight java %}
// nested JSON - "social" contains two properties we'd like to store as integers
// override how Jackson parses "social"
@JsonProperty("social")
public int numFollowers;
public int numFollowees;
public void setSocial(Map<String, Object> socialJsonMap){
	numFollowers = Integer.parseInt(socialJsonMap.get("numFollowers").toString());
	numFollowees = Integer.parseInt(socialJsonMap.get("numFollowees").toString());
}
{% endhighlight %}

<hr class="separator"/>

Overriding the setter is also useful if you have **data you want to change at the time of parsing** because sometimes an API doesn't give it to you like you want it.

{% highlight java %}
// override how we parse/set "time" so we can get the value in the desired format
@JsonProperty("time") public Date time;
public void setTime(String timeValue) {
  time = new Date(Long.valueOf(timeValue).longValue() * 1000);
}
{% endhighlight %}

<hr class="separator"/>

**Overriding setters requires you to properly identify the JSON structure referenced by the key**. For example, when we overrode how "time" was parsed above, our setTime method took a String because in our JSON, the "time" key contained a string. Up higher, when parsing "social" our setSocial method took a map because "social" contained a map. Things can get even fancier:

{% highlight java %}
// "performances" is used to determine the number of performances a user has in each Smule app
@JsonProperty("performances")
public void setPerformances(List<Map<String, String>> numPerformancesByAppList) {      
	for(Map<String, String> appPerformanceCountMap : numPerformancesByAppList) {
		// do stuff!
	}
}
{% endhighlight %}

In this example, "performances" in the JSON is an array of hashes. Note that the parameter you specify for the argument to your overriden set method must be relevant - if "performances" actually contained a hash of hashes, this method would not be called! **If you specify the type of the argument as JsonNode, you will always get called**. In the above snippet if we specified the argument as type JsonNode, you would get called with an ArrayNode containing ObjectNodes that contain HashMaps. If you're not sure what you are going to get back, start with JsonNode and work from there!

<hr class="separator"/>

Here is an example of **overriding a setter to parse an array of a custom model object that is nested within our JSON**. Here is some sample JSON containing some user information: 

{% highlight json %}
{
    "subjects": {
        "total": 2,
        "accountIcons": [
            {
                "accountId": 123456,
                "handle": "SmuleUser"
            },
            {
                "accountId": 654321,
                "handle": "SmuleSinger"
            }
        ]
    }
}
{% endhighlight %}

If we want to parse the "accountIcons" array, we override how "subjects" is set and parse out the AccountIcons:

{% highlight java %}
// we want to grab "accountIcons" in "subjects" so override how we process subjects
// "accountIcons" contains  AccountIcon objects so Jackson will automatically parse those
@JsonProperty("subjects") public List<AccountIcon> subjects;
public void setSubjects(JsonNode subjectsJsonNode) {
	JsonNode accountIconsNode = subjectsJsonNode.get("accountIcons");
	subjects = JsonUtils.defaultMapper().readValue(accountIconsNode, new TypeReference<List<AccountIcon>>() {});
}
{% endhighlight %}

Note that for the setSubjects method we specify the argument as a JsonNode since the readValue() method requires a JsonNode. If we wanted to manually parse the data, we could change the type of subjectsJsonNode to be a Map&lt;String, Object&gt;. We could grab the Object with key "accountIcons," cast it to a List&lt;Map&lt;String, String&gt;&gt;, and then iterate over and parse the items as desired. 

<hr class="separator"/>

I hope this helps anyone considering considering or having problems using Jackson for their JSON parsing. If there is something totally awesome I missed about Jackson or did something not quite right here, please feel free to [send me a tweet](https://twitter.com/markmcerqueira) and I'll update this post! 
