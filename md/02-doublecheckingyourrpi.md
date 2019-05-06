class: center, middle, darkslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 2:]

#Double-Checking Your Raspberry Pi's Setup

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 1](step1.html)]

---

name: ssh
##Double-Checking Your Raspberry Pi's Setup
Your tutors should have already set most of the following steps correctly while preparing your RPi for this course, but in some cases a step may have been overlooked. We will double check all these settings now, because they are crucial for the rest of the course.

###1. Make sure that SSH is enabled on your Pi
**SSH** (which stands for: _**s**ecure **sh**ell_) is used to access your RPi **remotely** via the **command line** of your laptop. For this course, we will use SSH instead of the the mouse, keyboard and monitor to control the RPi. This is not just good practice for your command line skills, **it also makes for a more realistic setup**. 

In real life, servers are rarely located in the same building as you are: probably it is not even in the same country. And often it is just one well hidden rack in a larger server farm. In such cases, you cannot just connect a mouse and a monitor to your server to set it up. Instead, these servers are configured through remote access, as we will practice here.

On your RPi, select the **raspberry icon** in the top left corner, and go to `Preferences/Raspberry Pi Configuration`. Here, select the tab `Interfaces` and ensure, that SSH is `Enabled`.

---

###2. Ensure that the keyboard layout is set to Belgian
Until we will be able to SSH into our RPis, we will need to use the keyboard.

Go to `Preferences/Mouse and Keyboard Settings`, select the tab `Keyboard` and there the button `Keyboard Layout`. Select the layout of the keyboard you are using, in our case `Belgium/Belgian`.

--

###3. Ensure that the system language is set to English
We want all RPis to be operated in English.

Go to `Preferences/Raspberry Pi Configuration` again, this time select the tab `Localisation`. Click on `Set Locale` and make sure the `Language` is set to `English` and the `Character Set` is `UTF-8`.

---

name: pw
###4. Set the System Password
Although we are in a closed network for this course and do not expect any hacking attempts, **it is always good practice to change your RPi's password.** Especially when SSH is enabled, changing the default password (`raspberry`) will **prevent others from accessing and controlling your computer without your knowledge**.

Go to `Preferences/Raspberry Pi Configuration` again, this time select the tab `System` and set the password to the one provided by your tutor.

If your keyboard layout is not set correctly you will change the password to an unexpected value. This will make the SSH access impossible later. (see [Step 1](#step1)).

--

###5. Reboot your RPi
Go to your **terminal**, and enter the following command:
```bash
sudo reboot now
```

---

class: center, middle, darkslide

#Done!
.yellow[Move to [Step 3](step3.html) to connect your RPi to the internet.]

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