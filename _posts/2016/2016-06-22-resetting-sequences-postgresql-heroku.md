---
layout: post
title: "Resetting Sequences in PostgreSQL on Heroku"
description: ""
category: 
tags: [technical]
---
{% include JB/setup %}

Today [Glatering][1] -- a world-class Rails app with a Postgres database I'm running on Heroku -- kicked the bucket! Time to debug... To the Heroku logs!

{% highlight bash %} 
~ heroku logs --app {app_name}
    ActionView::Template::Error
    PG::UniqueViolation: ERROR: duplicate key value violates unique constraint "events_pkey"
    Rendered welcome/index.html.erb within layouts/application (324.8ms)
    Completed 500 Internal Server Error in 413ms (ActiveRecord: 90.0ms)
    DETAIL: Key (id)=(47) already exists.
{% endhighlight %}

Looks like when we were creating a new event object the auto-assigned id for it (which has to be unique) already existed in the database. We were trying to use id 47 when the database had an event with that id already in it. This is weird because that id should be assigned and auto-incremented for us.

So what do we do? **Get Postgres to check itself** a.k.a. reset the value "events_pkey" to a valid value. 

To connect to the database, I use my favorite Postgres GUI [Postico][2]. All the information you need to connect to the database (e.g. user, password, host, database name) is in the Heroku DATABASE_URL environmental variable in the Settings section of the app dashboard.

{% highlight bash %} 
~ echo $DATABASE_URL
    postgres://{user}:{password}@{host}:{port}/{database}
{% endhighlight %}

Once connected, click on SQL query, paste the query below (and replace events with the name of the table you're having issues with), and hit Execute Statement. 

{% highlight bash %} 
SELECT pg_catalog.setval(pg_get_serial_sequence('events', 'id'), MAX(id)) FROM events;
{% endhighlight %}

Boom! Hopefully your database is still in one piece, your Postgres sequence should be reset it, and it won't generate duplicate ids any more!

[1]: /2016/01/26/evernote-hackathon-report
[2]: https://eggerapps.at/postico/

