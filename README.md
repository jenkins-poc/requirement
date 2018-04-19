# Jenkins POC requirement

This organization is created for Jenkins multiple repositories POC. 

Requirements:

### Build multiple repositories from three branches

Need to build at the same time for develop, feature1 and feature2 branches of 

- light-4j
- openapi-parser
- light-rest-4j
- light-example-4j/rest/swagger/ms_chain/api_a/httpschain
- light-example-4j/rest/swagger/ms_chain/api_b/httpschain
- light-example-4j/rest/swagger/ms_chain/api_c/httpschain
- light-example-4j/rest/swagger/ms_chain/api_d/httpschain

Note that these repositories have to be built in a shared workspace for the same branch so that artifacts can be shared by subsequent maven tasks. It will not work to push the artifact to any centralized artifact repository as the code in three branches are not compatible. 


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

Here is the exmaple command. 

```
curl -k https://localhost:7441/v1/data
```

And the result is

```
["API D: Message 1","API D: Message 2","API C: Message 1","API C: Message 2","API B: Message 1","API B: Message 2","API A: Message 1","API A: Message 2"]
```

### Build Feature Branch

### Test with external services

### Test with seperate environment tag

### Test with different configurations

### Dockerize servivces

### Test with docker-compsoe

### Test with Kubernetes cluster


