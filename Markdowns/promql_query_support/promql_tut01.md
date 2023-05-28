# <ins> PromQL DataTypes </ins> #

- to query its `multi dimentional time series databases` prometheus provide the `PromQL support`

-  we can query the `Prometheous Multi dimentional Timeseries DB` but also provide the support for `arithmatic and aggregation` support as well

- when using the `promQL` which can support `4 datatype ` it can support which are of below types
  
  - instant vector
  - Range vector
  - scaler
  - string

### <ins> Instant Vector </ins> ###

- `instant vector` is a `set of time series` containing `single sample for each time series` all sharing the `same time stamp`

-  An instant vector is a `set of zero or more time series`

-  where `each time series has one sample` and each sample has both 
  `value and timestamp`

- if we query the `prometheus_http_requests_total` metrics then this will show the result in `prometheus_http_requests_total` with the values 

- each `time series` has a sample which corresponds to `sample` which is `timestamp and corresponding value`

### <ins> Range Vector </ins> ###

- A range vector is also a `set of time series` which contains the `range of data points over time for each time series`

- unlike `instant vector` where each time series has `one sample`

- but in case of `Range Vector` which can return `many sample per each time series ` i.e many `timestamp and values for each time series based on the time`

- we can write the `range metrics exporession` as `<metrics name>[<time duration>]`

- for this for each time series we have `multiple sample` which means multiple `timestamp and  values for the duration mentioned` based on the `scrape_interval`

### <ins> Scaler </ins> ###

- scaler are `single number with no dimentionality`

- its just a `simple numeric floating point value` that don't have `labels and option` like vector 

- they are only numbers 

- ex:L-15.21

### <ins> String </ins> ###

- string is very rarely used 

- its just a string value without having any label or option 

- 



