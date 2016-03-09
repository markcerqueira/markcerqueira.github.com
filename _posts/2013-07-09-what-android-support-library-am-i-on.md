---
layout: post
title: "What Android Library Am I On?"
description: ""
category: 
tags: [android]
---
{% include JB/setup %}

<style type="text/css">
	table, td, th {
		border: 2px solid gray;
		margin: 0 auto;
		padding: 6px 12px 6px 12px;
	}
	th {
		font-size: 0.75em;
		text-align: center;
		background-color: #333333;
		color: white;
	}
	td {
		text-align: center;
		font-size: 0.66em;
	}
</style>

Google maintains some handy support packages that allow older versions of Android to use otherwise unavailable APIs. It's a win-win for most - developers can support older devices more easily, Google looks great because they are making developers' lives easier, and Android users aren't forced to upgrade their phones to have access to a large selection of apps. There are losers, and one of them is me: the developer who looks at the [revision history][1] for the support library and realizes there may be relevant fixes in newer revisions. I need to figure out which revision I'm on now, so I look in the **libs** folder, see the support library **android-support-v4.jar** and ask myself, "What is the version of this support library?" 

<!--break-->

The filename of the JAR itself yields nothing; v4 simply refers to the minimum API level supported by that particular library. The manifest file of the JAR disappointingly does not have any information. Fine; let's grab the MD5 checksum. But what to do with this checksum? Google's Android documentation does not provide checksums for the different revisions of the library. Launching the Android SDK Manager, I find revision 13 installed in my Android SDK bundle, but the checksum of that revision does not match the checksum of the mysterious library currently sitting in my project.

Okay, let's go through all the previous versions and get checksums for them. But wait... I can't downgrade my support library via the Android SDK Manager! The revision history page also doesn't have any download links for older revisions. Although Google has done a poor job of putting download links in a visible place, it has fortunately done a good job of maintaining their revisions in an orderly manner. Visit [this URL][2], replacing the rXX with the version of the support package you want (e.g. r04 through r13 as of July 2013). After grabbing all available revisions, I created a table filled with the support libraries' MD5 checksums:

<div>
<table style="margin-bottom: 1em;">
<tr><th>&nbsp;Revision&nbsp;</th><th>v4 library MD5</th><th>v7 library MD5</th><th>v13 library MD5</th></tr>
<tr><td>4</td><td>86dfb3c6ac2db479ff396906fe4ee1be</td><td>-</td><td>7aa30cf7bb854e98670e3b5ad9b15f87</td></tr>
<tr><td>5</td><td>6ed7cfa457967cb8d5924c93b96847e7</td><td>-</td><td>4e4868c990252855cc14b8ac83656172</td></tr>
<tr><td>6</td><td>bcf017dfe2243c8d72b4b2aa40101040</td><td>-</td><td>43715e49c8c89f1c844cbb3cc1a4638d</td></tr>
<tr><td>7</td><td>c6c2148762c614d3bad120ca01491e34</td><td>0a796c18e64c30b0cb64b1802dcb022b</td><td>abdf04d97d538c7425e0314b21767e87</td></tr>
<tr><td>8</td><td>776555f10c632cd4f2790b6bbd2465bf</td><td>c278ba81b8a7ca1a56901411959eee1a</td><td>522c1d3d8fbe42d0ea7872b619961492</td></tr>
<tr><td>9</td><td>d0107ad5a43839ecdc08fbcf783bdb4f</td><td>56d2becf9ba0ce495d3dddc6e38e1232</td><td>1c68c31497a77af15797882f2daac9cf</td></tr>
<tr><td>10</td><td>7c357558b1ef5cd16f1d312fe87c38a0</td><td>102ca4ff9de8c0294a42987dbee92e58</td><td>4adc2acf706396225495c43bb60cbb78</td></tr>
<tr><td>11</td><td>7b5efe58fd28cbc7fa8f9e88ab9c7d65</td><td>64a88c9b9cd7d755498984c5034a81c9</td><td>2a7dd0b32bef6da952f9adea5dbab998</td></tr>
<tr><td>12</td><td>9974894df6e8ba95bb27f5e85e2cdfb5</td><td>a94112d8249a193143ec19d35f11552a</td><td>98b359e98f5c7407432877c88d1cd2f3</td></tr>
<tr><td>13</td><td>5dce8843261486180715e459d953885d</td><td>63dcac01d302b2a2b6479dfb4496b070</td><td>2aceba35370fa10721e8af40decb1955</td></tr>
</table>
</div>

Turns out, we were using revision 6 of the v4 support library. Between this and the latest version, new functionality was added and "many [Fragment] bugs" were fixed. We use Fragments in a few places, so we're pushing ahead with the upgrade. Figuring out what version you are using shouldn't be this difficult. Some might argue that developers should do book-keeping on the libraries they are using. But if you're dedicating resources to putting out and iterating on packages used by many, you could at least invest some time to attach relevant metadata to those packages. In this particular case, involving a JAR file, setting up a manifest file with a bundle version is both easy for those creating the packages and helpful for those using the packages. In the meantime, the JAR file has been renamed to **android-support-v4-rev13.jar**.

[1]: https://developer.android.com/tools/extras/support-library.html 
[2]: https://dl-ssl.google.com/android/repository/support_rXX.zip
