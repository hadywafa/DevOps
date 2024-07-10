# Secrets and ConfigMaps in Kubernetes

**Secrets** and **ConfigMaps** are Kubernetes resources used to store configuration data and sensitive information such as passwords, OAuth tokens, SSH keys, and configuration files.

## Secrets

**Secrets** are used to store and manage sensitive information securely. They can be stored as key-value pairs or files and are encoded in base64 format.

### Example of a Secret

#### Create a Secret YAML (Key-Value Pair)

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  username: YWRtaW4=  # base64 encoded value of "admin"
  password: MWYyZDFlMmU2N2Rm  # base64 encoded value of "1f2d1e2e67df"
```

#### Create a Secret from a File

To create a Secret from a file, use the following command:

```sh
kubectl create secret generic my-secret --from-file=path/to/your/file
```

This will generate a YAML file similar to this:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  my-file: <base64 encoded file content>
```

#### Use the Secret in a Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secret-pod
spec:
  containers:
  - name: mycontainer
    image: nginx
    env:
    - name: USERNAME
      valueFrom:
        secretKeyRef:
          name: my-secret
          key: username
    - name: PASSWORD
      valueFrom:
        secretKeyRef:
          name: my-secret
          key: password
    volumeMounts:
    - name: secret-volume
      mountPath: /etc/secret-files
      readOnly: true
  volumes:
  - name: secret-volume
    secret:
      secretName: my-secret
```

## ConfigMaps

**ConfigMaps** are used to store non-confidential configuration data in key-value pairs or as files.

### Example of a ConfigMap

#### Create a ConfigMap YAML (Key-Value Pair)

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
data:
  configKey1: configValue1
  configKey2: configValue2
```

#### Create a ConfigMap from a File

To create a ConfigMap from a file, use the following command:

```sh
kubectl create configmap my-config --from-file=path/to/your/file
```

This will generate a YAML file similar to this:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
data:
  my-file: |
    file content here
```

#### Use the ConfigMap in a Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: configmap-pod
spec:
  containers:
  - name: mycontainer
    image: nginx
    env:
    - name: CONFIG_KEY1
      valueFrom:
        configMapKeyRef:
          name: my-config
          key: configKey1
    - name: CONFIG_KEY2
      valueFrom:
        configMapKeyRef:
          name: my-config
          key: configKey2
    volumeMounts:
    - name: config-volume
      mountPath: /etc/config-files
      readOnly: true
  volumes:
  - name: config-volume
    configMap:
      name: my-config
```

## Summary

- **Secrets**: Used for storing sensitive data, can be encoded in base64 and include key-value pairs or files.
  - Example Key-Value Pair: `kubectl create secret generic my-secret --from-literal=username=admin --from-literal=password=1f2d1e2e67df`
  - Example File: `kubectl create secret generic my-secret --from-file=path/to/your/file`

- **ConfigMaps**: Used for storing configuration data, can include key-value pairs or files.
  - Example Key-Value Pair: `kubectl create configmap my-config --from-literal=configKey1=configValue1 --from-literal=configKey2=configValue2`
  - Example File: `kubectl create configmap my-config --from-file=path/to/your/file`

- **Usage**: Both can be used to inject data into pods via environment variables, volume mounts, or command-line arguments, ensuring applications have the necessary configurations and sensitive data securely and efficiently.
