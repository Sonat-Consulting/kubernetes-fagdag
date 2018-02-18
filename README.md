# Ekstra oppgaver
Her er noen ekstra oppgaver dersom du er ferdig og har lyst å teste ut mere kubernetes.

## Rulle ut elk stak på aws
1. Åpne to kommando linje vindu
2. kubectl config use-context k8s.spasmodic.info
3. Åpne extra/elk.yml og se på hva som rulles ut
4. Legg inn navnet på namespacet ditt i alle steder merket med: [TODO: Fyll inn namespace navnet ditt her] (fjern klammer)
  - Skal se noenlunde slik ut: "elasticsearch-0.elasticsearch.john.svc.cluster.local,elasticsearch-1.elasticsearch.john.svc.cluster.local,elasticsearch-2.elasticsearch.john.svc.cluster.local"
5. kubectl apply -f extra/elk.yml
6. kubectl get pods
7. kubectl exec kibana-db6ccc9c7-4mkjr curl http://elasticsearch:9200/_cluster/health?pretty
  - Her skal "number_of_nodes" være "3"
  - "status" skal være "green"
  - Dersom dette ikke stemmer må du sjekke at du har satt opp alt rett i punkt nr. 4
8. kubectl port-forward kibana-db6ccc9c7-cvdgd 5000:5601
    - Bytt ut pod navnet, men det du får ut på punkt 5. 
