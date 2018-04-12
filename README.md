# Jenkins POC requirement

This organization is created for Jenkins multiple repositories POC. 

Requirements:

### Build multiple repositories from develop branch

Need to build the develop branch of 

- light-4j
- openapi-parser
- light-rest-4j
- light-example-4j/rest/swagger/ms_chain/api_a/httpschain
- light-example-4j/rest/swagger/ms_chain/api_b/httpschain
- light-example-4j/rest/swagger/ms_chain/api_c/httpschain
- light-example-4j/rest/swagger/ms_chain/api_d/httpschain

Note that these repositories have to be built in a shared workspace so that artifacts can be shared by subsequent maven tasks. 


### End to end test for ms_chain APIs

Once the build is completed, there are four fat jars can be found in the target folders of ms_chain projects. 

These servers can be started by issuing the following command. 

```
java -jar light-example-4j/rest/swagger/ms_chain/api_d/httpschain/target/apid-1.0.0.jar
java -jar light-example-4j/rest/swagger/ms_chain/api_c/httpschain/target/apic-1.0.0.jar
java -jar light-example-4j/rest/swagger/ms_chain/api_b/httpschain/target/apib-1.0.0.jar
java -jar light-example-4j/rest/swagger/ms_chain/api_a/httpschain/target/apia-1.0.0.jar
```

Once all the servers are up and running, send a request to the api_a server. 


* host: https://localhost:7441
* path: "/v1/data"
*  method: get
 
Assert that response status code is 200 and the body is an array of strings with lengths of 8. 

### Build Feature Branch

### Test with external services

### Test with seperate environment tag

### Test with different configurations

### Dockerize servivces

### Test with docker-compsoe

### Test with Kubernetes cluster


