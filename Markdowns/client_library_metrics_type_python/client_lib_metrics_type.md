# <ins> What is Client Library and How to add Metrics Type into it </ins> #

- if we want the `custom application metrics` into `prometheus` then we need to add the `instrumentation code` into the `application code`

- we can add the `instrumentation code` to display the `metrics onto prometheus server` using the `client library`

- we can add the `instrumentation` to the `aopplication code` using the `client Library of Prometheus`

# <ins> What is Client Library and What type of metrics we can publish to the Prometheus using the client library </ins> #


# <ins> What is Client Library </ins> #

- by using the `client library` and adding `two or three lines` of the code into the `application code ` we can get the desired instrumentation to your code and define the ` custom metrics` that we want to expose

- there are number of client libraries available for all major language and runtimes 

- prometheus project officially support client library for below languages 

    - Go
    - Java or Scala
    - python 
    - Ruby

- unofficial third-party client library available for 

    - Bash
    - C
    - C++
    - PHP
    - more 

- we can  add the `instrumentation` to the `application code` and then its the repsonsibility of the `client library` to expose the `metrics` to the prometheus server along with `rest all book keeping activity`


# <ins> What are the `core metrics type` that prometheus client library can support </ins> #

- prometheus client library support `4` type of `core metrics type` 

    - Counter Metrics
    - Gauge Metrics
    - Summary Metrics
    - Histogram Metrics

- Counter Metrics 
  
  -  A `Counter` is a `cumulative metrics /increasing metrics` that represents a `single monotonically increasing counter ` (i.e not very oftern)
  whose `value can only increase or reset to zero on restart `

  - `Counter` are mostly used as `instrumentation metrics for custom application` when we are using `client library`

  - by using the `Counter metrics` we can `track How often the code path been executed`

  - by using the `Counter metrics` we can calculate the 

    - How Many number of requests been served
    - How Many Task been completed 
    - How Many error Encountered 

  - `counter metrics` can only serve those `metrics` which `value` will increase in Number 

  - it has only one method `inc()` that increases the `counter metrics value` by `1`

  - we can increase the `Counter Metrics` value by any `arbitary number` by using the `set()`

  - we should bit use the `counter Metrics` to expose a `value` which can decrease in  `Number` for example 
    
    - Temperature as it can decrease 
    - Number of Running Process which can also decrease 
  
- Gauge Metrics  

  - A `Gauge Metrics` is a metrics which represent a `single numeric value` and can `arbitarily go up and down `
  
  - `Gauge Metrics` represent a `snapshot of some current state`

  - `Gauge Metrics` used for `measured values` like

    - temperature whose value can go up and Down over the time 
    - current memory usage whose value can go up and Down over the time 
    - number of currently active thread whose value can go up and Down over the time
    - anything whose value can go up or down over the time

  - `Gauge Metrics` has `3` different method that we can `override`
    
    - `inc()` :- which increases the `value by 1` by default
    - `dec()` :- which decreases the `value by 1` by default
    - `set()` :- by using which we can set the `arbitary number` to `increase or decrease`

- Summary Metrics

  - A `Summary Metrics` samples `observation` like `request duration`

    - How long the `your app take to respond to a request`
    - `Request Size`
    - `latency`
    - `Response Sizes`
    - `Request Size`

  - Summary track the `size and Number of events`
  
  - Summary has `observe()` to which we pass the `size of the event`


  - Summary exposes `multiple time series during the scrape`
    - the `total sum` by using the `basename_sum` of all observed values 
    - the `count` by using the `basename_count` of all events that have been observed 

     
  - Summary metrics may also include the `quantile` over a sliding `time window`


- Histogram Metrics

    - A Histogram also sample `observation` just like `Summary Metrics` such as `Requests Duration and Response Size`
    
    - Then it count them into `configurable bucket`
    
    - The inbstrumentation of `Histogram` will be same as the `Summary` Metrics
    
    - Histogram exposes `multiple time series during the scrape`
     
      - the `total sum` by using the `basename_sum` of all observed values 
      - the `count` by using the `basename_count` of all events that have been observed 

    - The main purpose of `Hostogram` is to calculate the `quantiles` 













