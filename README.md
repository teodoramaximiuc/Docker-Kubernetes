# Docker + Kubernetes (Rancher Desktop, containerd)

## Build & run local (nerdctl, namespace k8s.io)
nerdctl -n k8s.io build -t hello-docker:1.0 .
nerdctl -n k8s.io run --rm -p 5000:5000 hello-docker:1.0
# test: http://localhost:5000

## Deploy pe Kubernetes
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl get pods -w
kubectl get svc

## Test prin port-forward
kubectl port-forward service/hello-service 8080:80
# test: http://localhost:8080

## Debug rapid
kubectl logs deploy/hello-deployment
kubectl describe deploy/hello-deployment