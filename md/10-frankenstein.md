class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 10:]

# Frankenstein 
.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 9](step9.html)]

---

## 1. Loading Manifests in Mirador

On his laptop, that is also connected to our IIIFarm, Josh also has a version of Apache running, that should make data from his laptop accessible to you. 

In his web-shared folder he installed a version of **Mirador,** a IIIF compliant image viewer with a couple of nice features such as deep zooming.

But one of this viewers coolest features is, that you can load IIIF manifests “dynamically” if you have the `URL` of the manifest.

Luckily, each team knows the `URL` of their manifest, you have just entered it in your browser.

Lets load them all - one by one - in Mirador.

Load Josh’s Mirador instance on your own IIIFarm-connected laptop and add your own manifest.

```bash
http://joshs.laptop.ip]/mirador
```

Play with the viewer. Make yourself  familiar with the functionality it provides. Then load some of the manifests of other teams into the viewer too.

---

## 2. Adding Metdata to the Manifest

At this point, your IIIF manifests do not yet provide a lot of metadata. 

Let’s first experiment by improving what is there already. Open your manifest (`frankenstein.json`) with `nano` and edit the existing JSON data.

.warning[**Warning:** Try not to change the file's structure and don’t change the `id`s.]

What you enter here does not have to make sense for now, but whenever you change something, save the file (hit `CTRL+o`, then `enter` – **but don’t exit nano!**) and reload your manifest in the Mirador viewer.

Try to see how mirador views the `JSON` data you changed. Which change is visualized where?

On the initial image folder we gave to you (`/home/pi/Desktop/yourPisName/images/`), your `.png` imagess still had individual names. Their name (a number) was the position of the image in the sequence of the entire notebook. 

.exercise[Try to get this information into your canvas information. For example: if your files were called `023.png` and `024.png`, make sure that your canvas for `image1.tif` reads `“Page 23”`, and `image2.tif` would correspond to `“Page 24”`, etc.] 

---

## 3. Including Other Teams' Manifests 

Dries explained canvases and how to sequence them earlier. You have one sequence with two canvases, one for each image.

.exercise[**Exercise:**

1.  Study the canvas area of your manifest. Open another team’s manifest and look at their `JSON`. **Find their canvases** 

2. Figure out if their two images should come _before_ or _after_ your own images.

3. Try to copy their canvases from their manifest into your manifest: find the right position to add their canvases (either before or after your own canvases) copy them there.

4. Load your manifest again in mirador. **Did it work?** If not… _debug!_

5. Add the canvases of at least two other teams at the correct position in the sequence.]

---

## 4. Finding the Missing Information Online

Maybe you would be happy to have more real metadata in your manifest.

Luckily, the [Shelley Godwin Archive](http://shelleygodwinarchive.org) recently published the entire notebook in IIIF. Here is the corresponding blog post:

```bash
https://blogs.bodleian.ox.ac.uk/digital/2017/08/16/iiifrankenstein/
``` 

Can you find the manifest? You cannot load it in our instance of Mirador (because we don’t have internet) but you can load the `JSON` manifest on your internet-connected laptop and use the given information to improve your own manifest.

---

class: center, middle, darkslide

#Done!
.yellow[IS THIS THE END?]

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