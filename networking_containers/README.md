## Steps for multi-host overlay network
> Paraphrased from [Networking with overlay networks documentation](https://docs.docker.com/network/network-tutorial-overlay/#:~:text=Create%20the%20user%2Ddefined%20overlay%20network.&text=Start%20a%20service%20using%20the,8080%20on%20the%20Docker%20host.&text=Run%20docker%20network%20inspect%20my,the%20service%20and%20the%20network.))

1. Initialize Docker swarm on primary host machine. Note the token output; it is needed for other hosts to join the swarm.
```
docker swarm init
```
2. Create attachable overlay network on primary host machine
```
docker network create --driver=overlay --attachable my-overlay-net
```
3. Join Docker swarm on secondary host machine
```
docker swarm join --token <TOKEN>
```
4. Bring up containers on the hosts so they attach to the overlay as an external network
> e.g. For docker compose, add the following lines to the compose file:
```
  networks:
    default:
      name: "my-overlay-net"
      external: true
```
