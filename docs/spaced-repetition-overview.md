---
title: "Spaced Repetition Overview"
---

# Spaced Repetition Overview

These notes summarize the contents of the following post [Spaced Repetition: A Three Day Journey from Novice to Expert](https://github.com/open-spaced-repetition/fsrs4anki/wiki/Spaced-Repetition-Algorithm:-A-Three%E2%80%90Day-Journey-from-Novice-to-Expert)
$x^2 + 3x - 4$

Spaced repetition tries to estimate and predict:

1. how much knowledge we forget
2. how quickly knoledge is forgotten
3. the optimal schedule for reviewing information to optimize retention

Empirical algorithms and empirical models have been developed to understand
how humans deal with memory

## Imperical Methods

The forgetting curve models how memory is retained. The decay looks like
the curve \\( e^(1 \over x^0.5) \\)\_. Initially there is a steep decline in retention
rate and then it increases rapidly.

In absence of active review, memory decay is rapid and slows down over time.
Periodic review of materials flattens the forgetting curve. After each review,
the interval corresponding to a certain level of retention increases. Shorter
intervals are better suited for unfamiliar materials and longer intervals are
suited for more familiar materials.

The effectiveness of the Spaced repetition algorithm is explored in the papers:

- [Rea & Modigliani 1985, The effect of expanded versus massed practice on the retention of multiplication facts and spelling lists](https://gwern.net/doc/psychology/spaced-repetition/1985-rea.pdf)

- [Donovan & Radosevich 1999, A meta-analytic review of the distribution of practice effect: Now you see it, now you don’t](https://gwern.net/doc/psychology/spaced-repetition/1999-donovan.pdf)

The above papers demonstrated that testing immediately folowing training showed
superior performance and spaced practice is significantly superior to massed
practice in terms of task performance. [[#imperical-methods]]

Spaced repetition software automates the tracking of memory states and
efficient scheduling of reviews. Determining the optimal "short" intervals for
unfamiliar materials and the "long" intervals for familiar materials is
a critical component of sapced repetition software.

### SM-0

Piotr Woźniak, a young college student in 1985, was struggling to memorize vocabulary words.
He kept careful track of when he reviwed words and how many he forgot. Based on this
captured data he wanted to find the longest possible time between reviews with a 95% retention
rate.

He used the following experiment to determine his optimal review schedule:

1. Initial Learning: memorize all the words. Eliminate correct word-pairs and keep reviewing
   failing word-pairs until all answers are correct.
1. Initial review: one-day intervals were employed for the first review. The Stages were labeled answers A, B and C:
   - _Stage A_ five pages of notes were reviewed at 2, 4, 6, 8, and 10 days. The forgetting
     rate were 1% at 8-days and 17% at 10 days. He determined that 7-day interval was
     optimal for the second review.
   - _Stage B_ A new set of five pages was reviewed after 1 day for the first
     time and after 7 days for the second time. The third review had intervals
     of 6, 8, 11, 13, and 16 days. The 16-day retention rate was 1% and was
     selected for the 3rd review.
   - _Stage C_ another fresh set of five pages was reviewed at 1, 7, and
     16-day intervals. For the Fourth review, he selected intervals of 20, 24,
     28, 33, and 38 days. The forgetting rates were 0% at 38 days. He chose a 35
     day interval for the fourth review.

The formal SM-0 algorithm, where I(_i_) denotes the interval employed for the ith review.

- I(1) = 1 days
- I(2) = 7 days
- I(3) = 16 days
- I(4) = 35 days
- for i > 4: I(i) = I(i-1) \* 2
- Words forgitten in tehe first four reviews were moved to a new page and
  cycled into repetition along with new materials.

Goal of SM-0 algorithm was to extend the review interval as long as possible
while minimizing the rate of memory decay. It used page of notes as the unit of
review, which makes tracking of memory retention at a granular level untenable.

Based on SM-0 algorithm, Wozniak derived two key conclusions:

1. Over time, the total amount of knowledge increases rather than decreases
2. In the long run, the knowledge acquisition rate remains relatively constant

## SM-2

- [] TODO:
