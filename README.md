# Control Plane Deployment

Services related with the control plane of IDEA4RC project

# Table of contents

- [CONTROL PLANE](#control-plane-deployment)
  - [Table of contents](#table-of-contents)
  - [Requirements](#requirements)
  - [Deployment](#step-by-step-deployment)
  - [Test deployment](#test-deployment)
  - [Clean Up](#clean-up)
  - [Development](#development)
  - [Getting help](#getting-help)
  - [License](#license)
  - [Authors and history](#authors-and-history) 
  


## Requirements

This deployment uses a kuberntes cluster and the recomended amount of resources is 4 CPUs and 16GB of RAM for the Istio deployment to run smoothly.

## Step-by-step Deployment


After downloading Istio procced with:

Install Istio and enable injection in the datamesh ns

```shell
istioctl install --set profile=demo -y 

```
Set up a namespace to ensure the encapsulation of the services with mTLS. It also set the Istio sidecar injection automatically
```shell
kubectl apply -f kubernetes/base/001_datamesh-ns.yaml
```
Now we enforce the mTLS policy along the namespace we just created and we create the Istio Gateway resource pointing to localhost for local development 

```shell 
kubectl apply -f kubernetes/base/002_mtls-policy.yaml

kubectl apply -f kubernetes/base/003_gateway.yaml
```

## Clean up

Follow the steps to clean up

```bash
kubectl delete -f ./kubernetes

istioctl uninstall --purge -y

kubectl delete namespace istio-system
```

## Development

To contribute to the repo create a fork and make a pull request explaining the behaviour of the changes.

## Getting help

Feel free to create an issue if some bugs are detected or you need help.


License
------

```
Copyright 2023 Universidad Politécnica de Madrid

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

Authors and history
---------------------------
- Alejo Esteban ([@aeolmo]())
