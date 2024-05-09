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

First step is having [HELM](https://helm.sh/docs/intro/install/) installed.

After downloading [Istio](https://istio.io/latest/docs/setup/install/istioctl/) procced with:

Install Istio and enable injection in the control-pane name space

```shell
istioctl install --set profile=demo -y 

kubectl create namespace control-plane

kubectl label namespace control-plane istio-injection=enabled

```

Next install the control plane chart

```shell
helm install control-plane-chart ./control-plane-chart/
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
