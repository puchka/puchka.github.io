---
layout: post
comments: true
---

Some time ago, me and my friends created an Android app for helping people
finding bus lines from one place to one another in the urban area of
Antananarivo. [1]

This has sparked iterests from the public and we got many reviews and
feature requests.

The main feature mostly requested by users is the ability to find a
way to go from one place to one another by taking more than one direct bus line.

In the wish to implement this feature we had to get data about
the bus stops and the bus lines in Antananarivo.

We got geographical data from IMV (Institut des Métiers de la Ville) and we
began to process it.

Finally, the data was not conform to the intended use we wanted to make of it.

So, exposing this problem to a friend (Tsiry Sandratraina)
he proposed an approach that I give a succint description below.

The solution was to draw manually in Google Maps the path followed by
a bus that we know.

I'll release and describe in a future post the scripts we used to make it and the bus line paths we managed to make.

It uses of the DirectionsService object to fetch directions for a route including waypoints. [2]

I hope the community interested in making the public transportation in Madagascar better will be eager to participate in this initiative.

Meanwhile, I look forward for your comments and propositions.

References
==============

[1] [BetaX](http://www.betax.mg)

[2] [Using Waypoints in Routes](https://developers.google.com/maps/documentation/javascript/directions?hl=en#Waypoints)
