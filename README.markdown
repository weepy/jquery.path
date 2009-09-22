jQuery.path
========

Provides animation along bezier and circular arcs. 

The animation engine in jQuery is focussed on single dimensional animation - hence it's difficult to animate two variables along a path.

This simple plugin provides a method of multidimensional animation, and in particular provides a method for animating along bezier curves and arcs.

Bezier
---

Example: animate along a bezier path

<pre>
var bezier_params = {
    start: { 
      x: 185, 
      y: 185, 
      angle: 10
    },	
    end: { 
      x:540,
      y:110, 
      angle: -10, 
      length: 0.25
    }
  }
  
$("my_elem").animate({path : new $.path.bezier(bezier_params)})
</pre>

Bezier curves are made form a start point, an end point each with a control point

* start is starting point
* end is the final point
* x,y indicate the coordinates at that point. Required
* angle is the angle of the control point from the line joining the start and end. Optional, default is 0
* length is the distance from the point to it's control point as a ratio of the distance from start to end. Optional, default is 1/3

Arc
---

Exampe: animate along an arc

<pre>
  
var arc_params = {
    center: [285,185],	
		radius: 100,	
		start: 30,
		end: 200,
		dir: -1
  }
  
$("my_elem").animate({path : new $.path.arc(arc_params)})
</pre>

* center is the coords of the centre of an imaginary circle that contains the start and end point
* radius is the radius of this circle
* start is the angle of the start point. 0 is "North", measured clockwise
* end is the angle of the start point. 0 is "North", measured clockwise
* dir is the direction to move in. Only required if not obvious from start and end (e.g. if start is 100, end is 30, but you want to animate clockwise)

Other Paths
----

It is trivial to create other paths, or even animate other parameters. E.g:

<pre>
var SineWave = function() {
  this.css = function(p) {
    var s = Math.sin(p*20)
    var x = 500 - p * 300 
    var y = s * 50 + 150
    var o = ((s+2)/4+0.1)
    return {top: y + "px", left: x + "px", opacity: o}
  } 
};
  
$("my_elem").animate({path : new SineWave})
</pre>

Links
----

* [Demo](http://weepy.github.com/jquery.path)
* [Javascript File](http://github.com/weepy/jquery.path/raw/master/jquery.path.js)
* [Github Project](http://github.com/weepy/jquery.path)
* [Issue Tracker](http://github.com/weepy/jquery.path/issues)

Compatibility
----

Tested in

* Firefox 3.5
* Safari 4
* IE 6, 7, 8



