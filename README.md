# cURL for Performance Engineers

## Examples

In WSL:
```curl --version```

In Windows PowerShell:

```curl -version``` will fail. Type ```curl.exe --version``` for valid output.

```curl https://example.com```

```curl -v https://example.com```

```curl --trace output https://example.com```

```curl --trace - --trace-time example.com```

```curl --trace-ascii ascii_output https://example.com```

### Globbing

```curl https://reqres.in/api/users/\[1-10\]```

```curl https://reqres.in/api/users/\{1,10,111,5\}```

#### Storing Output
```curl https://reqres.in/api/users/\{1,10,111,5\} -o "output_#1"```

> ls  

> output_1  output_10  output_111  output_5

### Progress Bar

```curl https://reqres.in/api/users/\{1,10,111,5\} -o "output_#1" -#```

### Redirects
```curl http://example.com/ > example.html```

```curl example.com --next example.net```

### Follow Redirects

```curl google.com -L```

### Proxy
```curl -x localhost:8080 http://example.com/```

```curl --proxy localhost:8080 http://example.com/```

### POST
```curl -X POST -d '{"name":"morpheus","job":"leader"}' https://reqres.in/api/users```

####  Multipart Form
```
curl -F custname=tester \
 -F custtel=1234 \
 -F custemail=test%40test.com \
 -F size=small \
 -F topping=bacon \
 -F delivery=15%3A00 \
 -F comments=knock+the+door \
 http://httpbin.org/post
```

### Cookies

#### Save
```curl -c cookies.txt http://example.com```

#### Load
```curl -b cookies.txt https://www.google.com```

### Basic Auth

```curl --user client321:test123 https://zigzag-selective-boysenberry.glitch.me```

### Performance Measurements

```curl -w "Request Done \n" http://example.com/```

```curl -w @output.txt http://example.com```

```curl -w "HTTP Version: %{http_version}\nCode: %{response_code}\nTotal Time: %{time_total} \n" --head http://example.com```

```curl -w @timings.txt --head http://bing.com```

timings.txt
```
url: %{url}\n
code: %{response_code}\n
number of bytes: %{size_download}\n
average download speed: %{speed_download}\n
average download speed: %{speed_upload}\n
redirect_url : %{redirect_url}\n

time_namelookup:  %{time_namelookup}s\n
time_connect:  %{time_connect}s\n
time_appconnect:  %{time_appconnect}s\n
time_pretransfer:  %{time_pretransfer}s\n
time_redirect:  %{time_redirect}s\n
time_starttransfer:  %{time_starttransfer}s\n

time_total:  %{time_total}s\n
```
