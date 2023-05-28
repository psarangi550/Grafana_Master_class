# <ins> Ignoring and On Keyword in PromQL </ins> #

- when we are using the `and/or` which are of `logical/set binary operator ` we can also use the `ignoring and on keyword` for its `extended functionality`

- by using the `ignoring` keyword we can ignore certain `label` which we don't want to match while matching certain element

- where as the `on` keyword will `limit the label to match` to `specified list only`

- we can write the code as below for the `ignore` keyword with `logical set operator `
  
    ```
        prometheus_http_requests_total and ignoring (handler) promhttp_metrics_handler_requests_total 
        # here it is similar to the vector 1 and ignore (<label we want to ignore>) vector 2
        # this will potentially ignore the label header while applying the `logical set operator which is and in this case`
    ```

- we can write the code as below for the `on` keyword with `logical set operator `

    ```
        using the `on` keyword we can match only those label which being mentioned in the `list`
        prometheus_http_requests_total and on (code) promhttp_metrics_handler_requests_total 
        # here it is similar to the vector 1 and on (<label we want to see the match only >) vector 2
        # this will potentially match the label which are provided  while applying the `logical set operator which is and in this case`

    ```

