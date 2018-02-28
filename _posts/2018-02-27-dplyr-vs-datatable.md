---
layout: post
title: dplyr vs. data.table
---

I have now used both `dplyr` and `data.table` for some time.  Both packages provide an excellent toolkit to wrangle and clean data, so it may help to discuss when to use which.

# dplyr

`dplyr` is a part of RStudio's [`tidyverse`](https://www.tidyverse.org).  Accordingly, it shares the philosophy of readable code: it leverages such simple yet expressive verbs as "mutate" and "summarize" to make more clear what is being done at each step of data transformation.  Hence, `dplyr` is well-suited when readable code is particularly important.  This is usually the case for actual analysis steps, where even the cleaned data need to be transposed, split, summarized, and so on to get a certain desired result.  For instance, it rarely happens that we can simply use the cleaned data for our modeling; we need to further transform it to suit the particular input requirements of the model being used.  My experience tells that data transformation of this sort is likely more subtle and possibly more complicated as it is done for a very specific aim.  Hence, clarity is very important for not only reviewers of the analysis but also for the analyst himself (Do you recall the last time you got frustrated at undecipherable code only to realize that it was you who wrote that monster?).  `dplyr` well serves this need for readability as its very design helps (or even *pushes*) the programmer to be more clear on what he is doing.

# data.table

As I highly value reproducible research, I use `dplyr` in my analysis whenever I can.  However, `dplyr`'s clarity and expressiveness come with costs too: it is quite slow in working with larger data.  Don't get me wrong -- `dplyr`'s performance is excellent for most analysis tasks.  It is when you try to summarize or transpose a data set with hundreds of millions of rows (e.g., summarizing a decade of entire student data from Chicago Public Schools) that `dplyr`'s performance starts to become an issue.

This is where [`data.table`](https://github.com/Rdatatable/data.table/wiki) comes to rescue.  `data.table` is implemented such that the performance gets a priority: although its syntax is not as intuitive or easy to understand as `dplyr`'s, `data.table` is very, very fast in wrangling data.  Chances are you will not notice the difference when you are working with fair-sized data, but once you start working on larger data (> 1GB) you will come to thank Matt Dowle, a guy behind this amazing workhorse.

My experience tells that processes involving data this large do and should occur as part of a separate data "engineering" step rather than the analysis itself.  In other words, we should have these processes in a script dedicated to data wrangling prior to analysis; this script will then produce streamlined data that can be used in relevant analyses without further heavy wrangling.  Personally, I always choose `data.table` over `dplyr` to write these data wrangling scripts because `data.table` allows for scalability if such needs arise.

Finally, some words on readability in `data.table`: although it is true that `data.table`'s syntax is not as clear or intuitive as `dplyr`'s, this does not mean that we should give up on readable code -- there are ways we can do better.  One such practice is to use the pipe operator (`%>%`) to better structure and comment our code in `data.table`.  Consider the following code snippet:

```r
mtcars[, mpg_per_wt := mpg / wt]
mtcars[, hp_per_wt := hp / wt]
desired_summary <- mtcars[gear >= 4, .(n_obs = .N, avg_mpg = mean(mpg), avg_hp_per_wt = mean(hp_per_wt)), by = cyl]
```

As shown, `data.table`'s syntax induces many discrete one-line commands, some of which can be quite long and complicated, and we can see how easily the code can get unwieldy.  The pipe operator (`%>%`) can help to better organize and clarify the code:

```r
desired_summary <- copy(mtcars) %>%
  # Create variables of interest
  .[, hp_per_wt := hp / wt] %>%
  .[, mpg_per_wt := mpg / wt] %>%
  # Only consider observations of interest
  .[gear >= 4,] %>%
  # Summarize data
  .[,
    .(n_obs = .N,
      avg_mpg_per_wt = mean(mpg_per_wt),
      avg_hp_per_wt = mean(hp_per_wt)),
    by = cyl]
```

The code is now better organized such that each logical step is visually distinct yet in an *organic* manner: we can see how these steps work together to achieve the common data wrangling goal.  True, we still lack such expressive function calls as "select" and "mutate", but this new shape of the code allows us to better comment what happens (and why it happens) in each step.  This way, we can considerably increase the readability and hence reproducibility of code written in `data.table`.
