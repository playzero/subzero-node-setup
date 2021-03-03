# Subzero-Alphaville Testnet Node

#### 5 minutes.

## This will show you how to run a node and get rewards.
## If you are serious / want to become an advanced user you can follow the VALIDATOR tutorial instead

<br/>

---

## 0 The Super Easy way:
### azure
*oneclick azure*

### digitalcoean
*digitalocean vm'

### laptop/other
all you need is docker-comnpose and git


<br/>

## Naming your node:

There is a file named `.env` in the repository the content is quite manageable
This is the name that will show up in the telemetry

```
NAME=ExampleNode
```

## Testing the Node:

We can now easily start the node with `docker-compose up`.
Once we verified this works we can actually start the node for long term production:

## Starting the Node öong-ter,:

With `docker-compose up -d` the process runs in the background.
 
We can always open the logs with `docker-compose logs -f`

`docker-compose down` to stop the container

## Updating the Node:
```
docker-compose down
docker-compose pull
docker-comnpose up -d
```
