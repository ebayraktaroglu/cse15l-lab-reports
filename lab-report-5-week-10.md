# Lab Report 5 - Week 10

[Back to Main Page](https://ebayraktaroglu.github.io/cse15l-lab-reports/)




## First File: 149.md

```
<table>
  <tr>
    <td>
           hi
    </td>
  </tr>
</table>

okay.
```

### Output for My Group's Implementation:

![File 1 - My Group's Implementation](Lab_Report_Week_10_Screenshots/MyImplementationFirstFile.png)

### Output for the Lab 9 Implementation:

![File 1 - Lab 9 Implementation](Lab_Report_Week_10_Screenshots/TeacherImplementationFirstFile.png)

### Explanation:

>I found this difference in results by looking back at my group's lab notes and choosing one of the test files that gave different results for the two implementations. We found this difference using the `dif` command on the text files for the result of all the tests.

>The expected result is an `[]`, since there are no valid links in the Markdown file. This means that my group's implmentation gave the wrong output, while the Lab 9 implementation gave the correct output.

>The bug in my group's implementation that caused this error is that we completely misinterpreted the instructions for markdown-parse, and we thought that we wanted to get all the links, regardless of whether they were in a proper format or not. To do this, we operated under the (flawed) belief that any valid link would have a period in it, so our implementation got each period and expanded outward until we got to a space or other character we defined as not being part of a link, and then took that as a link. Because of this, our implementation took `okay.` to be a link, even thought it wasn't. To fix this, we would have to completely change our implementation to check for the valid link formats in Markdown, rather than any link.

#### Basically all the code has to be changed for this bug to be fixed. Here is part of the bug:

![File 1 - My Group's Bug](Lab_Report_Week_10_Screenshots/OurGroupBug.png)




