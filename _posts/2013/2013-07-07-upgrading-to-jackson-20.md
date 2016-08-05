---
layout: post
title: "Upgrading to Jackson 2.0"
description: ""
category: 
tags: [android]
---

In March 2012, the first major update to the JSON processing library, Jackson, was released. Smule's Android team uses Jackson for manipulating JSON, but until recently, we were using version 1.9. While version 1.9 worked perfectly fine, I took some time to get us on the latest and greatest Jackson has to offer. The upgrade to 2.0 is not as trivial as swapping JAR files, so here are some tips for a successful upgrade.

<!--break-->

**Note:** This post is a supplement to my [earlier post](/2013/05/26/tips-for-android-json-parsing-using-jackson/) about using Jackson that applied to version 1.9.

<p class="header">1. Updating JAR Files</p>
We were previously using 2 JAR files: **jackson-core-asl-1.9.4.jar** and **jackson-mapper-asl-1.9.4.jar**. The 2.0 update reorganized how Jackson is packaged so you'll want to now use these 3 JAR files: **jackson-annotations.jar**, **jackson-core.jar**, and **jackson-databind.jar**. Remember to update your IDE project settings and any build scripts to use these new JAR files.

<p class="header">2. Fixing Imports</p>
Aside from things getting shuffled from 2 to 3 JAR files, the Java package names have also been updated for from **org.codehaus.jackson** to **com.fasterxml.jackson**, so you'll need to update import statements. My favorite Android IDE, IntelliJ IDEA, makes this easy. Don't touch anything after updating the JAR files, try to compile, remove all the missing import errors, and let IntelliJ's auto-import feature handle all the grunt work for you.

<p class="header">3. Get the "get" out!</p>
After fixing all the import statements, don't be alarmed by the number of errors you may still be seeing. You likely just need to remove the word **get** from a bunch of places. For example, JsonNode methods in 1.9 like getBooleanValue(), getFields(), getElements(), getIntValue() have dropped the get in 2.0 to become booleanValue(), fields(), elements(), and intValue(). 

<p class="header">4. Parsing JSON Arrays</p>
You will still have lingering compiler errors if you were parsing JSON arrays. In Jackson 1.9, you could parse an array of objects like this:

{% highlight java %}
public List<Subject> subjects;
public void setSubjects(JsonNode jsonArrayNode) {
   subjects = mObjectMapper.readValue(jsonArrayNode, new TypeReference<List<Subject>>() {});
}
{% endhighlight %}

In Jackson 2.0, the **readValue** method now takes as its first parameter a **JsonParser** instead of a **JsonNode**. Going down my hierarchy of compiler-error-problem-solving, I first looked through header files and futzed around a bit to no avail. I turned to Google and Stack Overflow, but couldn't find any solutions. So I posted a question on Stack Overflow and implemented this temporary solution, which manually iterates over the JsonNode containing our array of objects and parses each object in it.

{% highlight java %}
public List<Subject> subjects = new ArrayList<Subject>();
public void setSubjects(JsonNode jsonArrayNode) {
   for(JsonNode jsonNode : jsonArrayNode) {
      subjects.add(objectMapper.treeToValue(jsonNode, Subject.class));
   }
}
{% endhighlight %}

Within the hour, an answer was posted. Turns out, the trick is to simply call **traverse()** on your JSON ArrayNode before passing it to **readValue**. The **readValue** method throws exceptions, so I created a new helper method in my JsonUtils class.

{% highlight java %}
// helper method to make JSON array parsing a one-liner
public static <T> List<T> parseJsonList(JsonNode node, TypeReference<List<T>> typeReference) {
   try {
      return JsonUtils.defaultMapper().readValue(node.traverse(), typeReference);
   } catch (IOException e) {
      Log.e(TAG, "Failed to parse JSON list " + typeReference.getType(), e);
      throw new RuntimeException(e);
   }
}
{% endhighlight %}

With this new method, we can now easily parse our JSON containing an array of objects.

{% highlight java %}
public List<Subject> subjects;
public void setSubjects(JsonNode jsonArrayNode) {
   subjects = JsonUtils.parseJsonList(jsonArrayNode, new TypeReference<List<Subject>>() {});
}
{% endhighlight %}

<hr class="separator"/>

Jackson 2.0 adds some cool [new features](https://github.com/FasterXML/jackson-docs/wiki/Presentation-Jackson-2.0) that we're not planning to use yet. But now, we're in a good place to use them when the time comes. If you're upgrading Jackson and running into any problems not covered here, please feel free to [send me a tweet](https://twitter.com/markmcerqueira); I'll try to help and update this post.