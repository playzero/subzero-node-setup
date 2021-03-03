# Subzero-Alphaville Testnet Node

#### 5 minutes.

## This will show you how to run a node and get rewards.
## If you are serious / want to become an advanced user you can follow the VALIDATOR tutorial insteas [](url)

<br/>

---

## 0 Setup:
you will need one of the following:

### azure
*oneclick azure*
continue at step 1

### digitalcoean
*digitalocean vm'
continue at step 1

### laptop/other vm
all you need is docker-comnpose and git
continrue at step 1

<br/>

## 1: Naming your node:

There is a file named `.env` in the repository the content is quite manageable
This is the name that will show up in the telemetry

```
NAME=ExampleNode
```

![naming the node](images/naming.png)

## 2: Testing the Node:

We can now easily start the node with `docker-compose up`.
Once we verified this works we can actually start the node for long term production:

![testing the node](images/testing.png)

## 3: Running the Node in production:

With `docker-compose up -d` the process runs in the background.
We can always open the logs with `docker-compose logs -f`
`docker-compose down` to stop the container

![running the node](images/running.png)

## Updating the Node:
```
docker-compose down
docker-compose pull
docker-comnpose up -d
```

![naming the node](images/updating.png)
