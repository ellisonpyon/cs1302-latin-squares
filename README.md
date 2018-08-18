# CSCI 1302 - Latin Squares v2018.fa

**DUE SUN 2018-09-02 (Sep 2) @ 11:55 PM**

This repository contains the skeleton code for the Latin Squares project
assigned to the students in the Fall 2018 CSCI 1302 classes
at the University of Georgia. 

**Please read the entirety of this file before beginning your project.**

**Seriously. Read this entire file *before* starting.**

## Academic Honesty

You agree to the Academic Honesty policy as outlined in the course syllabus and
course website. In accordance with this notice, I must caution you **not** to 
fork this repository on GitHub if you have an account. Doing so will more than
likely make your copy of the project publicly visible. Please follow the 
instructions contained in the "How to Download the Project" section below in 
order to do your development on nike. Furthermore, you must adhere to the 
copyright notice and licensing information at the bottom of this document.

## Updates

Updates will be posted here.
If there has been an update and you have already cloned the project to Nike, 
then you can update your copy of the project using the <code>$ git pull</code>
command while inside of your project directory.

## Project Description

This first project is meant to ensure that you are able to apply and extend
your prerequisite knowledge as well as introduce you to developing and testing
a Java application in a Linux environment (i.e., the Nike development
server). Many aspects of this project may be new to you. You will be asked
to do things that you have never been given explicit directions for before.
This is just a part of software development. Sometimes you need to research
how to solve a problem in order to implement a solution. That being said,
the material included in this document should hopefully answer the majority
of your questions.

Your goal is to develop an interactive, text-based version of a game called 
**Latin Squares**. Before we describe the game, let us first discuss what
a *latin square* is.

### What is a Latin Square?

Let *n* denote some non-negative integer. Suppose you have *n*-many 
characters. Then, an *n-by-n* *latin square* is an arrangement of all the
characters in an *n-by-n* grid such that no orthogonal (row or column) 
contains the same character twice.

For example, consider *n = 2* and characters: `A`, `B`. There are two
possible latin squares that can be made with this information:

```
A B
B A
```

```
B A
A B
```

### What is the Latin Squares Game?

TODO

This project must be implemented in Java 8, and it must compile and run 
correctly on Nike using instructions that you will provide in an
<code>INSTRUCTIONS.md</code> file (more on that later).

## Project Requirements & Grading

### Functional Requirements

TODO

### Non-Functional Requirements

TODO

## Suggestions

TODO

## How to Download the Project

On Nike, execute the following terminal command in order to download the project
files into sub-directory within your present working directory:

```
$ git clone https://github.com/cs1302uga/cs1302-latin-squares.git
```

This should create a directory called <code>cs1302-latin-squares</code> in
your present working directory that contains the project files.

If any updates to the project files are announced by your instructor, you can
merge those changes into your copy by changing into your project's directory
on Nike and issuing the following terminal command:

```
$ git pull
```

If you have any problems with any of these procedures, then please contact
your instructor via Piazza. 

## Submission Instructions

You will still be submitting your project via Nike. Make sure your project files
are on <code>nike.cs.uga.edu</code>. Change into the parent directory of your
project directory. If you've followed the
instructions provided in this document, then the name of your project directory
is likely <code>cs1302-latin-squares</code>. While in your project parent
directory, execute the following command: 

```
$ submit cs1302-latin-squares cs1302a
```

It is also a good idea to email a copy to yourself. To do this, simply execute 
the following command, replacing `your@email` with your actual email address:

```
$ tar zcvf cs1302-latin-squares.tar.gz cs1302-latin-squares
$ mutt -s "[cs1302] cs1302-latin-squares" -a cs1302-latin-squares.tar.gz -- your@email.com < /dev/null
```

If you have any problems submitting your project then please make a private Piazza
post to "Instructors" as soon as possible. 

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>

