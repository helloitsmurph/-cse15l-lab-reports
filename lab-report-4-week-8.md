# Welcome to Lab Report #4 Week 8
## On this Lab Report we will be discussing more Markdown Parse!! 

Here are the links to [my Markdown-Parser Repo](https://github.com/helloitsmurph/markdown-parser.git) and to the [reviewed Markdown-Parser Repo]( https://github.com/tcarman/markdown-parser) 
---
Okay, so...cutting right to the chase. I, along with my fellow peers in the CSE 15L course, were 
given three snippets which we each put into three seperate markdown files. The content of these 
snippets is as follows:
#### Snippet 1
```
[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

#### Snippet 2
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
#### Snippet 3
```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```
## Okay, all up to speed? *Cool*
Now the purpose of this was we were supposed to determine what the expected output of each of these files was supposed to be
and how this matches up with our implemention as well as the implementation of the group's we reviewed.

### Excepted Output
VS code has this neat feature call preview which I used to help decipher what the output for each snippet should be.

#### Snippet 1
<img width="1143" alt="Screen Shot 2022-05-22 at 10 30 04 AM" src="https://user-images.githubusercontent.com/103203095/169708774-4a7555f6-173e-4d3e-9082-7f6af32753e5.png">

#### Snippet 2
<img width="1143" alt="Screen Shot 2022-05-22 at 10 30 12 AM" src="https://user-images.githubusercontent.com/103203095/169708786-ef415f65-7e6a-4a7f-bb1f-7efc47c960b8.png">

#### Snippet 3
<img width="1143" alt="Screen Shot 2022-05-22 at 10 30 21 AM" src="https://user-images.githubusercontent.com/103203095/169708796-8a25808c-be5a-4bf2-81b6-154d41a2f0ae.png">

From each of these previews, I thought the expected output should be:

Snippet 1: [google.com, google.com, ucsd.edu]

Snippet 2: [a.com, a.com(()), example.com]

Snippet 3: [https://www.twitter.com, https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule, https://cse.ucsd.edu/]

And then made tests in the MarkdownParseTest.java file to check if either implemenation has these expected outputs.
Here are the tests I wrote and added to the file MarkdownParseTest.java:

<img width="1160" alt="Screen Shot 2022-05-22 at 11 47 29 AM" src="https://user-images.githubusercontent.com/103203095/169710888-9bdadf08-0950-458b-aae4-012000dc5e29.png">

I used the exact same test cases in my MarkdownParse.java file.

#### My Implementation
All three tests of the Snippets failed. Getting the Links from each Snippet yeilding these
results:

<img width="1160" alt="Screen Shot 2022-05-22 at 11 56 43 AM" src="https://user-images.githubusercontent.com/103203095/169711352-10154266-fa88-4ac5-a816-a1a94fc28a50.png">

Snippet 1: Did not recongnize ucsd.edu as a link.

Snippet 2: Did not close the parenthesis on a.com(()) which may have lead 
to some sort of problem that made it so it did recongize example.com as a link.

Snippet 3: Only thought the course scheudle for CSE15L was a link even though there were 
other links present.
#### Reviewed Group's Implementation 
The Reviewed Group's Implementation passed for two of the Snippets, but not the third one.

<img width="1158" alt="Screen Shot 2022-05-28 at 5 04 00 PM" src="https://user-images.githubusercontent.com/103203095/170846580-528bdc82-62eb-4d58-ac9c-8237c3aa5a8d.png">

Snippet 1 passed.

Snippet 2 passed.

Snippet 3 Shows an error in the code in which the program thought that the text before the link was a link in and of itself. So, the list of a files links contains unnecessary information.

I think the underlining cause for all these test failing is this: I simply did not think to test for these very specfic edge cases. It's a commonality in all of computer science. Programmers most often want to make sure their code works for the most general cases, because these are the cases
the code will most typically be run through. However, the outlining cases, thinking about the possible edge cases are actually the most important part of 
writing good code. I think that was the point of this exercise as a whole. 

### What could possibly be changed so cases would pass for my implementation?

#### Snippet 1: 

What caused "url.com" to not be seen as a link is a ` right before the bracket open.
I think that some kind of method that checks for brakcets inside of strings would help in this case. That way the openBracket and closeBracket variables are still updated accordingly.

#### Snippet 2: 
A stack would work really well here to check to make sure that the open paren also 
has a close paren and whatever was inside the two was a link. Using a stack with a last-in-first-out (LIFO) data structure 
would add the first open paren into the stack and then only remove it when the closing paren at the end is found. This means the link has a valid
structure. Then, another method would read what was inside those two parenthesis. However, this approach would I assume, take greater than or equal to 10 lines. 
This is because we would have to reconfigure all of MarkdownParse to a stack data struture. Or in other words, starting from scratch. 

#### Snippet 3:
Again, I think what would work here is some kind of approach with a stack that strictly looks
for an open paren and a close paren and something that reads what is in between. I also think this
approach would take greater than or equal to 10 lines of code.
