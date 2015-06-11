Marching Cubes for blender
==========================

This is an optimized version of Tom Sapiens' marching cubes
implementation for blender.  It is useful for fabricating a blender
mesh approximating an isosurface of a scalar field function.

I found the original at
http://blenderartists.org/forum/showthread.php?265240-Generation-of-Isosurfaces-skript-%28Marching-Cubes%29
and made
* some fixes to compensate for API drift
* minor stylistic changes
* and some significant performance improvements.

It is not (strictly speaking) an addon for blender.  It is instead a
python script which can be executed from blender's text editor to
build a mesh for an isosurface of the field function defined inside
the python script.

https://www.blender.org/manual/extensions/python/text_editor.html has
a section explaining how to execute scripts from blender's text
editor.

The script comes with a sample scalarfield function (embedded inside
the main() function near the top of the file) you can test with, but
you will want to replace this with your own scalarfield function.  The
most common problem I anticipate is picking p0, p1, or isolevel in
such a way that nothing interesting happens in the analysis box
(Imagine if you tried to compute the isosurface for a sphere of radius
4 but only used a box of radius 1).

Resolutions of 100x100x100 can be computed in a matter of seconds on
modern hardware (depending on how complicated your field function is).
Going up to 200x200x200 can easily push your compute times up to a
minute on low-end hardware.  Going higher than that is recommended
only for the patient.

Performance may be improved over the original, but is still inferior
to the cython port:
https://github.com/Pyroevil/CubeSurfer/blob/master/README.md



Authors:
Robert Forsman (API fixes and optimization)
Tom Sapiens (blender python port)
Paul Bourke (author of source article with C++ code examples)
