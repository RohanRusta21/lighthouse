

# To deploy lighthouse in minikube

Step 1 : Build docker image and push image to docker hub


```shell
docker build -t rohanmaharjan100/lighthouse .
docker image push rohanmaharjan100/lighthouse:latest
docker run -dit  rohanmaharjan100/lighthouse
docker exec f66bde16b4841d66310ea24b60bd5355163a4559554c59d33828881a2cc5e3e5 npx get --url https://facebook.com
```

Step 2: Start minikube with command :

```shell
minikube start
```

Step 3: Create deployment using deployment command :

```shell
kubectl apply -f Deployment.yaml
kubectl apply -f Service.yaml
```

check deployments using commands

```shell
kubectl get deployments
minikube dashboard

```

Step 4:Expose the pods running within the cluster to the outside world to be accessible:

```shell
kubectl expose deployment lighthouse-deployment --port=4000
kubectl port-forward service/lighthouse-deployment   4000:4000

```
