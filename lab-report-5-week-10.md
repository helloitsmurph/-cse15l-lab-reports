# Week 10 Lab Report #5
## Last Lab Report :..( 
Very bittersweet to be writing my very last lab report for CSE-15L. I really enjoyed this class and the people I have met in it.
But all good things must come to an end.
---
Let's talk about what we did during Lab 9. During Lab 9 we figured out how to use ```vimdiff``` to see the difference between two files.
After cloning the TA's markdown-parser repo, running the bash script, and saving the results to a folder named ```results.txt``` I was able to 
do a very similar process with my own markdown-parser repo and the following image is the ```results.txt``` files compared. I was able to compare 
them using the terminal command: ```vimdiff my-markdown-parser/results.txt markdown-parser-week-9/markdown-parser/results.txt```

<img width="1155" alt="Screen Shot 2022-06-10 at 6 46 24 PM" src="https://user-images.githubusercontent.com/103203095/173168213-b735fbc4-0ed8-4dea-a97c-1764643e70f3.png">

Now, a lot of pretty colors but the color represents differences between the two files. The blue represents a file having a line that the other 
file does not and the pink represents a file having noteable text differences from another file. 
So, what can we determine from this information? Well, my code thought a certain file for example test-files/512.md contained no links while the other implementation thought that there was a link. Another example is just a little further down in the screenshot showing the different outputs for test-files/519.md. Again, mine thought there was no link while the TA's thought there was.
Well, the first noteable difference is my code threw a lot of exceptions hence why there is a lot of blue as there was no output for my implementation. But amist all of that you can see that test-files/577.md's output also differs.
### Now Who's Implementation is correct?
Here are the links for the two files mentioned above:

[511.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/511.html.test)

[519.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/519.html.test)

To show whether or not one implementation was correct, here a screenshot showing the preview of each file in VS Code.

*511.md*
<img width="1151" alt="Screen Shot 2022-06-10 at 7 15 00 PM" src="https://user-images.githubusercontent.com/103203095/173168850-1052d0a6-174c-44c8-89b3-1088d7f9cc7f.png">

As you can see, the expected output for this file is [/uri], meaning VS code 
interprets that part of the test file to be a link. So the TA's implementation is correct.

*519.md*
<img width="1151" alt="Screen Shot 2022-06-10 at 7 15 46 PM" src="https://user-images.githubusercontent.com/103203095/173168940-7f45c410-613f-4b59-8bec-564bba789f7c.png">

So, there actually are no links in this test file as VS Code preview feature interprets the contents to be an image. Which means in this case my output of [] was correct. 

### What Needs to be Done
To fix the error in code that caused my implementation to produce the wrong output I think these lines need to be changed: 

<img width="1131" alt="Screen Shot 2022-06-10 at 7 36 14 PM" src="https://user-images.githubusercontent.com/103203095/173169406-160c4c99-46e0-4f4a-8862-b2f489da70e9.png">

Because for file 511.md my markdown didn't recongize /uri as a link. So it needs to check that every open bracket has a matching closed bracket and once this is done then the same needs to be checks that every open parenthesis has a closed parenthesis and then check inside of the open and closed parenthesis for links. 
