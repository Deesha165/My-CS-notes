- having uses aggregated results after calculations unlike where 
- if you want to use result of aggregation in condition at same query use having
- self join is important trick to compare rows based on specific conditions 
- use left join if you want always left table to appear in results
- use cross join if you want to introduce match with each other row
- Use CTEs if you want to make immediate calculations before calculating result
- Always use limit with offset to start with specific nth row 
-  Always use exists and not exists to check existence of row instead of In
- Use union to combine between results without repeation and union all if you want repeated values
- you can include conditions with aggregated functions such as 
  select count(case when rating>3 then 1 else 0 end)
- you can select based on conditions like:
   case when rating>3 and rating <5 then 1 
      when rating >5 then 2
      else 3 
      end as rating_value
- 