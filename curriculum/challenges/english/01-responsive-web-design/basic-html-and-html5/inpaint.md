---
id:
title: Inpaint
challengeType: 0
videoUrl:
---

## Description
<section id='description'>
"Inpaint" method will help you restore your damaged picture via using one of the two algorithms: Fast Marching Method and algorithm based on fluid dynamics. In the current sample we are going to use Fast Marching Method(<code>cv.INPAINT_TELEA</code>): we are consider region of the picture for being inpainted. Algorithm starts from the boundary of this region and goes inside the region gradually filling everything in the boundary first. It takes a small neighbourhood around the pixel on the neigbourhood to be inpainted. This pixel is replaced by normalized weighted sum of all the known pixels in the neigbourhood.
In this sample we are using next OpenCV functions:
<code>cv.imread("id of the source image")</code>
<code>cv.imshow("id of output canvas", name of the showed object)</code>
<code>cv.line(cv.Mat for drawing, start point as new cv.Point(), end point as new cv.Point(), color as cv.Scalar(), thickness as a  number of pixels)</code>
<code>cv.cvtColor(source, destination, method)</code>
<code>cv.inpaint(source image, mask, destination, region of neighborhood as a number of pixels, method)</code>
</section>

## Instructions
<section id='instructions'>
In the current sample we using <code>cv.line()</code> function for damage picture with black lines. You should restore picture with inpaint function.
Write a function which can draw a region the picture. Via using that function you can create mask for <code>cv.inpaint()</code> function. Then use "inpaint" function with source picture, created mask, and empty <code>cv.Mat()</code> for saving and showing result.
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
