---
id: 5d383f6f2cd33e8211fad377
title: Enter in openCV
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
   - text: <code>cv.imread</code> is not initialized
     testString: assert(code.match(/cv.imread/g),'<code>cv.imread</code> is not in initializes'); 
   - text: <code>cv.cvtColor()</code> is not initialized
     testString: assert(code.match(/cv.cvtColor/g),'<code>cv.cvtColor</code> is not in initializes'); 
   - text: <code>COLOR_RGBA2GRAY</code> is not argument in <code>cv.cvtColor()</code>
     testString:  assert(code.match(/COLOR_RGBA2GRAY/g),'<code>COLOR_RGBA2GRAY</code> is not argument in <code>cv.cvtColor()</code>');
   - text: <code>cv.imshow</code> is not initialized
     testString: assert(code.match(/cv.imshow/g),'<code>cv.imshow</code> is not in initializes'); 
  
```
</section>

## Challenge Seed

<section id='challengeSeed'>

<div id='html-seed'>

```html
<script>
    
    function draw() {
      let src = cv.imread("imageSrc");
      let dst = new cv.Mat();  
      cv.cvtColor(src, dst, cv.COLOR_RGBA2GRAY);
      cv.imshow('canvasOutput', dst);
      src.delete();
      dst.delete();
    };
    function onOpenCvReady() {
      document.getElementById('status').innerHTML = 'OpenCV.js is ready.';
      cv["onRuntimeInitialized"]=()=> {
        document.getElementById("runSampl").disabled = false;
      }
    }
  </script>
   
    <script async src="https://docs.opencv.org/master/opencv.js" onload="onOpenCvReady();" type="text/javascript">
    </script>  
 <h2>OpenCV.js</h2>
 <input type="button" id="runSampl" onclick="draw()" value="Run test" disabled=true />
 <p id="status">OpenCV.js is loading...</p>
 <img id="imageSrc" src="http://bit.ly/fcc-relaxing-cat" /> 
 <canvas id="canvasOutput" >
 </canvas>
```

</div>



</section>

## Solution
<section id='solution'>

```html
 
```

</section>
