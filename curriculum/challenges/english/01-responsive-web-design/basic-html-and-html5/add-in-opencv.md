---
id: 5d3ffa56e5b42a8be2747034
title: Add in opencv
challengeType: 0
videoUrl: 
---

## Description
<section id='description'>
Welcome to freeCodeCamp's HTML coding challenges. These will walk you through web development step-by-step.
First, you'll start by building a simple web page using HTML. You can edit <code>code</code> in your <code>code editor</code>, which is embedded into this web page.
Do you see the code in your code editor that says <code>&#60;h1&#62;Hello&#60;/h1&#62;</code>? That's an HTML <code>element</code>.
Most HTML elements have an <code>opening tag</code> and a <code>closing tag</code>.
Opening tags look like this:
<code>&#60;h1&#62;</code>
Closing tags look like this:
<code>&#60;/h1&#62;</code>
The only difference between opening and closing tags is the forward slash after the opening bracket of a closing tag.
Each challenge has tests you can run at any time by clicking the "Run tests" button. When you pass all tests, you'll be prompted to submit your solution and go to the next coding challenge.
</section>

## Instructions
<section id='instructions'>
I don't know what is happaning
</section>

## Tests
<section id='tests'>

```yml
tests:
   - text: Use <code>cv.addWeighted</code> to read image and create a matix of image
     testString: assert(code.match(/cv.addWeighted/g),'Use <code>cv.addWeighted</code> to read image and create a matix of image'); 

```
 
</section>

## Challenge Seed

<section id='challengeSeed'>

<div id='html-seed'>

```html
<script>
  function runSample() {
    let dst = new cv.Mat();
    let firstSrc = cv.imread("firstImageSrc");
    let secondSrc = cv.imread("secondImageSrc");
    cv.addWeighted(firstSrc, 0.5, secondSrc, 1, 0.0, dst);
    cv.imshow("canvasOutput", dst);
    firstSrc.delete();
    secondSrc.delete();
    dst.delete();
  };
</script>

<img id="firstImageSrc" src="http://bit.ly/fcc-relaxing-cat" style="width:200px;height:200px;"/>

<img id="secondImageSrc" src="https://s3.amazonaws.com/freecodecamp/FCCStickers-CamperBot200x200.jpg" style="width:200px;height:200px;"/>

<canvas id="canvasOutput" ></canvas>

<script async src="https://docs.opencv.org/master/opencv.js" 
        onload= 'cv["onRuntimeInitialized"]=()=> { runSample() }' 
        type="text/javascript">
</script>
```
</div>

</section>

## Solution
<section id='solution'>

```html
 
```

</section>