# kubeadm-vagrant
Create a 3-nodes k8s cluster running on local VirtualBox using kubeadm and Ansible with a specific k8s version. 

This configuration will deploy k8s cluster v1.13.4.

This work is based on the [Kubernetes Setup Using Ansible and Vagrant](https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/) with some update on Calico deployment and predefined k8s version deployment

## Requirements
- Vagrant: [download](https://www.vagrantup.com/downloads.html) or install via ` brew cask install vagrant` (MacOS)
- Oracle Virtualbox: install via `brew cask install virtualbox`
- Ansible (>= v2.7.x): install via `brew install ansible`

## Deployment

```
$ vagrant up
...

$ vagrant status
vagrant status
Current machine states:

k8s-master                running (virtualbox)
node-1                    running (virtualbox)
node-2                    running (virtualbox)

$ vagrant ssh k8s-master

$ kubectl get nodes -o wide
NAME         STATUS   ROLES    AGE     VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
k8s-master   Ready    master   4m55s   v1.13.4   10.0.2.15     <none>        Ubuntu 16.04.5 LTS   4.4.0-131-generic   docker://18.9.3
node-1       Ready    <none>   2m42s   v1.13.4   10.0.2.15     <none>        Ubuntu 16.04.5 LTS   4.4.0-131-generic   docker://18.9.3
node-2       Ready    <none>   40s     v1.13.4   10.0.2.15     <none>        Ubuntu 16.04.5 LTS   4.4.0-131-generic   docker://18.9.3 
```
