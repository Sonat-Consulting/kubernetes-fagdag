# kubernetes-fagdag
Kjøring av en enkelt pod, Oppsett av cats and dogs applikasjonen til fagdag. Har oppsett til minikube og azure


### Minikube oppgave 

## Start minikube og list servicer
```
minikube start
```

Se hvilke servicer som er eksponert
```
minikube service list
```

## Deploy backend
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

## Deploy frontend
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

## Sjekk at samme servicer finnes i minikube, og åpne frontenden i browser
```
minikube service list
minikube service frontend
```

