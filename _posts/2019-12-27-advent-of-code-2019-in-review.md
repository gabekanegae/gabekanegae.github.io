---
layout: post
title: Advent of Code 2019 in Review
show-more-link: true
---

![]({{site.baseurl}}/images/aoc19.png)

At last, **[Advent of Code 2019](https://adventofcode.com/2019)** has come to an end! If you are new to it, it's an Advent calendar full of programming puzzles from December 1st all the way to Christmas, made by the amazing [Eric Wastl](http://was.tl/) every year since 2015.

This was my second year participating, but the first time actually completing all days before the end of the month! You can check my **Python 3** solutions on my **[GitHub](https://github.com/kanegaegabriel/advent-of-code-2019)**, and you can also **keep reading for more info and my comments on the event.**

<!--more--> ---

Other than being a collection of 50 very fun programming puzzles (each day has two parts!), Advent of Code is also a [competition](https://adventofcode.com/2019/leaderboard), but [only if you want it to be](https://www.reddit.com/r/adventofcode/comments/e2wjhf/tips_for_getting_on_the_advent_of_code_leaderboard/f90ksek/). And, way more importantly than that, it's a mission for you to save Christmas! This year, **"Santa has become stranded at the edge of the Solar System while delivering presents to other planets!"**, and so every puzzle is space-themed! Neat!

The 2019 edition of the event also had a brand new twist: usually, there are only a couple of puzzles that rely on the solution of a previous one. This time, almost half of them did! Starting at Day 2 and revisiting it every other day from Day 5 onwards, we were tasked with **building an Intcode computer**: in other words, **creating a Virtual Machine to run machine code from a very specific architecture description**, much similar to the [Synacor Challenge]({{site.baseurl}}/synacor-challenge-in-review/). I was introduced to low-level programming at my Computer Organization and Computer Architecture courses, and I've since loved doing these! Indeed, that was the highlight of this year for me, by far.

Of course, another big highlight was me actually managing to get some sweet leaderboard points! As puzzles unlock at midnight EST/UTC-5, aka 2AM my local time, it wasn't always feasible to be up and ready to compete. However, **I did get a total of 351 points, placing me at [196th on the Global Leaderboard](https://betaveros.github.io/extra-aoc-stats/)!** Although definitely far from the top 100, I'm more than excited about it.

All in all, **I had an amazing time with it and I highly recommend it to anyone looking to learn or practice programming and problem solving.** Now, to fill the void it left on me, I have to go back and complete all previous years...

### Notable Comments

**Day 1:** Leaderboard get! The first day has always been a very simple problem to introduce newcomers to the event format and answer submission, this year being a twist on "sum all numbers of a list". By hastily skimming through the problem statement and having my boilerplate code ready, I managed to finish Part 1 in just 46 seconds!

**Day 6:** Basic knowledge of trees required. Part 2 was a nice refresher on the classic Lowest Common Ancestor problem.

**Day 7:** This was when I noticed that I should probably modularize away my Intcode computer into its own class (eventually it evolved to being its own file). Great decision, by the way.

**Day 10:** Tough. Trigonometry galore. After a few hours of brainstorming, I had to resort to some tips from other people's solutions. It was only after [doodling a bunch and explaining it to other people](https://www.reddit.com/r/adventofcode/comments/e8m1z3/2019_day_10_solutions/fadhbo2/) that I fully understood what was going on. Much needed refresher on trig, though!

**Day 11:** Took me a bit to understand what I was actually supposed to do, but other than that it was a simple puzzle to exemplify the usage of the Intcode program as a [Black Box](https://en.wikipedia.org/wiki/Black_box). Instead, one could also [reverse-engineer it using Excel](https://www.reddit.com/r/adventofcode/comments/e9lxtv/2019_day_11_excel_cred_to_the_creators_of_aoc/).

**Day 12:** Another math-based puzzle, requiring some thinking to find the optimization trick for Part 2.

**Day 13:** So. Much. Fun! Definitely my favorite one of the year. Sadly, I missed Part 1's leaderboard by mistyping the answer and being hit by the one-minute timeout. Always copy and paste, people!

**Day 14:** Many [Factorio](https://store.steampowered.com/app/427520/Factorio/) vibes. This one threw me off a lot by having to take into account the leftovers, but I eventually found my way through.

**Day 16:** Arguably another math puzzle? Maybe half math and half programming. My original code for Part 1 took around two minutes, so Part 2 would finish computing in a couple thousand years! Of course, I had other things to do in that meantime so I ended up getting the trick for Part 2 from the subreddit. Reverse partial sum it was!

**Day 17:** Leaderboard get once again! For Part 2, I winged it and figured it was [faster to do it by hand](https://twitter.com/sophiebits/status/1206816590613733376) than figuring out a compressing algorithm on the fly. Apparently that was the better choice, as I got top 5! Of course, I later figured out the general solution for it.

**Day 18:** Pathfinding again, turned up to eleven. After hours of thinking and a couple tips later, my initial solution got me the right answer with a couple minutes of computing. Some [really fun optimization rounds](https://github.com/KanegaeGabriel/advent-of-code-2019/commits/master/day18.py) later, I brought my solution down to a reasonable runtime.

**Day 22:** The mother of all math puzzles for this year. Heavy usage of modular arithmetic and number theory. The only day in the event that social life did not allow me to finish it in under 24 hours of it being released. I had to go through so much theory and so many explanations and breakdowns to understand it all that I feel like I learned more with it than in my whole Discrete Mathematics course.

**Day 24:** Finally, a cellular automaton! I loved those last year, and at this point I was worried they wouldn't be making an appearance this time around. It did take me a while to wrap my head around Part 2's problem statement, but I guess that's just the nature of recursiveness!

**Day 25:** I've [waited so long for this](https://www.reddit.com/r/adventofcode/comments/e9zgse/2019_day_13_solutions/fan36t2/)! I spent more than a few minutes misunderstanding the "lighter" and "heavier" terms and swapping them in my mind, and as a result I kept looking for more items. After I finally got over that, I wrote a quick and dirty bruteforce, so the solution was reached half manually and half automated. Once again, of course I did code the general solution afterwards. Second favorite, mainly because of the [really fun rounds of runtime optimization](https://github.com/KanegaeGabriel/advent-of-code-2019/commits/e4b251cc0e31d521fce709ac162bb3c31a0cb455/day25.py).