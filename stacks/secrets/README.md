# MongoDB with Docker Secrets stack on Docker Swarm

## Instructions

1. Create the required secrets for MongoDB
    ```
    printf $MONGO_ROOT_USERNAME | docker secret create mongo-root-username-v1 -
    printf $MONGO_ROOT_PASSWORD | docker secret create mongo-root-password-v1 -
    ```
2. Deploy the MongoDB with Docker Secrets stack
    ```
    docker stack deploy -c docker-compose.yml mongo-secrets
    ```
3. Verify that MongoDB is running alright by signing into its shell
    ```
    docker exec -ti \
    $(docker ps -q --filter=label=com.docker.stack.namespace=mongo-secrets) \
    mongo -u $MONGO_ROOT_USERNAME -p $MONGO_ROOT_PASSWORD --authenticationDatabase admin
    ```
