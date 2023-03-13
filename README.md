# Chaosblade-operator: A Chaos Engineering Tool for Cloud-native 
asdasdasdasdasd

## Introduction
Chaosblade Operator is a chaos experiments injection tool for cloud-native on kubernetes platform. By defining Kubernetes CRD to manage chaos experiments, each experiment has a very clear execution status. The tool has the characteristics of simple deployment, convenient execution, standardized implementation, and rich experiments. The chaos experimental model in chaosblade is well integrated with Kubernetes, which can realize the reuse of experiments such as basic resources, application services, and containers on the Kubernetes platform, which facilitates the expansion of resource experiments under Kubernetes, and can be executed uniformly through chaosblade cli tool.

## Supported experiments (continuously adding ...)
The current experimental scenarios involve resources including Node, Pod, and Container. The specific supported experimental scenarios are as follows:
* Node:
    * CPU: specify CPU usage
    * Network: specify network card, port, IP, etc. packet delay, packet loss, packet blocking, packet duplication, packet re-ordering, packet corruption, etc.
    * Process: specify process Hang, kill process, etc.
    * Disk: specify the directory disk occupation, disk IO read and write load, etc.
    * Memory: specify memory usage
* Pod:
    * Network: specify network card, port, IP, etc. packet delay, packet loss, packet blocking, packet duplication, packet re-ordering, packet corruption, etc.
    * Disk: specify the directory disk occupation, disk IO read and write load, etc.
    * Memory: specify memory usage
    * Pod: kill pod
    * IO: specify the file system io exception. Supports 31 file operations and 11 exception scenarios, such as "Too many open files", "Device or resource busy" and so on.
* Container:
    * CPU: specify CPU usage
    * Network: specify network card, port, IP, etc. packet delay, packet loss, packet blocking, packet duplication, packet re-ordering, packet corruption, etc.
    * Process: specify process Hang, kill process, etc.
    * Disk: specify the directory disk occupation, disk IO read and write load, etc.
    * Memory: specify memory usage
    * Container: remove container

## 

## Install and uninstall
The lowest version of kubernetes supported is 1.12. Chaosblade operator can be installed through kubectl or helm, the installation method is as follows:

Note: For the following `VERSION`, please use the latest version number instead

### Helm v2
* Download the latest `chaosblade-operator-VERSION-v2.tgz` package at [Release](https://github.com/chaosblade-io/chaosblade-operator/releases)
* Install using `helm install --namespace chaosblade --name chaosblade-operator chaosblade-operator-VERSION-v2.tgz`
* Use `kubectl get pod -l part-of=chaosblade -n chaosblade` to check the installation status of the Pod. If both are running, the installation was successful
* Use the following command to uninstall, pay attention to the execution order:
```shell script
kubectl delete crd chaosblades.chaosblade.io
helm del --purge chaosblade-operator
```
### Helm v3
* Download the latest `chaosblade-operator-VERSION-v3.tgz` package at [Release](https://github.com/chaosblade-io/chaosblade-operator/releases)
* Use `helm install chaosblade-operator chaosblade-operator-VERSION-v3.tgz --namespace chaosblade` command to install
* Use `kubectl get pod -l part-of=chaosblade -n chaosblade` to check the installation status of the Pod. If both are running, the installation was successful
* Use the following command to uninstall, pay attention to the execution order:
```shell script
kubectl delete crd chaosblades.chaosblade.io
helm uninstall chaosblade-operator -n chaosblade
```
### Kubectl
* Download the latest `chaosblade-operator-yaml-VERSION.tar.gz` package at [Release](https://github.com/chaosblade-io/chaosblade-operator/releases)
* After decompression, execute `kubectl apply -f chaosblade-operator-yaml-VERSION/` installation
* Use `kubectl get pod -l part-of=chaosblade -n chaosblade` to check the installation status of the Pod. If both are running, the installation was successful
* Use the following command to uninstall, pay attention to the execution order:
```shell script
kubectl delete crd chaosblades.chaosblade.io
kubectl delete -f chaosblade-operator-yaml-VERSION/
```