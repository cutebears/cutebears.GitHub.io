---
layout: post
title: 这是一篇博客文章模板
date: 2015-3-02
categories: blog
tags: [标签一,标签二]
description: 文章金句。
---

This assignment is inspired by a typical real-life scenario. Imagine you have been hired as a Data
Scientist by a major news organization. Your job is to analyse the news feed to determine the
topic of incoming news articles so they can be organized and distributed to your readers.
For this assignment, you will be given a collection of BBC news articles and also summaries
of the same articles. The articles have been manually labelled as one of five topics: business,
entertainment, politics, sport and tech. Important: Do not distribute these news articles
on the Internet, as this breaches BBC copyright.
You are expected to assess various supervised machine learning methods using a variety of features and settings to determine what methods work best for topic classification in this domain.
The assignment has two components: programming to produce a collection of models for topic
classification, and a report to evaluate the effectiveness of the models. The programming part
involves development of Python code for data preprocessing of articles and experimentation of
methods using NLP and machine learning toolkits. The report involves evaluating and comparing
the models using various metrics.
You will use the NLTK toolkit for basic language preprocessing, and scikit-learn for feature construction and evaluating the machine learning models. You will be given an example of how to use
NLTK and scikit-learn to define the machine learning methods (example.py), and an example of
how to plot metrics in a graph (plot.py).
Data and Methods
A training dataset is a .tsv (tab separated values) file containing a number of articles, with one
article per line, and linebreaks within articles removed. Each line of the .tsv file has three fields:
instance number, text and topic (business, entertainment, politics, sport, tech).
A test dataset is a .tsv file in the same format as the training dataset except that your code should
ignore the topic field. Training and test datasets can be drawn from supplied files articles.tsv
or summaries.tsv (see below).
For all models, consider an article to be a collection of words, where a word is a string of at
least two letters, numbers or the symbols #, @, , $ or %, delimited by a space, after removing
all other characters (two characters is the default minimum word length for CountVectorizer in
scikit-learn). URLs should be treated as a space, so delimit words. Note that deleting “junk”
characters may create longer words that were previously separated by those characters.
Use the supervised learning methods discussed in the lectures: Decision Trees (DT), Bernoulli
Naive Bayes (BNB) and Multinomial Naive Bayes (MNB). Do not code these methods: instead
use the implementations from scikit-learn. Read the scikit-learn documentation on Decision Trees1
and Naive Bayes,2 and the linked pages describing the parameters of the methods.
Look at example.py to see how to use CountVectorizer and train and test the machine learning
algorithms, including how to generate metrics for the models developed, and plot.py to see how
to plot these metrics on a graph for inclusion in your report.
The programming part of the assignment is to produce DT, BNB and MNB models and your own
model for topic classification in Python programs that can be called from the command line to train
and classify articles read from correctly formatted .tsv files. The report part of the assignment
is to analyse these models using a variety of parameters, preprocessing tools and scenarios.
Programming
You will submit four Python programs: (i) DT classifier.py, (ii) BNB classifier.py, (iii)
MNB classifier.py and (iv) my classifier.py. The first three of these are standard models as
defined below. The last is a model that you develop following experimentation with the data. Use
the given datasets (articles.tsv and summaries.tsv) containing 1000 labelled articles and their
summaries to develop and test the models, as described below.
These programs, when called from the command line with two file names as arguments, the
first a training dataset and the second a test dataset (i.e. not hard-coded as training.tsv
and test.tsv), should print (to standard output, not a hard-coded file output.txt), the instance number and topic produced by the classifier of each article in the test set when trained on
the training set (one per line with a space between the instance number and topic) – each topic
being the string “business”, “entertainment”, “politics”, “sport” or “tech”. For example:
python3 DT classifier.py training.tsv test.tsv > output.txt
should write to the file output.txt the instance number and topic of each article in test.tsv, as
determined by the Decision Tree classifier trained on training.tsv.
When reading in training and test datasets, make sure your code reads all the instances (some
Python readers use “excel” format, which uses double quotes as separators).
Standard Models
You will develop three standard models. For all models, make sure that scikit-learn does not
convert the text to lower case. For Decision Trees, use scikit-learn’s Decision Tree method with
criterion set to ’entropy’ and with random state=0. Scikit-learn’s Decision Tree method does not
implement pruning, rather you should ensure that Decision Tree construction stops when a node
covers fewer than 1% of the training set. Decision Trees are prone to fragmentation, so to avoid
overfitting and reduce computation time, for the Decision Tree models use as features only the
1000 most frequent words from the vocabulary, after preprocessing to remove “junk” characters
as described above. Write code to train and test a Decision Tree model in DT classifier.py.
For both BNB and MNB, use scikit-learn’s implementations, but use all of the words in the
vocabulary as features. Write two Pythons programs for training and testing Naive Bayes models,
one a BNB model and one an MNB model, in BNB classifier.py and MNB classifier.py.
Your Model
Develop your best model for topic classification by either varying the number and type of input
features for the learners, the parameters of the learners, and the training/test set split, or by using
another method from scikit-learn. Submit one program, my classifier.py, that trains and tests
a model in the same way as for the standard models. Conduct new experiments to analyse your
model and present results that justify your choice of this model in the report.Report
In the report, you will first evaluate the standard models, then present your own model. For
questions 1–4 below, consider two scenarios:
(1) with the full articles in articles.tsv for training and testing, and
(2) with the summaries in summaries.tsv for training and testing.
For evaluating all models, report the results of training on the first 800 instances in the dataset
(the “training set”) and testing on the remaining 200 instances (the “test set”), rather than using
the full datasets of 1000 instances for training – so the 1% stopping rule for Decision Trees is when
nodes cover less than 8 instances rather than 10.
Use the metrics (micro- and macro-accuracy, precision, recall and F1) and classification reports
from scikit-learn. Show the results in Python plots (do not take screenshots of sklearn classification
reports), and write a short response to each question below. The answer to each question should
be self contained. Your report should be at most 10 pages. Do not include appendices.
1. (3 marks) Develop Decision Tree models for training and testing: (a) with the 1% stopping
criterion (the standard model), and (b) without the 1% stopping criterion.
(i) Show all metrics on the test set for scenario 1 comparing the two models (a) and (b), and
explain any similarities and differences.
(ii) Show all metrics on the test set for scenario 2 comparing the two models (a) and (b), and
explain any similarities and differences.
(iii) Explain any differences in the results between scenarios 1 and 2.
2. (3 marks) Develop BNB and MNB models from the training set using: (a) the whole vocabulary
(standard models), and (b) the most frequent 1000 words from the vocabulary, as defined using
sklearn’s CountVectorizer, after preprocessing by removing “junk” characters.
(i) Show all metrics on the test set for scenario 1 comparing the corresponding models (a) and
(b), and explain any similarities and differences.
(ii) Show all metrics on the test set for scenario 2 comparing the corresponding models (a) and
(b), and explain any similarities and differences.
(iii) Explain any differences in the results between scenarios 1 and 2.
3. (3 marks) Evaluate the effect of preprocessing for the three standard models by comparing
models developed with: (a) only the preprocessing described above (standard models), and (b)
applying, in addition, Porter stemming using NLTK then English stop word removal using sklearn’s
CountVectorizer.
(i) Show all metrics on the test set for scenario 1 comparing the corresponding models (a) and
(b), and explain any similarities and differences.
(ii) Show all metrics on the test set for scenario 2 comparing the corresponding models (a) and
(b), and explain any similarities and differences.
(iii) Explain any differences in the results between scenarios 1 and 2.
4. (3 marks) Evaluate the effect of converting all letters to lower case for the three standard models
by comparing models with: (a) no conversion to lower case, and (b) all input text converted to
lower case.
(i) Show all metrics on the test set for scenario 1 comparing the corresponding models (a) and
(b), and explain any similarities and differences.
(ii) Show all metrics on the test set for scenario 2 comparing the corresponding models (a) and
(b), and explain any similarities and differences.
(iii) Explain any differences in the results between scenarios 1 and 2.5. (5 marks) Describe your chosen “best” method for topic classification. Give new experimental
results for your method trained on the training sets of 800 articles/summaries and tested on
the test sets of 200 articles/summaries. Explain how this experimental evaluation justifies your
choice of model, including settings and parameters, against a range of alternatives. Provide new
experiments and justifications: do not just refer to previous answers.
Submission
• Make sure your name and zid appears on each page of the report
• Submit all your files using a command such as (this includes Python code and report):
give cs9414 ass2 DT*.py BNB*.py MNB*.py my classifier.py report.pdf
• Your submission should include:
– Your .py files for the specified models and your model, plus any .py “helper” files
– A .pdf file containing your report
• When your files are submitted, a test will be done to ensure that one of your Python files
runs on the CSE machine (take note of any error messages printed out)
• When running your code on CSE machines:
– Set SKLEARN SITE JOBLIB=TRUE to avoid warning messages
– Do not download NLTK in your code: CSE machines have NLTK installed
• Check that your submission has been received using the command:
9414 classrun -check ass2
Assessment
Marks for this assignment are allocated as follows:
• Programming (auto-marked): 8 marks
• Report: 17 marks
Late penalty: 5 marks per day or part-day late off the mark obtainable for up to 3
(calendar) days after the due date.
Assessment Criteria
• Correctness: Assessed on standard input tests, using calls such as:
python3 DT classifier.py training.tsv test.tsv > output.txt
Each such test will give two files, a training dataset and a test dataset, which contain any
number of articles (one on each line) in the correct format. The training and test datasets
can have any names, not just training.tsv and test.tsv, so read the file names from
sys.argv. The output should be a sequence of lines (one line for each article) giving the
instance number and classified topic, separated by a space and with no extra spaces on each
line or extra newline characters following any newline character after the last classification.
There are 2 marks allocated for correctness of each of the three standard models.
For your own method, 2 marks are allocated for correctness of your methods on test sets of
articles that include unseen examples.• Report: Assessed on correctness and thoroughness of experimental analysis, clarity and
succinctness of explanations, and presentation quality.
There are 12 marks allocated to items 1–4 as above, and 5 marks for item 5. Of these 5
marks, 1 mark is for the description of your model, 2 marks are for new experimental analysis
of your model, and 2 marks are for the justification of your model using new analysis. In
general, if the presentation is of poor quality, at most 50% of the marks can be obtained.












