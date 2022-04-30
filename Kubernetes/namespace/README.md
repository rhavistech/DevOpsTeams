# Namespace

1. Resource Quotas
  ```
  apiVersion: v1
  kind: ResourceQuota
  metadata:
    name: joaolobo-resourcequota
    #namespace:
  spec:
    hard:
      pods: "100"
  ```
 
 2. Limit Range
  ```
  apiVersion: v1
  kind: LimitRange
  metadata:
    name: joaolobo-limitrange
    namespace: demo
  spec:
    limits:
    - default:
        cpu: "500m"
        memory: "256Mi"
      defaultRequest:
        cpu: "200m"
        memory: 128Mi"
      type: COntainer
  ```
