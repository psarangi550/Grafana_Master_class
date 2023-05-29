# <ins> How to Use the Http Server with Python Application </ins> #

- we can use thew command as `puython3 -m http.server` which will open a `webserver` on the port `8000`

- we can see all the `file related info` in `http://localhost:8000`

- if we want to run it on a different port then we can use the command as `python -m http.server <port number>`

- we can use the `-b` or `--bind` to bind the `ipv4 address` which can be written as below 

        ```
            python3 -m http.server <port number> -b/--bind <ip address that we want to bind to>
        
        ```

# <ins> How to Use the Http Server with Python Application to Build a Custom Web Application </ins> #

- we need to import the `HTTPServer`,`BaseHTTPRequestHandler` from `http.server` module 

- we need to define a class which will inherit the `BaseHTTPRequestHandler` class

- we can overide the `do_GET()` in order to define the `get()` response for the `get request`

- we can send the resopnse by using the `send_response(<repsonse code>)` on the `custom class instance that we created ` using which we can access the `response status code` when the request been coming for the `get request`

- we can also send the header by using the `send_header("content_type","text/html")` on the `custom class instance that we created `using which we can send `a header` to the `webpage`

- we can also use the `end_header()` to `end the header section that we want to send `

- then we can use the `wfile.write(bytes("<html code>","<encoding type can be of ascii or utf-8>"))` on the `custom class instance that we created ` to write the `html` onto the `server` so that we can get the `page displayed`

- we have to close  html writing by using the `wfile.close()`

- in order top start the http server based on the custom code then we need to instanciate the `HTTPServer` class by providing the `host` and `port number` and `custom child class of the BaseHTTPRequestHandler ` which will return a `HTTPServer class object` 

- here the `host` is a `string` but the port number will be of `integer number` 

- then we can call the `serve_forever()` on the `object of HTTPServer class object` in order to `start serving the request`

- we can also use the `server_close()` in order to close the `HTTPServer class instance`



# <ins> How to Use the Http Server with Python Application to Build a Custom Web Application with post request </ins> #

- for the `post` requests we need to override the `do_POST` method 

- we can send the resopnse by using the `send_response(<repsonse code>)` on the `custom class instance that we created ` using which we can access the `response status code` when the request been coming for the `post request`

- we can also send the `header` with `send_header("Content-Type","application/json")`  with which we can get the `json` in response

- then we can close the header using the `end_header()`

- As we are sending the `post requests` as the `JSON` then we can show that by using `wfile.write(bytes("<json string>","<encoding format>"))`

- we can close the `wfile` by using the command as `wfile.close()`


# <ins> How to Get the Local Time in String Format </ins> #

- we need to import the `time` module 

- `time` module has `strftime()` which takes the `format` and `localtime` as the `aegs`

- so we can write the code as 

    ```
        import time 
        #importing the Time module 
        str_time=time.strftime("%Y-%m-%d %H:%M:%S",time.localtime(time.time()))
        #by using this only time module we can get the localtime instring format 

    ```

# <ins> How to Use the `curl` to fetch the `POST and PUT` requests </ins> #

- we can use the `curl <ipv4>:<port>` to send the `Get Request`

- we can use the `curl <ipv4>:<port> -X POST` to send a `Post Request`

- we can use the `curl <ipv4>:<port> -X PUT` to send a `PUT Request`