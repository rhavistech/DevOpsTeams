# Architecture K8S

### How to install minikube

1. Install Kubectl

Kubectl is Kubernetes’ command line tool which you need to interact with your cluster. To download the latest release, you can use the following command:

`curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"`

2. Make your binary executable:

`chmod +x ./kubectl`

3. Move it to your executable path. For example if `/usr/local/bin/` is in your executable path:

`sudo mv ./kubectl /usr/local/bin/kubectl`

4. Install Minikube
There are three ways you can install Minikube, via a package, direct download, or with Homebrew. If you want to use a package, you can use your built-in package tool to find the right option.

If you want to install via direct download, use the following command:

`curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \ && chmod +x minikube`

5. Confirm installation

After your installation of the hypervisor and Minikube are complete you can start your local cluster.

`minikube start `


### How to install Docker Desktop

Do it download [click here](https://docs.docker.com/desktop/windows/install/)

After enable docker and kubernetes

It's worked.