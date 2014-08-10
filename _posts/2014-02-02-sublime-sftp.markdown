---
layout: post
title: Sublime SFTP
date: 2014-02-02 16:17:39.000000000 -08:00
---
<small> Oops! It's been so long since I've written anything. (It's like i made a new year's resolution to not blog or something) </small>

This is a guide to set up Sublime Text/SFTP and how to connect it to UMich's CAEN computers. (It's pretty specialized oops) I'm certainly not an expert on any of these things so I'll probably use some terms incorrectly - feel free to correct them!

<small> Okay in retrospect this is a <s> pretty sad post which mainly consists of links oops</s>  wonderful guide! </small> 

---

###Background (aka skip to [here](#start) if you just want to get started)

A few weeks ago, after the [gEECS](http://umich.edu/~geecs) mass meeting, a couple of us stuck around and began chatting about all the programming-related things we wish were taught in the intro class ( or wish we knew about earlier<sup>[*](#footnote)</sup>).  So here's the beginning of "stuff you might want to know!" blog posts for people just beginning to program.    

In my experience, a lot of students go through the introductory programming courses by VNCing to UMich's linux computers and using gedit to code (since our programs are graded by compiling/runing on linux.)

Not only is this kind of annoying - it's really annoying. But after this guide, not only will 1 million puppies joyfully leap about you, it'll also be possible to write and run your code on your own computer (with nice syntax highlighting/autocomplete)!

Let's get started!


<a name="footnote"/> </a>
<sub> *Admittedly I was lucky enough to have someone awesome show me this the night before classes started! </sub>

---
<a name="start"/> </a>

**0. Windows users, install Putty if you haven't already** 

Click [here](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and then click on "putty.exe".  I'll talk more about this below!


**1. Download Sublime Text**

Click on the appropriate link on this [page](http://www.sublimetext.com/2) depending on your operating system and follow the instructions. 

**2.Install the sublime package manager**

Now head on over to this [page](https://sublime.wbond.net/installation#st2) and follow the instructions. (Basically it should look like this after you paste in the code) Now restart Sublime Text (close and reopen)

![](/content/images/2014/Feb/Screenshot_from_2014_02_02_20_15_37.png)

**3. Install Sublime SFTP**

This is what will sync your files from the server to your computer. I don't really know what SFTP means without looking it up but hey it's cool!  Basically, press `ctrl` + `shift` + `p` (windows) or `cmd` + `shift` + `p` to open up package control. Enter (or select) "Package Control: Install Package", and then select "SFTP" and press enter (boom!).  
<small> (For the long version head over [here](http://wbond.net/sublime_packages/sftp/installation).) </small>


**4. Open up the folder whose contents you want to sync**

From the toolbar, click `file` -> `open folder` and then select the folder whose contents you want to sync. This folder should show up in the sidebar (like in the image above). If not, simply click from the toolbar `view` -> `show sidebar`. 

**5. Almost done!**

Right click on your folder and select ` SFTP/FTP` -> ` Map to Remote...`. Good! A file called something like  sftp-config.json should now pop up.

I've copied it below and omitted the less important things we wont change.

<pre><code>  
{
    // The tab key will cycle through the settings when first created
    // Visit http://wbond.net/sublime_packages/sftp/settings for help
  
    "save_before_upload": true,
    "upload_on_save": false,
    "sync_down_on_open": false,
    "sync_skip_deletes": false,
    "sync_same_age": true,
    "confirm_downloads": false,
    "confirm_sync": true,
    "confirm_overwrite_newer": false,
    
    "host": "example.com",
    "user": "username",
    //"password": "password",
    //"port": "22",
    
    "remote_path": "/example/path/",
    
    
    // Omitted stuff below is important but no need to edit!
...
</code></pre>


Time to configure away! Depending on your preferences, you can modify the top 8 settings however you see fit. I typically recommend changing `upload_on_save` to be true since it's more convenient.

The important thing is to change `host`, `user` and `password`. For example, if you are a UMich student, host will be `login.engin.umich.edu` and your username and password are your uniquename and password. Make sure you delete the `//` before password!

Your `remote_path` will be the remote folder that your open folder's files will be saved to. For example ` /afs/umich.edu/user/e/x/example/school/engr101` or something like that if you want your files to be saved in the `engr101` folder when you sync. (The `~` just means home directory.)

Now save!

**6. Does it work?**

Right click on the folder again  -> `SFTP/FTP` and if all went well you should see more options now! Try writing a new file and saving/clicking `STFP/FTP` -> `Upload folder`. If you see a little pop up below ratting on about how it's trying to connect or whatnot then sucess! It works!

Feel free to create a ".cpp" or ".py" or ".whatever" file and get started!


---

### "Umm that's cool and all but what does that mean for me?"

Now that you can write your C++ files on your own computer, how do we run them?

If you're a linux/mac<sup>[*]()</sup> user, just open up a terminal. If you want to compile on the remote machine, `ssh` into the remote location (ex caen) and type away. Otherwise you can just work on your local files.


If you are a windows user, open up PuTTY! For the host name, type in youruniquename.login.engin.umich.edu. Now you're logged into caen!

 Get to the directory with your .cpp file and type something along the lines of: `g++ youfile.cpp -o namethiswhatevr` to compile your code, and then run it with `./namethiswhatevr` just like you would anywhere else.



