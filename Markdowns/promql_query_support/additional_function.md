# <ins> how to apply the Aggregation on the `range vector`  or aggregation over the `Time function` </ins> #

- the aggregation operator such as below can be easily applied on the the  instant vector but if we have a range vector how to apply those  aggregation operator as below

  - `sum` (calculate the sum over the dimensions)
  - `min` (select the min over dimensions)
  - `max` (select the max over dimensions)
  - `avg` (calculate the average over dimensions)
  - `count` (count the number of elements in the vector)
  - `count_values` (count the number of elements with same value)


- we need to append `_over_time` to the existing `aggregation function` if we want to perform the `aggregation` over the `range vector`

  - `sum_over_time` (calculate the sum over the dimensions over time)
  - `min_over_time` (select the min over dimensions over time)
  - `max_over_time` (select the max over dimensions over time)
  - `avg_over_time` (calculate the average over dimensions over time)  
  - `count_over_time` (count the number of elements in the vector over time)
  - `count_values_over_time` (count the number of elements with same value over time)

- here these aggregation function will take the `range vector` as input and provide the `instant vector` as the output function based on the `pre range vector series value`





### <ins> Sorting Fuinction to Sort the sample in Prometheus </ins> ###

- by default the `prometheus` will not sort the return `value` in any order by default 

- but we can use the `sort function` to sort the return value as below 

- we can use the `sort()` in order to sort the `values` return by the `prometheus expression`

- the example of sort_function can be of 

    ```
        sort(node_cpu_seconds_total)
        # this will sort the `instant vector` return on ascending order based on their values 

    ```

- but if we want to sort it on the `descending order` then we can do that as below 

- by using the `sort_desc()` function we can sort the metrics value in descending order 

    ```
        sort_desc(node_cpu_seconds_total)
        # this will sort_descending the `instant vector` return on descending order based on their values 

    ```


### <ins> Time and Date Fuinction in Prometheus </ins> ###

- for dealing with the `date and time` prometheus provide number of function 

- `time()` is one of the example which return the `time inseconds since epoche i.e jan 1  1970 UTC `

- the `time()` does not take any argument only return the `epoche time in UTC`

- using the `time()` we can seehow long the `node_exporter` / `WMI_exporter` been up as below 

    ```
        time()-process_start_time_seconds{job="node_exporter"}
        # the metrics process_start_time_seconds will provide the start time of the pspecific process when it started 

    ```

- most of the `time` related queries `time()` is very helpful 

- `day_of_week()` which day of the week it is  where `0` stands for `sunday` and `6` is for `saturday`

- the `day_of_week()` also does not take any args in its function 

- similarly `day_of_month()` which will return the `date of the month` which will be `1 to 31` based on the value 

