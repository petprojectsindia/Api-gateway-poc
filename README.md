# API-Gateway for web applications

 Let us assume that we have 2 different web applications which can be accessed by their own Urls.
 Let the names of the applications are app1, app2 respectively. Below are the Urls of app1 and app2.
 
 ```
    app 1 url - http://localhost:8081/app1
    app 2 url - http://localhost:8082/app2
 ```
 If we want to access these 2 applications using a single host in the url then they can be wrapped 
 under an API Gateway. Let us assume the Url of the API Gateway is as below.
 
 ```
 API Gateway url - http://localhost:8080/
 ```
 As mentioned above, if app1 and app2 are wrapped under the API Gateway then they can be accessed using
 below Url

 ```
 Generic Url to access app1 - http://localhost:8080/gateway/app1 - To access app1
 Generic url to access app2 - http://localhost:8080/gateway/app2 - To access app2
 ```

 Please note that both the applications are accessible under the common context /gateway/

## How to use this API Gateway for your projects - 

1) Open the application.yaml file in the src/main/resources/application.yaml.
2) Please add your application uri after the http://localhost:8080/gateway/<your application uri here without host>.
   Please refer below example.

```
       routes:
        - id: app1
          uri: http://localhost:8081/app1/
          predicates:
            - Path=/gateway/app1/**
          filters:
            - StripPrefix=1
        - id: app2
          uri: http://localhost:8082/app2/
          predicates:
            - Path=/gateway/app2/**
          filters:
            - StripPrefix=1

```



 
