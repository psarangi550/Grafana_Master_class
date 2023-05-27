### <ins> Node Exporter for Linux Sytstem </ins> ###

- node exporter is a  `prometheous exporter` for `hardware an d OS metrics` exposed by `Unix Kernal` 

- it exposes the below `metrics` on unix system
  
  - kernal-lavel metrics
  - machine-level metrics 

- it provide the below metrics info such as 

    - CPU
    - Memory
    - disk space
    - disk I/O
    - network bandwidth

- the `node exporter` been written in `go language` with plugable metrics collector

### <ins> How to Install and Run the `node_exporter` </ins> ###

- we can download from `prometheus.io` &rarr; `download` &rarr; `node_exporter` &rarr; `select the Linux version`

-  there is no `node_exporter` available for windows system , They have a `separate exporter` for the `windows system` which is the `WMI exporter`

- extract the `Downloaded node_exporter zip ` and rename it to `node_exporter`

- go to the `extracted and renamed node_exporter folder` and start that with terminal by using it as below `node_exporter` on the terminal

- the default port of the `node_exporter` is `9100` which can be access by `http://localhost:9100`

- node exporter will only pull the data from the `Unix metrics` and transform them into the `prometheous metrics format` and handover the `metrics data` to the `prometheous server which required the metrics in specific format`

- every metrics of the `node exporter` will be prefix by `node_`

- if we want the `node_exporter metrics` which been exposed by `node_exporter` into the `prometheous Server` then we need to update the `prometheus.yml` file


#### <ins> How to Update the `prometheus.yml` in order to support the `node_exporter` metrics </ins> ####

- if we want to add a `new target` then we need to amend the `scrape_config` section in the `prometheus.yml` file 

- we can add a new `job_name` param as well as the `target` in the `static_configs` which is underneath the `scrape_configs` data

- here the taget address will be `target:['localhost:9100']`

- we need to be very precise about the `indentation` in the `prometheus.yml` file otherwise it will not work and the `new target` will not be recognised

- we need to restart the `promethous` in order appy the changes which is adding a new target

- we can start the prometheous by using the command as `./prometheous` in the extracted directory

- the default port for the `prometheous` is `9090` which is the `first Target` by defualt

- hence we can open the same using the command as `http://localhost:9090` 

- then we can go to the `status` &rarr; `targets` then we can see 2 target that we defined in the `prometheous.yml` file

- we have to see both should be in `up` state

- if we are searching then we can see the `node_` which is for the `node_exporter`

- if we evaluate the `up` expression which evaluate how many `metrics` currently associated with the `prometheous` and execute
and the corresponding value should be of `1`

-  fewe metrics are well documented which are 
   
   - CPU Usage
   - Memory Usage

- few are no so well documented


- we can see the `How much memory available over the time`

- for that we can use the `metrics` as &rarr;  `node_memory_mem_available_bytes`

- any metrics which starts with `node_memory` prefix known as `Mem info collectors` which has all the `standard memory related Data`

-  which will show the values in `Bytes` format

- we can see the `Graph View` to see the `usage in GB`

- we can also reduce the `time` in that manner

- for each `scape_interval` it will show the info which been defined in the `prometheus.yml` in the `global config section`



