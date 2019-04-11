# MongoDB on external network stack on Docker Swarm

## Instructions

1. Create an attachable overlay network
    ```
    docker network create --attachable --driver overlay mongo-external network
    ```
2. Deploy the MongoDB external network stack
    ```
    docker stack deploy -c docker-compose.yml mongo-external network
    ```
3. Verify that MongoDB is running alright by signing into its shell
    ```
    docker exec -ti $(docker ps -q -n 1 --filter=label=com.docker.stack.namespace=mongo-external network) mongo
    ```
