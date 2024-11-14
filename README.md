# repositoriopublicoSRI-6
Configuración cliente + servidor DNS

### 1. Inspección de la red en Docker
docker network create --driver bridge \
  --subnet=192.168.10.0/24 \
  --ip-range=192.168.10.0/28 \
  --gateway=192.168.10.1 \
  oscar_bind_network
### 2 Inspeccionamos la red
docker network inspect oscar_bind_network


