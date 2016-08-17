---
layout: post
title: "Acing Technical Interviews"
description: ""
category: 
tags: [technical, java]
---

Technical interviews are a pain. But here’s a 2-step plan to ace them:

1. **Pick Java as your programming language du jour.**
2. **Use [LinkedHashMaps][1].**

The HashMap is great and usually the go-to data structure during an interview. But an interviewer who’s a jerk will always try to unnecessarily put down the HashMap. Here’s how that conversation might go:

**Interviewer:** HashMap, eh? But what if you want to keep the map to a certain size by removing the oldest entry when you hit the size limit?

**You:** Did you know about the LinkedHashMap method removeEldestEntry?

**Interviewer:** What if you want to have the performance of a map but you want to know the order things were put in?

**You:** Did you know keys can be iterated over in insertion-order? And before you ask - yes, you can iterate over the items in the order they were accessed. 

**Interview:** Wow! You really know a lot! But can you reverse a linked list?

**You:** Yes I may know how to do something I would never actually do if you hired me, but did you know that internally the LinkedHashMap implementation maintains a doubly-linked list?

**Interviewer:** Wow! You’re great! When can you start?

**You:** I’ve already converted every pleb data structure in your codebase into a LinkedHashMap. **\*walk out\***

Boom! You're hired!

[1]: https://developer.android.com/reference/java/util/LinkedHashMap.html
