# <ins> Aggrregation operators in PromQL </ins> #

- when we have thousand of `instance metrics` in thae target application then in that case it is practically impossible to `take all the instances into consideration` in that case we have to use the `aggregation operator`

- we can use the `aggregation operator` on the `instance metrics` to see the `combined group result` into a single value 

- agregator operator are `special mathmetical function` that are used to combine information 

- prometheus support few aggregation operator which is used to combine the `instant vector` to return a new `instant vector` with aggregated values 

- the following aggregation operator are supported in prometheus 
  
  - `sum` (calculate the sum over the dimensions)
  - `min` (select the min over dimensions)
  - `max` (select the max over dimensions)
  - `avg` (calculate the average over dimensions)
  - `stddev` (calaculate he population standard deviation over dimension)
  - `stdvar` (calaculate he population standard variance over dimension)
  - `count` (count the number of elements in the vector)
  - `count_values` (count the number of elements with same value)
  - `bottomk` (smallest k element by sample value)
  - `topk` (largest k element by sample value)
  - `quantile` (calaculate  Θ-quantile (0<Θ<1) over dimension) 


- we can see the example of the same as below 
  
  ```
    sum(prometheus_http_requests_total)
    # using the sum aggregated method on the  prometheus_http_requests_total metrics 
    # this will all the `value` of `each sample metrics` in order to display it as the total value 

  ```

- by using the `by` keyword we can group the `metrics labels into specific group`

- the `by` operator can be used it with aggregation operator as below 

    ```
    sum(prometheus_http_requests_total) by (code)
    #here we are also using the `by` keyword to devide that into multiple groups as `by(<label name>)`
    # using the sum aggregated method on the  prometheus_http_requests_total metrics 
    # this will all the `value` of `each sample metrics` in order to display it as the total value 

    ```

- the `topk` aggregation operator return the `largest k element based on the samplke value ehich is the time series and its value `

- the example for the same can be written as below with the `k` value

    ```
        sum(node_cpu_seconds_total)by(node)
        # this will first group the `instant cvector based on the node`
        # then it will perform the sum on those gropuped values 
        # then  we can fetch the top3 values as below 
        topk(3,sum(node_cpu_seconds_total)by(node))
        # this will provide the top 3 mode where cpu spending most of the time 
        #here the syntax of the topk and bottomk operator is as below 
        topk(<number>,<expression that we want to aggregate upon>)

    ```

- we can here use the `rate function as well ` which we learn later 

- same like `topk` the `bottomk` can be used as below 

    ```
        bottomk(<number>,<expression that we want to aggregate upon>)

    ```

- when we use the `sum/max/min/average/count/count_values` it will be consider over the `dimentsion` it will return the `aggregated value` even though the `element name comes as {}` we can group them well in order to see the `element name`


