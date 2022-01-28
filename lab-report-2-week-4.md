# Lab Report 2 - Week 4

[Back to Main Page](https://ebayraktaroglu.github.io/cse15l-lab-reports/)

## Process

>For these two labs, our objective was to make a program that takes all the links in a markdown file and print them out. Our group was given a basic java file that worked for ideal conditions, but we were supposed to make it work for other unusual cases as well. We worked together in our group on the code, and only some people commited certain parts of the code, so the github commits that I will be showing is from my fork of one of my groupmates' fork of the markdown-parse repo.

## Bug One

>One bug our group encountered occurred when a markdown file contained the information in brackets, but the link wasn't in paranthesis, it would give an `IndexOutOfBoundsException`. [Here](https://github.com/ebayraktaroglu/markdown-parse/blob/e8730c20114c72506184840112ea49158778f291/markdown-test-three.md) is the file that contains the failure-inducing input.
>Here is the symptom of this bug:
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 152
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:4601)
        at java.base/java.lang.String.substring(String.java:2704)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:26)
 ```
>The bug was that the original file was using `indexOf` to find the next open and closed parenthesis. In this file, there was no open or closed parenthesis. This means that the `indexOf` returned -1, and when the method tried to add the "link" between the indexes of -1 and -1, it gave an `IndexOutOfBoundsException`. The fix for the bug makes sure to use if statements to check is the `indexOf` is -1, and acts accordingly to avoid the exception.

This is a image of the code change diff:
![Bug One Code Diff](cse15l-lab-reports/Lab_Report_Week_4_Screenshots/BugOneFix.png)
