---
layout: post
title: "Screw Command-Line Interface Elitism"
description: ""
category: 
tags: [technical, rant]
---

I recently read a post by Chris Beams on [How to Write a Git Commit Message][1]. Before I get into it, I want to emphasize that this post isn't about hating on Chris or his advice; they're both awesome. ♥

This post is about something I noticed in Chris' post and something I hear come up way too often in the programming world: how amazing the command-line interface (CLI) is and how everyone should be using it as exclusively as possible because **it's the best thing ever**.

Towards the end of Chris' post, we are left with some helpful tips to be the best git-people that no one ever was. One tip focuses on the importance of using git on the CLI:

<blockquote>
Learn to love the command line. Leave the IDE behind.<br><br>

For as many reasons as there are git subcommands, it's wise to embrace the command line. Git is insanely powerful; IDEs are too, but each in different ways. I use an IDE every day (IntelliJ IDEA) and have used others extensively (Eclipse), but I have never seen IDE integration for git that could begin to match the ease and power of the command line (once you know it).<br><br>

Certain git-related IDE functions are invaluable, like calling git rm when you delete a file, and doing the right stuff with git when you rename one. Where everything falls apart is when you start trying to commit, merge, rebase, or do sophisticated history analysis through the IDE.<br><br>

When it comes to wielding the full power of git, it's command-line all the way.
</blockquote>

You know what I think? **SCREW COMMAND-LINE INTERFACE ELITISM**. 

Look, I use git on both the command-line and with my preferred git GUI of choice: [Tower][2]. I like to do certain things in Tower (review commits, stage individual files, write commit messages) and I like to do other things on the CLI (interactive rebases, fetches, resolving merge conflicts, pushes). It works well for me. I am comfortable and capable with my workflow, and I'm pretty fast at getting from point A to point B in the git world, even though I am not going "command-line all the way."

<div>
	<img class="rounded-corners" style="max-width: 400px; margin-top: 10px; border: 0px;" src="/assets/images/posts/2015-07-28/harmony.png"/>
	<p class="caption-text" style="line-height: 1.5em;  margin-bottom: 24px;"><strong>We can all live in HARMONY!</strong></p>
</div>

For anyone getting started with git I always tell them about my own workflow. They'll learn about how you can use both GUIs and CLI, which is more than enough to get them going. If they have any questions down the road, I'll also already be familiar with their setup. :) I don't feel like I'm setting them up for failure by encouraging using a GUI but rather just showing them that there are many ways to get git done. Becoming comfortable and good at anything is a process and it should be treated as such.

I think this whole "CLI or bust" attitude is really silly. Writing a blog post about it ~~is definitely~~ may be even sillier...

P.S. I also can't stand bad commit messages so if you haven't already, go read [Chris' post][1] now!

[1]: http://chris.beams.io/posts/git-commit/
[2]: http://www.git-tower.com/
