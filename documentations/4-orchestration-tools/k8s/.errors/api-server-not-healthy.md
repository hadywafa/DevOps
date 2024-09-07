# API Server Not Healthy

## Problem

```ini
Unfortunately, an error has occurred:
context deadline exceeded

This error is likely caused by: - The kubelet is not running - The kubelet is unhealthy due to a misconfiguration of the node in some way (required cgroups disabled)

If you are on a systemd-powered system, you can try to troubleshoot the error with the following commands: - 'systemctl status kubelet' - 'journalctl -xeu kubelet'
error execution phase kubelet-start: context deadline exceeded
To see the stack trace of this error execute with --v=5 or higher
```

## Solution 1 => Disabling the swap memory and enabling the cgroup memory

the solution is by disabling the swap memory and enabling the cgroup memory

```bash
sudo swapoff -a
sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```

If the directory `/etc/systemd/system/kubelet.service.d/` does not exist, you can create it and then configure the `kubelet` options, or modify the main `kubelet` service file directly.

Here’s how you can disable the cgroup driver for `kubelet` by modifying the correct configuration:

## Solution 2 => Steps to Disable Cgroups for Kubelet

To disable cgroup for the kubelet service, you'll need to modify the kubelet configuration file, specifically the kubelet systemd service options. Here's how you can do it:

### Option 1: Create the `kubelet.service.d` Directory and Config

1. **Create the directory**:

   If the directory doesn’t exist, create it using the following command:

   ```bash
   sudo mkdir -p /etc/systemd/system/kubelet.service.d/
   ```

2. **Create a new configuration file**:

   Create a new drop-in file to configure `kubelet` options:

   ```bash
   sudo nano /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
   ```

3. **Add the `--cgroup-driver=none` option**:

   Add the following content to the file:

   ```bash
   [Service]
   Environment="KUBELET_EXTRA_ARGS=--cgroup-driver=none"
   ```

4. **Reload systemd and restart `kubelet`**:

   ```bash
   sudo systemctl daemon-reload
   sudo systemctl restart kubelet
   ```

### Option 2: Modify the Main `kubelet` Service File

If modifying the `kubelet` drop-in config is not possible, you can try editing the main `kubelet` service file.

1. **Edit the `kubelet.service` file**:

   The `kubelet` service file is typically located at `/usr/lib/systemd/system/kubelet.service`.

   Open it for editing:

   ```bash
   sudo nano /usr/lib/systemd/system/kubelet.service
   ```

2. **Modify the `ExecStart` line**:

   Find the line that starts with `ExecStart=` and add the `--cgroup-driver=none` option to it:

   ```bash
   ExecStart=/usr/bin/kubelet --cgroup-driver=none <other kubelet options>
   ```

3. **Reload systemd and restart `kubelet`**:

   ```bash
   sudo systemctl daemon-reload
   sudo systemctl restart kubelet
   ```

4. **Verify the changes**:

   Ensure the changes are applied by checking the `kubelet` status:

   ```bash
   systemctl status kubelet
   ```

Let me know if this resolves your issue or if you need further assistance!
