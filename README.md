# Ekstra oppgaver
Her er noen ekstra oppgaver dersom du er ferdig og har lyst å teste ut mere kubernetes.

## Rulle ut elk stak på aws
1. Åpne to kommando linje vindu
2. kubectl config use-context k8s.spasmodic.info
3. Åpne extra/elk.yml og se på hva som rulles ut
4. kubectl apply -f extra/elk.yml
5. kubectl get pods
6. kubectl port-forward kibana-db6ccc9c7-cvdgd 5000:5601
    - Bytt ut pod navnet, men det du får ut på punkt 5. 
