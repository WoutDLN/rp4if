class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 9:]

# Reusing IIIF Images 
.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 8](step8.html)]

---


## 1. Include Images in your `html` Web Page.

Now that we have a series of links to images (our own as well as our neighbours'), we can embed their `URL`s into our `html` page to incorporate them in our websites.

Open the `index.html` file [we created earlier](step4.html#clexp1) with `nano`: 

```bash
sudo nano /var/www/html/index.html
```

In this file, add the following two lines after the `frankenstein.jpg` image:

```bash
<br/><img src="your.ip.address/iipsrv/iipsrv.fcgi?IIIF=image1.tif/full/400,/0/default.jpg" />

<br/><img src="your.neighbours.ip.address/iipsrv/iipsrv.fcgi?IIIF=image1.tif/full/400,/0/default.jpg" />
```

**Copy these links carefully** – although you will of course have to to **change the IP addresses** in these `URL`s with [the ones you came up with earlier](step8.html#accessurimg).

Save the `index.html` file (hit `Ctrl+o`, then `enter`) and exit `nano` (hit `Ctrl+x`). Then enter your RPi’s IP address in your browser (on the laptop!) again, and look at the effect your changes had on your website.


---

class: center, middle, darkslide

#Done!
.yellow[Move to [Step 10](step10.html) to start assembling the monster!]

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