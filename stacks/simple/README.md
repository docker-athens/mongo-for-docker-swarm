# MongoDB simple stack on Docker Swarm

## Instructions

1. Deploy the MongoDB simple stack
    ```
    docker stack deploy -c docker-compose.yml mongo-simple
    ```
2. Verify that MongoDB is running alright by signing into its shell
    ```
    docker exec -ti $(docker ps -q --filter=label=com.docker.stack.namespace=mongo-simple) mongo
    ```
