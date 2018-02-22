# Ekstra oppgaver
Her er noen ekstra oppgaver dersom du er ferdig og har lyst å teste ut mere kubernetes.

## Rulle ut elk stak på aws
1. Åpne to kommando linje vindu
2. kubectl config use-context k8s.spasmodic.info
3. Åpne extra/elk.yml og se på hva som rulles ut
4. Legg inn navnet på namespacet ditt i alle steder merket med: [TODO: Fyll inn namespace navnet ditt her] (fjern klammer)
   - Skal se noenlunde slik ut: "elasticsearch-0.elasticsearch.*john*.svc.cluster.local,elasticsearch-1.elasticsearch.*john*.svc.cluster.local,elasticsearch-2.elasticsearch.*john*.svc.cluster.local"
5. kubectl apply -f extra/elk.yml
6. kubectl get pods
7. kubectl exec kibana-db6ccc9c7-4mkjr curl http://elasticsearch:9200/_cluster/health?pretty
    - Her skal "number_of_nodes" være "3"
    - "status" skal være "green"
    - Dersom dette ikke stemmer må du sjekke at du har satt opp alt rett i punkt nr. 4
8. kubectl port-forward kibana-db6ccc9c7-cvdgd 5000:5601
      - Bytt ut pod navnet, men det du får ut på punkt 5. 


## Sjekke DNS
Alle underpunkter til nummerlisten, gjøres i kommandolinjen på ubuntu containeren du spinner opp.

1. Kjøre opp en ubuntu container og logge på denne
    - kubectl run -it cmd --image=sonatconsulting/debugger
2. Liste ut dns for elasticsearch 
    - nslookup elasticsearch
3. Vise helse på cluster
    - curl elasticsearch:9200/_cluster/health?pretty
    - number_of_nodes skal være "3" her
    - status skal være "green"

## Importere data til elastic
*Fortsatt innlogget i containeren du nettopp laget*
  1. cd /data
  2. ls
      - Her vil du se en shakespear.json fil. Denne inneholder mye data som kan importeres til clustered du nettopp satt opp
  3. curl -H 'Content-Type: application/x-ndjson' -XPOST 'elasticsearch:9200/shakespeare/doc/_bulk?pretty' --data-binary @shakespeare.json
      - Dette tar litt tid, så vær vennlig å vente her
  4. curl elasticsearch:9200/_cat/indices?v
      - Lister ut alle indexer
  5. Åpne kibana i nettleseren din
      - kubectl get pods
      - kubectl port-forward kibana-xxxx-xxx 5000:5601
      - Lek deg i kibana

Gå ut av containeren ved å skrive "exit". 

## Rydding
kubectl delete deployment cmd
