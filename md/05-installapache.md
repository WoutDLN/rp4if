class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 5:]

#Set Up a Web Server on Your RPi

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 4](step4.html)]

---

##Introduction

In [the previous step](step4.html#html), we have created a document that a browser can read: `index.html`. As the file's extension already suggests, this document is written in `html`, or **HyperText Markup Language**. 

That `html` is a markup language explains why it is structured with so many angled brackets (like `<html>` for example). But we won't go into that here. What's more important for us now, is that this document is a **hypertext** – a text that is potentially linked with other text, through what are called **hyperlinks**. This is basically how the internet functions. When you visit a **site**, you arrive on a specific **page** (typically the homepage) that contains a small part of all the site's information. This information is distributed among a series of such pages, that you can navigate to (or **browse**) by clicking on the many **links** between the pages. Each of these pages is typically an individual `html` document.

We visit these pages through use our **browser** (Firefox, Chrome, Safari, Internet Explorer, etc.). As the word _visit_ suggests, these pages are typically not stored locally, but elsewhere – on a faraway server in an undisclosed location. To be able to communicate with these servers, the browser uses `HTTP`, or **HyperText Transfer Protocol**. That is why the links of web pages usually start with `http://` (even though at first sight most modern browsers hide this information from the address bar). 

In this act of communication, a _request_ is sent by the **client**, typically a browser – an application that you host on your computer. And the _response_ is sent by an application hosted on another computer – typically a **web server**: an application that serves web pages to browsers. It is this type of application that we will now be setting up on our RPi, so the browsers inside of our network can access the web pages on our RPis. 


---

### 1. Update APT Package Lists

We can download and install software (like the web server that we need) via APT (or: Application Package Tool). This is basically an **app store** for Debian – the Linux-based operating system that your RPi's is built on. More specifically, the command line command we can use to download and install software from APT is `apt-get`.

Before we do that, however, it's good practice to first run the following command:

```bash
sudo apt-get update
```

This command will update APT's package list – a list of links to the public repositories where the most up-to-date versions of APT's software packages are hosted. In other words: this command makes sure that when you use `apt-get` to download and install a specific software package, that it uses the most up-to-date version of that software to do so.

---
name: fcgid

### 2. Install Apache2 (with fcgid)

Now it's time to download our software! The web server that we're going to use is the commonly used Apache2 webserver. In addition, we also need to install one of Apache2's modules (a kind of _sub-software-package_) called `fcgid`. 

With `apt-get install`, you can line up a series of software packages to install them all with a single command.So go ahead and run:

```bash
sudo apt-get install apache2 libapache2-mod-fcgid
```

On running this command, `apt-get` will inform you if the software has any dependencies (other software that needs to be downloaded), and tells you how much disk space these downloads will take up on your RPi. You'll have to confirm with `y`, and wait until your packages are downloaded and installed. As we're all on the same network and the RPi's aren't very fast, this may take a while.  

---

### 3. Start Web Server

Once the software is downloaded, we can start it up on the RPi. Run:

```bash
systemctl start apache2
```

Here, you will be asked which user you want to use to run the Apache2 service. Choose `1` (pi) and confirm with `enter`. The command line will then prompt you for a password, so type in [your RPi's password](step2.html#pw) and confirm by hitting `enter` again. 

The command we've just run – `systemctl` – is a utility to manage (start, stop, restart) services on your RPi (like the Apache2 service we've just installed). We'll be using it a lot in this tutorial, so make sure you remember your RPi password!

--

### 4. Test Apache

Before we do anything else, we'd like to make sure that our Apache **webserver is actually running**. On your computer, open a browser, enter [your RPi's IP Address](step3.html#ip) into the browser's address bar, and confirm with `enter`.

You should now see the Apache2 Debian Default Page. On the top of that page, in a red banner, you’ll read **“It works!”**

---

name: contentfolder

### 5. Viewing Your Website

.question[Apache grants external (browser) access only to select folders on your system. Anything more than that would be crazy. **Can you tell why?**]


--

By default only contents that are in the folder `/var/www/html/` are accessible. Although this folder could be changed (e.g. to your `Desktop`, or a folder in your `Documents`) doing so is **not considered good practice**. 

Instead of relocating the folder Apache points to, we move our content (those files we want to access via the browser) to the default folder.

--

.exercise[**Exercise** ([cheat sheet](cheat.html#toc))

Copy the `html` folder from the `Desktop` to `/var/www`. Tip: remember that you will also need to copy all **subdirectories** and their contents.]

---
### 5. Viewing Your Website

Now you can enter your IP address into the browser of your laptop. If everything went well, you can load the website from your RPi (which now functions as your server) on your laptop (which funtions as the client). 

.warning[**Warning!** Note that the other people in your network (in this case: this room) can also access your website via their browsers now. If you would be connected to the internet, this could open up your files to the rest of the world.]

???
.solution[**Solution:** 
```bash
	sudo cp -r /home/pi/Desktop/html/ /var/www/
```]
---

### 6. Viewing Each Other's websites

When [your tutors received your RPi's IP addresses](step) earlier, 

---
class: center, middle, darkslide

#Done!
.yellow[Move to [Step 6](step6.html) to set up an image server on your RPi.]

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