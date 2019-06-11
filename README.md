
# Max Miller and Georgiy Treyvus Module 3 Final Project


## Introduction

In this final project Max and Georgiy examined grade distribution data from the University of Wisconsin-Madison with an eye towards performing statistical tests to see if there were differences in the grade distributions between classes, subjects, or sections within a class.

## Final Project Summary

The UW-Madison grade distribution data was available on Kaggle and luckily required only a little bit of cleaning. Navigating between tables was made a little cumbersome given confusing/inconsistently named keys (there were course uuid's, course offering uuid's, section uuid's and schedule uuid's, and the different sorts of uuid's frequently had different names in different tables), but only one of the tables required substantial cleaning before it was usable.

Our goal was to create a framework that would allow for easy comparison of any two arbitrary classes or subjects/lists-of-classes. To that end, we wrote a series of functions that serialized the various processes required in any given comparison (a function to pull out grade distributions, a function to neaten them into easier to read/compare tables, a function to repeat the process over a series of classes and combine the tables into master summaries, etc.) and wrapped them all up in master functions that could take in simply two names and produce grade distribution visualizations and perform one of two sorts of tests.

The first was a simple t-test, using the proportion of the class receiving A's. For instance, in the below example, we have quickly compiled lists of classes in the chemistry and physics departments, and run them through our function that creates master grade distributions, graphs them and runs a t-test.

![Chemistry appears to grade harder than physics](https://raw.githubusercontent.com/max-miller/Project-3/master/chem%20phys%20compare.png)

There's a more than 8% difference in the number of A's granted between the two departments, and given the size of these samples (dozens of classes, each with dozens of sections over the 10 year period), our t-test thinks the chance of seeing this sort of difference due to chance is vanishingly small.

We built all our tests to be two-sided - looking to see if the sample means were different rather than if one was greater than the other. The goal was to build a structure that doesn't assume anything about the classes or subjects being compared. You can simply plug in any two classes, and the order you plug them in shouldn't matter.

We also used the Mann-Whitney U Test to compare overall distributions. This is a rank-sum test that allows you to compare overall distributions of variables that are discrete and categorial, but have rank. In this case, grades were encoded as A's, B's, C's, etc, which are discrete categories (unlike number grades), but which luckily can be ranked. The Mann-Whitney test compares the overall distributions by asking whether a randomly selected item from one distribution is likely to outrank a randomly selected item from the other.
