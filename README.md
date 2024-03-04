## Time based Workload Scaling

```bash
kubectl apply -f cronjob-scale-workload.yaml
```

## Implement K8S Operator
```bash
apiVersion: autoscaler.charolia.io/v1beta1
kind: AutoScaler
metadata:
  name: cron-scaled-workload
  namespace: default
spec:
  scaleTargetRef:
    name: nginx
    type: <deployment|statefulset|replicaset>
  triggers:
  - type: cron
    metadata:
      timezone: Europe/Berlin
      start: 30 * * * *
      end: 45 * * * *
      desiredReplicas: "10"
```

### **COMING SOON!**