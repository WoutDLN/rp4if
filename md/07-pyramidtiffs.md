class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 7:]

#Pyramid TIFFs for IIPImage Server

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 6](step6.html)]

---

### Introduction

.flexbox-ltr[
.boxitem[

IIPImage, [the image server we've now installed on our RPis](step6.html) is an **advanced, high-performance** image server that allows for the web-based streamed viewing of **ultra-high resolution images** – which is exactly what we need. 

This means that (as long as they have a somewhat decent internet connection), our users can visualize the high-resolution images in our collections in their browsers at very **high speeds**, and zoom in and out on the image with ease. 

For this to work, to make the system as fast and efficient as possible, IIPImage server requires us to load our images in a specific format: a _tiled, multi-resolution_ format. There are a couple of tiled image formats out there, but we will be working with **Pyramid TIFF** images, because it is supported natively by IIPImage. You could also use JPEG2000, but this would require a proprietary codec. 
]
.boxitem[
<img src="img/step7/pyramid.svg" width="500px"/>
]
]

---

### Introduction

.flexbox-ltr[
.boxitem[

A multiresolution image, like a Pyramid TIFF, is actually a bunch of different versions (in different resolutions) of the same image, **all stored in a single file**.

You start with one, **high resolution image**, and you let the computer make a series of **lower resolution copies** of that image. First at half the resolution, then at a quarter, an eight, etc. 

The computer then maps these images onto one another by using **tiles**: it cuts each image in the same number of pieces (_tiles_), and remembers which tile corresponds to which tile on the corresponding level in a different resolution. 
]

.boxitem[
<img src="img/step7/pyramid.svg" width="500px"/>
]
]

---

### Introduction

.flexbox-ltr[
.boxitem[

This allows you to **quickly move from one resolution level to the next** by zooming in an out of the image. 

And that is exactly the job of an image server like IIPImage: to **decide which version of the image the user needs** as she is zooming in and out, and to **serve** them that image **quickly and efficiently,** on the fly.
]

.boxitem[
<img src="img/step7/pyramid.svg" width="500px"/>
]
]
---

### 1. Install Image Processor: VIPS

To convert our high-resolution images into Pyramid TIFFs, we will first need to install another package on our RPi – this time we need an **image processor**. There are a couple of different options available for this, but we'll use the software package **VIPS**.

Use `apt-get` to install the package `libvips-tools`:

```bash
sudo apt-get install libvips-tools
```

--

### 2. Find Your Images

.exercise[**Exercise:** Change to the folder `/var/www/html/images/`. [At an earlier stage](step4.html#clexp2), we stored two _Frankenstein_ facsimile images in this folder: `image1.png` and `image2.png`. Make sure they are still there using `ls`.
]

---

### 3. Transform Your Images

To transform these `.png` images into (tiled pyramid) `.tif` images, run the following command:

```bash
sudo vips im_vips2tiff image1.png image1.tif:deflate,tile:256x256,pyramid
```

Once you've hit `enter`, wait until the processing is done. This can take several minutes, because Pyramid TIFFs are huge files. 

.exercise[**Exercise:** Once the first image is processed, move on to the second image. Afterwards make sure, both `.tif` files (`image1.tif` and `image2.tif`) are in the folder, alongside to the `.png` files – which should still be there too.]

---

### 4. Copy the Pyramid TIFFs to the Image Server's Data Directory

Just like Apache stores the accessible documents in a specific data directory (`/var/www/html`, see [Step 5](step5.html#contentfolder)), our IIPImage server also has a directory where our images need to be stored. [Earlier](step6.html#imgdir), we've set this directory to `/var/www/iipimage-server/`.

In order to make our images accessible via the image server module (and not only via apache) we have to copy (`cp`) them into this folder. 

```bash
sudo cp image*.tif ../../iipimage-server/.
```

--

Have a look at this command and think about the following questions:

.question[

1. Can you think of a reason for using `cp` instead of `mv` here?
2. Do you see any problems with this approach in a real-life scenario?
3. How does the command process both images simultaneously?
3. What kind of a path is `../../iipimage-server/.`?
4. What is the function of the `.` at the end?

]

---

### 4. Copy the Pyramid TIFFs to the Image Server's Data Directory

.note[**Note:** `../../` only works as long as you are in the `/var/www/html/images/` folder. It would not lead to the correct target from any other `pwd`. An alternative would be to use an [absolute path](commandline.html#relative).]

---

class: center, middle, darkslide

#Done!
.yellow[Move to [Step 8](step8.html) to access your image server in your browser.]

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