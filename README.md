![logo zero.io](images/zero.jpg)
# zero.io

    Time: 5 min
    Difficulty: Moderately Easy
    Required: light terminal skills
    Goal: A Syncing Alphaville testnet-node

*Advanced Validator Turorial:* [Validator Turorial](README_VALIDATOR.md)

---

## 🛠️ 1 - Setup
### Heroku One-Click Setup:
[heroku-One-Click](https://herkou.com)

**continue at step 2**

---

### DigitalOcean:
[Docker-Droplet](https://marketplace.digitalocean.com/apps/docker)

**continue at step 2**

---

### Other:
##### First we need to install the tools needed:

**docker & docker-compose**

Linux
- [Docker Engine](https://docs.docker.com/engine/install/ubuntu/) & [docker-compose](https://docs.docker.com/compose/install/) & [postinstall](https://docs.docker.com/engine/install/linux-postinstall/)

Windows
- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

---

**git**
- [Linux](https://git-scm.com/download/linux) || [Mac](https://git-scm.com/download/mac) || [Windows](https://git-scm.com/download/win)

##### Now we clone the repository:
```git clone https://gitlab.com/zero.io/subzero_alphaville```

---

## 2 - Naming your node:

There is a file named `.env` in the repository the content is quite manageable
This is the name that will show up in the telemetry

```
NAME=ExampleNode
```

![naming the node](images/naming.png)

---

## 2 - Testing the Node:

We can now easily start the node with `docker-compose up`.
Once we verified this works we can actually start the node for long term production:

![testing the node](images/testing.png)

---

## 3 - Running the Node in production:

With `docker-compose up -d` the process runs in the background.
We can always open the logs with `docker-compose logs -f`
`docker-compose down` to stop the container

![running the node](images/running.png)

---

## 4 - Updating the Node:
```
docker-compose down
docker-compose pull
docker-comnpose up -d
```

![naming the node](images/updating.png)
