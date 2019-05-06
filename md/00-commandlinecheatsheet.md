class: center, middle, darkslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Command Line:]

#Cheat Sheet

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Read our [Short Introduction to the Command Line](commandline.html)]

---

name: toc
class: darkslide
## Table of Contents

A simple cheat sheet for some of the most common command line commands to be used in the [RPi-IIIF Tutorials](intro.html). 

1. [pwd](#pwd)
2. [ls](#ls)
3. [cd](#cd) (& paths)
4. [mkdir](#mkdir)
5. [touch](#touch)
6. [rm](#rm)
7. [cp](#cp)
8. [mv](#mv)
9. [flags](#-r)

.note[**Note:** These commands are all **bash** commands (Unix shell), that work on **Linux-Based Operating Systems**. 

In this tutorial we will be controling our RPi (which runs on the Linux-Based Operating System ([Raspbian](https://www.raspbian.org)) via [SSH](step2.html#ssh). That means that **these commands will work for us, regardless of the type of computer you use** (Windows, Mac, Linux). 

If you are using this cheat sheet for another purpose, keep in mind that some of these commands will need to be adapted to work on Windows systems.]

---

name: pwd
class: darkslide
## Present Working Directory | `pwd`

.yellow[Example command:]

```bash
pwd 
```

.yellow[What does it do?]

Shows you where you are in the terminal. 

.yellow[Example output:]

```bash
/Users/WoutDLN/Documents
```

---

name: ls
class: darkslide
## List | `ls`

.yellow[Example command:]

```bash
ls 
```

.yellow[What does it do?]

Shows you a list of all the documents and folders in your present working directory.  

.yellow[Example output:]

```bash
Applications
Desktop
Documents
Pictures
```

---

name: cd
class: darkslide
## Change Directory | `cd`

.yellow[Example command:]

```bash
cd /Users/WoutDLN/Documents
```
or

```bash
cd Documents
```
or

```bash
cd ..
```

.yellow[What does it do?]

Changes your position in the file system. After typing the `cd` command, you type where you want to move to. An **absolute path** (begins with `/`) brings you to a specific location. A **relative path** brings you to a location relative to where you are currently working (your `pwd`). Using `..` will move you one folder up.

---

name: mkdir
class: darkslide
## Make Directory | `mkdir`

.yellow[Example command:]

```bash
mkdir new 
```

.yellow[What does it do?]

Creates a new folder (directory) in your `pwd`. After typing the `mkdir` command, you type a name for your new folder. In this case the (empty) folder will be called `new`. 

---

name: touch
class: darkslide
## Make File | `touch`

.yellow[Example command:]

```bash
touch newfile.txt
```

.yellow[What does it do?]

Creates a new file in your `pwd`. After typing the `touch` command, you type a name for your new file (preferably ending in an “extension” such as: `.txt` `.html` `.doc` `.pdf` -- so your computer knows how to open it). In this case the (empty) file will be called `newfile.txt`.

---

name: rm
class: darkslide
## Remove File | `rm`

.yellow[Example command:]

```bash
rm new/newfile.txt
```

.yellow[What does it do?]

Erases a file from your hard drive. **Careful!** It will not be recoverable through your “trash” folder. After typing the `rm` command, you type the path (*relative* or *absolute)* to the file you want to remove. 

---

name: cp
class: darkslide
## Copy File | `cp`

.yellow[Example command:]

```bash
cp source.txt Desktop/.
```
or

```bash
cp source.txt Desktop/target.txt
```

.yellow[What does it do?]

Makes a copy of a file. After typing the `cp` command, you type the path (*relative* or *absolute*) of the file you want to copied, and then the path (*relative* or *absolute*) of the place you want to copy it to. In the first example above, the `.` indicates that the name of the file should remain the same. In the second example, putting a new file name at the end of the target path indicates that you want to change the name of the file while copying. In the second example, the copied file will change its name to `target.txt` in the process.

---

name: mv
class: darkslide
## Move File | `mv`

.yellow[Example command:]

```bash
> mv source.txt Desktop/.
```
or

```bash
mv source.txt Desktop/newsource.txt
```
or

```bash
mv Desktop/source.txt Desktop/newsource.txt
```

.yellow[What does it do?]

Moves your file to a new location without copying it. After typing the `mv` command, you type the path (*relative* or *absolute*) of the file you want to move, and then the path (*relative* or *absolute*) of the place where you want to move it too. In the first example, the `.` indicates that the name of the file should remain the same while moving. In the second example, putting a new file name at the end of the end of the target path indicates that you want to change the name of the file while copying. In the third example, the file is only renamed, because the location of the source file and the target file is the same. (In other words: you move a file into the same spot, but rename it in the process). 

---

name: -r
class: darkslide

## Flags

### Recursively | `-r`

.yellow[Example Command:]

```bash
rm -r new
```
.yellow[What does it do?]

Tells the terminal to apply the command to any and all sub-directories or files the selected directory may contain (in this case: the `new` directory). 

---

name: -f
class: darkslide

## Flags

### Forcefully | `-f`
 
.yellow[Example Command:]

```bash
rm -f new
```
.yellow[What does it do?]

Urges the terminal to not ask your permission for any sub-tasks it needs to perform – such as copying or removing [subdirectories and their contents with](#-r) `-r`.

.warning[**CAREFUL:** By using the shell, you are bypassing your system's GUI, which means that the files and directories you delete will no longer be recoverably through your system's trash folder!

**USE WITH CAUTION!** This gives you the power to remove your entire hard drive with a single command!]


---

class: center, middle, darkslide

#Done!

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