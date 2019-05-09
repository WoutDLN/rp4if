class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 6:]

#Install the IIPImage Server on Your RPi

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 5](step5.html)]

---

##Introduction

In [the previous step](step5.html), we installed Apache – a **web server** that allows each of us to host web pages (such as [our own page](step4.html#html) in `html`) and share them within our [network](step1.html). 

As we've seen, we can easily hard-code images into such `html` web pages (by providing a link to the image in the `@src` attribute of an `<img>` tag) – but that is not enough for our purposes. Instead, we need to install a dedicated **image server** alongside our web server, to process the images on the fly. 

For that, we will install a **IIIF-compliant** image server called **IIPImage**.

--

.question[**Question:** even if our website didn't have to be IIIF-compliant, what would the benefet be of installing a dedicated image server for your website?]

---
name: imgdir

### 1. Install the IIPImage-Server

Install the package `iipimage-server` by entering the following command: 

```bash
sudo apt-get install iipimage-server
```

You will have to download some dependencies (between 50-100MB), confirm with `y` and wait until the image server is installed.


--

### 2. Change the image server's data directory

By default, the data directory of the image server is under `/usr/lib/iipimage-server/`. We want to change this to `/var/www/iipimage-server/`. 

To do so, we have to copy the folder over to `/var/www/` and tell the image server where the data directory has moved.

.exercise[**Exercise:** copy the `iipimage-server` directory from `/usr/lib/` to `/var/www`. When you are done, check that the folder has really been copied (e.g. change directories to the new folder and list its contents).]

---

.solution[**Solution:**```bash
sudo cp -r /usr/lib/iipimage-server/ /var/www/iipimage-server/ 
```]

To use the image server in our website, we need to run it as an Apache module. Such modules are configured in the directory `/etc/apache2/mods-available/`. 

**Change to this directory.**

Now we need to open the image server's **config file** with `nano` so we can make some changes (don’t forget the `sudo`!). the config file is called `iipsrv.conf`.

```bash
sudo nano /etc/apache2/mods-available/iipsrv.conf 
```

In this file change the following line: 

```bash
ScriptAlias /iipsrv/ "/usr/lib/iipimage-server/"
```

to:

```bash
ScriptAlias /iipsrv/ "/var/www/iipimage-server/"
```

Save the file (with `Ctrl+o`, and hit `enter` to confirm) and close nano (`Ctrl+x`). Now once we enable the module, apache knows where we put the image server's data directory, and the two servers can work together.

---

### 3. Enable the necessary Apache modules for the image server

First, we want to double check that the `fcgid` module is enabled. Since [we installed it earlier](step5.fcgid), this should already have happened by default. Enter:

```bash
sudo a2enmod fcgid
```

You should now see a message that confirms that `fcgid` was already enabled. Next, we need enable the `headers` module. Enter:

```bash
sudo a2enmod headers
```

If one of these two modules was not enabled before, you will have to restart apache now. In that case, enter:

```bash
systemctl restart apache2
```

Finally, we'll want to check if our image server's module (`iipsrv`) is enabled too. Enter:

```bash
sudo a2enmod iipsrv
```
Now that all three modules are definitely enabled, we need to **restart Apache** (again). Enter:

```bash
systemctl restart apache2
```
---

### 4. Enable CORS

In the image servers configuration file we have to enable “cross origin resource sharing” (CORS). It is important to enable this setting to make sure the image server is IIIF-compliant, because it allows others to embed your images into their website. 

.question[**Question:** Outside of the IIIF community, the general rule in web development is not to enable CORS in any event. **Can you guess why?**]

--

To enable CORS, open the apache configuration file with `nano`.

```bash
sudo nano /etc/apache2/apache2.conf
```

Move down (arrow-down key `↓`) to the end of the file and add the following line:

```bash
Header set Access-Control-Allow-Origin *
```

Make sure there are no spelling mistakes in this line! Save the file (`Ctrl+o`, `enter`) and leave nano (`Ctrl+x`).

And, again, Apache needs to be restarted:

```bash
systemctl restart apache2
``` 

---

### 5. Check if your IIPImage Server is running

Finally, we'll want to make sure that everything is working correctly, and that the image server we just configured is actually running. 

In your **laptop's browser** go to:  

```bash
your.ip.address/iipsrv/iipsrv.fcgi
```  

If the IIPImage Server start screen appears, your server should run correctly. 

Well done!

---

class: center, middle, darkslide

#Done!
.yellow[Move to [Step 7](step7.html) to produce pyramid `.tiff` images for the IIPImage Server.]

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