- it is common place between persistence contexts and DB 
- to enable it we use emcache and it is common for all persistence contexts
- it involve four cache concurrency strategy
   1- Read_Only
   2- Read_Write
   3- nonstrict read_write
   4- Transactional
- second level cache appear when we make the first get call not insert into DB
- 