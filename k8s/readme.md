## Setting up kubernetes in local machine

To set up Kubernetes on your local machine, you can use tools like Minikube, Kind, or MicroK8s. Below are step-by-step instructions for setting up Kubernetes using Minikube, one of the most popular tools for local development.

### Step 1: Install Prerequisites

1. **Install Virtualization**: Minikube requires a hypervisor. Install one of the following:
   - **VirtualBox**: [Download here](https://www.virtualbox.org/wiki/Downloads).
   - **Docker**: [Download Docker Desktop](https://www.docker.com/products/docker-desktop) (preferred option).

2. **Install Kubectl**: This is the Kubernetes command-line tool.
   - **For macOS**:
     ```bash
     brew install kubectl
     ```
   - **For Windows**: Use `choco install kubernetes-cli` (if using Chocolatey) or download from the [Kubernetes website](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

3. **Install Minikube**:
   - **For macOS**:
     ```bash
     brew install minikube
     ```
   - **For Windows**: Use `choco install minikube` or download the installer from the [Minikube website](https://minikube.sigs.k8s.io/docs/start/).

### Step 2: Start Minikube

1. Open a terminal or command prompt.
2. Start Minikube:
   ```bash
   minikube start --driver=docker
   ```
   This command will start Minikube using Docker as the hypervisor. If you are using VirtualBox or another driver, specify it with `--driver=virtualbox`.

### Step 3: Verify Installation

1. Check the status of Minikube:
   ```bash
   minikube status
   ```
2. Check the status of your cluster:
   ```bash
   kubectl cluster-info
   ```
   If your setup is correct, you should see details about your Kubernetes control plane and DNS.

### Step 4: Interact with Kubernetes

1. **Deploy an Application**: For example, deploy a simple Nginx application.
   ```bash
   kubectl create deployment nginx --image=nginx
   ```
2. **Expose the Deployment**: Make the application accessible outside the cluster.
   ```bash
   kubectl expose deployment nginx --type=NodePort --port=80
   ```
3. **Access the Application**: Get the URL to access the application.
   ```bash
   minikube service nginx --url
   ```
   This command will give you a URL that you can open in your browser to see the Nginx welcome page.

### Step 5: Manage Minikube

- **Stop Minikube**:
  ```bash
  minikube stop
  ```
- **Delete Minikube Cluster**:
  ```bash
  minikube delete
  ```

### Additional Tips

- **Configuring Resources**: Minikube allows you to configure the amount of CPU and memory allocated.
  ```bash
  minikube start --cpus=4 --memory=8192 --driver=docker
  ```
- **Using Minikube Dashboard**: Minikube comes with a built-in Kubernetes Dashboard.
  ```bash
  minikube dashboard
  ```

### Troubleshooting

- If Minikube fails to start, check logs using:
  ```bash
  minikube logs
  ```
- Ensure that virtualization is enabled in your BIOS/UEFI settings if using VirtualBox or similar hypervisor.

Following these steps will help you get Kubernetes up and running on your local machine using Minikube, enabling you to test and develop Kubernetes applications locally.
