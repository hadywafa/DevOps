# RBAC (Role-Based Access Control) in Kubernetes

Role-Based Access Control (RBAC) is a method of regulating access to resources based on the roles of individual users within an organization. In Kubernetes, RBAC allows you to control who can access what within your cluster, providing a way to manage permissions and enforce security policies.

## Key Concepts

1. **Role**: Defines a set of permissions (rules) within a namespace. It grants access to specific resources (like pods, services) and actions (like get, list, create).

2. **ClusterRole**: Similar to Role, but applicable cluster-wide across all namespaces.

3. **RoleBinding**: Associates a Role with a user, group, or service account within a namespace. It grants the permissions defined in the Role to the subjects specified in the binding.

4. **ClusterRoleBinding**: Associates a ClusterRole with a user, group, or service account cluster-wide.

## RBAC Resources

1. **Role**:

   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: Role
   metadata:
     namespace: default
     name: pod-reader
   rules:
   - apiGroups: [""]
     resources: ["pods"]
     verbs: ["get", "watch", "list"]
   ```

2. **ClusterRole**:

   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: ClusterRole
   metadata:
     name: pod-reader
   rules:
   - apiGroups: [""]
     resources: ["pods"]
     verbs: ["get", "watch", "list"]
   ```

3. **RoleBinding**:

   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: RoleBinding
   metadata:
     name: read-pods
     namespace: default
   subjects:
   - kind: User
     name: "jane"
     apiGroup: rbac.authorization.k8s.io
   roleRef:
     kind: Role
     name: pod-reader
     apiGroup: rbac.authorization.k8s.io
   ```

4. **ClusterRoleBinding**:

   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: ClusterRoleBinding
   metadata:
     name: read-pods-global
   subjects:
   - kind: User
     name: "jane"
     apiGroup: rbac.authorization.k8s.io
   roleRef:
     kind: ClusterRole
     name: pod-reader
     apiGroup: rbac.authorization.k8s.io
   ```

## Steps to Implement RBAC

1. **Create a Role**:
   Define the permissions (rules) within a specific namespace.

2. **Create a RoleBinding**:
   Bind the Role to a user, group, or service account within the same namespace.

3. **Create a ClusterRole**:
   Define the permissions (rules) that apply across all namespaces.

4. **Create a ClusterRoleBinding**:
   Bind the ClusterRole to a user, group, or service account cluster-wide.

## Example Use Case

1. **Create a Role to Allow Pod Reading**:

   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: Role
   metadata:
     namespace: default
     name: pod-reader
   rules:
   - apiGroups: [""]
     resources: ["pods"]
     verbs: ["get", "watch", "list"]
   ```

   Apply the Role:

   ```sh
   kubectl apply -f role.yaml
   ```

2. **Create a RoleBinding to Bind the Role to a User**:

   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: RoleBinding
   metadata:
     name: read-pods
     namespace: default
   subjects:
   - kind: User
     name: "jane"
     apiGroup: rbac.authorization.k8s.io
   roleRef:
     kind: Role
     name: pod-reader
     apiGroup: rbac.authorization.k8s.io
   ```

   Apply the RoleBinding:

   ```sh
   kubectl apply -f rolebinding.yaml
   ```

## Benefits of RBAC

- **Fine-Grained Access Control**: Allows precise control over who can do what within your cluster.
- **Separation of Duties**: Helps enforce the principle of least privilege by granting only necessary permissions.
- **Improved Security**: Reduces the risk of accidental or malicious actions by restricting access to critical resources.
- **Scalability**: Simplifies permission management in large clusters with many users and resources.

By leveraging RBAC in Kubernetes, you can effectively manage access to cluster resources, ensuring a secure and organized environment.
