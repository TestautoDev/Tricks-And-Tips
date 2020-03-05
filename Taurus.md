 ### Taurus install linux
 
 sudo yum install java-1.8.0  
 sudo yum remove java-1.7.0-openjdk  
 sudo yum install python default-jre-headless python-tk python-pip python-dev \ libxml2-dev libxslt-dev zlib1g-dev net-tools  
 sudo yum -y install gcc  
 sudo yum install bzt  


### Docker command
docker run --rm -v C:\ccviews\taurus:/bzt-configs -v C:\ccviews\taurus\artifact:/tmp/artifacts blazemeter/taurus taurus_execution.yml

### Demo Script 1
```
execution:
- scenario: testlogin
  concurrency: 170
  hold-for: 50s
  duration: 60
scenarios:
  testlogin:
    headers:
      Content-type: application/json
      User-Agent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.122 Safari/537.36'
    requests:
    - url: https://
      method: POST
      label: '/signin'
      body:
        'username': 
        'password': 
      assert-jsonpath:
        - jsonpath: "$.ErrorNo" # path to value, validation fails if path not exists
          validate: true # validate against expected value
          expected-value: "0" # the value we are expecting to validate, default: false
          regexp: true  # if the value is regular expression, default: true
          expect-null: false  # expected value is null
          invert: false # invert condition 

reporting:
- module: console
- module: final-stats
  summary: true
  percentiles: true
  failed-labels: false   
  test-duration: true

```
### Demo Script 2
```
execution:
- scenario: testlogin
  concurrency: 300
  hold-for: 3000s
  duration: 1000
scenarios:
  testlogin:
    headers:
      Content-type: application/json
      User-Agent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36'
    requests:
    - url: https://
      method: POST
      body:
        'username': 
        'password': 
        
reporting:
- final-stats
- console        

```
