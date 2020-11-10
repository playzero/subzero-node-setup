# Subzero Validator

#### Should take around 15 Minutes. 😁

<br/>

---

## What is needed to create a node with this repository:

<br/>

Tools: 🛠️

<details><summary>docker and docker-compose | Docker is so to say our runtime in which the node and the webserver are executed.</summary>
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

<br/>

Other: ⚗️

<details><summary>Subdomain | In short a reference from a dns to our server(ip)</summary>
<br/>
There are several ways to get a subdomain. I will show you 2 ways

<br/>

- You can buy a domain from a provider like https://www.namecheap.com/
- There are also free providers that quickly provide you with a subdomain, for example https://www.noip.com/remote-access

<h3>Namecheap</h3>

1.  Buy a domain you like.
2.  DNS Config -> Here is a nice tutorial for your settings (Subdomain that points to an IP address
    ): https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain

<h3>Noip</h3>

1.  Create an account
2.  Create DNS HOST (A) Record -> Here is a nice tutorial: https://www.noip.com/support/knowledgebase/configure-ip-hostname/
</details>
<br/>

---

## Create the keys Babe and Gran for the node

Preparation:
- (generate an address and save the seed phrase for example with: https://polkadot.js.org/extension/)
- For the key type babe we use the public key in SR25519 format.
- For the key type gran we use the public key in ED25519 format.
- Suri | Most people probably know it as mnemonic (Mostly a set of 12 words)

⚠️ If you haven't noticed, the format is different for gran and babe (SR, ED) ⚠️

<br/>

## The Short Way - use Our Discord Faucet Chan (and get some PLAY tokens while your at it)

ZERO-FAUCET
https://discord.gg/d94Hrz4udy

To get the SR25519 and ED25519:

Get subkey infromation for Address
!fc subkey <Address>

Example
```!fc subkey 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY```

Also, be sure to Get tokens to play and test
!fc get <Address>

<details><summary>The Long Way - Compile Subkey</summary>
## How do we get the SR25519 and ED25519 public key from our suri:

> As an example I use `detect silk hidden item media foster brief maple proof belt absurd genius` as suri

We can get more detailed information about our suri with the <a href="https://substrate.dev/docs/en/knowledgebase/integrate/subkey">subkey tool:</a>

```
curl https://getsubstrate.io -sSf | bash -s -- --fast
source ~/.cargo/env
cargo install --force subkey --git https://github.com/paritytech/substrate --version 2.0.0
```

### Keys

SR25519(babe):

> subkey inspect --scheme sr25519 "detect silk hidden item media foster brief maple proof belt absurd genius"

```
Secret phrase `detect silk hidden item media foster brief maple proof belt absurd genius` is account:
  Secret seed:      0x1aed0fdf143ae27af37f3d0e7025733756a2c45a62c887216871074a2efcc162
  Public key (hex): 0x3ee10e31a28caefe0fb45c33aa5f79d83758a2006abcd6bf387b21025f7ad720
  Account ID:       0x3ee10e31a28caefe0fb45c33aa5f79d83758a2006abcd6bf387b21025f7ad720
  SS58 Address:     5DV9gUdX8ijEwvmdnxs2EPLGTfCJv88MvUbZ1Y8sSaXyktHA
```

ED25519(gran):

> subkey inspect --scheme ed25519 "detect silk hidden item media foster brief maple proof belt absurd genius"

```
Secret phrase `detect silk hidden item media foster brief maple proof belt absurd genius` is account:
  Secret seed:      0x1aed0fdf143ae27af37f3d0e7025733756a2c45a62c887216871074a2efcc162
  Public key (hex): 0x216c3621cfe4f2a0877d6090a8c9aa8e5efc28fe830dfcbe02e289912cb9e228
  Account ID:       0x216c3621cfe4f2a0877d6090a8c9aa8e5efc28fe830dfcbe02e289912cb9e228
  SS58 Address:     5CpXam2wJnDQPeatRAFBr3Q45EzRJgamHVxSWguBsnfswvTG
```
</details>

---

## Ok now that we have our public keys we need to create 2 files in the folder ./keys

---

#### The first file is for babe:

<br/>

Create a file with the name `62616265` concatenated with your public key in sr25519 format you acquired in the previous step (babe)

> My file is named 626162653ee10e31a28caefe0fb45c33aa5f79d83758a2006abcd6bf387b21025f7ad720

Now all that remains is to write our suri in the file.

> The content of my file is `"detect silk hidden item media foster brief maple proof belt absurd genius"` ⚠️There must be a " before and after your suri ⚠️

---

#### The second file is for gran:

<br/>

Create a file with the name `6772616e` concatenated with your public key in ed25519 format you acquired in the previous step (gran)

> My file is named 6772616e216c3621cfe4f2a0877d6090a8c9aa8e5efc28fe830dfcbe02e289912cb9e228

Now all that remains is to write our suri in the file.

> The content of my file is `"detect silk hidden item media foster brief maple proof belt absurd genius"` ⚠️There must be a " before and after your suri ⚠️

---

The folder `./keys` should now contain 2 files

├── 626162653ee10e31a28caefe0fb45c33aa5f79d83758a2006abcd6bf387b21025f7ad720<br/>
└── 6772616e216c3621cfe4f2a0877d6090a8c9aa8e5efc28fe830dfcbe02e289912cb9e228
<br/>

---

<br/>

## Ok, first we do the simplest config. The node needs a name

There is a file named `.env` in the repository the content is quite manageable
This is the name that will show up in the telemetry

```
NAME=ExampleNode
```

## Next is the configuration of our subdomain:

The file location is `.\config\node.subdomain.conf`.

We actually only need to edit this part:

```
  # TODO replace node with your subdomain
    server_name node.*;
```

Example:

> We have created a subdomain at noip with the name `magic-node`.
>
> Then our url would be something like `magic-node.ddns.net`
>
> So we change `node.*` to `magic-node.*` actually quite simple.

## Last but not least. The letsencrypt configs

The file location is `.\config\letsencrypt-env`.

We are actually only interested in 2 entries

```
URL=example.com
SUBDOMAINS=myNode
```

> If we take again the example from above we have to change the entries as follows
>
> URL=`ddns.net`
>
> SUBDOMAINS=magic-node

-> Who wants to read more about the settings can click <a href="https://github.com/linuxserver/docker-letsencrypt#parameters">here</a>

## How to start the node now:

We can now easily start the node with `docker-compose up`.

> Tip:
>
> With `docker-compose up -d` the process runs in the background.
>
> We can always open the logs with `docker-compose logs -f`
>
> `docker-compose down` to stop the container
