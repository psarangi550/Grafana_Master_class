# <ins> Selector and Matcher in promQL </ins> #

- we have a lot of `different time series with different labels and option`

- if we want to filter out the `time series based on the labels` then we have to use `matchers`

### <ins> Matcher </ins> ###


- we can also run the metrics as below 
  
  - `process_cpu_seconds_total` metrics which will return the values in `instant vector format` which will provide the `total user and system cpu time in second`
  
  - it will return all the time series with the value `process_cpu_seconds_total` with the name and `label and option` associated with it 

  - this will return the `instant vector` with `all the metrics connected to the prometheus server`

  - but if we want to only see the `WMI_exporter` total user and system cpu time in seconds then we can filter that using it as matcher as below which will filter the `label and option`
  
  - if we want to filter the `instant vector` based on the `label and option` then we can use the matcher in here

  -  we can narrow the `instant vector time series` only fetching the required `time series value`
  
  - in order to apply the filter we can apply the set of `{}` over here along with the query expression
  
  -  inside the `{}` we can define the `label name` and  `label value` for which we want the value 

  - this `filter` that we decided with the `{<label>=<value>}` known as the `matcher`

  - we can alsio have matcher with `and` condition in between them

  - the `,` can also be consider as the `and` condition over here 

  - this can be easily considered as the `select * from <metrics name> where filder_condition=<value>`
  

### <ins> Type of Matcher </ins> ###

  - There are 4 type of `matcher` being present in here
    
    - Equality matcher represented by `=` sign which will return those matrics which has the `same label value provided in the filtering condition` and it is `case sensitive`
    
    - Negetive Equality matcher represented by `!=` sign which will return those metrics which does not have the  same label value provided in the filtering condition and`  it is case sensitive`
    
    -  Regular expression matcher represented by `=~` which will return those time series metrics which does contains the value provided in the `regular expression`  
       
       -  `prometheus_http_requests_total` which will return the `http request made by the prometheus server` which will return the value in `instant vector format`
       
       -  but if we want to filter a specific `endpoint http request` then we can do that by using the `regular expression Matcher` as below 
       
       - by using the `prometheus_http_requests_total{handler=~/api.*}` then we can filter only those end point which been have the handler as `/api` as the `beginning`    

       - it is also `case sensitive` by default 
    
    -  Negetive Regular expression matcher represented by `!~` which will return those time series metrics which does not contains the value provided in the `regular expression`  
       
       -  `prometheus_http_requests_total` which will return the `http request made by the prometheus server` which will return the value in `instant vector format`
       
       -  but if we want to filter  not a specific `endpoint http request` then we can do that by using the ` negetive regular expression Matcher` as below 

       - by using the `prometheus_http_requests_total{handler!~/api.*}` then we can filter only those end point which been have not have the handler as `/api` as the `beginning`

- Even though we are `filtering tjhe time series but still that comes under the instant vector time series ` ie one `sample` fopr each time series even after the `filtering`

- but we can make it as `range vector` by providing the `time` in the `[<time duration>/<range duration>]` and based on the `time provided` correspoding value will be selected

- when we select the `range duration` then we can see for the `range duration time` we can see the value based on the `scrape duration` 

