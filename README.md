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

y nos dará: 

"Name": "oscar_bind_network",

"Id": "d3c1b71843a934b4bfc8398c047efb56784d4f9177d74d4b9f8090e4f45c8c1a",

        "Created": "2024-11-14T12:35:30.123456789+00:00",
        "Scope": "local",
        
        "Driver": "bridge",
        
        "EnableIPv6": false,
        
        "IPAM": {
        
            "Driver": "default",
            "Options": {},
            "Config": [
{
                    "Subnet": "192.168.10.0/24",
                    "IPRange": "192.168.10.0/28",
                    "Gateway": "192.168.10.1"
### 3. Archivo docker-compose.yml
Usamos docker-compose para crear y configurar el servidor BIND9 y un contenedor cliente en la red oscar_bind_network.

version: '3.8'

services:

  oscar_bind:
  
    container_name: oscar_bind
    
    image: ubuntu/bind9
    
    platform: linux/amd64
    
    ports:
      - "53:53/tcp"
      
      - "53:53/udp"
      
    networks:
    
      oscar_bind_network:
      
        ipv4_address: 192.168.10.2
        
    volumes:
    
      - ./bind_conf:/etc/bind
      
      - ./zone_data:/var/lib/bind

  dns_client:
  
    container_name: dns_client
    
    image: debian:latest
    
    platform: linux/amd64
    
    tty: true
    
    stdin_open: true
    
    dns:
      - 192.168.10.2
      
    networks:
    
      oscar_bind_network:
      
        ipv4_address: 192.168.10.3

networks:

  oscar_bind_network:
  
    external: true





