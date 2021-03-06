# MachineTriangulation
Build Constrained Delaunay Triangulations (CDTs) of 2D Polygons with Tensorflow


This project came to my mind as a good way to learn about Neural Network Architectures. The input polygon contour is ordered and circular (i.e. last comes before first).  The output is an array of vertices where index i is the third point of a triangle together with input indices i and i+1, and so on. This method omits some triangles of the CDT, which is a minor downside. However, it has the big advantage of providing a canonical order to the output, which should make it easier for the neural network to learn.

I started by writing Triangulator, a C++ header-only library for making Constrained Delaunay Triangulations of 2D polygons. It is based on ear-clipping and Delaunay-Lawson flips. The ear-clipping part has a novel priority queue, which greedily selects high quality triangles, thus reducing the number of Delaunay-Lawson flips needed in the second stage.

Training, Test, and Validation datasets (sized to 50000, 15000, and 5000 respectively) were generated by running triangulator on randomly generated polygons. To start, all polygons have exactly 8 vertices. The eventual goal is to find a good representation for handling variable-length polygons with 8 to 16 vertices.

Please open the MachineTriangulation.ipynb Jupyter Notebook file for all the details if you are interested.
