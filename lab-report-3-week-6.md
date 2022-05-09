# CSE15l Lab Report #3
## Before We Get Started, Here's a Link to my Index Page

[index page link](https://github.com/helloitsmurph/-cse15l-lab-reports.git)
---
## Streamling ssh Configuration
Right now, I have a file on my notes app with the command to log into my specfic course account for CSE15l. I can never remember what to type into
terminal so I always just copy and paste directly from this one note. Still, even this takes time. 
This brings up the question, how can we make this process go a lot smoother and subsequently faster?

The answer: use a ssh Configuration 

I found this [article](https://www.tecmint.com/configure-custom-ssh-connection-in-linux/) particilarily helpful. It explains the whole process pretty throughly for any ssh and I used it to help me with logining into ieng6.

This is what all the steps laid out in terminal looks like:
<img width="1351" alt="Screen Shot 2022-05-06 at 8 35 29 PM" src="https://user-images.githubusercontent.com/103203095/167237339-a1444d4d-1fe4-49f0-9a9d-ee6d7677d041.png">

Before we get started, make sure you have a public key enabled to login to shh, check out Lab Report #1 if loggining into shh still requires a password!!

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






