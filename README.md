# Projection-and-Line-Drawing
As stated in the project objective, you will be implementing a basic graphics library that is similar in style to the popular openGL library. Part of these routines are the ones that you wrote for Project 1A. The following routines should act as they did in that earlier project:

Init_Matrix()

Push_Matrix(), Pop_Matrix()

Translate (x, y, z)

Scale (sx, sy, sz)

RotateX (theta), RotateY (theta), RotateZ (theta)

You will also implement several new routines which allow a user to manipulate and display 3D lines. The provided source code contains empty methods for each of the following routines:

Ortho (left, right, bottom, top, near, far)

Specifies that an orthographic projection will be performed on subsequent vertices. The direction of projection is assumed to be along the z-axis. The six values passed to this routine describe a box to which all lines will be clipped. The “left” and “right” values specify the minimum and maximum x values that will be mapped to the left and right edges of the framebuffer. The “bottom” and “top” values specify the y values that map to the bottom and top edges of the framebuffer. The “near” and “far” values are ignored for this project. The eye point is assumed to be facing the negative z-axis.

Perspective (fov, near, far)

Specifies that a perspective projection will be performed on subsequent vertices. The center of projection is assumed to be the origin, and the viewing direction is along the negative z-axis. The value “fov” is an angle (in degrees) that describes the field of view. In order to make it easier to write this routine, we will assume that all screen sizes will be square, so you don't need to worry about the vertical and horizontal field-of-view being different. The “near” and “far” values are ignored for this project.

In OpenGL, you can specify projections at any time before you draw lines and polygons. We will do the same for our assignment. Which ever projection that you specify (Ortho or Perspective) should be the last operation that is applied to the line endpoints, regardless of where those procedure calls appear with respect to the other transformations.

Begin_Shape(), End_Shape(), Vertex (x, y, z)

The Begin_Shape() and End_Shape() commands signal the start and end of a list of endpoints for line segments that are to be drawn. Each call to the routine Vertex() between these two commands specifies a 3D vertex that is a line endpoint. Black lines are drawn between successive odd/even pairs of these vertices. If, for example, the four vertices v1, v2, v3, v4 are given in four sequential Vertex() commands then two line segments will be drawn, one between v1 and v2 and another between v3 and v4.

The vertices of the lines are first modified by the current transformation matrix, and then by which ever projection was most recently described (Ortho or Perspective). Only one of Ortho or Perspective is in effect at any one time. These projections do not affect the matrix stack and the current transformation matrix! Your Begin_Shape(), Vertex() and End_Shape() commands must be able to draw any number of lines. You can draw the lines as soon as both vertices are given to you (using Vertex), or you can store all of the vertices and draw all of the lines when End_Shape() is called. Which way you use is up to you. To draw the lines, use the built-in line() routine in Processing.
