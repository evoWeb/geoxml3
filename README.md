JavaScript Module ``geoxml3`` [![Build Status](https://travis-ci.org/evoWeb/geoxml3.svg?branch=master)](https://travis-ci.org/evoWeb/geoxml3)
=================

The geoxml3 project is an effort to develop a KML processor for use with Version 3 of the Google Maps JavaScript API. This API is specifically designed to be lightweight and modular; accordingly, it did not originally contain the built-in KML support of Version 2. This library was originally intended to fill that need; as KML support has been added natively in Version 3, it now allows access to individual markers, polylines and polygons, rendered from KML. (Automatically exported from code.google.com/p/geoxml3
)

Original code inspired by Mike Williams' EGeoXml object (http://econym.org.uk/gmap/egeoxml.htm).

**Refactoring efford**
Project was forked from https://github.com/geocodezip/geoxml3 to refactor it.

**General Notes**
<ul>
<li>Be aware that this code, like v3 itself, is a work in progress. There is no support for 3D, labels, or any other aspect of KML that the underlying Maps API fundation does not support. In other words, the current version only supports markers and ground overlays.
<li>Support for polylines and polygons is present in the polys and kmz branches. Note that the v3 implementation of polygons uses CANVAS. To create holes in polygons, the inner holes must wind opposite the outer boundary.
<li>One other area that's not supported is a sidebar, and it may never be. In my experience, this is something that's a real stretch for any general-purpose library; everyone has their own idea of what they want their sidebar entries to look like. There's also a valid argument that content outside the map is off-topic for a map extension anyway. If you want to create sidebar entries, there are callbacks that you can use to do it yourself. Also investigate the v3 port of Lance Dyas' GeoXml parser (http://code.google.com/p/geoxml-v3/) which has sidebar support.
<li>In keeping with the modular nature of v3, ground overlay support in geoxml3 relies upon the  ProjectedOverlay  class released by John Coryat (http://www.usnaviguide.com). A compatible version of  ProjectedOverlay.js  is available for download from the Source section of this site.
<li>In keeping with the modular nature of v3, KMZ support in geoxml3 relies upon the  ZipFile.complete.js  library. A compatible version of  ZipFile.complete.js  is available for download from the Source section of this site.
<li>Geoxml3 is subject to the same cross-domain download restrictions as any JavaScript, so any KML document you expect it to process will need to be served from the same domain as the containing map page.
</ul>

**Basic Usage**

1. Download  GeoXML3.js  to your web site from the Source tab above. You may also need  ProjectedOverlay.js  and/or  ZipFile.complete.js  (see above).

2. Include it in your map page, something like this:

````javascript
  <script src="GeoXML3.js"></script>
````

3. Instantiate and initialize the object in JS, something like this:

````javascript
  var myParser = new geoXML3.parser({map: map});
  myParser.parse('/path/to/data.kml');
````
