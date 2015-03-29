---
layout: study
title: What Shape Is It
permalink: /work/what-shape-is-it
js-script: /js/what-shape/index.js
---

<div class="container container--padded container--pushed-down">
<canvas id="main" style="width: 100%; height: 100%; margin-top: -20%;"></canvas>
  <h1 class="h3 text--grey align-center" id="time" style="position: relative; margin-top: -18%">17:32:05</h1>
  <div class="work__client">
  <p class="text--grey align-center text--no-top-margin">A canvas experiment to create abstract shapes from the current time.</p>
  </div>
  <div class="work__roles align-center">
    <p class="text--grey" >Javascript</p>
    <p class="text--grey" >Canvas</p>
    <p class="text--grey" >Data Visualisation</p>
  </div>
</div>

<div class="container content bordered-top">

<p>This experiment was only very quick to make. I was feeling quite bored and it was around the time of me having to write my dissertation. I decided I needed a welcome distraction. I'd recently seen something online called <a href="http://whatcolourisit.scn9a.org/" target="_blank">what color is it?</a></p>

<p>It was incredibly simple, colour representing time by splitting the time into a 6 string hexadecimal value and then setting that as a colour property on the dom. I thought I'd try some data visualisation too. I'd dabbled in canvas a bit before so I thought this would be fun.</p>

<p>I also used it as an excuse to properly try out <a href="http://gulpjs.com/">gulp</a> and <a href="http://browserify.org/">browserify</a>. These allowed me to write my code in modules similiar to the commonjs format that is massively popular in nodejs.</p>

<p>I now had a chance to abstract ideas out, this mainly consisted of abstracting away a point class / object that could be generated and placed onscreen based on x, y and radius.</p>

<h3 class="h3">How I visualised it</h3>

<p>I decided, that I would make a shape with 6 points, I would map them using polar coordinates around a circle based on splitting up a realtime timestring representation. Each number simply acted as a point of the shape and then I would connect and fill all the points creating a shape that looks like it has depth, yet also looks very abstract. The angles are worked out by dividing 360/amount of possible numbers. For the hours this means 0 or 1, so 2 and so on. This was more of an art piece other than actually being helpful.</p>

<h3 class="h3">Polar Coordinates</h3>

<p>In order to map points around a circle that was the first thing I was going to have to learn. I did some google searching (I don't ever remember learning to do this at school) I learned that I needed to use something called polar coordinates.</p>

<p>To do this the formula was equal to something along the lines of <code>x = x + (radius * cos of the angle)</code> and for y it was <code>y = y + (radius * sin of angle)</code></p>

<p>To make this as easy as possible I decided it would be cool to make a polarcoords function that would return a new x and y based on the x,y,radius and angle I passed it. This also meant that it's possible to pass it directly to my point / circle's <code>update</code> method.</p>
</div>
{% highlight javascript %}
  function polarCoords(x,y,r,angle) {
    return {
      x: x + (r * Math.cos(angle)),
      y: y + (r * Math.sin(angle))
    };
  }
{% endhighlight %}

<div class="container content">

<h3 class="h3">Mapping the points to the time</h3>

<p>Everything was now in place to turn the time into the points. To do this I made a <code>timeToPoints</code> function which accepts an array which is made from the current time. I then tied this into draw loop and simply get the time each tick, regenerate the array based of the new time. map them using the timeToPoints function and then connect them all, then repeat every frame.</p>

<p>The result was the abstract time you see at the top of the page. Here is the draw function</p>

</div>

{% highlight javascript %}
  function draw() {
    ctx.clearRect(0,0,_window.innerWidth,_window.innerHeight);
    circle.draw();
    var timeArray = timeToArray();
    timeToPoints(timeArray);
    DOMtime.innerHTML = timeToString(timeArray);
    connectDots(points);
  }
{% endhighlight %}

<div class="container content">

<p>There is a lot more than what I mention going on in this project. However the important details to cover was learning about polar coordinates and mapping the time from an array to those points each second.</p>

<p>For a couple of days it was really good. I learned how to map points to a circle which I'm sure if something that can easily be applied to other things in the future. I was also able to play around with gulp and write client side code in a more modular fashion.</p>

<p>*I tweaked some values to get a more desirable shape. so have a fiddle.</p>

<p>If you're really interested on how the code works then please <a href="http://www.github.com/birdyboy18/whatshapeisit">check it out on github</a></p>

</div>
