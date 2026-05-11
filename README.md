## Kubernetes-Pods-and-Labels-Practical

# What is a Pod?
A Pod is the smallest deployable unit in Kubernetes.
It can contain one or more containers.

## Create Simple Pod
# pod1.yml
apiVersion: v1
kind: Pod

metadata:
  name: pod1

spec:
  containers:
    - name: c00
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo hello-devops-engineer; sleep 5; done"]
      
 # Apply Pod
 kubectl apply -f pod1.yml
 
 # Check Pods
 kubectl get pods
 
 ## Kubernetes Labels
 Labels are key-value pairs used to organize Kubernetes objects.

# Example:
labels:
  department: dev
  
# Get Labels
kubectl get pods --show-labels

# Filter Pods using Labels
kubectl get pods -l department=dev

## Node Selector
Node Selector is used to schedule a pod on a specific node.

# nodeSelector:
  hardware: ssdi5
  
# Add Label to Node
kubectl label nodes minikube hardware=ssdi5

## Replication Controller

Replication Controller ensures the desired number of pods are always running.

# Benefits:
High Availability
Load Balancing
Auto Recovery

# Scale Pods
kubectl scale --replicas=5 rc/myreplica

## ReplicaSet

ReplicaSet is an advanced version of Replication Controller.

# Supports:
Match Labels
Match Expressions
Better Scaling

# Useful Commands 
kubectl get pods
kubectl get rs
kubectl get rc
kubectl describe pod pod1
kubectl delete pod pod1
kubectl get pods -o wide
