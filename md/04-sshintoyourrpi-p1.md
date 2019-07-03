class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 4:]

#SSH into your RPi

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 3](step3.html)]

---

class: darkslide, middle, center

.note.center[We will now start to control our RPi from a different system (your laptop) using the **command line.** At several points in this tutorial, you will be asked to **write your own commands.**

So now would be the time to dig into the second part of  our [Short Introduction to the Command Line](commandline.html#part2). 

Or, to freshen up your skills [Command Line Cheat Sheet](cheat.html).]

---

###1. SSH Connect

On your laptop (the one that is connected to the `IIIFarm` WiFi) open a [Command Line Interface](commandline.html#what)..marginicon[<img src="img/icons/terminal.png" height="25px"/>] Here, enter:

```bash
ssh pi@your.ip.address
```

and confirm with `enter`.

On your first login to a new resource you will get a security warning. Confirm by typing:
```bash
yes
```

You will be prompted for your RPi's password. Type in [the password that you've set up for your RPi](step2.html#pw), and confirm with `enter`.


.note[**You are now connected to your RPi!** Everything you do on this ssh shell is executed on the raspberry. Working on the ssh shell is like working on a terminal directly on the raspberry.]

---
name: clexp1
###2. Creating Files and Directories


**Command Line Exercise: Part 1** (You can use the [cheat sheet](cheat.html#toc))
* Navigate to the `Desktop` 
* Create a new directory called `html`
* Navigate into that directory
* Create a new document in that folder, called `index.html`
* Also create a new directory in that folder, called `images`
* Verify that your `html` directory now containes an `index.html` file and an `images` subdirectory


---
name: clexp2
###2. Creating Files and Directories

**Command Line Exercise: Part 2** (You can use the [cheat sheet](cheat.html#toc))

* Check your Present Working Directory
* Navigate back to the `Desktop`
* Verify that the Desktop has at least the following two directories: `html` and one with `your_RPi_name`
* Navigate into the directory with `your_RPi_name`
* List the contents of this directory

.note[As this list will show, the directory contains 2 `.png` images, and one `.jpg` image. The `.png` images are high-resolution facsimile images of random pages of the first draft of Mary Shelley's _Frankenstein_. For this tutorial, they are your institution's pieces of the Monster we are creating.] 

* Copy these contents into the following directory: `/home/pi/Desktop/html/images`
* Navigate into that directory, and verify that it indeed contains these three images
* Rename the `.png` images using `mv`. Their new names should be `image1.png` and `.image2.png`

.note[Let a tutor know that you have finished the exercise. They will double-check with you that everything is where it is supposed to be (and named with the correct names). This is crucial for the next step.]



---
class: center, middle, darkslide

#Done!
.yellow[Move to [the second part of this step in the tutorial](ssh2.html) to create a `html` page in `nano`.]

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