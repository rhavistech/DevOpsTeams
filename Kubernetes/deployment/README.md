# Deployment

1. Resource Management
    - Resource limit
    ```
    spec:
      containers:
        - name: joaolobo-dev
          image: joaolgn/joaolobo
          ports:
          - containerPort: 8888
          resources:
            requests:
              memory: "10Mi"
              cpu: "100m"
    ```
    - Liveness probes
    ```
    livenessProbe:
      httpGet:
        path: /healthz
        port: 8888
      initialDelaySeconds: 3
      periodSeconds: 3
    ```
      - Another kind of probes tcpSocket
        ```
        livenessProbe:
          tcpSocket:
            port: 8888
        ```
      - exec
        ```
        livenessProbe:
          exec:
            command:
            -  cat
            -  /tmp/healthy
        ```
    - Readiness probes
    ```
    readinessProbe:
      httpGet:
        path: /healthz
        port: 8888
      initialDelaySeconds: 3
      periodSeconds: 3
    ```
2. PodDisruptionBudget
  - minAvailable

  ```
  apiVersion: policy/v1
  kind: PodDisruptionBudget
  metadata:
    name: demo-pdb
  spec:
    minAvailable: 3
    selector:
      matchLabels:
        app: joaolobo-dev
  ```
  - maxUnavailable
  ```
  apiVersion: policy/v1
  kind: PodDisruptionBudget
  metadata:
    name: demo-pdb
  spec:
    maxUnavailable: 10%
    selector:
      matchLabels:
        app: joaolobo-dev
  ```
  3. Vertical Pod Autoscaler
    It helps to discover the ideal values for requesting resources.

  4. Annotations
    Specific owner
  
  5. Diff

    kubectl diff -f deployment.yaml