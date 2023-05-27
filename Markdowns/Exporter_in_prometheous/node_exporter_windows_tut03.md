# <ins> How to Get Windows Machine Metrics using the WMI_exporter </ins> #

- Same like `node_exporter` which exposes the `hardware and OS metrics` for the unix system `WMI exporter` does the Same for the Windows Machine 

- the `WMI` stands for `Windows Management Instrumentation` which allow the `hardware and OS related info of the Windows system` to be send to `prometheous server`

- to use the `WMI exporter` we need the windows machine and also its not available in the `prometheus official documentation` hence we need to download externally

- choose the `github account of WMI exporter`

- the `WMI exporter` will expose itself into the port `9182` 

- click on the `releases` &rarr; download the `latest version` for `64 bit`

## <ins> How to Install the `WMI exporter` </ins> ##

- by default if we open it then it will going to be get started and windows defender might intervene but we can see the details there 

- we can open to see the WMI exporter in `http://localhost:9182`

- it will expose the `metrics` in to the exposed metrics and send the `prometheus server` with its format only 

- then we need to configure the `scrap_configs` in here with the `job_name` and the `taget` in the `static_configs` section

- if we have prometheous installed on `windows` then we can just add to the `prometheus.yml` then we can see those info
  
- but if we have `prometheous` in `linux` and want to run the same in the `windows` machine then we have to do few `network related things`

### <ins> Network Support for running `prometheus` on linux and add the Target as `WMI_exporter` </ins> ####

- in the `Virtual Box ` we need to create a `Host Only Network` betweeen the `Host` and `VM which is Ubuntu` so that they can communicate over the `HTTP`

#### <ins>steps</ins> ####

  -   go to the `Virtual Box` &rarr; if `VM been running` then make it `stop`
  -   we need to create a `New Network Adapter` but before only the `Host Only Network` to which our VM can connect over http
  -   go to the `file manager` &rarr; `Host Network Manager` &rarr; `click on network` to create a `Host Only Network`
  -   we can see that in `virtual box Host-only ethernet Adapter <number>` will be created when we click on the `create button`
  -   we can also see the `ipv4` address of the `Host Only Network that we created`
  -   we can use the same `ipv4` address to use it in `VM` to connect to the `Host Network`

  <br/><br/>

  - go the `specific VM instance` &rarr; go to `settings` &rarr; go to `Networks` 
  - by default it has only `1 Network adapter` which is been giving `VM` the `internet connection`
  - but if we need to create a new network adapter in order to connect to the `Host Network`
  - `click on the adapter 2` &rarr; `enable the adapter`
  - select the `host only adapter` as the `attached to` section
  - select the `Host only network` that we have created 
  - then save the `info` to get the details and restart the ubuntu

<br/><br/>

  - we need to  check that whether we can `ping` to the `system` or not 
  - for that we can use it as `ping -c <ipv4 address of the Host only network>`
  - 





