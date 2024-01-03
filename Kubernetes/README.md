To View Current Namespace
```
kubectl config view | grep namespace
```

Switch to other namespace
```
kubectl config set-context --current --namespace=my-namespace
```
