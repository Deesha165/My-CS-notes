- it is an interface has some implementations:
   1- HashMap: 
        - doesn't maintain the insertion order because it has no link between them only next pointer refer to next in bucket only for all in same index
        - consist of array of buckets 
        - same index resulting from (hashing key% bucket size) result in linked list and after threshold become red black tree
    2- HashTable: synchronized version of Hash Map
    3- LinkedHashMap: 
        - maintains the insertion order because it has after and before pointers which link all entry nodes
        - internally uses doubly linked list to maintain order
        - maintain access order which sorts from least frequent to most frequent makes it available for LRU caching
    4- Tree map : 
      - sorts data internally because it depends on red black tree which maintains order
      - all operations in O(log N)
    