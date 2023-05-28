# <ins> rate and irate function in promQL </ins> #

- `promQL` support 40 to 45 built in function where `few are common math function and few are specific to specific metrics `

#### <ins> rate function </ins> ####

- the rate function are mostly used with `counter type metrics`

- the `rate()` calculate the `per-second average rate of increase of the time series `in the `range vector metrics`

- `rate()` return how fast the `counter is moving or increasing per seconds in range vector time series `

- in other words we can say `rate()` output the `rate at which particular counter is increasing in the range vector time series `


- for example if we are considering the `prometheus_http_requests_total` metrics then it will return the `per second increase in http request in the range vector series`

- we can apply the range vector as below 

    ```
        prometheus_http_requests_total[1m]
        # this will provide the range vector as we have provided with [1m]
        but we can apply the rate() onto it which will provide the `per second increaase in time series as below `
        rate(prometheus_http_requests_total[1m])
        # this will provide the http requests happend on per seconds basis

    ```

- we can also filter out the `handler` label using the `matcher` as below for filtering 

    ```
        prometheus_http_requests_total{handler=~'/api.*'}[1m]
        # using the matcher operator with regular expression as below with `=~` symbol
        # when we use this then it will not able to see the graph as we are using the range vector instead of instant vector 
        # if we want to fetch the value for the range vector then we need to use the rate() as below 
        rate(prometheus_http_requets_total{handlers=~"/api.*"}[1m])
        #fetching the rate() over here to fetch the graph for the range vector where we want to filter by using the matcher

    ```

- we can't noramlly `graph` the `range vector output` by default 

- but the `rate()` by default takes an `range vector` as `input` and return the `instant vector` as output which is pretty easy to `graph`

- hence if we have a `range vector` as output then we can just apply the `rate()` to it in order to `graph` the range vector output


#### <ins> irate function </ins> ####

- unlike the `rate()` which calculate the `per second increase in the range vector ` the `irate()` functiopn calculate the `instant rate of increment  of time series in the range vector `

- the `irate()` calculate the `rate of increment` based on the `2 data point in the range vector based on the scrap interval `

- for example :-

    ```
        prometheus_http_requests_total{handler=~'/api.*'}[1m]
        # using the matcher operator with regular expression as below with `=~` symbol
        # when we use this then it will not able to see the graph as we are using the range vector instead of instant vector 
        # if we want to fetch the value for the range vector then we need to use the irate() as below 
        irate(prometheus_http_requets_total{handlers=~"/api.*"}[1m])
        #fetching the irate() over here to fetch the graph for the range vector where we want to filter by using the matcher

    ```

- the `rate()` used when we are `graphing the slow moving` range vectors 
- 
- where as the `irate()` used for graphing the `volatile or fast moving ` range vector 
