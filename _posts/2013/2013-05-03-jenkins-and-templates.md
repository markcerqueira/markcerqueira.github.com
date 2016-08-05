---
layout: post
title: "Staving Rampant Copy-and-Paste in Jenkins with Templates"
description: ""
category: 
tags: [ci]
---

At Smule, we use Jenkins build servers for our iOS and Android projects. Along the way, we have learned a lot and continue to learn and improve our build system.Changing anything in Jenkins could be viewed as a double-edged sword. Awesome changes make things better, but when you have (in our case) tens or more jobs per project for different combinations of branches/environments/configurations, applying these changes involves a lot of copy-and-paste. The standard Jenkins installation does not provide any serious power in helping to abstract out shared logic into reusable chunks that have fewer points of maintenance. 

<!--break-->

### Templates to the Rescue
CloudBees has created the [Templates Plugin](http://www.cloudbees.com/jenkins-enterprise-by-cloudbees-features-templates-plugin.cb). But to use it, you need to pay CloudBees to access their entire suite of enterprise plugins. Others have explored and are developing an [inheritance-based approach](http://www.cloudbees.com/jenkins-user-conference-2012-san-francisco-abstracts.cb#MartinSchroder), but the plugin is not available yet. At Smule we use the [Template Project Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Template+Project+Plugin). Best of all, it is free, open, actively maintained, and works! Just for our Android build system, we went from maintaining nearly one hundred jobs (by copying-and-pasting any changes we made to jobs) to maintaining only a handful — and this covers two separate projects with multiple branches and environments! 

### Template Project Plugin in Action
To use the template plugin, you create a job that will have modules - source code management (SCM), builders, publishers - that will be used by other projects. Here is the SCM for the template project, *sing-build-template*, for all Sing Android builds:

<div>
	<img class="rounded-corners" src="/assets/images/posts/2013-05-03/SCM-build-template.png"/>
	<p class="caption-text">SCM module of the Sing Android template job.</p>
</div>

Before the template plugin, we had to copy the repository URL and branch into every job. Now, jobs can use the SCM module of the *sing-build-template* job:

<div>
	<img class="rounded-corners" src="/assets/images/posts/2013-05-03/SCM-using-template.png"/>
	<p class="caption-text">SCM module of a regular Sing Android job using the SCM from the template job.</p>
</div>

The template plugin also allows jobs using modules from other jobs to pass configuration to the template job via environmental variables. In the above example, you can see that the branch that is being checked out is denoted by the value of the *BRANCH* environmental variable.

<div>
	<img class="rounded-corners" src="/assets/images/posts/2013-05-03/SCM-defining-environmental.png"/>
	<p class="caption-text">A Sing Android job configuring which branch it would like to check out.</p>
</div>

This basic example shows how easy it is to consolidate shared functionality into a single location that can be reused. If we migrated away from GitHub as our hosting service, updating all our jobs would be much easier!

This system does not completely remove the need for copy-and-paste as modules that are being used still need to be configured for every new job. An inheritance-based system would allow children jobs to inherit all functionality from its parent and override only what's necessary. That said, with the Template Project plugin our Jenkins servers have become much easier to maintain and improve upon!
