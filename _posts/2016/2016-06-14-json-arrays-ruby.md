---
layout: post
title: "Producing JSON Arrays in Ruby"
description: ""
category: 
tags: [ruby, technical]
---
{% include JB/setup %}

I've been working on a project and building the backend with Ruby and Sinatra. So far so good, until I wanted to take a list of objects I fetched from ActiveRecord and produce a JSON array. I had a function set up to JSONify a single object:

{% highlight ruby %}
# Returns passed model as a hash
# This is separate from to_json because we'll use it later!
def to_hash(model)
  {
    'id' => model.id,
    'name' => model.name
  }
end

# Returns JSON for given model
def to_json(patch)
  to_hash(model).to_json
end
{% endhighlight %}

Extending this to produce a JSON array for a bunch of model objects is simple for anyone who is familiar with Ruby.... Something I'm clearly not! Here's the clean solution I eventually got:

{% highlight ruby %}
# Returns JSON for given models
def to_json_list(models)
  return models.each_with_object([]) { |model, array| array << to_hash(model) }.to_json
end
{% endhighlight %}

For the laughs (and sadness), here was my initial (and ghetto) implementation of to_json_list:

{% highlight ruby %}
# Ghetto but I wasn't able to find a better way to do this!
def to_json_list(models)
  i = 1
  result = '['
  models.each do |model|
    result += to_json(model)
    if (i += 1) <= models.length
      result += ','
    end
  end
  return (result += ']')
end
{% endhighlight %}

Replacing the above method with the single-line version felt almost as good as removing that # Ghetto comment! 
