---
layout: post
title: "Slick Carousel Operational!"
description: ""
category: 
tags: [meta]
---
{% include JB/setup %}

Alyce has mentioned how great it'd be to add a photo carousel to my blog, especially for the photo-heavy posts. I always agreed, but really never put in the time to get one in. **Until today!** After trying many alternatives, I got Ken Wheeler's [slick][1] integrated. From start to finish this endeavor took a while so I'm hoping Wheeler's claim that slick is **"the last carousel you'll ever need"** holds to be very true.

<p style="margin-bottom: 8px;">Some reflection on the past three hours:</p>

* [Jekyll][3] has made blogging a breeze, but my lack of command over how it generates my blog made this a somewhat frustrating exercise in trial-and-error.
* CSS files are terrifying!
* I thought [GitHub Pages][4] (where my blog is hosted) blocked all scripting. Fortunately, it allows jQuery and Javascript!  
* The [Firebug][2] extension is pretty great. It helped me figure out what was going wrong as I was attempting to integrate the various libraries.

And now... **The carousel in action!**

<div class="featured" style="max-width: 600px; margin-left: auto; margin-right: auto;">
     <div id="5cm"><img src="/assets/images/posts/2013-12-05/anime-5cm.jpg"/></div>
     <div id="drrr"><img src="/assets/images/posts/2013-12-05/anime-drrr.jpg"/></div>
     <div id="gc"><img src="/assets/images/posts/2013-12-05/anime-gc.jpg"/></div>
     <div id="xamd"><img src="/assets/images/posts/2013-12-05/anime-xamd.jpg"/></div>
</div>

<div id="5cm-text">
This is from the movie 5 Centimeters per Second!
</div>

<div id="drrr-text" style="display: none;">
I'm super pumped for season 2 of Durarara!
</div>

<div id="gc-text" style="display: none;">
If you're thinking of watching Guilty Crown, just watch Code Geass instead.
</div>

<div id="xamd-text" style="display: none;">
I really never got into Xamd...
</div>

<hr class="separator"/>

Pretty slick, huh? If you're in the market for a carousel, check out [slick][1] today. If you're feeling particularly generous, give [Ken Wheeler][5] a follow on Twitter. He's earned it in my book.

<script type="text/javascript">
function updateVisibleText(slideId) {
    document.getElementById('5cm'.concat('-text')).style.display = ('5cm'.localeCompare(slideId) == 0 ? 'block' : 'none')
    document.getElementById('drrr'.concat('-text')).style.display = ('drrr'.localeCompare(slideId) == 0 ? 'block' : 'none')
    document.getElementById('gc'.concat('-text')).style.display = ('gc'.localeCompare(slideId) == 0 ? 'block' : 'none')
    document.getElementById('xamd'.concat('-text')).style.display = ('xamd'.localeCompare(slideId) == 0 ? 'block' : 'none')
}

$(document).ready(function(){
	$('.featured').slick({
		infinite: true,
		fade: true,
		dots: true,
		onAfterChange: function(slide, index){
			var slideId = $(slide.$slides.get(index)).attr('id')

			updateVisibleText(slideId)
		}
	});
});
</script>

[1]: https://kenwheeler.github.io/slick/
[2]: https://getfirebug.com/
[3]: http://jekyllrb.com/
[4]: https://pages.github.com/
[5]: https://twitter.com/ken_wheeler