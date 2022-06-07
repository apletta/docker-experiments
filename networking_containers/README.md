Steps for overlay network:
1. Initialize Docker swarm
2. Create attachable overlay network
```
docker network create --driver=overlay --attachable test-net
```
3. Bring up the containers so they attach to the overlay as an external network
