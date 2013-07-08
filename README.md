360-panorama
============

WebGL
-----

[three.js](http://othree.github.io/360-panorama/three-3d/) Example

* Use Case:
  * Google Street View
* Equirectangular Projection（等距圓柱投影）


<img alt="equirectangular projection" src="three-3d/textures/2294472375_24a3b8ef46_o.jpg" width="500" />

* Paste this image on a sphere.
* Saw this kind of image before?


<img alt="equirectangular earth" src="doc/images/Equirectangular-projection.jpg" width="500" />
<img alt="earth" src="doc/images/earth.jpg" width="500" />

* Problems:
  * ProblemsMobile device not support WebGL
  * Android 4.1 native supports this format
  * Want to build a web service to serve this image format and support mobile device

CSS
---

* How about
  * Use hyperrectangular instead of sphere
    Which is much simpler
  * Cubic Projection !!

![基礎](doc/images/1.basic.png)

Demo: [CSS cubic](http://codepen.io/linmic/pen/hGmBp)

* Images!!

<img src="css/texture/cube0000.jpg" width="300" alt="" />
<img src="css/texture/cube0001.jpg" width="300" alt="" />
<img src="css/texture/cube0002.jpg" width="300" alt="" />
<img src="css/texture/cube0003.jpg" width="300" alt="" />
<img src="css/texture/cube0004.jpg" width="300" alt="" />
<img src="css/texture/cube0005.jpg" width="300" alt="" />

* How to get the image for six faces?
* Ref: [Converting an Equirectangular Panorama to Cubic Faces](http://vinayhacks.blogspot.tw/2010/11/converting-equirectangular-panorama-to.html)
  * CPAN Panotools for erect2cubic 
  * [Hugin](http://hugin.sourceforge.net/) for nona
  * `/Applications/Hugin/HuginTools/nona`
  * [See Here](https://github.com/othree/360-panorama/tree/master/css/texture)

How to control mouse drag?
--------------------------

![拖動](doc/images/2.drag.png)
![拖動結果](doc/images/3.drag-result.png)

* θ is ?

    theta = Math.atan2(0.5l, d);

Demo: [CSS #1](http://othree.github.io/360-panorama/css-first/)

* Somthing still wrong
* How about increase the face of the polygon

More Faces
----------

![12面體](doc/images/500px-POV-Ray-Dodecahedron.svg.png)

* Hard to generate images for dodecahedron
  * Use google stree view image API
  * Not perfect

Demo: [CSS dodecahedron](http://othree.github.io/360-panorama/dodecahedron/)

* Learned:
  * Use SVG clippath to clip the pentagon（五邊形）
    or you will see face overlape
  * Remember to center pentagon, it is smaller than the square.

* Problems
  * Must support SVG
  * Must work well when use both SVG and 3D transform

Back to Cubic
-------------

* Actually…
* My perspective is wrong on cubic version
 * Thanks bigcat

![transform](doc/images/4.transform.png)

Demo: [CSS](http://othree.github.io/360-panorama/css/)

* Problem:
  * Canvas support is better than 3D transform (ref: caniuse)
 
Canvas 2D
---------

* three.js supports 2d canvas….
* Other 3D library also supports too.
  
Demo: [three.js](http://othree.github.io/360-panorama/three-2d/) 2D example, please open in Firefox.

* Implement 3d projection by 3D JS library

