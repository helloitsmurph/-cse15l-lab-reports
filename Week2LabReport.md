# Week 2 Lab Report 
Welcome to my week 2 lab report! Sit back, relax, enjoy my tutorial for logging into the course specfic account for CSE15L using a MacBook Processing System.
## First thing's first. We gotta set up a coding environment.  For this class that environment is Visual Studio Code (VS Code)
**Installing VS Code**

To install VS Code, first go to their [website](https://code.visualstudio.com)

Should look something like this (unless they did some serious rebranding):
<img width="1403" alt="Screen Shot 2022-04-07 at 2 31 59 PM" src="https://user-images.githubusercontent.com/103203095/162323615-018b7987-0b1e-4ec4-ab33-bca8d8ebe76e.png">
Now notice the blue button looking real *cute* at the top right corner? Yep, maybe you guessed it...click away.
Cool. Done Clicking? Something new in your downloads now? **COOL!!**
Now follow standard procedure for finishing up new downloads. I'm no tech genuis but there are people on the internet that are. Feel free to ask them if you have issues. **Or better yet** ask your peers!
Everyone lives, laughs, and loves differently so feel free to choose your own adventure.
## Now it's time to figure out your course specfic account
Okay, to do this first go to this [link](https://sdacs.ucsd.edu/~icc/index.php)
<img width="1403" alt="Screen Shot 2022-04-07 at 2 59 38 PM" src="https://user-images.githubusercontent.com/103203095/162326807-19a29292-2fbd-48f9-a817-3fddc0e0b28a.png">
Look like this? **COOL!!**
Now give that website your info
<img width="1403" alt="Screen Shot 2022-04-07 at 3 00 52 PM" src="https://user-images.githubusercontent.com/103203095/162326952-bb837370-e8c7-43d5-a972-40c72393f535.png">
Look for the account in the grey little box. Should begin with cse15l followed by an abbreviation of whatever quarter and year we're in when you're reading this (what even is time anyway?!?!...off topic...hehe didn't mean to cause an existential crisis there)

*Getting back on topic*

Find someway to store that course spefic account somewhere. Ingrain it into your memory, put in your notes, if you are a *distinguished individual* write it on an index card with a fountain pen. 
*note* for this class it's CSE 15 then lowercase letter "L". I know it looks like an uppercase "i" or number 1. I know.

Okay so I mentioned previously I am no genuis but I would for sure design a better system than this if it were up to me. But alas, yours truly had nothing to do with this and I'm just giving instructions. 
Click on your course specfic account.

<img width="1403" alt="Screen Shot 2022-04-07 at 3 14 29 PM" src="https://user-images.githubusercontent.com/103203095/162328320-14c9362c-d17f-4861-bff7-b2aa8699084f.png">
Click that link that says "change your password". You may need to put in your info again (like I said, I had nothing to do with this design).
<img width="1403" alt="Screen Shot 2022-04-07 at 3 17 17 PM" src="https://user-images.githubusercontent.com/103203095/162328616-30345b43-bd76-478c-84bb-5cc451a1b6e5.png">
Now put in a new password, want to change your tritonlink password too? Possibly help make your account more secrure? Also maybe makethe next couple of days a little annoying when you have to relogin and enter your new password for everything???? Then by all means make sure you leave it selected as yes on the "Change MyTritonLink password". 
If you want to keep the two passwords seperate, click no. In theory they should be seperate but nothing works out so simply here so (at least in my case) my tritonlink password was still changed. :..(
The one thing you want to make sure it says "Yes" on is "Change course-specific account passwords?". 

**Important Message** Make sure you get to a page that says "password change successful" if not, your password was not changed. The guidelines are pretty specfic as far as the kind of password it is looking for.

***

# Okay now we can take a break. Few. We've done a lot. Here's a picture of my cat as a thanks for getting this far present.
<img width="592" alt="Screen Shot 2022-04-07 at 3 24 26 PM" src="https://user-images.githubusercontent.com/103203095/162329375-9038157c-baf3-4a40-8296-2dac6c3f1bda.png">
Her name is Ruby and she's very proud of you. Take a break and admire that adorable face...don't get me started on the little toe beans.

***

Hopefully you've spent at least 10-15 minutes looking at that photo and if you haven't then look at it some more. This is because that is the amount of time it takes for the password change to take effect. Until then you probably won't be able to login.
**COOL!!** 
# Now we can finally login to ssh. 
Open up VS Code. Select Terminal<-New Terminal at the top of the screen. 
<img width="1399" alt="Screen Shot 2022-04-07 at 3 47 35 PM" src="https://user-images.githubusercontent.com/103203095/162331910-b46158d5-d795-4435-a85f-e6fb31712e1d.png">
Awesome. Now in the command line copy and paste this: 
```ssh cs15lsp22zz@ieng6.ucsd.edu```

*note* don't forget to replace with your own course specfic account. Hopefully your fountain pen handwriting was legible.

You may be prompted with a question ending with "(yes/no[fingerprint])" type "yes" and move on
Enter in your password now
Should get something like this:
<img width="1440" alt="Screen Shot 2022-03-31 at 8 35 17 AM" src="https://user-images.githubusercontent.com/103203095/162333574-25cbacd4-81a3-4ebd-8351-4ea31555c119.png">
Congrats! Now you're connected. Great job. Ruby is even more proud of you. 
# Let's test this thing out
Now it's time to run some commands. Figure out what those commands means too. How exciting!!
First try: cd, ls, pwd, mkdir, and cp. If you can't figure out exactly what each command is doing: ask!!
Next try running:

``` cd ~ ```

``` cd ```

``` ls -lat ```

``` ls -a ```

Fun colors should now appear.
<img width="1440" alt="Screen Shot 2022-03-31 at 8 51 17 AM" src="https://user-images.githubusercontent.com/103203095/162335370-0d0ef007-da96-42ad-80c0-cfe6caaa0370.png">
Play around with it for a while. Have some fun!
**Now Log Out by either typing ```exit``` then the enter buttom in terminal or simply press Ctrl-D**
But we did so many steps to login in? Why are we logging out so soon?
Great question! We logged out to figure out how to transfer files from your personal computer over to ssh.

# Moving Files over SSH with scp 

For the purposes of this demo simply create a new fily in VS Code and name it WhereAmI.java and copy and paste this bad boi in there:
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
} 
```

Compile and run in terminal. This was my result:
<img width="1271" alt="Screen Shot 2022-04-07 at 7 42 05 PM" src="https://user-images.githubusercontent.com/103203095/162352586-81515e6b-98a9-4d03-a6e4-c7654f25d8c2.png">

To copy it over to ssh simply run the command:
```scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/```

*note* Don't forget to replace with **your** course username

Put in your password same as before

<img width="1271" alt="Screen Shot 2022-04-07 at 7 48 26 PM" src="https://user-images.githubusercontent.com/103203095/162353202-13e17163-daa0-400f-9b46-d478e269e220.png">
Run the command: 

```ls``` 

You should now see the WhereAmI.java file in there. And you thought magicans never reveled their secrets.

# But that's annoying so let's this process easier and the _Key_ to making it less time lies in some funky symbols
I am no genuis, but there are certain people in this world that are and they figured out a way to copy files over to SSH really quickly.
Basically a public key (think of it like a combination to a lock) gets stored on your computer and a private key (the lock itself)
gets stored in SSH. When the keys are set each time you log into SSH after setting it all up, the two should be like "heyyyyyyyy look at this guy!! I know this guy"
and you won't have to enter in your password anymore. Fun stuff. Let's do it!!

Copy and paste into terminal:

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key
(/Users/<user-name>/.ssh/id_rsa): /Users/<user-name>/.ssh/id_rsa
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/<user-name>/.ssh/id_rsa.
Your public key has been saved in /Users/<user-name>/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:jZaZH6fI8E2I1D35hnvGeBePQ4ELOf2Ge+G0XknoXp0 <user-name>@<system>.local
The key's randomart image is:
```
  
<img width="1115" alt="Screen Shot 2022-04-07 at 9 53 37 PM" src="https://user-images.githubusercontent.com/103203095/162367328-a78c7e2e-3ec0-4138-bce6-ea7ada193de8.png">

Personally I think the key could use more pizzazz:

<img width="1115" alt="Screen Shot 2022-04-07 at 9 49 35 PM" src="https://user-images.githubusercontent.com/103203095/162366848-355af53a-406b-4b95-a860-6d7b22b063e4.png">

Like comeon it fits **PERFECTLY** makes me sad. But I digress.
After this process is complete you should be left with something like this:
  
<img width="1440" alt="Screen Shot 2022-03-31 at 9 23 17 AM" src="https://user-images.githubusercontent.com/103203095/162367560-4dae6070-dca0-4d7b-9e5f-1aa7c5bd24d9.png">

Process is now super screamlined. Take a look at this:
  
<img width="623" alt="Screen Shot 2022-04-07 at 9 59 15 PM" src="https://user-images.githubusercontent.com/103203095/162367944-dd1c2413-2695-4451-93e0-0567f22c47ca.png">

  # But can we make this process EVEN BETTER? 
  ## short answer: yes
  
  But how? Glad you asked!
  
  <img width="1396" alt="Screen Shot 2022-04-07 at 10 09 22 PM" src="https://user-images.githubusercontent.com/103203095/162368891-425cecf7-0c63-4e62-938e-ea1d7adf245e.png">
  
  Few simple command line arguments and *boom* **ALL DONE**
  Here's it broken down into steps:
  1. Use the command line argument cd to make sure your currect directory is wherever you have decided to save the file you are trying to copy over
  2. Copy the file over to SSH using scp using command:  ```scp WhereAmI.java cs15lsp22xx@ieng6.ucsd.edu:~/```
  3. next, using the keys established previously login to you can login to SSH, complie, and run the file all in the same command line arguement just use this:  ```ssh cs15lsp22xx@ieng6.ucsd.edu javac WhereAmI.java; java WhereAmI```
**as always, don't forget to change the username to your own**
  ---
  Okay that's it. We're done here. Thanks!!!

  




