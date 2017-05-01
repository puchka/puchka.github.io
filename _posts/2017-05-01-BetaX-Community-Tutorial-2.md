---
layout: post
comments: true
---

There are some restrictions when using the toolchain
I realeased previously. [1]

Firt, there is the restriction on the number of way points allowed by the Directions API.

The number of way points is limited to 23 max. [2]

To overcome this, we have to split the bus path in multiple parts
with number of way points less than 23.

With proper naming convention for the generated files
-as you can see in the bus routes we already made, it shouldn't
be difficult to manage.

For convenience, use the last point of the previous path part
to begin the next one to make it diplay smoothly after merging.

Second, sometimes the driving mode doesn't allow us to take the route followed by the bus.

For this, there is the **-w** switch for the *directions.py* script when using Directions API
with the walking mode and select walking in Google Maps when making the path.

![ ]({{ site.url }}/assets/img/walking-mode-google-maps.png "Walking mode on Google Maps")

References
============

[1] [BetaX Community repository](https://github.com/puchka/BetaX-Community)

[2] [Limits and Restrictions for Waypoints](https://developers.google.com/maps/documentation/javascript/directions?hl=en#waypoint-limits)
