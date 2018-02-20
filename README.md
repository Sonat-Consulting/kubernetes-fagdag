# kubernetes-fagdag
Kjøring av en enkelt pod, Oppsett av cats and dogs applikasjonen til fagdag. Har oppsett til minikube og azure


### Minikube oppgave 

##Start minikube og list servicer
```
minikube start
```

Se hvilke servicer som er eksponert
```
minikube service list
```

##Deploy backend
```
kubectl create -f backend.yml
```

Sjekk at deploy finnes
```
kubectl get deploy
```

Sjekk at pod finnes
```
kubectl get pod
```

##Deploy frontend
```
kubectl create -f frontend.yml
```

Sjekk at deploy finnes
```
kubectl get deploy
```

Sjekk at pod finnes
```
kubectl get pod
```

Sjekk at servicer er eksponert
```
kubectl get service
```

##Sjekk at samme servicer finnes i minikube, og åpne frontenden i browser
```
minikube service list
minikube service azure-vote-front
```


## Kjøre cheatsheet på kubernetes
kubectl run cheat --port=80 --namespace=ditt-namespace --image=sonatconsulting/kubernetes-cheat:0.5

## Bygge og kjøre cheatsheet container lokalt
docker build -t cheat .
docker run -d --name cheat -p 80:80 cheat

### Azure oppgave 1
Hente context fra azure-cli

```
az aks get-credentials -g fagdag -n chaos
kubectl get nodes
```

### Azure oppgave 2

Lage namespace. Sliter du med å finne namespace navn, kan du bruke denne tjenesten: https://mrsharpoblunto.github.io/foswig.js/

```
kubectl create namepsace "ditt-namespace-navn"

kubectl config set-context $(kubectl config current-context) --namespace=ditt-namespace-navn
	```

### Azure oppgave 3
Kjøre deployment via kommandolinje

```
kubectl run cheatsheet --image=sonatconsulting/kubernetes-cheat:0.1 --port=80
kubectl delete deployment
kubectl run cheatsheet --image=coderpews/kubernetes-cheat:0.1 --port=80
kubectl get pod
kubectl port-forward pod-name 5000:80
kubectl scale deployment/cheetsheet --replicas=2
kubectl set image deployment/cheatsheet cheatsheet=image=sonatconsulting/kubernetes-cheat:0.8
kubectl expose deployment cheetsheet --port=80 --type=LoadBalancer
kubectl get services


```


### Azure oppgave 4

Deploye applikasjonen

```
cd azure
kubectl apply -f deploy_azure.yml
```
