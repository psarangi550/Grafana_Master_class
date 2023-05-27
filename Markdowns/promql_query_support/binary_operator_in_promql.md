# <ins> Operators in promQL query supports </ins> #

- promQl supports 2 types of operators  
  
  - Binary operator
  - Aggregation operator 

-  with this we can apply these operator in the `instant vector`

### <ins> Binary Operators </ins> ###

- Binary operator is the `operator` which takes 2 `operands` and perform specific calculation on them 

- Binary operator are then devided into 3 more categories 
   
   - Arithmetic Binaruy Operator 
   - Compairison binary operator 
   - Logical/Set binary operator 

##### <ins> Arithmetic Binary Operator </ins> #

- the standing binary arthmatic operator are of below type 
  
  - `+` (addition)
  - `-` (substraction)
  - `*` (multiplication)
  - `/` (division)
  - `%` (modulo)
  - `^` (power or exponentioal operator)
  
- Binary arithmatic opertor can be applied in between below values pairs
  
  - `scaler/scaler`
  - `vecor/scaler`
  - `vector/vector` 

- ex:- `node_memory_mem_active_bytes/8` which is the example of using the `binary arithmatic operator` on `vector and scaler value`

- when we apply the `binary arthmatic opertor` between the `vector and scaler` then that will be applied to `every instant vector value` which comes as the outcome


##### <ins> Compairison Binary Operator </ins> #

- compairsion binary operator is the `math symbol` which is used for `comparision`

-  the standing binary comparision operator are of below type 
   
   - `==` equal
   - `!=` not equal  
   - `>` greater than
   - `<` less than
   - `>=` greater than or equal
   - `<=` less than equal

- Binary comparision opertor can be applied in between below values pairs
  
  - `scaler/scaler`
  - `vecor/scaler`
  - `vector/vector`  

- ex:- `process_open_fds>2` which is an example of using `comparision operator` from `vector/scaler` values 

- this operator also help in `narrow` the `result` based on the condition 

- this can be also used for `Alerting` as well so that when the `CPU` ges beyong the `specific thresold` we can generate the `Alert`

##### <ins> Loigical or Set Binary Operator </ins> # 

- the `logical or set operator` are used for commbine `simple relational expression` into more `complex operation`

- the logical operator used to provide the `complex combination` based on multiple `comparision operator`

- the standing logical/set comparision operator are of below type 

  - `and` (intersection)
  - `or` (union)
  - `unless` (complement)

- unlike others the `logical/set binary operator` can be applied between the `instant vector only`

- we can use it as below 
  
  - `vector1 and vector2`
  - `vector1 or vector2`
  - `vector1 unless vector2`

- when we use the `logical and i.e intersection operator` used to find the `inbstant vector which been present in both the relational expression` with matching `label and option` and `metrics name`

- but when we apply the `logical or operation` then used to find the `instant vector` from both the `expression` but if a value is common then only the `left hand value` will be populated 

#### <ins> Different Metrics Expression Examples </ins> ####

- `node_memory_mem_total_bytes` is the `metrics` which will show how many bytes consumed by the `Memory` in total

- `node_memory_mem_available_bytes` is the metrics which will show `how much memory each disk space been consuming` 

- `prometheous_http_requests_total` metrics will show the `total http request made by the prometheus server`

- `node_cpu_seconds_total` is used for showing the metrics `each cpu been spending in its various mode`

- `promhttp_metric_handler_request_total` which will show the request based on the `metrics`

##### <ins> Important Notes </ins> #####

- we can devide by the `1024` to make it in `kb`

- further we can divide by `1024` to make it as `mb`
