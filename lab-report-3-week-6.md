# CSE15l Lab Report #3
## Before We Get Started, Here's a Link to my [Index Page](https://github.com/helloitsmurph/-cse15l-lab-reports.git)

---
## Streamling ssh Configuration
Right now, I have a file on my notes app with the command to log into my specfic course account for CSE15l. I can never remember what to type into
terminal so I always just copy and paste directly from this one note. Still, even this takes time. 
This brings up the question, how can we make this process go a lot smoother and subsequently faster?

The answer: use a ssh Configuration 

I found this [article](https://www.tecmint.com/configure-custom-ssh-connection-in-linux/) particilarily helpful. It explains the whole process pretty throughly for any ssh and I used it to help me with logining into ieng6.

This is what all the steps laid out in terminal looks like:
<img width="1351" alt="Screen Shot 2022-05-06 at 8 35 29 PM" src="https://user-images.githubusercontent.com/103203095/167237339-a1444d4d-1fe4-49f0-9a9d-ee6d7677d041.png">

Before we get started, make sure you have a public key enabled to login to shh, check out Lab Report #1 if logging into ssh still requires a password!!

**Okay, let's unpack those terminal commands**
First off, if the ssh directory does not already exist on a machine we want to run the command: ```mkdir -p ~/.ssh```.

From the article mentioned above: "The chmod command above implies that only the user can have read, write and execute permissions on the directory as required by ssh settings". Hence why next I ran the command:  ```chmod 0700 ~/.ssh```

Now to finally create a configuration file, start by saying:  ```vi ~/.ssh/config```

Should look something like this:

<img width="1451" alt="Screen Shot 2022-05-06 at 8 36 25 PM" src="https://user-images.githubusercontent.com/103203095/167240776-8a081cdf-0738-4620-8e63-4c4c3ff94ecf.png">

Now, press the "i" key on the keyboard and now you can begin adding stuff to the configuration
file. If its not already in there, copy and paste this:

```
Host ieng6
  HostName ieng6.ucsd.edu
  User cs15lsp22zzz
```
    
    
**Don't forget to chance the zzz to YOUR course username**

Finally tap the exit key "esc" to get out of insert mode and then type ":wq" to save and quit the text editor.

Test it out!! See if typing ```ssh ieng6``` into terminal instanly logs into ssh. 

Now, this whole process also makes copying files over really easy. Let's try it!!

As orginally implemented during the first lab report of this class, the WhereAmI.java file will once again be making an appearance. Basically, the file shows what system the user is  currently operating on.

This is what is looks like running the file on my personal computer:
<img width="1340" alt="Screen Shot 2022-05-07 at 9 00 27 AM" src="https://user-images.githubusercontent.com/103203095/167262281-6c2ff66c-2bf1-4f47-bde9-e0b0f6bd0ff8.png">

Okay, now we can copy over the file contents to ssh using the command: ```scp WhereAmI.java ieng6:~/```
If you ssh is not nicknamed ieng6, don't forget to change it.

Putting it all together, this is what it should look like:

<img width="1340" alt="Screen Shot 2022-05-07 at 9 06 30 AM" src="https://user-images.githubusercontent.com/103203095/167262547-fb0b075b-f0f0-4b66-884a-c8def5d499d3.png">

*Cool* Moving on.

## Setup Github Access from ieng6

The directions for how I was able to do this are found [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
After following those directions, I was able to place my public key in my github account:
<img width="1199" alt="Screen Shot 2022-05-07 at 9 20 45 AM" src="https://user-images.githubusercontent.com/103203095/167263150-7e83fdae-83aa-4838-a84f-d87e6a938650.png">
I decided to just generate a new key. 
<img width="1348" alt="Screen Shot 2022-05-07 at 9 31 19 AM" src="https://user-images.githubusercontent.com/103203095/167263416-0f323826-61c9-4c50-b2ae-a3fb19a89e46.png">
As you can see, my "identification has been saved in /Users/gracemurphy/.ssh/id_ed25519". *Cool*

Now, let's change something about MarkdownParse.java and commit it to github!
<img width="802" alt="Screen Shot 2022-05-15 at 3 48 24 PM" src="https://user-images.githubusercontent.com/103203095/168497289-e49d8f03-eba2-42a4-a03a-6e173a65a1fc.png">

As you can see, I was able to add a line to my code, commit and push changes to Github all right from the comfort of my ssh terminal!!
*sigh of relief* 

The link for the resulting commit is right [here](https://github.com/helloitsmurph/markdown-parser/commit/cf509b2da45555ebc0b478535c43d485fd021336).

## Copy whole directories with scp -r
For the last task of this lab report let's copy a whole directory onto ssh! 

Now, just doing this with the ```scp -r``` command, I got this output:
<img width="978" alt="Screen Shot 2022-05-15 at 4 04 41 PM" src="https://user-images.githubusercontent.com/103203095/168497785-ae18cd3f-6d48-4b2a-9424-edac47319461.png">
<img width="1098" alt="Screen Shot 2022-05-15 at 4 05 20 PM" src="https://user-images.githubusercontent.com/103203095/168497802-f8e7c46a-05a1-4762-9aae-9bc25400bcb1.png">

That is **A LOT** of code. The reason there is so much is because the directory is being copied recursively thanks to the ```-r```  in the ```scp -r``` command. And, I haven't even gotten the chance to run any tests yet. Let's see if this whole process can be simplified further. 

<img width="1098" alt="Screen Shot 2022-05-15 at 4 17 08 PM" src="https://user-images.githubusercontent.com/103203095/168498273-76553019-f4d5-427c-8af3-74ec3037d5e2.png">

A lot less code. I think it's because we are basically saying "hey ignore all the other files we are only looking to copy things that end in: '.md', '.java', or the contents of the lib file".

But, what about that nickname (ieng6) we created earlier to make logging in easier? That would come in handy right now.

And it does!!

<img width="715" alt="Screen Shot 2022-05-15 at 4 23 43 PM" src="https://user-images.githubusercontent.com/103203095/168498517-14f830e9-a823-40bf-bd67-202c7c669045.png">

I can't seem to get all the commands together all on one line but the process is a lot easier than it used to be. 

<img width="1005" alt="Screen Shot 2022-05-15 at 5 26 01 PM" src="https://user-images.githubusercontent.com/103203095/168501205-e8e012bf-eda6-4641-81a0-590f9d082d0e.png">

Here's the shortest I could make the whole process right now. Started with copying the directory over using ```scp -r *.java *.md lib/ ieng6:markdown-parse``` making sure I was already in the directory markdown-parse. Then, the recursive process of copying all the files in that directory start. Then, I type ```ssh ieng6``` to get logged into ssh. Once that is done, I make my current directory there the newly copied over markdown-parse directory using the command ```cd markdown-parse```. Finally, I compile and run my tester file using the following commands:
```javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java;
java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest```
Which terminal put on two different lines for me as a result of the ```;```
