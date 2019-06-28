class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Computer Skill Crash Course:]

#A Short Introduction to the Command Line

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 2](step2.html)]

---

class: darkslide

##Table of Contents

.flexbox-ltr[
.boxitem[.orange[Introduction]
1. [What is the Command Line](#what)
2. [Shell Flavours](#shells)

.orange[Navigating the Command Line]
1. [Paths](#paths)
2. [Present Working Directory](#pwd)
3. [List files](#ls)
4. [Change Directory](#cd)
5. [Absolute vs. Relative Paths](#relative)
6. [Useful Tips](#tips)
]

.boxitem[.orange[Files and folders]
1. [Make Directories](#mkdir)
2. [Make Files](#touch)
3. [Checking Your Progress](#progress)
4. [Remove Files](#rm)
5. [Remove Directories](#rf)
6. [Copy Files](#cp)
7. [Move Files](#mv)
8. [Rename Files](#rename)
9. [Wildcards](#wildcards)

[Exercise](#ex)

[Credits and Copyright](#credits)
]
]
---

class: middle, darkslide

##Introduction

---

name: what

###1. What is the Command Line?

**Graphical User Interface** (GUI)

* Interact with the computer through graphic interface (buttons, sliders)

	⇒ Point and click, drag and drop

**Command-line Interface** (CLI)

* Interact with the computer directly 
	
	⇒ Typing commands into a minimalistic console such as “PowerShell” (Windows) or “terminal” (MAC)

---

###1. What is the Command Line?

**Advantages** of command line shells over graphical user interfaces include:

* More freedom (precision, flexibility)
* Speed up repetitive tasks (batch processing)
* Many scientific programmes don’t have a GUI (demands development time and processing power)
* Indispensable to install, manage, maintain advanced tools and software

**Disadvantages** of command line shells over graphical user interfaces include: 

* With great power comes great responsibility
* Learning curve

---

name: shells

###2. 	Shell Flavours

**Unix-Based Operating Systems** | standard CLI = Bash

* **Mac OS X**: locate the Terminal app in your applications folder and double-click on it to fire it up. Alternative: click on the magnifying glass-icon (`Cmd+spacebar`), search for 'Terminal', and hit `enter`.
* **Linux**: locate the Terminal app in your applications folder and double-click on it to fire it up. (In some distributions, like Ubuntu, the keyboard shortcut would also work `CTRL+ALT+t.`)

**Windows** | standard CLI = PowerShell

* From the Start menu, click Start, click All Programs, click Accessories, click the Windows PowerShell folder, and then click Windows PowerShell.

---

###2. 	Shell Flavours

.note[**Note:** These commands are all **bash** commands (Unix shell), that work on **Linux-Based Operating Systems**. 

In this tutorial we will be controling our RPi (which runs on the Linux-Based Operating System ([Raspbian](https://www.raspbian.org)) via [SSH](step2.html#ssh). That means that **these commands will work for us, regardless of the type of computer you use** (Windows, Mac, Linux). 

If you are using this tutorial for another purpose, keep in mind that some of these commands will need to be adapted to work on Windows systems.]

---

class: middle, darkslide

##Navigating the Shell

---

name: paths

###1. Paths

All the data on your computer are organized in what is called a **file system**: a system that controls how the data on your computer is **stored** and **retreived**. And the organizing principle of this file system is that of a **tree structure**. 

There is a **root directory** – the starting point of all the data stored on your hard drive – that contains more **directories** (usually named and/or visualized as *folders* in your operating system) and **files** (like an image, a textfile, a Word document, a PDF, a script, etc.). 

By creating more and more directories within directories, your file system starts to branch out like a tree, with the individual files in the system functioning as the end-points of each of the branches.

---

background-image: url(img/commandline/filesystem.png)

---

###1. Paths

In the command line, we use this file system to navigate through the data on our computer. Say we want to point to the `manual.pdf` file from the file system in the previous slide, we need to specify a **path** to navigate trough the different **directories** on the system like so: 

```bash
/Users/User_1/Documents/manual.pdf
```

In this path, we move further and further down into new directories by using a forward slashes. We start at the root `/`, move into the `Users` directory, then into the home directory of `User_1`, then into her `Documents` folder, where we find the `manual.pdf` file. 

.note[**Note**: The `/` at the start of the path is **crucial** here! It indicates that this is an **absolute path**, meaning that it starts at the **root** of the file system. We will distinguish this from **relative paths** [further down in this crash course.](#relative)]

---

background-image: url(img/commandline/path.png)

---

name: pwd

###2. Present Working Directory | `pwd`

Like when you are navigating through folders and files on your computer, in the shell too you are always located in a specific place on your computer. The first command you'll learn will tell you exactly where you are in your computer's file system: your **present working directory**

To find out where you are, type: `pwd` in the terminal and hit `enter`. The output you will receive in at the bottom of your terminal window, represents the **path** to the location where you currently are in your computer's file system.

```bash
pwd
	
/Users/User_1
```

.note[**Note**: when you open a new terminal, your default present working directory is always your user’s `Home Directory`]

---

name: ls

###3. List Files | `ls`

To have a look at what's inside your present working directory, type `ls` and hit `enter`:

```bash
ls

Applications				
Desktop					
Documents
Downloads
Images
Music
```

This command will output a list of all the files and directories that are inside your `pwd`. You can usually differentiate files from directories because files have **extensions** (like `.pdf`, `.jpg`, `.doc`, etc.) that tell us what kind of file it is (and your Operating System which default software package to use to open it).

---

name: cd

###4. Change Directory | `cd`

To change to a directory inside of your `pwd`, use the `cd` command. To see the change, first we'll check again where we are in the file system:

```bash
pwd 

/Users/User_1
```

Now we change into the `Documents` directory inside of our present working directory: 

```bash
cd Documents
```

This command only changes your `pwd`, it does not give you any output in the terminal window. To see where you've moved to, you can use `pwd` again:

```bash
pwd

/Users/User_1/Documents
```

And to check which files or directories are inside this new present working directory, you can use `ls` again:

```bash
ls

manual.pdf
```

---

###4. Change Directory | `cd`

To move one directory up, we use can two dots:

```bash
cd ..
```

Now we are back in our `Home Directory`:

```bash
pwd

/Users/WoutDLN
```

And we can stack upwards and downwards movement in the file system by using forward slashes again. So typing `../..` will move you two more directories up, all the way to the root:

```bash
cd ../..

pwd
/
```

---

###4. Change Directory | `cd`

.note[**Note**: regardless of where you are in your file system, just typing `cd` and hitting `enter` will move you back to your `Home Directory`.]

For example:

```bash
cd

pwd

/Users/User_1
```

---

name: relative

###5. Absolute vs. Relative Paths

As you may have noticed, the path that `pwd` returns always starts with a `/`, so it's an **absolute path**:

```bash
/Users/User_1/Documents
```

While the paths that we have entered to change directories into are **relative paths**: paths that are not precided by a `/`. This type of path always pecifies a location **relative to our current position in the directory tree**. So:

```bash
cd Documents
```

takes us into the `Documents` directory **inside the directory we currently are in** – i.e. our `pwd` (here: `/Users/User_1`)

You can always use an absolute path to get you where you want to, regardless of where you are: 

```bash
cd /Users/User_1
```

takes us exactly there:

```bash
pwd

/Users/User_1
```

---

name: tips

###6. Useful tips

- **Autocomplete** | `tab`

    The terminal has an autocomplete function, where it will finish writing directory and file names for you when you enter the `tab` key. 
    
    So when you are in your `Home Directory`, start to type `cd Doc`, and hit the `tab` key, the terminal will complete this into `cd Documents/`.
    
    If there are multiple files or directories that start with the same combination of letters, terminal will not return anything. Hitting the `tab` key twice in such a case will return a list of all the files or directories that start with that combination of letters.
    
    For example:
    

```bash
cd Do+tab+tab
    
Documents/ Downloads
 ```

---

###6. Useful tips

- **previously entered commands** | `arrow-up`, `arrow-down`

    The terminal also stores the commands you've recently entered in it's memory, and you can navigate through them by hitting the `arrow-up` and `arrow-down` keys. This can be handy when you need to repeat a long and complicated command.

- **Remember**: computers are case sensitive! 

    Writing `documents` instead of `Documents` as a path in your `cd` command will return:
    
```bash
No such file or directory
```

---

###6. Useful tips

- **A Note on Whitespace**

    Using whitespace in file and folder names makes it more difficult to navigate your computer from the command line. Say we have a directory inside `Documents` that's called `My Thesis`. Entering the following command will then return an error:
    
```bash
cd Documents/My Thesis

cp: My: no such file or directory
```

This is because the terminal uses whitespace to differentiate between individual arguments (e.g. the command `cd` and the path `Documents`), so it will treat  `My` and `Thesis` as two separate directories. We can avoid this by escaping the characters with the backslash like so:

```bash
cd Documents/My\ Thesis
```

Or, by adopting a practice of avoiding to use spaces in file- and directory names in the first place, and name the directory `My_Thesis` instead:

```bash
cd Documents/My_Thesis
```

---

class: middle, darkslide

##Files and Folders

---

name: mkdir

###1. Make Directories | `mkdir`

A new directory is created using the `mkdir` (**make directory**) command followed by the name you want to assign to it. Here we’ll name the directory `new`. First, we'll move to the directory where we want to create a new subdirectory – like in our `Documents` directory:

```bash
cd /Users/User_1/Documents

```
Then we make a new directory:
```bash
mkdir new
```
If you list the files and directories in your `pwd` now, you should see the newly created directory listed there too:

```bash
ls

manual.pdf
new
```

---

name: touch

###2. Make files | `touch`

A new file is created using the `touch` command, followed by the name you want to assign to it. Here we’ll create a text-file called _newfile_:
```bash
touch newfile.txt

ls

manual.pdf
new
newfile.txt
```
Or, you can create `anothernewfile.txt` directly inside the `new` directory we just created by using another relative path: 
```bash
touch new/newfile.txt
```
We can use relative (and absolute) paths for `ls` too, to snow items in the `new` directory without changing your `pwd`:
```bash
ls new
	
anothernewfile.txt
```

---

name: progress

###3. Checking your Progress in your Computer’s GUI

You can open your `Finder` (Mac) or `Explorer` (Windows) directly from the terminal to show your `pwd` in the GUI:

Mac:
```bash
open .
```
Windows:
```bash
explorer .
```
The `.` in both commands indicates that you want to show your `pwd`. You can also replace this `.` with an absolute or relative path.

.note[**Note**: no equivalent command exists for non-OSX UNIX systems, so it will not work on your RPi.]

---

name: rm

###4. Removing files | `rm`

Removing a file is simple, using the `rm` command: 

```bash
rm new/newfile.txt
```
If you now use `ls new`, you should notice that the files are no longer listed in the directory’s contents. If you are working on a Windows or Mac system, you can always double-check this in the GUI by using `open new` or `explorer new`.


---

name: rf

###5. Removing folders | `rm -rf`

Folders are more difficult to remove. The following command will produce an error:

```bash
rm new

rm: new: is a directory
```

Our shell is worried that you may still need the files inside the directory. You can override this by adding the `-rf` flag to your command. This is a combination of the  `-r` flag (recursively – to apply the command to all sub-directories and files) and `-f` flag (forcefully – to make sure the command line does not ask your permission to delete each indiviual sub-directory and file).

```bash
rm -rf new
```
This command will effectively remove your `new` directory from your hard drive, as well as anything else that may still be contained within that directory. 

.warning[**CAREFUL:** By using the shell, you are bypassing your system's GUI, which means that the files and directories you delete **will no longer be recoverably through your system's trash folder**!

**USE WITH CAUTION!** This gives you the power to **remove your entire hard drive** with a single command!]

---

name: cp

###6. Copying files | `cp`

.exercise[**Exercise:** create a file called `source.txt` in your `home` directory (using `touch`).]

Now, we can copy this file to the Desktop, using the `cp` command, which has two arguments, separated by a space:

1. **Source Path:** The location of the file that needs to be copied – in our case `source.txt`
2. **Target Path:** The location that the file needs to be copied to – in our case `Desktop/.`

.question[**Question:** These are two relative paths. **What would their absolute paths be?**]

The full command to copy `source.txt` to the `Desktop` would be:

```bash
cp source.txt Desktop/.
```

You should now have two instances of this file on your computer, one on your home folder, and one on your desktop. **Verify**.

---

###6. Copying files | `cp`

```bash
cp source.txt Desktop/.
```

As you will have noticed, the target path in the `cp` command we executed ends with a `.`. This dot stands for `source`, or could be more poetically translated into: _myself_. When we were [checking our progress in the GUI](#progress), this `.` refered to the `pwd`. In this context, a `.` in the target refers back to a (file or directory) name in the source – here `source.txt`. In other words, we could also write the command down in full as such:

```bash
cp source.txt Desktop/source.txt
```

This gives us the freedom to **change** the name of the file we are copying **in the process of copying that file**. We do this by specifying a new name for the document in the target path. Let's say we want to name our copy of `source.txt` as `target.txt`:

```bash
cp source.txt Desktop/target.txt
```

Executing this command after we executed the previous `cp` command makes sure that our `Desktop` now contains both a `source.txt` and a `target.txt` file. **Verify**.

---

name: mv

###7. Moving files | `mv`

**Moving files** works in the same way as copying files: you specify a source location and a target destination after entering the `mv` command:

```bash
mv source.txt Desktop/.
```

The `.` at the end here again indicates that we don’t want to change the file’s name in the process. 

Using `ls` you should now be able to verify that the `source.txt` file is no longer present in your `Home Directory`. It has been _moved_ rather than _copied_. 

.warning[**Careful!** At this point, there was already a file on your `Desktop` called `source.txt`. 

Copying or moving a file (a) into a directory that already contains a file with the same name (b) will effectively overwrite the former with the latter. 

In the command line, there is no prompt to warn you that you are doing so – unlike in your GUI, where you will typically be asked whether you would like to **overwrite** (b), or **rename** (a).]

---

class: darkslide, center, middle

.question[.center[**Question:**

Based on what we have learned so far, could you guess how we can use these commands to rename a file?]]

---

name: rename

###8. Renaming files

To rename a file, you would move the file to the same location, but with a different name:

```bash
mv source.txt newsource.txt
```

Using `ls` you should now be able to **verify** that the `source.txt` file is no longer present in your `Desktop` directory, but that it contains a `newsource.txt` file instead. 

---

name: wildcards

###9. Using Wildcards to Move Multiple Files | `*`

Last but not least, the asterisk `*` is great way to filter out certain file names. It is a so-called **wildcard**, that represent **any combination of letters**.

To move all (and only) the text files (ending in a `.txt` extension) in a directory for instance, you could issue the command:

```bash
mv Desktop/*.txt Documents/.
```

Using this syntax, you make sure that the command (and the same goes for e.g. `cp`) will be applied to all filenames ending in `.txt` and only those. As such, the asterisk functions as a kind of wildcard that would match any filename in the directory specified, as long as it ends in `.txt`.

This means that if you have entered the above command, there will be no more `.txt.` files on your `Desktop`, and that the ones that were there (such as `newsource.txt` and `target.txt` will have moved to your `Documents` instead.

---

name: ex 
class: darkslide

##Exercise

1. Create a new directory `gutenberg` inside your `Downloads` folder using the shell.
2. Direct your browser to **Project Gutenberg** (`https://www.gutenberg.org/`). Download three novels by Jane Austen in plain text format (i.e. the option "Plain Text UTF-8"). Then, download three novels by Charles Dickens in PDF format. Store all six files in the `gutenberg` directory inside your `Downloads` directory.
3. Move the `gutenberg` directory from  `Downloads`  your `Desktop`.
4. On your `Desktop`, create two new directories: `austen` and `dickens`.
5. Copy the Austen books under `Desktop/gutenberg` to `Desktop/austen` and copy the Dickens novels in PDF to `Desktop/dickens`. For this, **you can only use two copy commands** (i.e. one per author), relying only on the difference in **extension** for each author.
6. Remove the `gutenberg` folder and all of its contents.
7. Inspect the contents on one of the Austen text files, using the `ls` command followed by the path to the file.

---

layout: false
class: center, middle, darkslide

#Done!
.yellow[Move to a summarizing [cheat sheet](cheat.html) to freshen up this crash course.]

.bottomright[[Credits and Copyright](#credits) &#10148;]

---

name: credits
class: darkslide

.topright[[![UAntwerpen](img/logos/ua.svg)](https://www.uantwerpen.be/)]

##Credits and Copyright

This tutorial was developed by Wout Dillen and Joshua Schäuble at the [Centre for Manuscript Genetics](https://www.uantwerpen.be/en/research-groups/centre-for-manuscript-genetics/) (CMG), as part of the [IIIF](https://iiif.io) courses of the [University of Antwerp](https://www.uantwerpen.be/)'s Summer School on [Digital Humanities](https://www.uantwerpen.be/en/summer-schools/digital-humanities--/). This is a one-week summer school organized by the [Antwerp Centre for Digital humanities and literary Criticism](https://www.uantwerpen.be/en/research-groups/digitalhumanities/) (ACDC). 

The course was first taught in Antwerp in 2018 (3-7 September), and an adapted version was taught again in 2019 (1-5 July). In the course, students learn how to set up a IIIF-compatible image server ([iipimage](http://iipimage.sourceforge.net)) on a local network of [Raspberry Pi](https://www.raspberrypi.org) computers, to ultimately re-use and manipulate each other's images using the IIIF protocol. 

The summer school's first edition was generously sponsored by the University of Antwerp's [Literature Department](https://www.uantwerpen.be/en/faculties/faculty-of-arts/research-and-valoris/departments/department-of-literature/), the [Antwerp Summer University](https://www.uantwerpen.be/en/education/international/international-students/antwerp-summer-university/), the Flemish Government's [Department of Economy, Science, and Innovation](https://www.ewi-vlaanderen.be), [Digital Humanities Flanders](http://uahost.uantwerpen.be/platformdh/index.php/dhu-f/) (DHu.F), and [DARIAH-BE](http://be.dariah.eu) – the last of which provided us with the course's hardware and the opportunity to develop these tutorials further. 

These tutorials are published under a Creative Commons Share Alike licence ([CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)). This means that you can re-use (share and adapt) these slides provided you provide sufficient attribution and publish and distribute the result under the same license.

.bottomcenter[[.margins[![Digital Humanities Flanders](img/logos/dhuf.svg)]](http://uahost.uantwerpen.be/platformdh/index.php/dhu-f/) [.margins[![ewi-vlaanderen](img/logos/ewi.svg)]](https://www.ewi-vlaanderen.be) [.margins[![DARIAH-BE](img/logos/dariah.svg)]](http://be.dariah.eu) [.margins[![CC-BY-SA 4.0](img/logos/ccbysa.svg)]](https://creativecommons.org/licenses/by-sa/4.0/)]