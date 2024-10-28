# CKAD Exam Notes

## Readiness probe and Liveness probe

Please understand the different between these

1. initialDelaySeconds: 15
1. periodSeconds: 20
1. failureThreshold: 3

## Rote user id is `1`

```txt
CKAD Mock Exam 1
---------------
q10
---
Update pod app-sec-kff3345 to run as Root user and with the SYS_TIME capability.
--------------
apiVersion: v1
kind: Pod
metadata:
  name: security-context-demo
spec:
  securityContext:
    runAsUser: 1
  containers:
  - name: sec-ctx-demo
    image: registry.k8s.io/e2e-test-images/agnhost:2.45
    command: [ "sh", "-c", "sleep 1h" ]
    securityContext:
      capabilities:
        add: ["SYS_TIME"]
```

## What different between taint/toleration and nodeAffinity

## Please understand the resources units such as memory and cpu

## Any strange command run it using `sh -c [COMMAND]`

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: whalesay
spec:
  completions: 10
  backoffLimit: 6
  template:
    metadata:
      creationTimestamp: null
    spec:
      containers:
        - command:
            - sh
            - -c
            - "cowsay I am going to ace CKAD!"
          image: docker/whalesay
          name: whalesay
      restartPolicy: Never
```
