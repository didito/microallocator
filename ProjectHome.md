The micro allocator provides extremely high speed micro-allocations.  A micro-allocation is defined as any allocation 256 bytes or less.  It uses a fixed pool allocation system, similar to the LOKI memory allocator.  For fast allocation it has a pointer array for every size between 0 and 256 bytes.

In most cases allocations and de-allocations are 'order N', with allocations costing only a few instruction cycles.

De-allocations can take longer if you didn't reserve enough memory to begin with.  First estimate the total size you think your application will need for micro allocations.  Typically on the order of several megabytes.

The major performance benefit will be when you use it for STL allocations.

All memory allocations are 16 byte aligned and, since objects of similar size will end up the same area in memory, you will get a natural cache-coherency.

Feedback, bug-fixes welcome.  Should compile on most operating systems with few changes and should be 64 bit and thread safe.