# WSL Questions

## What it is WSL ?

- WSL 2 runs a lightweight VM using a Linux kernel, and all your WSL distributions run inside this single VM.
- This VM has its own IP address, and all WSL distributions share the same network namespace, meaning they use the same IP address for external communication.

## 1. Why All WSL Distributions Have the Same IP

- **Single Network Interface**: The WSL 2 VM has a single network interface that is shared by all running WSL distributions. Therefore, when you query the IP address within any WSL distribution, you get the IP address of the WSL 2 VM.

- **Shared Network Namespace**: WSL 2 distributions run within the same network namespace provided by the WSL 2 VM. This means they share the same network stack and consequently the same external IP address.
