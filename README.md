![logo zero.io](images/zerologo.svg)
# Subzero-Alphaville Node Tutorial
<hr>
#### 5 minutes.
This will show you how to run a simple node and get rewards for helong the network.
Advanced users you can follow the _VALIDATOR_ setup tutorial: [Validator Turorial](README_VALIDATOR.md)
<br/>
<hr>
## Goal:
At the end of this tutorial you will have a node online and synced to the network.
here will be snapshots taken regularly to calculate rewards


## 🛠️ Setup:
you will need one of the following:

### Azure
*oneclick azure*
continue at step 2

### DigitalOcean
*digitalocean vm'
continue at step 3

### laptop/other vm

#### docker & docker-compose
##### easy orchestraton of linux containers

#### Linux
<a href="https://docs.docker.com/engine/install/ubuntu/">Install Docker Engine</a>
<br/>
<a href ="https://docs.docker.com/compose/install/">Install Docker Compose</a>
<br/>
<a href="https://docs.docker.com/engine/install/linux-postinstall/">Post-installation steps for Linux</a>
<hr>
Windows:
<a href="https://hub.docker.com/editions/community/docker-ce-desktop-windows"> 
Docker Desktop for Windows</a>


### git
<h3>Linux</h3>
<a href="https://git-scm.com/download/linux"></a>
<hr>
<h3>OSX</h3>
<a href="https://git-scm.com/download/mac"></a>
<hr>
<h3>Windows:</h3>
<a href="https://git-scm.com/download/win"> 
Git SCM for Windows</a>


continue at step 1

<br/>

## 2: Naming your node:

There is a file named `.env` in the repository the content is quite manageable
This is the name that will show up in the telemetry

```
NAME=ExampleNode
```

![naming the node](images/naming.png)

## 2 - Testing the Node:

We can now easily start the node with `docker-compose up`.
Once we verified this works we can actually start the node for long term production:

![testing the node](images/testing.png)

## 3 - Running the Node in production:

With `docker-compose up -d` the process runs in the background.
We can always open the logs with `docker-compose logs -f`
`docker-compose down` to stop the container

![running the node](images/running.png)

## 4 - Updating the Node:
```
docker-compose down
docker-compose pull
docker-comnpose up -d
```

![naming the node](images/updating.png)
