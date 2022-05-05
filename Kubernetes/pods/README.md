# PODS

| Resume | Command | flags | 
|----------------------------------------------------------|----------------------------------------------|--------------|
| Create a Pod with image nginx to test                    | `kubectl run nginx-pod --image=nginx:latest` |              |
| Show the pods                                            | `kubectl get pods`                           |              |
| Show the pods in realtime to using the flag --wath or -w | `kubectl get pods --watch`                   | --watch / -w |
| Show all the pods in cluster to using the flag -A        | `kubectl get pods -A`                        | -A           |
| Describe all the pods                                    | `kubectl describe pod nginx-pod `            |              |