Sytème de monitoring d'infrastructure avec Docker Desktop : Prometheus + Grafana

 les commandes

Projet réalisé sous Linux mint Docker Desktop 


sudo apt install docker.io (installer Docker)

docker -v (pour vérifier)

créer le projet. 

mkdir monitoring-project (créer un dossier)

cd monitoring-project (ouvrir le dossier)


touch docker-compose.yml (créer le fichier)


code YAML - docker-compose.yml (à taper dans le fichier) 

Version : '3.8'

services: 
 Prometheus: 
 image: prom/prometheus
 container_name : prometheus
 volumes:
  - ./prmetheus.yml:/etc/prometheus/prometheus.yml
 ports: 
  - "9090:9090"
 grafana: 
 image: grafana/grafana
 container_name : grafana
 ports:
  - "3000:3000"
 depends_on : 
  -prometheus
 node-exporter : 
image prom/node-exporter
cntainer_name : node-exporter
ports:
  - "9100:9100"

  configurer Prometheus, Prometheus

global: 
scrape_interval : 5s
  - job_name : 'node'
  stactic_configs: 
- Targets: ['node-exporter:9100']

docker compose up -d

pour lancer l'application prometheus + grafana

docker compose ps (vérifier que les conteneurs tournent)

docker compose down(éteindre) 

 connecter Grafana à prometheus: http://prometheus: 9090

ne pas mettre localhost : 9090 ici 

Descend tout en bas - Clique save et text. 

importer le dashboard 
 
menue de gauche > Dashboard > new import 

ID du dashboard : 1960 et clique load

Data souces : selection Prometheus 

importe






  



