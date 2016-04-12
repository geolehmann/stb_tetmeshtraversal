# stb_tetmeshtraversal  

**Single-header mesh traversal library using tetgen.**
  
    
This library provides functions for traversing tetrahedral meshes generated with the Tetgen software by Hang Si (_Si, 2015_). Functions implemented include loading tetgen .face/.edge/.ele/.node/.neigh/.t2f files, locating the tetrahedra containing the ray origin, traversing the mesh until a constrained triangle face is found and mesh traversal until a tetrahedra containing a specific point is found.     

The library is particularly useful for applications using tetrahedral  meshes for rendering (Lagae & Dutré, 2008) or seismic processing.  

Usage:

- This library only works with the beta version of Tetgen: 1.5.1-beta1 (in previous versions no tetrahedra-face relations as .t2f files were stored)
- When generating the mesh with Tetgen, ensure the switches -n -nn -f -z are used. A typical example might be: 

tetgen -pq1.4 -n -nn -f -z cornellbox.stl 

- Use the loader functions provided in the class _tetrahedramesh_ to load the single tetgen files. Load order should be ele->neigh->node->face->t2f->edge.
- At the beginning, the tetrahedron containing the starting point has to be located with the function _GetTetrahedraFromPoint_. This has to be done only once. If the position changes later on, adjacency information of the tetrahedra can be exploited to keep track the movement of the starting point. 
- Mesh traversal is done with the function _traverse_ray_, which takes the mesh, ray origin/direction and index of the starting tetrahedron as input. The _rayhit_ structure stores the indices of the intersected face and tetrahedron. 

Example code:
	
	tetrahedra_mesh tetmesh;
	tetmesh.load_tet_ele("cornell_spheres.1.ele");
	tetmesh.load_tet_neigh("cornell_spheres.1.neigh");
	tetmesh.load_tet_node("cornell_spheres.1.node");
	tetmesh.load_tet_face("cornell_spheres.1.face");
	tetmesh.load_tet_t2f("cornell_spheres.1.t2f");
    
    // get starting tetrahedron
    float4 start_tet = GetTetrahedraFromPoint(tetmesh, camera_position);
    // stores the hit information
    rayhit hitpoint;
  	// ray traversal
    traverse_ray(tetmesh, camera_position, camera_direction, 						 	start_tet,hitpoint);
    

For a full working implementation of this library, have a look at: https://github.com/clehmann-geo/tetra_mesh
      
**References:**
        
Hang Si (2015). TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator. _ACM Trans. on Mathematical Software. 41 (2), Article 11 (February 2015), 36 pages._
        
Lagae, A. and Dutré, P. (2008). Accelerating Ray Tracing using Constrained Tetrahedralizations. _Computer Graphics Forum, 27: 1303–1312._
