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

So now would be the time to dig into the second part of  our [Short Introduction to the Command Line](commandline.html). 

Or, to freshen up your skills [Command Line Cheat Sheet](cheat.html).]

---

###1. SSH Connect

On your laptop (the one that is connected to the `IIIFarm` WiFi) open a [Command Line Interface](commandline.html#what). Here, enter:

```bash
ssh pi@your.ip.address
```

and confirm with enter.

On your first login to a new resource you will get a security warning. Confirm by typing:
```bash
yes
```

You will be prompted for your RPi's password. Type in [the password that you've set up for your RPi](step2.html#pw), and confirm with `enter`.


.note[**You are now connected to your RPi!** Everything you do on this ssh shell is executed on the raspberry. Working on the ssh shell is like working on a terminal directly on the raspberry.]

---
name: clexp1
###2. Creating Files and Directories

.note[**Note:** at this point, your tutors should have _either_ already put a folder on your RPi's `Desktop`, _or_ prepared a **USB-stick** that passes around while you complete this exercise. In the second case, when you get the USB, you can turn your RPi's monitor on, plug the USB into the RPi, and copy the directory with your RPi's name onto your `Desktop`. (The **whole** directory, **not just the files that are inside**). When this is done, turn the monitor off again, and continue with the following exercise.]

**Command Line Exercise: Part 1** (You can use the [cheat sheet](cheat.html#toc))
* Navigate to the `Desktop` 
* Create a new directory called `html`
* Navigate into that directory
* Create a new document in that folder, called `index.html`
* Also create a new directory in that folder, called `images`
* Verify that your `html` directory now containes an `index.html` file and an `images` subdirectory


.note[**Note:** To continue beyond this point, you will need the folder provided by your tutors to be copied to your `Desktop`.]

---
name: clexp2
###2. Creating Files and Directories

**Command Line Exercise: Part 2** (You can use the [cheat sheet](cheat.html#toc))

* Check your Present Working Directory
* Navigate back to the `Desktop`
* Verify that the Desktop has two directories: `html` and one with `your_RPi_name`
* Navigate into the directory with `your_RPi_name`
* List the contents of this directory

.note[As this list will show, the directory contains 2 `.png` images, and one `.jpg` image. The `.png` images are high-resolution facsimile images of random pages of the first draft of Mary Shelley's _Frankenstein_. For this tutorial, they are your institution's pieces of the Monster we are creating.] 

* Copy these contents into the following directory: `/home/pi/Desktop/html/images`
* Navigate into that directory, and verify that it indeed contains these three images
* Rename the `.png` images using `mv`. Their new names should be `image1.png` and `.image2.png`

.note[Let a tutor know that you have finished the exercise. They will double-check with you that everything is where it is supposed to be (and named with the correct names). This is crucial for the next step.]


---

name: html

###3. Creating a HTML Document in `nano`

.exercise[First, navigate back to the `html` directory on your `Desktop`.]

Now open the `index.html` file with `nano`:

```bash
nano index.html
```

Now you can use the command line text editor [nano](step3.html#nano) to write the following code into the file:

```html
<html>
    <head>
        <meta charset="utf-8" />
        <title>My Institution's Page</title>
    </head>
    <body>
        <h1>Welcome to [your_RPi_name]</h1>
        <p>See our beautiful pieces of the Monster:</p>
        <img src="images/frankenstein.jpg" style="width:300px;" />
    </body>
</html>
```

.question[Take a closer look at the code. **Can you figure out what it does?**]

???
```bash
cd /home/pi/Desktop/html
```
---

###3. Creating a HTML Document in `nano`

The code we just wrote  in `nano` is written in a language that your browser can read: `html`. This means that if you open it in your browser, it will display the document _as if_ it were an online web-page. 

In the code, the following line will load an image from your `html/images` directory, and resize it to a `width` of `300px` in your browser:

```html        
<img src="images/frankenstein.jpg" style="width:300px;" />
```

.question[Notice that we are using the `.jpg` image for our webpage, not the `.png` images. **Why could using the** `.png` **images be a bad idea?**]

When you're satisfied that the file is copied correctly into your command line through `nano`, save the file with `Ctrl+o`, and quit `nano` with `Ctrl+x`.

---

###4. Local vs. Online Webpages.

Now you can quickly **switch your RPi's monitor on again**, and use the GUI to navigate into the `html` folder on your `Desktop`, and double-click the `index.html` file. This will open the file in your browser. You should now see the webpage we created, with some text, and the `frankenstein.jpg` image from your `images` embedded into it.

Unfortunately, this website is **only** accessible **via the browser on your RPi**. It is only saved locally on the RPi, it is not _online_ in our network. In other words, there is no way yet to access this `index.html` file from a browser **on your laptop**.

To make our materials accessible to other devices in our network **via the browser** (rather than via the command line), we will now need to set up a web server environment on the RPi. 

---
class: center, middle, darkslide

#Done!
.yellow[Move to [Step 5](step5.html) to set up a web server environment on the RPi.]

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