## <ins> Exporter in Prometheous </ins> ##

- if we want to `monitor any application by using prometheous`  then we need to add the `instrumentation of the application`  
- promethous comes with a lot of `client library` which will help in monitoring the `corresponding application` using prometheous
- if we have a `python application` then we can add `instrumentation to the code` using the `prometheous client library` in order to get monitor by the `prometheous`
- sometimes for soime application like the `operating system` we don't have access to the code and hence we can't add instrumentation then we can use `exporter` in order to monitor those application

### <ins> What is An Exporter </ins> ####

- `An Exporter` is a `software/number of libraries or server` that help in `exporting the metrics` from `third party system (such as Linux or Windoes OS)` in the same format as `promethous metrics`


- `Exporter` are really helpful where its not feasible to `instrument a given system with promethous directly` for example (Linux system/HA proxy)

<br/><br/>


- we can deploy the `Exporter` right beside the `third party system or machine ` which will  
  - get the request from promethous what it actually need in terms of `metrics`
  - gather that data from the target i.e from the third party system
  - transform them into the correct format what promethous can understand
  - then send to the `promethous server` back as per the `request`


- exporter can also be considered as a `one to one proxy` which convert the `format of the meterics that the 3rd p[arty system provide and frmat required by promethous server`

