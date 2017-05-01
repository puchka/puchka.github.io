---
layout: post
comments: true
---

In this post, I will make an attempt do describe the next steps
we should follow starting from the point where we are.

- Create a mobile app for people without computer knowledge
to contribute data about bus lines an bus stops.

This should be an easy to use app with simple UI design.

The app should be able to work offline and enable the user to upload data
when they are online.

It will be great if we manage to build a multi-device app :)

- Make a web app to display and enable commutinity members to
comment and/or edit data about the collected data using the process described above.

This should enable the community to discuss about each piece
of data and make edit on it.

- Make a new version of BetaX using these data :)

I propose to store the data relative to bus lines and bus stops in
PostgreSQL with the PostGIS extension which is a spatial database extender for PostgreSQL. [1]

It allows storage and query of information about location and mapping.

After, pgRouting extends the PostGIS / PostgreSQL geospatial database
to provide geospatial routing functionality. [2]

I Hope that this post will motivate the community to contribute data.

There is more to happen, stay tuned ;)

References
===========

[1] [PostGIS](http://postgis.net/)

[2] [pgRouting](http://pgrouting.org/)
