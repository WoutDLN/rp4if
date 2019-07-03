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

## 2. On Reusing Other Peoples' Images

Now that we have edited the `index.html` file in RPI's `/var/www/html` directory, your self-made web page seamlessly loads from other servers (in this case: your neighbours' RPis). We are all in a small, closed network, where we all know each other We know how we are all reusing these images – images that have been added to this networke server farm for exactly that purpose.

.question[**Question:** Think about what this would mean if we would open this up to the wider internet. Would you like anyone with access to the internet to be able to do this kind of stuff with your own data? Why? Why not?]

--

.note[**Note:** To be clear: **there is nothing illegal about what we are doing here.** We are **not** _stealing_ these images. We are **not** downloading copyrighted materials, and hosting them ourselves to redistributing them. Instead, we are just linking to images that are hosted elsewhere.]  

--

Still, although we don’t steal the image from the other server (we only embed their `URL`s), it seems somehow unfair _not to give the other team proper credit for their work._ 


---

## 3. IIIF Manifests


So wouldn’t it be nice if we could also **embed additional metadata** about each image (or even an entire collection of images) directly from the server of the image provider? In a computer readable, standardized format? 

This would allow us to give credit where credit is due. And if the original hosts have enriched their images in any way (with dates, transcriptions, annotations, etc.), we might want to reference those, or reuse them in our website in some way too.

--

.note[IIIF provides a solution for this: **IIIF Manifests.** ]

--

A IIIF manifest is a container file (in the `JSON` format), that contains metadata about an image collection as well as the IIIF compliant `URL`s to the contained images.

For now, we will only look at a simple example, in detail we will learn about manifests and IIIF compliant image annotation later.

---

## 3. IIIF Manifests

We want to use an IIIF compliant Image Viewer called **Mirador** to view and join our images. Mirador does not want simple IIIF image `URL`s, but it expects manifest files in order to view images dynamically and including the annotated metadata.

The manifest file is usually provided by the institution that also provides the images. **This means: Each group has to create a manifest file for their image collection now.** 

Luckily we all named our images the same way, so we can all use the same  _dummy manifest_ (without really understanding it - yet). In this dummy manifest we simply change the IP address of the contained URLs to our individual server.

---

## 4. Download A Sample Manifest

Go to the data directory of your apache server:

```bash
cd /var/www/html/
```

Use `wget` (a **Terminal** program to download web contents) to download the dummy manifest from Joshua’s private server (yes, this is a _real_ real server):

```bash
sudo wget http://62.75.186.162/frankenstein.json
```
 
Then, make sure that the file is in your current working directory by listing the contents using `ls`.

.exercise[**Exercise:** Now, open `frankenstein.json` file with `nano` (don’t forget `sudo`!).]

---

## 5. Adapt the Manifest to Your Needs  

At this point, you don’t have to understand the file you're reading in `nano`. 

.exercise[**Exercise:** Instead, just replace all instances of the string `MY_IP_ADDRESS` with your actual IP Address.] 

.warning[**Warning:** If you make a mistake here, your manifest will not work later. **There should be 10 instances for you to replace.** Go through slowly line by line.] 

--

.exercise[**Exercise:** Go through the file again, looking for the line `"label": "Team [PI Name]",` (line 9). Now, replace the string `[PI NAME]` by **the name of your Raspberry Pi**.]

Once you are done, save (hitting `Ctrl+o`, then `enter`) and exit nano (`Ctrl+x`).

---

## 6. Double Check that the File Loads

Check in the browser if your manifest is publically accessible. Open the laptop browser and enter:

```bash
your.ip.address/frankenstein.json
```

The manifest `JSON` file should load in your browser. 

--

.note[**Congratulations!** You are now ready to assemble your piece of the monster!]

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