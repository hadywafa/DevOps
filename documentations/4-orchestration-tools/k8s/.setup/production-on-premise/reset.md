# Resetting a Kubernetes Cluster

## Remove Kubernetes Components and Reset `kubeadm init`

### 1. **Stop and Disable Kubernetes Services**

First, stop and disable the kubelet service:

```bash
sudo systemctl stop kubelet
sudo systemctl disable kubelet
```

### 2. **Remove Kubernetes Components**

Remove all Kubernetes components and configurations:

```bash
sudo kubeadm reset -f
```

The `-f` flag forces the reset without prompting for confirmation.

### 3. **Remove Kubernetes Configuration Files**

Remove the Kubernetes configuration directory:

```bash
sudo rm -rf /etc/kubernetes/
```

### 4. **Remove CNI (Container Network Interface) Configurations**

Remove any CNI configurations:

```bash
sudo rm -rf /etc/cni/net.d
```

### 5. **Remove Containerd Containers**

Remove all Containerd containers related to Kubernetes:

```bash
sudo ctr c rm $(sudo ctr c ls -q)
```

### 6. **Remove Containerd Images (Optional)**

If you want to remove all Containerd images related to Kubernetes:

```bash
sudo ctr i rm $(sudo ctr i ls -q | grep -E 'k8s|kube')
```

### 7. **Clear IPtables Rules**

Clear any IPtables rules that were set up by Kubernetes:

```bash
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -t mangle -F
sudo iptables -X
```

### 8. **Remove Kubeconfig**

Remove the kubeconfig file from your home directory:

```bash
rm -rf $HOME/.kube
```

### 9. **Remove Kubelet, Kubectl, and Kubeadm**

If you also want to remove the kubelet, kubectl, and kubeadm binaries:

```bash
sudo apt-mark unhold kubeadm kubectl kubelet

sudo apt-get purge -y kubelet kubectl kubeadm
sudo apt-get autoremove -y
```

### 10. **Reboot the System (Optional)**

Rebooting the system can help ensure that all processes and services related to Kubernetes are completely stopped:

```bash
sudo reboot
```

After performing these steps, your system should be free of any Kubernetes-related components or configurations. You can then start fresh with a new `kubeadm init` if needed.
