class: center, middle, darkslide

.topleft[[RPi-IIIF Tutorials](index.html)] 

#.white[Webdesign:]

#A Short Introduction to `html` and `css`

.yellow[Wout Dillen & Joshua Schäuble]

.bottomleft[.mirror[&#10148;] Back to [Step 4](step4.html)]

---

### 1. `HTML`

So we have a piece of `html` code that we wrote for each of our institution’s webpages.

`HTML` stands for **HyperText Markup Language,** and it’s a language for building 'hypertexts' – or webpages.

#### `HTML`
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


---

### `XML`

`XML` stands for **eXtensible Markup Language**. `XML` provides a basic syntax (the way in which the language is written) that allow for an infinite number of markup languages. Other, standardized types of XML are **ALTO-XML** (for OCR) and **TEI-XML** (for text encoding). 
 

#### `ALTO-XML`
```html
<alto>
	<Description>
		<MeasurementUnit/>
		<sourceImageInformation/>
		<Processing/>
	</Description>
	<Styles>
		<TextStyle/>
		<ParagraphStyle/>
	</Styles>
	<Layout>
		<Page>
          <TopMargin/>
          <LeftMargin/>
          <RightMargin/>
          <BottomMargin/>
          <PrintSpace/>
		</Page>
	</Layout>
</alto>
```

---

### `XML`

`XML` stands for **eXtensible Markup Language**. `XML` provides a basic syntax (the way in which the language is written) that allow for an infinite number of markup languages. Other, standardized types of XML are **ALTO-XML** (for OCR) and **TEI-XML** (for text encoding). 

#### `TEI-XML`
```html
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
      <fileDesc>
         <titleStmt>
            <title>Title</title>
         </titleStmt>
         <publicationStmt>
            <p>Publication Information</p>
         </publicationStmt>
         <sourceDesc>
            <p>Information about the source</p>
         </sourceDesc>
      </fileDesc>
  </teiHeader>
  <text>
      <body>
         <p>Some text here.</p>
      </body>
  </text>
</TEI>
```

---

### `XML`

`XML` stands for **eXtensible Markup Language**. `XML` provides a basic syntax (the way in which the language is written) that allow for an infinite number of markup languages. Other, standardized types of XML are **ALTO-XML** (for OCR) and **TEI-XML** (for text encoding). 

#### `HTML`
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

---


### 1. `HTML`

.exercise[Have a closer look at our `html` excerpt. **Can you figure out how `xml` is structured?**] 

#### `HTML`
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

---


class: center, middle, darkslide

#Done!

.yellow[When you're satisfied with how your web pages look, you're ready to learn how to [install a web server on your RPi](step5.html).]

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