class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 8:]

#IIIF Parameters

.yellow[Largely based on `<HANDS:ON>` a [digital training programme for medievalists](https://projects.history.qmul.ac.uk/handson/) organised by Cambridge University Library and Queen Mary University of London]

.bottomleft[.mirror[&#10148;] Back to [Step 7](step7.html)]

---

## 1. What is IIIF?

‘IIIF’ is a big buzzword in digital libraries and digital humanities right now. You may not have heard of it, but if you have you may be wondering why it should matter to you.

The IIIF (International Image Interoperability Framework) is two things:

- A **community** of research libraries and image repositories working towards the same goal — to make it easy for people to access and use their images;
- A **standardised** way that online image libraries should share their images to make them open, capable and compatible with each other.

---

## 1. What is IIIF?

If a digital library or repository says its images are ‘IIIF compatible’ or ‘IIIF enabled’, it means that you can:

- **Download** an image freely (although it may have license restrictions on how you can use it, which you should check);
- **Manipulate** the size, scale, crop, rotation, quality and format (without having to use editing software on your own computer e.g. Photoshop, and without affecting the original image);
- **Zoom** and pan around an image when viewing it;
- **Collect** images from different books, manuscripts (etc.) and compare them side by side, even if they come from completely different collections on different sides of the world;
- **Cite** and share an image at a stable web address (URL);
- **Annotate** an image with freeform drawings and text, and share those annotations with others (if a digital library has enabled this feature).


???
If a digital library or repository says its images are ‘IIIF compatible’ or ‘IIIF enabled’, it means that you can:

- **Download** an image freely (although it may have license restrictions on how you can use it, which you should check);
- **Manipulate** the size, scale, crop, rotation, quality and format (without having to use editing software on your own computer e.g. Photoshop, and without affecting the original image);
- **Zoom* and pan around an image when viewing it;
- **Collect** images from different books, manuscripts (etc.) and compare them side by side, even if they come from completely different collections on different sides of the world;
- **Cite** and share an image at a stable web address (URL);
- **Annotate** an image with freeform drawings and text, and share those annotations with others (if a digital library has enabled this feature).

IIIF means you are guaranteed to be able to do these things! IIIF is like a promise to you and other students, scholars and users around the world. 

The important thing to realise is that while the IIIF specifications are very technical, you do not need to understand them in any detail to take advantage of everything that IIIF has to offer. IIIF is a fairly new technology, and the community is still trying to work out all the details and get everything right. Once this groundwork has been done, and most digital libraries use IIIF, it will become so normal that no-one will really need to mention IIIF anymore. As a user, you will just get the great experience you have come to expect.

---

## 2. Where to find IIIF images

Most places will use the IIIF logo (below) to indicate that they are compliant with the standards.

.center[<img src="img/logos/iiif.svg" width="300" style="padding-left:125px;padding-right:125px"/>]

Currently, there is no simple way of finding a definitive list of IIIF-enabled repositories, but it is one of the things the IIIF community is working on. They want to make it easier to search for IIIF images within collections and discover IIIF images across different collections. This part of their work is not ready yet, but it promises to be a revolution when it is.


---
background-image: url(img/iiif/web.png)

---

## 2. Where to find IIIF images

Meanwhile, here are just a few collections that have well-established IIIF offerings:

- [Cambridge Digital Library](https://cudl.lib.cam.ac.uk/)
	- (example: [Newton’s Early Papers](https://cudl.lib.cam.ac.uk/mirador/MS-ADD-03958/0))
- [The Wellcome Library](https://wellcomelibrary.org/)
	- (example: [Rosalind Franklin Papers](https://wellcomelibrary.org/item/b19832023#?c=0&m=0&s=0&cv=5&z=-0.637%2C-0.0714%2C2.2739%2C1.4284))
- [Yale Centre for British Art](https://britishart.yale.edu/collections)
	- ([example Turner 1818](https://collections.britishart.yale.edu/vufind/Record/1667701))
- [The Bodleian Library](https://digital.bodleian.ox.ac.uk/)
	- (example: [Hertford Atlas](https://digital.bodleian.ox.ac.uk/inquire/Discover/Search/#/?p=c+5,t+%22Hertford%20Atlas%22,rsrs+0,rsps+10,fa+,so+ox%3Asort%5Easc,scids+,pid+3a2abefb-865b-4ab9-a3b2-e5d203e7d9b3,vi+))
- [University of Heidelberg](https://www.ub.uni-heidelberg.de/Englisch/helios/digi/digilit.html)
	- (example: [Codices Trübner](https://digi.ub.uni-heidelberg.de/diglit/codtruebner8/0001/thumbs))

---

## 3. Advantages for Digital Humanists

Let’s imagine for a moment the typical way you might go about a project to study some medieval manuscripts that are scattered in several different collections around the world. Before you apply for funding to cover your travel you want to see what they have available and perhaps do some preliminary research on the materials. (Here we make the assumption that what you want to see has been digitised — this may not be the case, of course!)


---

## 3. Advantages for Digital Humanists

### Research **without** IIIF

Here is a typical workflow you might recognise:

1. You search around the web to find websites or digital libraries that have images of the manuscripts you want.

--

2. You search through each website in turn for the manuscripts.

--

3. You manually download all the images you are interested in to your computer, one by one.

--

4. You want to compare the images of particular pages, so you open them in a program on your computer. You open each one individually in a different window and then arrange them on your monitor. Perhaps you print them out and arrange them on your desk.

--

5. After having travelled to one of the libraries on your list, you sit down with a real manuscript and start to work, with a notebook, a pencil and a printout of a manuscript from a different collection.

--

6. Having made an exciting discovery, you want to insert two images of comparable manuscripts in a slide for a talk you are giving. You open an editing program and crop them to the size you want and save them as new images. You insert them into your slide ready to go to the conference.

---

## 3. Advantages for Digital Humanists

### Typical Challenges

With this use of digital tools you may face some challenges:

- You are not sure of the provenance of the images on some of the websites you have found.
- It takes a long time to download all the images and it’s really boring to do it by hand.
- The images are very big and take up a lot of room on your computer’s hard drive.
- You end up with many folders with subfolders of images, and it’s hard to keep track of what is what.
- Your computer restarts (after a software update) and you lose your careful arrangement of images.
Some of the images are poor quality, but they were the only ones you could find.
- The printout is poor quality and you cannot quite make out the detail you need to make a proper comparison.
When you get home you find it is hard to attribute some of your handwritten notes to the relevant parts of the manuscript.
- You want to add a citation for the images on a talk slide, but you can’t remember exactly where you got them.
- Your slide does not really show the features of the manuscripts you want to talk about in any detail.

---

## 3. Advantages for Digital Humanists

### Research **with** IIIF

- No need for manual download and poor quality.
- No need to fill your hard drive and struggle with image software.
- Print outs aren’t always the right answer.
- Annotate on top of the manuscript if you need to be precise.
- Share your findings with your audience directly.

???
No need for manual download and poor quality.

- Using a simple software tool, you could download all the images from a particular manuscript automatically at the maximum quality available.

No need to fill your hard drive and struggle with image software.

- Using an online viewer, and without having to download anything, you can page through all the pages of a manuscript, and arrange the pages of different manuscripts next to one another for comparison.

Print outs aren’t always the right answer.

- Using the same online viewer, you can pan around the images, zoom in to see small details, rotate to read cross-written text, and convert them to grayscale to explore subtle details. You can take the full resolution of the entire library with you on your laptop or tablet, and always have the metadata/provenance to hand. (Sometimes you do really need a print out, of course.)

Annotate on top of the manuscript if you need to be precise.

- With the right online viewer, you can annotate directly on the digital image of the manuscript, circling the areas of interest and attaching text to the shapes.

Share your findings with your audience directly.

- Give your talk using the online viewer. Arrange the view with just the images you want to show them, zoom in to high-quality detail, highlight the annotations you’ve made, and save time editing a slide deck as well! Share the exact same view with your audience so they can explore for themselves, including the provenance of the images.

---

## 4. Beyond the Basics: Interesting Projects With IIIF Images

- Storiiies: [http://storiiies.cogapp.com/](http://storiiies.cogapp.com/)

- Digital Muṣḥaf Project — virtual reconstruction of dispersed early Qurʾānic fragments
[http://digitalmushaf.bodleian.ox.ac.uk/](http://digitalmushaf.bodleian.ox.ac.uk/
)

- Make your own message from Walters Art Museum MS. 200
[http://blalbrit.github.io/iiif_make_words.html](http://blalbrit.github.io/iiif_make_words.html)

- Mahābhārata Scroll — 72 metres of poetry on silk
[https://collections.ed.ac.uk/mahabharata](https://collections.ed.ac.uk/mahabharata)

---

## 5. Viewing, Annotating, and Manipulating images with IIIF


Shāhnāmah at CDL: `https://cudl.lib.cam.ac.uk/view/MS-ADD-00269/1`

Shāhnāmah Manifest: `https://cudl.lib.cam.ac.uk/iiif/MS-ADD-00269`

Mirador Demo: `http://projectmirador.org/demo/`

---

name: accessmyimg

## 6. Accessing Images in the Browser

Now that we have set up IIPImage, you can access all of the images in your `var/www/iipimage-server` directory in **any browser or IIIF-compliant image viewer** – such as [Mirador](http://projectmirador.org), [Universal Viewer](http://universalviewer.io), [OpenSeadragon](https://openseadragon.github.io/examples/tilesource-iiif/), or [Leaflet-IIIF](https://github.com/mejackreed/Leaflet-IIIF).

When you call an image via an IIPImage server `URL`, the image server will show you this image according to some **parameters** that you have set in the `URL`. **Let's have a look at how this works.**

Open your browser (on the laptop!) and go to:

```bash
your.ip.address/iipsrv/iipsrv.fcgi?IIIF=image1.tif/full/400,/0/default.jpg
```
 
Now, open another tab in your browser and go to:

```bash
your.ip.address/iipsrv/iipsrv.fcgi?IIIF=image1.tif/full/800,/90/grey.jpg
```

Both `URL`s show you the same image, but not in the same way.

.question[**Question:** compare the `URL`s above and try to find out how it influenced the server's presentation of that image in your browser.]

---

name: iiifparam

## 7. Experiment with the IIIF Image API

The IIIF consortium provides a detailed [**documentation** of the **IIIF Image API**'s parameters here](http://iiif.io/api/image/2.0/). Have a look at this documentation, and play with different settings for your images by manipulating the `URL` in the following exercise:

.exercise[
**Exercise:** Reading up on the IIIF parameters, find out how to:

- Rotate your image by `180` degrees
- Retrieve **only a section** of an image
- Retrieve an image with a width of `5000px` and a proportionally scaled height
- Retrieve an image with a `width` of `100px` and a `height` of `300px`
- Display your image in `greyscale`
]

.question[Once you have successfully completed these tasks, experiment some more with other parameters. Some of these parameters may produce an error. **Can you guess why?**]

---

name: accessurimg

## 8. Get the `info.json` from your image server

All the information that you need to build tools that show your images work on the basis of a `info.json` file, which is generated by the server for every image.

enter the following `URL` into your browser:

```bash
your.ip.address/iipsrv/iipsrv.fcgi?IIIF=image1.tif
```

When no further IIIF URL variables are specified, the IIPImage server will forward you to the `info.json` file.

--

## 9. Accessing Each Other's Images

So, each of us now has [a fully functioning RPi](step3.html) with [a web server](step5.html) and an [image server](step6.html), that provide access to a couple of [tiled pyramid TIFF images](step7.html) that we have learned to [access and manipulate](step8.html) with the [IIIF URL parameters](step8.html#iiifparam).

And since all of our RPis are [connected on the same network](step1.html), we can use the same technology that allows us to [view](step8.html#accessmyimg) and [manipulate](step8.html) the images on our own RPi in the browser of our own laptops allow us to do the same with each other's images too.


---

## 10. Accessing Each Other's Images

.question[**Question**: Think back about how you accessed your RPi's images on your laptop. What is the variable here? **What would you need to view your neighbour's images on your laptop?**]

--

.exercise[**Exercise:** Ask your neigbour to give you the information you need to **build IIIF compliant URLs for their images**. Then try to view and manipulate their images using the **IIIF parameters**.]

We will need `URL`s like these going forward. So **save some of these URLS on your laptop somewhere** (like a `.txt` or `.doc` file), so you will be able to copy and paste them.

---

class: center, middle, darkslide

#Done!
.yellow[Move to [Step 9](step9.html) to embed your (and your neighbours') inages into your own `html` page.]

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