---
layout: study
title: kartiplayer
permalink: /work/kartiplayer
---


<div class="hero container container--padded background--green">
  <div class="work__client">
    <div class="media-holder work-logo">
      <img class="logo--240" src="../../media/kartiplayer_logo@2x.png">
    </div>
    <p class="text--white align-center text--no-top-margin">Play SNES Mariokart using your phone’s gyroscope, democratically.</p>
  </div>
  <div class="work__roles align-center">
    <p class="text--white" >Web Sockets</p>
    <p class="text--white" >Gyroscope</p>
    <p class="text--white" >Nodejs</p>
  </div>
</div>


<div class="container container--padded content">

<p>This hack was made while attending <a href="http://hacksoton.com/">hack soton</a> an event in southampton where like-minded developers can spend a day hacking those projects they don't quite get time to spend on. All while being fed and watered with food and beer.</p>

<p>At this event I met up with <a href="http://www.twitter.com/bhawkes">Brandon</a> another developer who was year above on my course and who I worked with at the last hack soton event to make something called <a href="http://github.com/birdyboy18/QWOPtiplayer">QWOPtiplayer</a>. For a better read up on it, then please <a href="http://sean.mtracey.org/post/hacksoton-3">read this write up of it</a>, provided by <a href="http://twitter.com/seanmtracey">Sean Tracey</a> another developer we worked with on <a href="https://github.com/birdyboy18/QWOPtiplayer">QWOPtiplayer</a>. However I will also touch on it in the next section.</p>

<h3 class="h3">What is KARTiplayer?</h3>

<p><a href="http://github.com/bhawkes/KARTiplayer">KARTiplayer</a> was the idea to build on the foundations of QWOPtiplayer. For a quick overview of QWOPtiplayer, it's idea was conceived at the time of when Twitch plays pokemon was a thing. Jokingly while waiting for a train I thought it would be funny if we were to make a system where buttons are pressed based on the overall votes of the people playing. The action was decided democratically by our system.</p>

<p>This time we decided it would be cool if you could play Mario kart SNES but by using your actual phone as the controller, similar to how you do on the Wii. To make it more fun we decided it would be fun to include the democratic system from QWOPtiplayer, just to make it even more hectic.</p>

<h3 class="h3">What was my role?</h3>

<p>My role in KARTiplayer was to make it so that we could track how people were turning their phone, capture that data from the gyroscope using the browsers gyroscope api. Work out which direction they were turning and then send that over a web sockets connection to a nodejs server we were running on one of our laptops.</p>

<p>The server was responsible for handling all the clients socket data coming in and working out what overall choice was being selected and then pressing the required button. It would then send that data back out to the clients again.</p>

<p>With that data being sent back to all of the clients, it was also my job to take that data and reflect that on the front-end. I did this by making it so that when you tilted the phone a block would move up indicating which choice everyone was currently picking. It would also only work if a certain threshold was passed. If everyone didn't overall pick a choice it would remain neutral.</p>

<h3 class="h3">What about Brendan?</h3>

<p>While I was doing this Brendan though it'd be cool if we could take the computer that was running both the server and the game to see if it could capture part of the screen and then send that over too. This was so we had an actual item displayed on our phone when we could use it.</p>

<h3 class="h3">Conclusion</h3>

<p>To conclude, this was a super fun hack project and the most satisfying part was that we did everything we set out to do that day. Because we built it from our last hack project it was much quicker.</p>

<p>Unfortunately I don't have a video or anything to show you, I do recommend you grab it from our repo and sit down and play it. You need to make sure you're on a Mac though, have nodejs installed and a snes emulator and a Mario kart snes rom for the emulator. I recommend openemu and coolroms to find a SNES rom for it. Happy Racing!</p>

</div>
