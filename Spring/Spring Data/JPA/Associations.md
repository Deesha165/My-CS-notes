- `orphanRemoval = true`: _“If I no longer own this child, delete it completely.”_
    
- `cascade = REMOVE`: _“If I am deleted, delete my children too.”_
- so far, the conclusion is clear. Unidirectional @OneToMany association is less efficient than bidirectional @OneToMany association for reading, writing, and deleting data.
- Adding @OrderColumn can bring some benefits for removal operations. nevertheless, the closer an element to be removed is to the head of the fetched list, the more UPDATE statements are needed. this causes performance penalties. even in the best-case scenario (removing an element from the tail of the collection), this approach is not better than bidirectional @OneToMany association.
- Adding @JoinColumn instructs Hibernate that the @OneToMany association is capable of controlling the child-table foreign key. In other words, the junction table is eliminated and the number of tables is reduced from three to two
- Adding @JoinColumn can provide benefits over the regular unidirectional @OneToMany, but is not better than a bidirectional @OneToMany association. the additional UPDATE statements still cause a performance degradation.
-  Always try to query from the side that owns the foreign key 
- It looks like unidirectional @ManyToOne association is quite efficient and it can be used whenever a bidirectional @OneToMany association is not needed. Again, try to avoid the unidirectional @OneToMany association
- When using the @ManyToMany annotation, always use a java.util.Set. Do not use the java.util.List. In the case of other associations, use the one that best fits your case.
- this annotation (@OrderBy) can be used with @OneToMany/@ManyToMany associations and @ElementCollection. Adding @OrderBy without an explicit column will result in ordering the entities ascending by their primary key (ORDER BY author1_.id ASC). ordering by multiple columns is possible as well (e.g., order descending by age and ascending by name, @OrderBy("age DESC, name ASC"). obviously, @OrderBy can be used with java.util.List as well.
- In order to avoid outdated entities in the persistence Context, do not forget to flush the EntityManager before the query is executed (flushAutomatically = true) and clear it after the query is executed (clearAutomatically = true). If you don’t want/need to flush and/or clear then pay attention to how you manage to avoid outdated entities in persistence Context. As long as you know what you are doing, it’s not problematic to not flush and/or clear the Persistence Context. Ideally isolate bulk operations in dedicated transactional service-methods. This way, there is no need to explicitly flush and clear the Persistence Context. Issues may arise when you interleave bulk operations with managed entity operations.
- the most efficient way to delete all entities is via the built-in deleteAllInBatch(), which trigger a bulk operation.

---

- Fetch graph: This is the default fetching type represented by the javax.persistence.fetchgraph property. The attributes present in attributeNodes are treated as FetchType.EAGER. The remaining attributes are treated as FetchType.LAZY, regardless of the default/ explicit FetchType.
-  Load graph: This fetching type can be employed via the javax. persistence.loadgraph property. The attributes present in attributeNodes are treated as FetchType.EAGER. The remaining attributes are treated according to their specified or default FetchType.
- You can build dynamic api and make fully dynamic selection from db with only selected fields using JDBC.
- there are a bunch of advantages of using @MapsId, as follows: 
   • If Book is present in the second Level Cache it will be fetched accordingly (no extra database round trip is needed). this is the main drawback of a regular unidirectional @OneToOne.
    • Fetching the Author doesn’t automatically trigger an unnecessary additional query for fetching the Book as well. this is the main drawback of a regular bidirectional @OneToOne. 
    • sharing the primary key reduces memory footprint (no need to index both the primary key and the foreign key).
    