---
layout: post
title: "Let's Crunch Intelligence Squared"
description: ""
category: 
tags: [random]
---

**Intelligence Squared US** is a cool debate series I listen to on NPR every so often. Debate topics include "Death Is Not Final" and "Russia Is A Marginal Power." Debates feature two sides: one for the motion and one against the motion.

The audience is polled on their opinion before and after the debate; they can vote for the motion, against the motion, or be undecided. The winner of the debate is whichever side has the largest increase in percentage points. So if the split is 70/20/10 (for / against / undecided) before the debate and 72/25/3 after the debate, the against side wins because they increased by 5 points, whereas the for side only gained 2 points. Winning usually boils down to whoever can sway the most undecided voters. 

The other day a friend observed that, "I've listened to dozens of episodes, and not once has the number of unsure audience members increased." While it seems intuitive to me that fewer people would be undecided after hearing an extended discussion on a topic, I can also see where his confusion comes from. If you hear people present compelling arguments for two sides of a topic, it should have the power to convince some that their former positions may be incorrect -- maybe even sway some to decide that they are now undecided. I suppose people dislike NOT having an opinion.

A friend of disappointed friend, who also happens to be a data scientist, then crunched some numbers and wrote a [spectacular write-up][1] with some pretty interesting finds.

Said data scientist inputted all data into Google Spreadsheets before crunching some conclusions out, but **I'm a JSON-type-of-guy**. Enter [intelligence-json][2]: a repository containing all results of Intelligence Squared US debates in JSON format. Also enter [intelligence-analyzer][3]: a skeleton project that parses all this data into POJOs using Jackson, my favorite JSON parsing library. 

Crunch away friends! 

[1]: http://havingneweyes.com/2014/07/27/intelligence-squared-debates-voting-data/
[2]: https://github.com/markcerqueira/intelligence-json
[3]: https://github.com/markcerqueira/intelligence-analyzer
