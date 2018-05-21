# chinb-deploy
Deploy chinb-chain rapidly using Docker. 


# Getting started

## Installing

#### Prerequisites

Docker Toolbox installed. 
> To download and install Docker Toolbox for your environment please
follow [the Docker Toolbox instructions](https://www.docker.com/products/docker-toolbox). 

### docker-compose

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

### kubernetes for Google Cloud Platform

if you have set `keystore.secret` to `true` in [kuberneteth.yaml](./kuberneteth.yaml) create an account and upload the key

```bash
# Example
# create a new encrypted keyfile
$ geth account new
Your new account is locked with a password. Please give a password. Do not forget this password.
Passphrase:
Repeat passphrase:
Address: {30a75c364a57d7479b7c5d16c5dc4dcc2176eb5b}
# upload it to the kubernetes server for specified Node
$ kubectl create secret generic geth-key-<Node_UserIdent> --from-file ~/.ethereum/keystore/UTC--2017-11-20T18-36-59.948336313Z--30a75c364a57d7479b7c5d16c5dc4dcc2176eb5b
```

if not, just copy any existing geth key to the `keystore` folder, and add it's name and password to `kuberneteth.yaml` or use the key that is already present in the folder if you just want to play around (password is '123')

once the key is provided you can just create the cluster with those 2 commands:

```bash
cd k8s
./kuberneteth # this will create a file called 'deployment.yaml'
kubectl apply -f deployment.yaml # this will deploy the cluster to kubernetes
```
