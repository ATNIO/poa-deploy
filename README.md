# chinb-deploy
Deploy chinb-chain rapidly using Docker. 


# Getting started

## Installing

#### Prerequisites

Docker Toolbox installed. 
> To download and install Docker Toolbox for your environment please
follow [the Docker Toolbox instructions](https://www.docker.com/products/docker-toolbox). 

### POA chain with netstats monitoring and simple explorer

Just run the following:

```
$ docker-compose up -d
```

By default this will create:

* 1 container which is a signer node with bootstrapped
* 1 container which is another signer node (which connects to the bootstrapped container on launch)
* 1 container which is a normal node (which connects to the bootstrapped container on launch)
* 1 Netstats container (with a Web UI to view activity in the cluster)
* 1 Explorer container

To access the Netstats Web UI:

```
open http://localhost:3000
```

To access the explorer:

```
open http://localhost:8000
```

### Test accounts ready for use

As part of the bootstrapping process we bootstrap 3 Ethereum accounts, two are signer.

See `files/genesis.json`.
