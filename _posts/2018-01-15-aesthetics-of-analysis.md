---
layout: post
title: Aesthetics of Analysis
---

I regularly listen to ["Not So Standard Deviations"](http://nssdeviations.com), a data science podcast hosted by Roger Peng and  Parker.  In [Episode 38](http://nssdeviations.com/episode-38-banging-on-the-piano), Roger and Hilary discusses what makes an analysis "good", drawing interesting analogies between arts and data analysis and raising many important issues to be explored.

Based on their discussion, I have come up with my own list of elements that constitutes a "good" analysis.  In short, I believe a good analysis is *relevant*, *understandable*, *logical*, *reproducible*, and *concise*.

# 1. Relevant

Whether explicitly stated or not, any data analysis has a goal it serves.  For instance, many financial analyses are conducted to predict future behaviors of the stock market; pharmaceutical companies analyze data to decide whether a new drug is effective in disease treatment; and educational researchers analyze data to identify indicators of high school graduation, which can help school improvement efforts.  Even a seemingly carefree "exploratory" analysis, I believe, has an aim: to find interesting patterns in data, which will in turn help to identify and construct a productive goal to focus.

Now, a "good" analysis distinguishes itself by effectively meeting the goal it serves.  This, of course, requires precise understanding of the goal.  After all, how can one achieve his goal without knowing what the goal is?  Hence, any good analysis starts with a clear understanding of the goal it aims to achieve.  It should be noted that this is not necessarily an easy thing to do, especially when the goal comes from external sources like a client.  For instance, I have personally experienced occasions where the client complains that our analysis reports do not really answer their questions.  Further discussion often reveals the gap between the client's actual needs and our understanding of them.  In a case like this, an analysis can be excellent in meeting a certain goal yet fail to meet the relevant "correct" one.

Given a relevant (i.e. correct) and clear goal to achieve, an analysis can then be evaluated on how well and effectively it meets this goal.

# 2. Understandable

It may sound silly to maintain that an analysis should be comprehensible.  Yet, too many times one person's analysis is indecipherable to another.  Worse, the same person often cannot figure out what's going on in an analysis he ran a year ago.  Hence, it is highly significant that analysts organize and document their analyses in as much clear a way as possible.  Of course, this is not easy (recognizing personal assumptions/choices of the moment and stating them explicitly is quite a challenge) and time consuming (we all often work under tight schedules).  However, I believe that the long-term benefits eventually outweigh these immediate costs.

# 3. Logical

A good analysis does not only make sense but is also logically convincing.

# 4. Reproducible

It is possible and, in fact, does happen quite often that the client (or peer reviewer, in an academic setting) takes a particular interest or issue with a certain part of the analysis and requests it be re-checked or re-run in a different way.  This is where the issue of reproducibility takes in.  If the analysis has been set up and conducted in a reproducible fashion, then it should not be difficult to meet requests of this sort.  If the analysis has been performed "on the fly", on the other hand, it will very likely take a lot of time and pain to go back, gather, and align different pieces of the analysis to get the exactly same result as before.  Note that the "client" here can be the analyst himself: the analyst at some point may need to revisit or expand upon his previous analysis, in which case the same issues will arise as above.

Since data analysis is inherently iterative process, any good analysis should be reproducible at any point of the time.

# 5. Concise

With other things being equal, the more concise, the better.  This law of parsimony (also referred to as *Occam's razor*) has been applied to evaluate scientific theories across diverse fields.  So why not data analysis too?
