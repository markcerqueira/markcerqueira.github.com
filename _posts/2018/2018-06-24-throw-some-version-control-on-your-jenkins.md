---
layout: post
title: "Throw Some Version Control On Your Jenkins"
description: ""
category: 
tags: [ci, jenkins]
---

Years of doing Jenkins here and there has let me pick up some (perhaps unconventional) habits. One habit I'm willing to go to bat for is putting your Jenkins configuration and scripts in version control. And the best part: no fancy memory-leaking, performance-impacting plugins needed!

Just throw a `jenkins` folder in your repo and the execute shell of all your Jenkins jobs can start looking like this:

{% gist markcerqueira/c434e0854de2419382341f59e5b29bd0 %}

Sourcing `bootstrap.sh` will set up the environment for your Jenkins job. This should ideally be stuff that can be shared across all Jenkins jobs. In `comprehensive-test-suite.sh` you can do all the work our job needs to get done.

The benefits of a system like this:

* Bootstrapping is written once and shared across all jobs. If you need to update your bootstrapping, it's a one-time cost.
* Updates to the worker script are tied to the accompanying changes to the rest of the repo to support them. No need for conditionals in your execute shell block.
* If you bootstrap your own cmputer similar to the Jenkins bootstrap, you can run the Jenkins worker scripts locally to verify their behavior.
* Whatever version control you're using is far better than the JobConfigHistory plugin available on Jenkins.
* I have seen Jenkins updates clobber job configuration. This protects you somewhat against the occasional Jenkins hiccup.

One important caveat to this setup is inside your worker script you'll want to check for exit codes from calls inside there and fail if a non-zero exit code is found. If you don't do this, components of your worker script may fail but if the overall script exits without passing through a failure exit code, your job will (erroneously) succeed! What does this working around this look like?

{% gist markcerqueira/9d2c8e76aae171a43a504a4f64d202d7 %}

The `step`, `try`, `next` are brought in by sourcing `jenkins-helper.sh`. These functions allow grouping up chunks of work and checking the exit codes for all processes in those chunks of work after they're completed. Basically all the steps between `step` and `next` that are preceded with a `try` will be executed and their exit codes will be recorded. When the `next` is hit, all exit codes will be checked for success. Check out [jenkins-helper on Gist][1].

Hope that helps!

[1]: https://gist.github.com/markcerqueira/ff08867b3ad75e0c61d06a6ee28ef641
