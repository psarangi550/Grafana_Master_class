# <ins> Fuction for gauge type metrics such as changes, derivs and predict_linear  </ins> #

- the `gauge` type metric which `value can go up or down `

#### <ins> changes function for gauge metrics </ins> ####

- we can see the `How many times the gauge metrics changes it value over the time ` using the `changes()`

- `changes()` can only be applied on the `range vector can't applied on the instant vector`

- there are few metrics which are expected to change very less with the time such as `process start time`

- `process_start_time_seconds` which is a `gauge metrics` which provide the `start time of the process in seconds`

- for example :-

    ```
        changes(process_start_timne_in_seconds)
        # which will provide the how many times the `process_start_time_seconds` changed over the time 
        # here we are using the `changes()` over a gauge metrics

    ```

- we can also use it as below with a specific `process_start_time_seconds` for particular job using the `matcher` as below 

    ```
        changes(process_start_time_seconds{job="node_exporter"}[1h])
        # this will provide a node exporter value change over the time 
        # hwere if the node_exporter been running then we can see the value as the `0`
        #but if we stop the node_exporter and restart it again then we can see the value become 1 after the node_exporter been restarted and wait for 15 seconds
        # when we atop the `node_exporter` and restart it again then its value also changes in the time which been captured after restarting the node_exporter and waited for 15s 

    ```

#### <ins> deriv function for gauge metrics </ins> ####

- `deriv()` help in check `How Quickly the gauge metrics been changing `

- `deriv()` help in checking how quiockly the `gauge metrics been changing ` i.e `increasing or decreasing`

- the `deriv()` estimate the `slope of each timeseries in the range vector ` and calculate `per-second derivatives of that time series `

- the metrics `process_resident_memory_bytes` which show the `resident memory in bytes used for the process for specific job`

- for example for job `prometheus` how fast the `resident memory` been changing during the `past 1 hr` can be done by using the `deriv()`

    ```
        deriv(process_resident_memory_bytes{job='prometheus'}[1h])
        # here for the job='prometheus' how fast the process_resident_memory_bytes metrics been changing can be found out on the last 1hr 
        # deriv() can only be applied on the gauge metrics 
        # deriv() can only be applied on the range vector which return an instant vector 

    ```


#### <ins> predict_linear function for gauge metrics </ins> ####

- `predict_linear` function predict the future metrics value based on the current pattern of current `gauge metrics`

- this is one step ahead of the `deriv()` that we have used for the `gauge metrics`

- based on the `specific time duration corresponding value` predict the `future value of the metrics `

- we can predict `how memory will be availble in the windows os for the next 2 hr` then we can do this as below 

- for this we have to use the `metrics` as `windows_logical_disk_free_bytes` as below 

- the `predict_linear()` takes a `range vector` and `time in number` as `argument` and return the `instant vector` as the `prediction value `



    ```
        predict_linear(windows_logical_disk_free_bytes{volume="C:"}[1h],1)/1024/1024/1024
        # here this will show how much space will be there in the next 1 seconds based on the past 1hr value 
        # here we are using the windows_logical_disk_free_bytes as the metrics 
        # this predict_linear() can only work on the `gauge metrics`
        # this take an `range vector` and `numeric time value` as the args
        # also return the instant vector as an outcome

    ```
    - we can use the metrics as `node_memory_MemFree_bytes` for the linux system as well

    ```
        predict_linear(node_memory_MemFree_bytes{job="node_exporter"}[1h],1)/1024/1024/1024
        # here this will show how much space will be there in the next 1 seconds based on the past 1hr value 
        # here we are using the node_memory_MemFree_bytes as the metrics 
        # this predict_linear() can only work on the `gauge metrics`
        # this take an `range vector` and `numeric time value` as the args
        # also return the instant vector as an outcome

    ```

    - if we want to calcuate for the `next 2 hr` then it can be written as below

    ```
        predict_linear(node_memory_MemFree_bytes{job="node_exporter"}[1h],2*60*60)/1024/1024
        # here this will show how much space will be there in the next 2 hour in seconds format  based on the past 1hr value 
        # here we are using the node_memory_MemFree_bytes as the metrics 
        # this predict_linear() can only work on the `gauge metrics`
        # this take an `range vector` and `numeric time value` as the args
        # also return the instant vector as an outcome

    ```



    

