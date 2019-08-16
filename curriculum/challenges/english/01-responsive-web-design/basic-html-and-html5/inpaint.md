---
id:
title: Inpaint
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
    - text:  Use <code>cv.ellipse</code> to drow ellips on image
      testString: assert(code.match(/ellipse/g),'Use <code>cv.ellipse</code> to drow an ellips image');
    - text:  Use <code>cv.circle</code> to drow ellips on image
      testString: assert(code.match(/circle/g),'Use <code>cv.circle</code> to drow an ellips image');
```
</section>

## Challenge Seed

<section id='challengeSeed'>

<div id='html-seed'>

```html
<p id="status">OpenCV.js is loading...</p>
<canvas id="canvas" >
</canvas>
<img id="src" src="bird.jpg" style="display:none"/>
<input type="button" id="myButton" value="Test" disabled=true
onclick="inpaint()"/>

<script type="text/javascript">

var src;
var mask;
var lastX;
var lastY;

window.onload = function()
{
context = document.getElementById("canvas").getContext("2d");
img = document.getElementById("src");
context.canvas.width = img.width;
context.canvas.height = img.height;
context.drawImage(img, 0, 0);
};

document.getElementById("canvas").onmousedown = function(e)
{
  lastX = e.pageX - this.offsetLeft;
  lastY = e.pageY - this.offsetTop;
};

document.getElementById("canvas").onmousemove = function(e)
{
  if (lastX != undefined)
  {
    let x = e.pageX - this.offsetLeft;
    let y = e.pageY - this.offsetTop;
    cv.line(src, new cv.Point(lastX, lastY), new cv.Point(x, y),
    new cv.Scalar(255, 255, 255, 255), 2);
    cv.line(mask, new cv.Point(lastX, lastY), new cv.Point(x, y),
    new cv.Scalar(255, 255, 255, 255), 2);
    cv.imshow("canvas", src);
    lastX = x;
    lastY = y;
  }
};

document.getElementById("canvas").onmouseup =
document.getElementById("canvas").onmouseleave = function(e)
{
    lastX = undefined;
    lastY = undefined;
};

function init()
{
  let rgba = cv.imread("src");
  src = new cv.Mat();
  cv.cvtColor(rgba, src, cv.COLOR_RGBA2RGB);
  mask = new cv.Mat.zeros(src.size(), cv.CV_8UC1);
  rgba.delete();

  cv.line(src, new cv.Point(0, 0), new cv.Point(Math.floor(src.cols * 0.5),
  Math.floor(src.rows * 0.5)), new cv.Scalar(0, 0, 0, 255), 1);

  cv.line(src, new cv.Point(Math.floor(src.cols * 0.2), Math.floor(src.rows * 0.4)),
  new cv.Point(Math.floor(src.cols * 0.4), Math.floor(src.rows * 0.8)),
  new cv.Scalar(0, 0, 0, 255), 1);

  cv.line(src, new cv.Point(Math.floor(src.cols * 0.8), Math.floor(src.rows * 0.9)),
  new cv.Point(Math.floor(src.cols * 0.6), Math.floor(src.rows * 0.2)),
  new cv.Scalar(0, 0, 0, 255), 1);

  cv.imshow("canvas", src);
}

function inpaint()
{
  let dst = new cv.Mat();
  cv.inpaint(src, mask, dst, 3, cv.INPAINT_TELEA);
  cv.imshow("canvas", dst);
  src.delete();
  mask.delete();
  dst.delete();
}

function onOpenCvReady()
{
  document.getElementById("status").innerHTML = "OpenCV.js is ready.";
  cv["onRuntimeInitialized"] = () =>
  {
    document.getElementById("myButton").disabled = false;
    init();
  }
}

</script>

<script async src="opencv.js" onload="onOpenCvReady();" type="text/javascript">
</script>
```
</div>
</section>

## Solution
<section id='solution'>

```html
<p id="status">OpenCV.js is loading...</p>
<canvas id="canvas" >
</canvas>
<img id="src" src="bird.jpg" style="display:none"/>
<input type="button" id="myButton" value="Test" disabled=true
onclick="inpaint()"/>

<script type="text/javascript">

var src;
var mask;
var lastX;
var lastY;

window.onload = function()
{
context = document.getElementById("canvas").getContext("2d");
img = document.getElementById("src");
context.canvas.width = img.width;
context.canvas.height = img.height;
context.drawImage(img, 0, 0);
};

document.getElementById("canvas").onmousedown = function(e)
{
  lastX = e.pageX - this.offsetLeft;
  lastY = e.pageY - this.offsetTop;
};

document.getElementById("canvas").onmousemove = function(e)
{
  if (lastX != undefined)
  {
    let x = e.pageX - this.offsetLeft;
    let y = e.pageY - this.offsetTop;
    cv.line(src, new cv.Point(lastX, lastY), new cv.Point(x, y),
    new cv.Scalar(255, 255, 255, 255), 2);
    cv.line(mask, new cv.Point(lastX, lastY), new cv.Point(x, y),
    new cv.Scalar(255, 255, 255, 255), 2);
    cv.imshow("canvas", src);
    lastX = x;
    lastY = y;
  }
};

document.getElementById("canvas").onmouseup =
document.getElementById("canvas").onmouseleave = function(e)
{
    lastX = undefined;
    lastY = undefined;
};

function init()
{
  let rgba = cv.imread("src");
  src = new cv.Mat();
  cv.cvtColor(rgba, src, cv.COLOR_RGBA2RGB);
  mask = new cv.Mat.zeros(src.size(), cv.CV_8UC1);
  rgba.delete();

  cv.line(src, new cv.Point(0, 0), new cv.Point(Math.floor(src.cols * 0.5),
  Math.floor(src.rows * 0.5)), new cv.Scalar(0, 0, 0, 255), 1);

  cv.line(src, new cv.Point(Math.floor(src.cols * 0.2), Math.floor(src.rows * 0.4)),
  new cv.Point(Math.floor(src.cols * 0.4), Math.floor(src.rows * 0.8)),
  new cv.Scalar(0, 0, 0, 255), 1);

  cv.line(src, new cv.Point(Math.floor(src.cols * 0.8), Math.floor(src.rows * 0.9)),
  new cv.Point(Math.floor(src.cols * 0.6), Math.floor(src.rows * 0.2)),
  new cv.Scalar(0, 0, 0, 255), 1);

  cv.imshow("canvas", src);
}

function inpaint()
{
  let dst = new cv.Mat();
  cv.inpaint(src, mask, dst, 3, cv.INPAINT_TELEA);
  cv.imshow("canvas", dst);
  src.delete();
  mask.delete();
  dst.delete();
}

function onOpenCvReady()
{
  document.getElementById("status").innerHTML = "OpenCV.js is ready.";
  cv["onRuntimeInitialized"] = () =>
  {
    document.getElementById("myButton").disabled = false;
    init();
  }
}

</script>

<script async src="opencv.js" onload="onOpenCvReady();" type="text/javascript">
</script>
```

</section>
