## install jest
https://dev.to/ivadyhabimana/setup-jest-and-react-testing-library-in-a-react-project-a-step-by-step-guide-1mf0

## Prerequisites
You must install docker and k8s in local
1. Install docker
   > https://docs.docker.com/engine/install/

2. Install k8s
   > https://kubernetes.io/docs/setup/

3. Install ingress
   > https://kubernetes.io/docs/concepts/services-networking/ingress/
   > https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

## How to run

### Local
1. Build docker image: 
   > ./scripts/build-image.sh

2. Deploy to local cluster 
   > kubectl apply -f k8s/local

3. Enable Ingress
   minikube addons enable ingress

4. Forwarding port to localhost:8080 
   > kubectl port-forward service/aws-app-service 8080:80
   > minikube service aws-app-service --url

### AWS
For AWS CICD pipeline with CircleCI we will need setup infrastructure first:
1. Create network infrastructure
   > chmod +x ./scripts/deploy-network.sh
   > ./scripts/deploy-network.sh create

2. Create cluster infrastructure (EKS)
   > chmod +x ./scripts/deploy-cluster.sh
   > ./scripts/deploy-cluster.sh create

3. Add EKS cluster to prod kube config
   > aws eks update-kubeconfig --region us-east-1 --name aws-devops-capstone-cluster

4. Switch prod kube context to aws eks cluster
   > kubectl config get-contexts
   > kubectl config use-context $$CONTEXT_NAME

5. Build docker image:
   > ./scripts/build-image.sh

6. Enable Ingress
   minikube addons enable ingress

7. Deploy to prod cluster
   > kubectl apply -f k8s/prod

8. Get URL
   > kubectl get service/nginx-service-loadbalancer |  awk {'print $1" " $2 " " $4 " " $5'} | column -t

## Project preview

You can see my project quick view [here](./docs/PROJECT_QUICKVIEW.md)
