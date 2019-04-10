# MongoDB Replica Set for Docker Swarm

This repository demonstrates how to deploy a MongoDB Replica Set on Docker Swarm.

The code inside this repository was used as reference in the [Stateful applications on Docker Swarm](https://events.docker.com/events/details/docker-athens-presents-stateful-applications-on-docker-swarm/) meetup on Thursday 11 April 2019 of the Docker Athens User Group.

## Instructions

1. Choose the stack of your choice from the [`stacks/`](stacks/) directory
2. Deploy the MongoDB stack of your choice:
    ```
    docker stack deploy -c stacks/{stack_name}/docker-compose.yml {stack_name}
    ```

---

<center>Created by <a href="https://www.sourcelair.com/">SourceLair PC</a> in Athens.</center>


