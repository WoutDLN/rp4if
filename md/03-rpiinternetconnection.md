class: center, middle, darkslide
name: titleslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Step 3:]

#Connect your RPi to the Internet

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 2](step2.html)]

---

class: center, middle, darkslide
name: introduction

##Introduction

In [Step 1](step1.html), we've set up a **connected network of RPis**. This is a **wired** network, that uses **ethernet** cables and **switch ports** to connect the RPis to each other through a **router**, that also gives each of the RPis a unique identifier in the form of an **IP address**. These IP Addresses are what we are going to use to control our RPis from our own laptops through **SSH**.

---

##Why didn't we just use the WiFi to connect to the router?

When you are trying this at home, this elaborate setup with an extra router and ethernet cables will not be necessary. All you need, is to be on the same WiFi as your RPi, to have SSH enabled, and to know its IP address. We didn't go for this option for three reasons:

1. In a **real-world setup**, servers will always be connected to the internet through ethernet cables, because they are much faster and more reliable.

2. Creating a password protected subnet provides an **extra layer of security**. It prevents people outside of our class who are on the library network from hacking our RPis.

3. And, most importantly, the University Library Network that we using here wouldn't allow for it, because it activated **AP Isolation** for security reasons.

---

class: center, middle, darkslide

#AP Isolation

.yellow[To learn more about AP Isolation, and why it forced us to come up with a more creative solution for communicating with our Raspberry Pis via SSH, please watch [this video](youtubelink).] 

---

## Solving the Internet Dilemma 

For this tutorial to work, we need all RPis to (1) be **connected to the same network**, and (2) we need them all to have **access to the internet too**. 

1. .orange[Network:] this is necessary to be able to communicate to our RPi via SSH, and to work with each other's images later on. 

2. .orange[Internet:] this is necessary to update the RPis, and to download and install the software we will need (e.g. the image server).

Thanks to [Step 1](step1.html) we have (1) covered, but we still need (2). And in our current setup, we cannot connect the router to the intenet to share its connection, because within the University Library, our network only allows 1 device to be connected to each access point at the same time. 

In other words: every time a RPi would connect to the internet, another RPi would be automatically kicked off. And since we al want to download software simultaneously, that won't work for us. So we will need to find another solution for connecting the RPis to the internet, **individually**.

---

##Connecting your RPis to the Internet

Since your RPi's ethernet interface is already in use (to support our local RPi network), we can only **connect our RPi to the internet via WiFi**.  

Connect your RPi to the following WiFi network: `UA-guest`. 

.note[**Note for students:** `UA-guest` is the guest network at the [University of Antwerp](https://www.uantwerpen.be), where this course was first taught. If you are following this course at another institution, your tutor will tell you which WiFi network to connect to instead.]

**Open your browser**. 

.question[Nothing will happen – yet. **Can you guess why**?]

---

##Prioritize WiFi for Web Requests
Although you can connect to **multiple networks at the same time** as long as you use **different interfaces** (e.g. WiFi vs. ethernet), your system (in our case: the RPi) will decide **which of these networks it takes its internet connection from**. 

In most cases, when you are connected through both your WiFi and ethernet interfaces, your system will **prioritize the ethernet connection** for internet access, since this is the **more stable** and **faster** of the two. This is also the case for our RPis.

In other words, this means that our RPis will send all **web requests** via the **ethernet** interface to our router (which **is not** connected to the internet), instead of via the WiFi interface to the UA-guest network (which **is** connected to the internet). That is why we still do not have access to the internet on our RPi.

To change this, we will have to change the RPi's priorities, to make sure that it prefers WiFi over ethernet.

---

name: nano
###1. Using nano to change files
**Open a terminal** and enter:
```bash
sudo nano /etc/dhcpcd.conf
```

This will tell the RPi to use the programme `nano` to open a file located in the path `/etc/dhcpcd.conf`.

.question[**Question:** What kind of path is this? To freshen up your command line skills, have a look at our [Quick Reference Guide](cheat.html).]

`nano` is a **shell text editor**. It allows you to change and save text files straight from the command line, using some very rudimentary controls.

The `arrow` keys (`left`, `right`, `up`, `down`) let you move your cursor across the file (**do not use your mouse**), where you can use any key to start typing or deleting text. 

`Ctrl+o` **saves** the file (effectively overwriting the old file), and `Ctrl+x` **quits** the programme, bringing you back to your shell. If you quit the programme before saving, `nano` will ask you if you would like to save your changes before you do – in which case you type in `Y` for Yes or `N` for No.

---

###2. Assign metric values to your ports
Use the `arrow-down` key to move to the end of the configuration file. There, add the following lines:

```bash
interface wlan0
metric 202

interface eth0
metric 303
```

Hit `Ctrl+o` to save the file and confirm with `enter`.

These lines assign **metric values** to your WiFi and your ethernet ports. The lower the value, the higher its priority. So, since `202` is lower than `303`, `wlan0` (your WiFi port) will be rated higher than `eth0` (your ethernet port) and our system will send web requests via `wlan0` instead.

Hit `Ctrl+x` to leave `nano`.

---

###3. Reboot your RPi
To allow these changes to take effect, you will now have to reboot your RPi. We will do this using the terminal:

```bash
sudo reboot now
```

--

###4. Connect the RPi to the WiFi network again
Open the browser. You should be directed to the university's login page now. This means that assigning the metric values has worked!

Each group has received credentials for an account on the guest network. Log in using these access data.

Once you are logged in, visit any website to make sure your internet is connected.

---

###5. Double-check the metric values
Open a terminal and enter the following command:

```bash
route
```

This command will show you your routing table: a list of all the system's **routing destinations** (in the form of IP addresses), that tell the system where to send which data packages. Here you can double-check that the metric value of the `wlan0` interface is now lower than that of the `eth0` interface.

--
name: ip
###6. Find down your IP Address
As we explained in the [introduction](#introduction), we will need the IP address that our router has assigned to our RPi to [SSH into the RPi](step2.html#ssh) via our laptops. We can find the IP address we need by running the following command: 

```bash
ifconfig
```

This lists all your network settings. In the list, find the entry that starts with `eth0` (typically the first one), and note down the first IP address that you see, the one that directly follows the word `inet`. 

---
name: ipshare

###7. Share your IP Address With your Tutors

.exercise[
Your tutors will need your IP addresses later. So please **send them an email** to the email address they provide, with **your RPi's name** in the subject, and **your RPi's IP address** in the message.
]

--
###8. No more peeking!
Now that we have the IP addresses of our RPis, we can finally access them via SSH, using our laptops. That means we will no longer need to look at its desktop.

**Turn off the monitor that is connected to your RPi**.

---

class: center, middle, darkslide

#Done!
.yellow[Move to [Step 4](step4.html) to SSH into your RPi.]

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