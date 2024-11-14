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

                  }
            ]
            },
        "Internal": false,
        "Attachable": true
    }
]


