---
layout: post
title: "Don't Call Execute() on AsyncTasks"
description: ""
category: 
tags: [android]
---

AsyncTasks are pretty useful. But when you submit them for execution, you should know what you're getting yourself into. Regarding the order of execution for AsyncTasks, [documentation][1] states:

<blockquote>
"When first introduced, AsyncTasks were executed serially on a single background thread. Starting with DONUT, this was changed to a pool of threads allowing multiple tasks to operate in parallel. Starting with HONEYCOMB, tasks are executed on a single thread to avoid common application errors caused by parallel execution. If you truly want parallel execution, you can invoke executeOnExecutor() with THREAD_POOL_EXECUTOR."
</blockquote>

Cool - seems simple enough. **Calling execute() will queue your AsyncTask onto a single thread. But this can be problematic.** Consider this example:

{% highlight java %}
// this might take a long time
AsyncTask fileDownloadTask = getAsyncTaskToDownloadLargeFile();
fileDownloadTask.execute();

// this should not take a long time
AsyncTask databaseQueryTask = getAsyncTaskToMakeQuickQuery();
databaseQueryTask.execute();
{% endhighlight %}

What's wrong with this? Your quick database query task we will blocked by your long file download task. This is bad.

How to remedy this? **It's easy: NEVER use execute() and ALWAYS use executeOnExecutor().**

If you need things queued up serially pass SERIAL_EXECUTOR, otherwise pass THREAD_POOL_EXECUTOR. You'll need to do a little more thinking, but the end result will be a deliberate choice that YOU make.

Why not always just use THREAD_POOL_EXECUTOR to avoid blocking other AsyncTasks? Using the SERIAL_EXECUTOR is an easy way to get the functionality of a [barrier][2] without actually using a barrier. If you need multiple pieces of information fetched before you can do something, you can queue them up on the SERIAL_EXECUTOR. When the last task queued is done, you know the others must have finished running too. That said, you should still call executeOnExecutor(SERIAL_EXECUTOR) instead of execute() in this case!

Happy safe -- whether serially or parallel -- coding!

[1]: https://developer.android.com/reference/android/os/AsyncTask.html
[2]: https://en.wikipedia.org/wiki/Barrier_%28computer_science%29