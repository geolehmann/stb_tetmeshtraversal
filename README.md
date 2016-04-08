# stb_tetmeshtraversal  

**Single-header mesh traversal library using tetgen.**
  
    
This library provides functions for traversing tetrahedral meshes generated with the Tetgen software by Hang Si (_Si, 2015_). Functions implemented include loading tetgen .face/.edge/.ele/.node files, locating the tetrahedra containing the ray origin, traversing the mesh until a constrained triangle face is found and mesh traversal until a tetrahedra containing a specific point is found.     

The library is particularly useful for applications using tetrahedral  meshes for rendering (Lagae & Dutré, 2008) or seismic processing.    
      
**References:**
        
Hang Si (2015). TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator. _ACM Trans. on Mathematical Software. 41 (2), Article 11 (February 2015), 36 pages._
        
Lagae, A. and Dutré, P. (2008), Accelerating Ray Tracing using Constrained Tetrahedralizations. _Computer Graphics Forum, 27: 1303–1312._
