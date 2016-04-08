# stb_tetmeshtraversal  

Single-header mesh traversal library using tetgen.  
  
    
    This library provides functions for traversing tetrahedral meshes generated with the Tetgen software by Hang Si (Si, 2015).  
    Functions implemented include loading tetgen .face/.edge/.ele/.node files, locating the tetrahedra containing the ray origin, traversing the mesh until a contrained triangle face is found and traversing the mesh until a tetrahedra containing a specific point is found.   
    The library is particularly useful for applications using tetrahedral  meshes for rendering (Lagae & Dutré, 2008) or seismic processing.  
      
      References:  
        
      Hang Si (2015). "TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator". ACM Trans. on Mathematical Software. 41 (2),   
      Article 11 (February 2015), 36 pages.  
        
      Lagae, A. and Dutré, P. (2008), Accelerating Ray Tracing using Constrained Tetrahedralizations. Computer Graphics Forum, 27: 1303–1312.  
