# MongoDB Replica Set stack on Docker Swarm

## Instructions

1. Create the required secrets for MongoDB
    ```
    printf $MONGO_ROOT_USERNAME | docker secret create mongo-root-username-v1 -
    printf $MONGO_ROOT_PASSWORD | docker secret create mongo-root-password-v1 -
    openssl rand -base64 756 | docker secret create mongo-key-v1 -
    ```
2. Deploy the MongoDB Replica Set stack
    ```
    docker stack deploy -c docker-compose.yml mongo-replica-set
    ```
3. Sign into the MongoDB shell and create the Replica Set
    ```
    docker exec -ti \
    $(docker ps -q -n 1 --filter=label=com.docker.swarm.service.name=mongo-replica-set_mongo-00) \
    mongo -u $MONGO_ROOT_USERNAME -p $MONGO_ROOT_PASSWORD --authenticationDatabase admin

    rs.initiate({
      _id: "sample-replica-set",
      members: [
        {_id: 0, host: "mongo-00:27017"},
        {_id: 1, host: "mongo-01:27017"},
        {_id: 2, host: "mongo-02:27017", arbiterOnly: true},
      ]
    })
    ```
