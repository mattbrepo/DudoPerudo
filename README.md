# DudoPerudo
Analysis for Dudo/Perudo game.

**Language: Python**

**Start: 2024**

## Why
I recently played [Dudo](https://en.wikipedia.org/wiki/Dudo) (aka Perudo) for the first time. I wanted to calculate probability of the numeric claim, e.g. when a player says "three 6s", and the _paco_ (Dudo wild card) claim, e.g. when a player says "two pacos". The final goal is to identify the best strategy to call the "doubt".

The probability for both claims can be calculated using the binomial formula:

$$P(k; n, p) = \binom{n}{k} \cdot p^k \cdot (1-p)^{n-k}$$

The probability formula for the numeric claim is:

$$P(\text{at least n of m}) = \sum_{k=n}^m \binom{m}{k} \cdot (\frac{1}{3})^k \cdot (1 - \frac{1}{3})^{m-k}$$

where n is the number claimed, m is the number of dice in the game and 1/3 comes out of 2 / 6 (1 for the numeric value and 1 for the paco).

The probability formula for the paco claim is:

$$P(\text{at least n of m}) = \sum_{k=n}^m \binom{m}{k} \cdot (\frac{1}{6})^k \cdot (1 - \frac{1}{6})^{m-k}$$

where n is the number of pacos claimed and m is the number of dice in the game.

Here is a bar plot showing the probability of numeric claims when there are 20 dice in the game:

![chart](/images/prob_plot.png)

The chart and the previous formulas do not consider the knowledge that a player has regarding their own dice. A correction is implemented in the Excel file for that.

## To do

**I implemented the formulas in Excel. In the future, I want to write a Python code to simulate the best strategy among players applying different probability thresholds to their "doubt".**
