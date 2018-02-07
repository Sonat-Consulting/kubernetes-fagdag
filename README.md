# kubernetes-fagdag
Kjøring av en enkelt pod, Oppsett av cats and dogs applikasjonen til fagdag. Har oppsett til minikube og azure


## Minikube
```
  kubectl create namespace "unikt_navn"
  kubectl run cheat --namespace="unikt_navn" --port=80 coderpews/kubernetes-cheat:0.1
  kubectl config set-context $(kubectl config current-context) --namespace=unikt_navn
```


## Kjøre cheatsheet på kubernetes
kubectl run cheat --port=80 --namespace=ditt-namespace --image=coderpews/kubernetes-cheat:0.2

## Bygge og kjøre cheatsheet container lokalt
docker build -t cheat .
docker run -d --name cheat -p 80:80 cheat
