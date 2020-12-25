---
layout: post
title: Advent of Code 2020 in Review
show-more-link: true
---

![]({{site.baseurl}}/images/advent-of-code-2020-in-review/header.png)

Happy Holidays! Here I am at the end of another year, having just finished **[Advent of Code 2020](https://adventofcode.com/2020)**! If you are new to it, it's an Advent calendar full of programming puzzles from December 1st all the way to Christmas, made by the amazing [Eric Wastl](http://was.tl/) every year since 2015.

I've been participating since 2018 - [here's my comments on last year's edition]({{site.baseurl}}/advent-of-code-2019-in-review/) -, and this time I actually tried my best to get some sweet leaderboard points! You can check my **Python 3** solutions on my **[GitHub](https://github.com/kanegaegabriel/advent-of-code-2020)**, and you can also **keep reading for more info and my comments on the event.**

<!--more--> ---

Once again, the event consists of 50 great programming puzzles, which also award [internet points and clout](https://adventofcode.com/2020/leaderboard) for the first 100 people who complete each of them the fastest - again, as a reminder, [it's only a competition if you want it to be](https://www.reddit.com/r/adventofcode/comments/e2wjhf/tips_for_getting_on_the_advent_of_code_leaderboard/f90ksek/). **This year's storyline was about you, the Christmas savior for 5 years in a row, finally taking a break, vacationing on a chill tropical island.**

As puzzles release at midnight EST/UTC-5, or 2AM my time, it's often hard to be awake and ready to compete for leaderboard points. However, this year I did manage to be present for all puzzle release times, completing all of them in the following minutes/hours - which I consider a big personal accomplishment by itself. More than that, **I also scored a total of 389 points over 6 leaderboard spots, placing me at 167th on the Global Leaderboard**, topping last year's score of 351 points at 196th place! Outside of the strict top 100, I managed to complete 25 of the puzzles - exactly half of them - in the top 500! It's fair to note that **this year had [way more people participating](https://twitter.com/ericwastl/status/1333876936024743936), so the leaderboard competition was far fiercer!** If, in the future, you do feel like going down this route, I very much recommend [betaveros', this year's #1, blog post on How to Leaderboard](https://blog.vero.site/post/advent-leaderboard).

With all of those personal achievements in mind, I figured I would play a bit with some [Matplotlib](https://matplotlib.org/), and plotted a graph of my completion times and leaderboard positions! **Top 100s are marked in red, and top 500s are in black.** [Here's the code that I wrote to generate it.](https://github.com/kanegaegabriel/advent-of-code-2020/blob/main/time-plots/time-plots.ipynb)

![]({{site.baseurl}}/images/advent-of-code-2020-in-review/time-plot.png)

Finally, **a big thank you to all of the friends I managed to convince - or coerce - to join me on this month-long adventure**, and a special shout out for those who were there with me over Discord every day at 2AM! Sharing strategies, solutions, celebrating leaderboard positions and just being together for some coding fun early in the morning was my highlight of this year's event.

### Notable Comments

**[Day 1](https://adventofcode.com/2020/day/1):** Apparently there were just too many people playing and [the server decided to go for a walk](https://www.reddit.com/r/adventofcode/comments/k4ejjz/2020_day_1_unlock_crash_postmortem/). Anyway, the first day was a small twist on the classic [Two Sum](https://leetcode.com/problems/two-sum/) and [3Sum](https://leetcode.com/problems/3sum/) problems.

**[Day 6](https://adventofcode.com/2020/day/6):** Out of all the days in which rookie mistakes cost me leaderboard spots, this one was the most impressive: I managed to completely misread the prompt and solved Part 2 before Part 1. Hooray?

**[Day 7](https://adventofcode.com/2020/day/7):** Recursion is fun! Great basic intro/refresher on the topic.

**[Day 10](https://adventofcode.com/2020/day/10):** Dynamic programming is... eh. Not that much well versed in it, so Part 2 took me a while. Shame on me, though, as this day's puzzle was a simple variation of the classic [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) problem.

**[Day 12](https://adventofcode.com/2020/day/12):** It took me so, so long to figure out the simple linear algebra to rotate the points around the origin. Lesson learned, definitely won't forget that any time soon!

**[Day 13](https://adventofcode.com/2020/day/13):** Although very far from [the nightmare that was last year's Day 22](https://adventofcode.com/2019/day/22), this was 2020's Great Discrete Mathematics day. I quickly realized it had to be related to [modular inverses](https://en.wikipedia.org/wiki/Modular_multiplicative_inverse) and that something was up with all bus IDs being prime, but connecting the dots to arrive on the [Chinese Remainder Theorem](https://brilliant.org/wiki/chinese-remainder-theorem/) took an hour and change. Well needed refresher on Discrete Maths, once again!

**[Day 18](https://adventofcode.com/2020/day/18):** Simple and direct implementation of the [Shunting-yard algorithm](https://en.wikipedia.org/wiki/Shunting-yard_algorithm), which I had it implemented and ready to go from my first year's A&DS course at uni, but I totally did not realize that until after I solved it by [overloading the default integer operations](https://realpython.com/operator-function-overloading/#overloading-built-in-operators).

**[Day 19](https://adventofcode.com/2020/day/19):** All those Formal Languages classes came through! Great twist on Part 2 as well, making it a [CFG](https://en.wikipedia.org/wiki/Context-free_grammar) and requiring an actual understanding of the rules. However, for both parts I considered that building the regular expression from the language rules was challenging enough so I left it at that, and broke my sacred rule of avoiding RegEx on AoC at all costs. Will definitely come back later and implement the actual language parsing.

**[Day 20](https://adventofcode.com/2020/day/20):** Oof. This one threw my sleep schedule completely over the window, as I spent 4 hours just to complete it plus another 3 to tidy up my code, and by that point it was already 9AM. But oh boy was it fun. Without a doubt my favorite of this year, implementing a jigsaw solver has been on my bucket list for years now, and the brain-teasing while doing it was simply amazing. I do want to shine some light on [paiv's interactive version](https://paiv.github.io/aoc2020/day/20/) as a fantastic tool to play around with, understand the puzzle itself or explain it to other people.

**[Day 23](https://adventofcode.com/2020/day/23):** At first I got spooked at the thought of it being another Discrete Maths one. After being stumped for a good hour or so, I had to grab a tip from the [Advent of Code's subreddit](https://www.reddit.com/r/adventofcode/), and learned about the idea of combining a linked list and a hash map to fulfill the puzzle's requirement of accessing arbitrary nodes in constant time. Cool!

**[Day 24](https://adventofcode.com/2020/day/24):** A fun twist on cellular automata, this time using a hexagonal grid. Luckily, I quickly realized I had done something like this before, on [Day 11 of AoC 2017](https://adventofcode.com/2017/day/11)! [Here's an amazing blog post from Red Blob Games on hexagonal grids](https://www.redblobgames.com/grids/hexagons/), which I used as a basis for both 2017's edition and this one. If that piqued your interest, do check out their other posts, as they are all full of mindblowing insights!

**[Day 25](https://adventofcode.com/2020/day/25):** Another direct implementation, this time of brute-forcing a [Diffie-Hellman key exchange](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange). My RSA classes definitely helped!