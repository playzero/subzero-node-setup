# Subzero-Alphaville Testnet Node
#### 5 minutes.
This will show you how to run a simple node and get rewards for helong the network.
Advanced users you can follow the _VALIDATOR_ setup tutorial: [Validator Turorial](README_VALIDATOR.md)

<br/>

---

## Goal:
At the end of this tutorial you will have a node online and synced to the network.
here will be snapshots taken regularly to calculate rewards


## 🛠️ Setup:
you will need one of the following:

### azure
*oneclick azure*
continue at step 1

### digitalcoean
*digitalocean vm'
continue at step 1

### laptop/other vm
all you need is 

<details><summary>docker and docker-compose | easy orchestraton of linux containers</summary>
<h3>Linux</h3>
<a href="https://docs.docker.com/engine/install/ubuntu/">Install Docker Engine</a>
<br/>
<a href ="https://docs.docker.com/compose/install/">Install Docker Compose</a>
<br/>
<a href="https://docs.docker.com/engine/install/linux-postinstall/">Post-installation steps for Linux</a>
<hr>
<h3>Windows:</h3>
<a href="https://hub.docker.com/editions/community/docker-ce-desktop-windows"> 
Docker Desktop for Windows</a>
</details>

<details><summary>GIT - to clone repositories</summary>
<h3>Linux&OSX</h3>
<a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git"></a>
<hr>
<h3>Windows:</h3>
<a href="https://git-scm.com/"> 
Git SCM for Windows</a>
</details>

continue at step 1

<br/>

## 2: Naming your node:

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
