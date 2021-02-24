[![NPM version](https://badge.fury.io/js/cdk-apisix.svg)](https://badge.fury.io/js/cdk-apisix)
[![PyPI version](https://badge.fury.io/py/cdk-apisix.svg)](https://badge.fury.io/py/cdk-apisix)
![Release](https://github.com/pahud/cdk-apisix/workflows/Release/badge.svg)


# cdk-apisix

CDK construct library to generate serverless [Apache APISIX](https://github.com/apache/apisix) workload on AWS Fargate

![](images/apisix-fargate-cdk.png)

# sample

```ts
import { Apisix } from 'cdk-apisix';

// create a standard apisix service
const apisix = new Apisix(stack, 'apisix-demo')

// create a sample webservice with apisix in the same Amazon ECS cluster
apisix.createWebService('flask', {
  environment: {
    PLATFORM: 'Apache APISIX on AWS Fargate'
  },
  image: ContainerImage.fromRegistry('public.ecr.aws/d7p2r8s3/flask-docker-sample'),
} )
```

## custom container image from local assets

```ts
new Apisix(stack, 'apisix-demo', {
  apisixContainer: ContainerImage.fromAsset(path.join(__dirname, '../apisix_container')),
  dashboardContainer: ContainerImage.fromAsset(path.join(__dirname, '../apisix_dashboard')),
});
```
