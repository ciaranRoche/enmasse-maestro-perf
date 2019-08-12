# 3scale scaling on Openshift 3.11, Integreatly 1.4.x

## 3scale Components

| Component   |      Scaling information      |  Readiness Check |
|----------|:-------------:|------:|
| apicast-staging & apicast-production | <ul><li>Deploy a minimum of 2 PODs in different openshift nodes.</li><li>You can scale this component horizontally by adding more pods.</li><li>You can scale vertically this component by deploying one worker for each CPU core available to the apicast process. This is controlled by the variable APICAST_WORKERS</li></ul>  |  Both components have 
a definition of readiness probe checking: <ul><li>path: /status/ready</li><li>port: 8090</li></ul> |
| system-provider & system-developer | <ul><li>Deploy 2 or more pods</li><li>This POD scales horizontally you can simply add more PODs</li></ul> |   Both components have following readiness probe definition:
`httpGet:
  httpHeaders:
    - name:  X-Forwarded-Proto
     value: https
   path: /check.txt`|


<ul><li>item1</li><li>item2</li></ul>