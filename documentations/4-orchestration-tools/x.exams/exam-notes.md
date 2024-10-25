# Exams Notes

## When Creating SVC and service port not specified then make it same as target port (pod port)

`When Creating SVC and service port not specified then make it same as target port (pod port)`

## Static Pod file must be in the specific node not controlPlane always

```md
Create a static pod on node01 called nginx-critical with image nginx and make sure that it is recreated/restarted automatically in case of a failure.

Use /etc/kubernetes/manifests as the Static Pod path for example.
```

```md
Solution
To create a static pod called nginx-critical by using below command:

kubectl run nginx-critical --image=nginx --dry-run=client -o yaml > static.yaml

Copy the contents of this file or use scp command to transfer this file from controlplane to node01 node.

root@controlplane:~# scp static.yaml node01:/root/

To know the IP Address of the node01 node:

root@controlplane:~# kubectl get nodes -o wide

# Perform SSH

root@controlplane:~# ssh node01
OR
root@controlplane:~# ssh <IP of node01>

On node01 node:

Check if static pod directory is present which is /etc/kubernetes/manifests, if it's not present then create it.

root@node01:~# mkdir -p /etc/kubernetes/manifests

Add that complete path to the staticPodPath field in the kubelet config.yaml file.

root@node01:~# vi /var/lib/kubelet/config.yaml

now, move/copy the static.yaml to path /etc/kubernetes/manifests/.

root@node01:~# cp /root/static.yaml /etc/kubernetes/manifests/

Go back to the controlplane node and check the status of static pod:

root@node01:~# exit
logout
root@controlplane:~# kubectl get pods
```

## Best way to get info from pod to external node is to use -- commands

```md
Create a nginx pod called nginx-resolver using image nginx, expose it internally with a service called nginx-resolver-service. Test that you are able to look up the service and pod names from within the cluster. Use the image: busybox:1.28 for dns lookup. Record results in /root/CKA/nginx.svc and /root/CKA/nginx.pod
```

```md
Solution
Use the command kubectl run and create a nginx pod and busybox pod. Resolve it, nginx service and its pod name from busybox pod.

To create a pod nginx-resolver and expose it internally:

kubectl run nginx-resolver --image=nginx
kubectl expose pod nginx-resolver --name=nginx-resolver-service --port=80 --target-port=80 --type=ClusterIP

To create a pod test-nslookup. Test that you are able to look up the service and pod names from within the cluster:

kubectl run test-nslookup --image=busybox:1.28 --rm -it --restart=Never -- nslookup nginx-resolver-service
kubectl run test-nslookup --image=busybox:1.28 --rm -it --restart=Never -- nslookup nginx-resolver-service > /root/CKA/nginx.svc

Get the IP of the nginx-resolver pod and replace the dots(.) with hyphon(-) which will be used below.

kubectl get pod nginx-resolver -o wide
kubectl run test-nslookup --image=busybox:1.28 --rm -it --restart=Never -- nslookup <P-O-D-I-P.default.pod> > /root/CKA/nginx.pod
```

## Take Care of How set env for containers `-_-`

```yaml
---
apiVersion: v1
kind: Pod
metadata:
  name: multi-pod
spec:
  containers:
    - image: nginx
      name: alpha
      env:
        - name: name
          value: alpha
    - image: busybox
      name: beta
      command: ["sleep", "4800"]
      env:
        - name: name
          value: beta
```

> Here is the record of env set by `name`:<you-env-name> , `value`:<your-env-value>

## How to test service account RBAC

```bash
kubectl auth can-i list pv --as=system:serviceaccount:default:pvviewer
```

## NetworkPolicy: Applied to All sources (Incoming traffic from all pods)?

```yaml
---
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: ingress-to-nptest
  namespace: default
spec:
  podSelector:
    matchLabels:
      run: np-test-1
  policyTypes:
    - Ingress
  ingress:
    - ports:
        - protocol: TCP
          port: 80
```

## Review Command Section under pod definition

you have problem of execution order for command parameters in k8s pod definition

## you need to focus which nodes to save your answers

`PUT YOU ANSWER IN CORRECT PLACE BITCH 🥴`

## VIP Flags

1. `--sort-by=.status.podIP`
1. `--no-header`
1. `k top node --context=cluster1 --no-headers | sort -nr -k4 | head -1`
1. `k top po -A --context=cluster1 --no-headers | sort -nr -k4 | head -1`

## Take you time reading the pod logs

1. `may problem in Memory`
   - Initializing buffer pool, size = 128.0M
     Killed

## to execute script inside po you can use

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: looper-cka16-arch
spec:
  containers:
    - name: busybox
      image: busybox
      command: ["/bin/sh", "-c", "while true; do echo hello; sleep 10;done"]
```

## use event for troubleshooting

```bash
kubectl get event --field-selector involvedObject.name=demo-pod-cka29-trb
```

```bash
kubectl get event --field-selector involvedObject.name=demo-pvc-cka29-trb
```

## Make sure the pvc is mounted to pv

![alt text](images/events-troubleshooting.png)
