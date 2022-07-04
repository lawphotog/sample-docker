# docker-swarm-test

# Set up a Docker registry

docker service create --name registry --publish published=5000,target=5000 registry:2

docker service ls

curl http://localhost:5000/v2/

# Push the generated image to the registry

docker-compose push


# Deploy the stack to the swarm

docker stack deploy --compose-file docker-compose.yml stackdemo

docker stack services stackdemo


# Clean up

docker stack rm stackdemo

docker service rm registry

docker swarm leave --force


ref:

https://docs.docker.com/engine/swarm/stack-deploy/

