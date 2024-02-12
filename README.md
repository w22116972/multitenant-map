# multitenant-map

### Goals

- stores the entries **off-heap**
- serializing/deserializing KV objects to/from off-heap memory transparently
- caching/reusing KV for making **zero allocations (garbage) on queries**
- LRU entry eviction (X)

### Structure

Segments, each has
- independent memory allocation for storing KV
- hash table for search
- lock in shared memory (implemented via CAS loops) for managing concurrent access
