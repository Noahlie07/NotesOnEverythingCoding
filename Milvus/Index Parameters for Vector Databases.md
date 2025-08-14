# Index Parameters  
When we create a vector database, we specify index parameters. Index parameters are configuration parameters that determine how vectors are stored, organized, and retrieved successfully.  
These parameters affect:
1. Search Speed
2. Accuracy
3. Storage Usage

There are primarily two index parameters we need to be aware of:
1. Indexing Algorithm - determines how vectors are stored and searched
3. Distance Metric - determines how similarity/distance between vectors are calculated

## Indexing Algorithm  
Common options are:
1. **IVF** - IVF is an indexing technique focused on clustering. With this approach, you partition the vector database into clusters before indexing and give each cluster a representative centroid.
   The index is split into inverted lists, each containing vectors assigned to that cluster. When you run queries, you only compare the query to vectors in a select few clusters instead of the whole set.  
   Extra Parameters:  
   nlist - the number of centroids the vector database shall have  
   Pros:  
     - Fast Storage  
   Cons:  
     - Lower Accuracy  
2. **Product Quantization** - PQ compresses vectors into smaller codes to reduce memory usage and speed up distance calculations.  
   It splits a vector into subvectors (e.g., dividing a 128-dimensional vector into 8 subvectors of 16 dimensions each). Each subvector is mapped to a “codebook” of centroids, and the original vector is represented by a sequence of centroid IDs.  
   During a query, distances are approximated using precomputed lookup tables for subvector-centroid pairs.  
   Pros:  
     - Less Storage  
     - Faster Query Speed  
   Cons:  
     - Lower Accuracy  
   PQ is often combined with IVF (IVF-PQ) to first narrow the search space and then use compressed vectors for comparisons.
3. **HNSW (Hierarchical Navigable Small World)** - HNSW builds a layered graph where each layer is a subset of the previous one, with the top layer being sparse and lower layers denser.  
   During a query, the search starts at the top layer, navigating to nearby nodes, then refines the path in lower layers. This hierarchy mimics skipping lists in databases, enabling fast approximate searches.  
   For example, in a 10-layer HNSW index, a query might traverse 5 nodes in the top layer, then 20 in the middle layers, and finally 50 in the bottom layer—far fewer than checking all vectors.
   Pros:
     - Fast Query Speed  
   Cons:  
     - Large Storage Needed  

  ## Distance Metrics  
  1. 
