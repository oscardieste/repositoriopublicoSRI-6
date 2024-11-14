# repositoriopublicoSRI-6
Configuración cliente + servidor DNS

### 1. Inspección de la red en Docker
oscar@oscar-VirtualBox:~/Docker$ docker network inspect oscar_bind_network
[
   {
   "Name": "bind9_subnet",
        "Id": "ef5c911f15e82b5a9b59c0d1b8bc9fc49746ab040ae542b8f79b1e12d2312e0e",
        "Created": "2024-10-25T17:50:55.279860915+02:00",
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
                    },
        "ConfigOnly": false,
        "Containers": {
            "b9136bcf74cb1b91a23b8c9c8a3fdb68c0a30d3e2d1c5e5ad18e7048c812a2ea": {
                "Name": "dns_client",
                "EndpointID": "27fcbe432d3f47592e4f9483b0ec8bb2f032fc00e27c3a3c4e648a54040b9dd7",
                "MacAddress": "02:42:c0:a8:0a:03",
                "IPv4Address": "192.168.10.3/24",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
        }
]
