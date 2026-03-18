# Nginx Traffic Manager

Une alternative open-source à F5 BIG-IP, construite sur Nginx et livrée sous forme d'une image Docker unique.

Gérez le load balancing, le routage du trafic, les certificats SSL et le monitoring via une interface web moderne.

## Fonctionnalités principales

- **Virtual Servers** - Créez et gérez les server blocks Nginx via une interface visuelle
- **Pools & Members** - Gestion des serveurs backend avec suivi de l'état de santé
- **Load Balancing** - Plusieurs algorithmes : round-robin, least connections, IP hash, weighted
- **Health Monitors** - Health checks HTTP/TCP/ICMP automatisés avec seuils configurables
- **Gestion SSL/TLS** - Gestion des certificats avec intégration Let's Encrypt
- **Interfaces réseau** - Support multi-interfaces configurable depuis l'interface web
- **Monitoring & Analytics** - Tableau de bord temps réel avec métriques et logs

## Démarrage rapide

```bash
docker run -d \
  --name nginx-traffic-manager \
  -p 81:81 \
  -p 80:80 \
  -p 443:443 \
  tchevalleraud/nginx-traffic-manager:latest
```

Ouvrez ensuite [http://localhost:81](http://localhost:81) pour accéder à l'interface de gestion.
