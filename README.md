# stb_tetmeshtraversal  

**Single-header mesh traversal library using tetgen.**
  
    
This library provides functions for traversing tetrahedral meshes generated with the Tetgen software by Hang Si (_Si, 2015_). Functions implemented include loading tetgen .face/.edge/.ele/.node/.neigh/.t2f files, locating the tetrahedra containing the ray origin, traversing the mesh until a constrained triangle face is found and mesh traversal until a tetrahedra containing a specific point is found.     

The library is particularly useful for applications using tetrahedral  meshes for rendering (Lagae & Dutré, 2008) or seismic processing.  

Usage:

- This library only works with the beta version of tetgen 1.5.1-beta1 (in previous versions no tetrahedra-face realtions were stored)
- When generating the mesh with Tetgen, ensure the switches -n -nn -f -z are used.
- Use the functions provided in the class _tetrahedramesh_ to load the single tetgen files. Load order should be ele->neigh->node->face->t2f->edge.
- At the beginning, the tetrahedron containing the starting point has to be located with the function _GetTetrahedraFromPoint_. This has to be done only once. If the position changes later on, adjacency information of the tetrahedra can be exploited to track the movement of the starting point. 
- Mesh traversal is done with the function _traverse_ray_, which takes the mesh, ray origin/direction and starting tetrahedron as input. The _rayhit_ structure stores the intersected face and tetrahedra. 
      
**References:**
        
Hang Si (2015). TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator. _ACM Trans. on Mathematical Software. 41 (2), Article 11 (February 2015), 36 pages._
        
Lagae, A. and Dutré, P. (2008). Accelerating Ray Tracing using Constrained Tetrahedralizations. _Computer Graphics Forum, 27: 1303–1312._
