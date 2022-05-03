# Week 4 Lab Report 
## Introduction to Debugging 
### The following was adapted by "How to Debug - Embedded in Academia" by John Regehr
Something that all programmers, both beginners and the homies making the big buckaroos, have to go through almost every single day is a process
called debugging. The origin of the phrase actually came from a literal bug that was causing a malfunction in the hardware of a computer (back when 
computers **DEFINITELY** could not fit on your lap. Still, the phrase is still used to refer to fixing any problem that is causing the computer to not give the expected output. 

Now, I know you probably just thought that sounds broad and vague. 
And you would be absolutely correct. Which is why programmers often use these things called symptoms to try and spot problems with their code and will use these symptoms to try and track down what exactly is causing the error in the first place. Kind of like talking to a doctor and telling them how you've been feeling lately in the hopes that they can reccommend something that will help you feel better. Except you are the doctor and your code is the patient. 

---
## Debugging in Practice
So, in Lab #3 we were told to fork a repository and try to "fix" this file called: ```MarkdownParse.java```
But there was a catch, we were not informed what exactly was wrong with the file. It was up to us to figure that out for ourselves. 
After opening up the file on my workspace, my group and I noticed that a number of things could send the code into an infinite loop.

Terminal Output showing that Out of Memory Exception was thrown (meaning code sending the computer into an infitine loop). 

<img width="589" alt="Screen Shot 2022-05-02 at 4 39 08 PM" src="https://user-images.githubusercontent.com/103203095/166343105-484a6fd2-cb18-497e-8970-32eaf1e98c4f.png">

One of these things was the ```test-file.md``` not containing a second ")" or closeParen. Hazaa!! We have a symptom. Now, the real work 
begins in trying to fix this code.


Link to test file: https://github.com/helloitsmurph/markdown-parser/blob/main/test-file.md


This is not good. It's hard on...well your hardrive. My computer is a MacBook and it sounds like it's going to take off mid-zoom lecture. So imagine how 
hard the processor was working when I kept asking it to run code that wanted to run forever.
## Strategy #1 Add the Scanner Class
<img width="942" alt="Screen Shot 2022-04-24 at 5 41 32 PM" src="https://user-images.githubusercontent.com/103203095/165004050-0aba593b-8d64-4c5b-92aa-0b4eb83cd8d7.png"> 

Adding the Scanner class just what made the most sense to me. I am sure there are many different ways
of solving this problem but importing the Scanner class is just the direction I decided to head in. What is nice about this implemetation is you can program so the file stops importing
information when there aren't anymore lines of text in the file. A file cannot have infinite lines, so *nice* one bug dealt with.

Terminal output with this version of MardownParse.java:
<img width="732" alt="Screen Shot 2022-05-02 at 4 50 00 PM" src="https://user-images.githubusercontent.com/103203095/166343769-de7a36bf-b0ec-4137-970b-66c160990e4e.png">


Link to test file: https://github.com/helloitsmurph/markdown-parser/blob/main/test-file.md


Same test file; however, this time the computer is not sent into an infinite loop and we are actually able to see what is in the file so *nice*. Nevertheless, the file pictured above is a very basic md reader, it does 
not filter what is in the md file at all. This is a problem because the goal of this is for the code to get the specfic links which are contained in a file.
## Strategy #2 Use What Was Available
<img width="942" alt="Screen Shot 2022-04-24 at 6 10 33 PM" src="https://user-images.githubusercontent.com/103203095/165005387-7631ed0c-4340-4d32-9eb8-0f3c5ee41008.png">
<img width="942" alt="Screen Shot 2022-04-24 at 5 41 32 PM" src="https://user-images.githubusercontent.com/103203095/165005395-4329eb23-eca8-43c2-a353-c6851ff199eb.png">
Turns out, I was not the only one that looked to the Scanner class to find the best way to produce a funtional piece of code. My groupmate Isabella also had the same idea.
So, as a group we decided this was the direction we wanted to head in. Usiing a loop which read the file line by line we then came up with a way to use the code already 
given to us orginally to pull out the links that we needed in the file. Thinking back on it now, I don't know what I orginally decided "Oh I'll start from scratch" import Scanner class
and work from there. Hindsight really is the best vision one can have. 
<img width="672" alt="Screen Shot 2022-04-24 at 6 29 04 PM" src="https://user-images.githubusercontent.com/103203095/165006453-ba938bf9-a6d1-4960-a388-5f3331409fdd.png">

Link to test file causing error: https://github.com/helloitsmurph/markdown-parser/blob/main/test6-file.md

But alas, still more problems. The code had no way of seeing if something was an image or a link. For this program, we
only wanted links to be returned.

## Strategy #3 Checking If Something is an Image

Had  to modify the code to make sure that the program could recognize that something was a image and not put it in terminal as a link.
<img width="1228" alt="Screen Shot 2022-04-24 at 6 40 52 PM" src="https://user-images.githubusercontent.com/103203095/165007175-61be68db-c0f3-4409-a40e-40cc7753b4ba.png">
Now this should make sure only correctly formated links can get printed into terminal. *Nice*

## Final thoughts
Awesome. Now the code was taken to a almost-there-not-quite working phase to a much more robust impletation that can easily tackle a multitude of more problems. Awesome!! Thanks for reading!!

