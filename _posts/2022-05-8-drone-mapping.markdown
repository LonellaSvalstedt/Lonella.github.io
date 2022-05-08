---
layout: post
title:  "Point clouds and drones"
date:   2022-05-08 13:00:00 +0200
categories: drone mapping
---

During the spring of 2022, I was part of a team working on a system for mapping a room using a drone.
This was a project I was part of in the course M7012E at Luleå University of Technology. 

<iframe style="display: block; margin-left: auto; margin-right: auto;" width="560" height="315" src="https://www.youtube.com/embed/hKLTdr7tsGw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>

To accomplish this, we developed a system consisting of three parts: 

<ol>
  <li>An android app controlling the drone and collecting points from the drone's sensor. <br/> Responsible for sending the point cloud to the server. </li>
  <li>A service, with access to a database, that stores and fetches point clouds. <br/> Stores points under a specific session name given by the user. </li>
  <li>A program for fetching and showing point clouds. Communicates with the database. <br/> Applies post-processing to remove statistical outliers from the data.</li>
</ol>

I was responsible mostly for the first part. The app was developed using Java and Android Studio.

A problem we discovered early on was that the drone, a DJI Air 2S, did not keep track of its own position. Therefore we had to manually calculate
the position of the drone from the velocity of the drone. The app also keeps track of the rotation of the drone. This amount of information was needed,
as the points from the ultrasonic sensors will be in relation to the drone. To be able to build a map using these points, the points have to be in relation
to a starting position.

Seen below is a screenshot of the app. Not a lot of effort was put into the UI, as can be seen!

![Drone App](/img/drone/drone_app.jpg)

In contrast, somewhere where a lot of effort went in was using the DJI SDK. The SDK is a library that allows us to link to and communicate with the drone.
This was probably the biggest road bump for the team. It was quite fiddly to get started. 

I might write some more on this later. For now, here is an example of a finished point cloud.

![Point Cloud](/img/drone/point_cloud.jpg)