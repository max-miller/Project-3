
# Max Miller and Georgiy Treyvus Module 3 Final Project


## Introduction

In this final project Max and Georgiy examined grade distribution data from the University of Wisconsin-Madison with an eye towards performing statistical tests to see if there were differences in the grade distributions between classes, subjects, or sections within a class.

## Final Project Summary

The UW-Madison grade distribution data was available on Kaggle and luckily required only a little bit of cleaning. Navigating between tables was made a little cumbersome given confusing/inconsistently named keys (there were course uuid's, course offering uuid's, section uuid's and schedule uuid's, and the different sorts of uuid's frequently had different names in different tables), but only one of the tables required substantial cleaning before it was usable.

Our goal was to create a framework that would allow for easy comparison of any two arbitrary classes or subjects/lists-of-classes. To that end, we wrote a series of functions that serialized the various processes required in any given comparison (a function to pull out grade distributions, a function to neaten them into easier to read/compare tables, a function to repeat the process over a series of classes and combine the tables into master summaries, etc.) and wrapped them all up in master functions that could take in simply two names and produce grade distribution visualizations and perform one of two sorts of tests.

The first was a simple t-test, using the proportion of the class receiving A's.

![alt text](https://github.com/max-miller/Project-1/blob/master/unadjusted%202.png?raw=true "Unadjusted house prices")
