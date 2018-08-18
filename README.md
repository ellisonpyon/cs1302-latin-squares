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
**Latin Squares**, which is based on a mathematical concept of the same name.
The next two subsections describe the general mathematical concept and the
game that is based on it, respectively.

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

Here is another example. Consider *n = 3* and characters: `x`, `y`, `z`. 
There are actually twelve possible latin squares that can be made with 
this information, two of which are presented below:

```
x y z
z x y
y z x
```

```
x y z
y z x
z x y
```

For good measure, here is one more example. Consider *n = 4* and 
characters: `@`, `#`, `$`, `%`. There are 576 possible latin squares 
that can be made with this information! Here are two them:

```
@ # $ %
# @ % $
$ % @ #
% $ # @
```

```
@ # $ %
$ % @ #
# @ % $
% $ # @
```

Computer programs can store latin squares in memory in various
different ways, but a two-dimensional array of characters is
a common approach. The way that a latin square is stored should
be irrespective of how it is displayed to users. For example, 
each of the following outputs could use the exact same array
as storage since the formatting for the index values and 
surrounding characters can be printed as the contents of
the array are processed (i.e., while the array is looped 
through):

```
  0 1 2
0 x y z
1 z x y
2 y z x
```

```
    0   1   2
0 | x | y | z
1 | y | z | x
2 | z | x | y
```

### What is the Latin Squares Game?

For the purposes of this assignment, the **Latin Squares** game is 
defined as an interactive, text-based game where users attempt to
complete a latin square. In the next couple of paragraphs, we will
discuss how the game is displayed to users as well as how users 
interact with the game. Later sections provide more detail about
requirements required to game's implementation. Although this is
mentioned later in this document, it is important to note here: all
game output should match the descriptions provided in this document
as closely as possible. 

If a user wishes to play a game of Latin Squares, they should be
able to by typing in the following command at the shell prompt:
```
$ java -cp bin cs1302.game.LatinSquares config.txt 
```
where 

* `-cp bin` denotes that the class path to the compiled version
  of the game's default package is `bin`, 
* `cs1302.game.LatinSquares` denotes the fully qualified name of
  the game's driver class, and
* `config.txt` is the path to a text file that provides the game's 
  starting configuration. 
  
#### Starting Configuration

The starting configuration for a game is provided in some readable
text file adhering to a specific format, detailed below. For the
purposes of defining the specification, we will first describe
the file as containing *tokens* separated by *whitespace*. A token
is simply a string of non-whitespace characrers, and whitespace
is defined as a string of whitespace characters. A whitespace
character is any character recognized by
[`Character.isWhitespace`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#isWhitespace-char-).
If you use the 
[`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)
class to parse the file, then tokens and whitespaces are handled
as described here. 

Here is the format for a file containing a starting configuration
for a Latin Square's game:

* The first token in the file represents *n*, the size of the game.
* The next *n*-many tokens represent the characters for the game.
* The next token represents *k*, the number of pre-determined locations
  in the latin square grid.
* The next *3k* tokens represent the placement and character for
  each of the pre-determined lcoations. Each location is made up
  of three tokens that provide the row, column, and character,
  respectively.
  
For the purposes of this assignment, you may safely assume that a
correctly formated file will be used to provide the game's 
starting configuration.
  
To read the file, let us assume that we have the path to the file
stored in a `String` variable called `config` and use the
following classes:

* [`File`](https://docs.oracle.com/javase/8/docs/api/java/io/File.html) 
* [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)

Most of you have used the `Scanner` class to read from standard input.
Here, we will use it to read from a text file. This is accomplished using 
something similar to the following code snippet:

```java
try {
  File configFile = new File(config);
  Scanner configScanner = new Scanner(configFile);
  // use scanner here as usual
} catch (Exception e) {
  // handler exception here
} // try
```

Information about the `try` and `catch` blocks is provided in 
Ch. 10 of the LDC4 textbook (see syllabus).

#### Welcome Banner

When the game first starts, the following text should be displayed
to standard output:

```
  _           _   _        _____
 | |         | | (_)      / ____|
 | |     __ _| |_ _ _ __ | (___   __ _ _   _  __ _ _ __ ___  ___
 | |    / _` | __| | '_ \ \___ \ / _` | | | |/ _` | '__/ _ \/ __|
 | |___| (_| | |_| | | | |____) | (_| | |_| | (_| | | |  __/\__ \
 |______\__,_|\__|_|_| |_|_____/ \__, |\__,_|\__,_|_|  \___||___/
                          CSCI 1302 | | v2018.fa
                                    |_|
n = 3 { x, y, z }
k = 1
```
where the text below the game title summarizes some of the
information about the game's starting configuration. 

#### Displaying the Square



#### Prompting the User


#### Game Loop

#### Winning Conditions

When the game first starts, the following banner 

TODO


## Project Requirements & Grading

### Functional Requirements

A functional requirement is *added* to your point total if satisfied.

TODO

### Non-Functional Requirements

A non-functional requirement is *subtracted* from your point total if
not satisfied.

* **(100 points)** This project must be implemented in Java 8, 
  and it must compile and run correctly on Nike using the specific
  version of Java 8 that is setup according to the instructions
  provided in the first homework assignment.
  
* **(100 points)** Only one `Scanner` object for `System.in` (i.e., for
  standard input) should be created. You are free to make `Scanner` 
  objects for other inputs as needed.
  
* **(100 points)** Use of static variables is not allowed for this
  assignment.

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

