# Stateful Set Deployment (K8s)

- stateless app vs stateful app
    ![alt text](../images/stateless-vs-stateful.png)

- deployment vs statefulset
    ![alt text](../images/deployment-vs-statefulset.png)

- pod entity
    ![alt text](../images/pod-entity.png)

- scaling database apps
    ![alt text](../images/scaling-database-1.png)
    ![alt text](../images/scaling-database-2.png)
  - statefulset replicas don't use the same physical storage!
  - statefulset replicas use the same persistent volume claim (PVC) but different persistent volumes (PV)
  - statefulset replicas are created in order, one by one
  - statefulset replicas are deleted in reverse order, one by one
  - statefulset replicas are not created until the previous one is running
  - statefulset replicas are not deleted until the next one is terminated
  - To ensure that replicas stay up to date, they need to be aware of any changes.

- each pod gets its own dns endpoint from service
    ![alt text](../images/statefulset-service-1.png)
    ![alt text](../images/statefulset-service-2.png)
