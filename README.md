# Vault on Kubernetes (KIND)

This is for Provisioning a Vault on Kind cluster 


## [Vault](https://github.com/hashicorp/vault-helm)

When vault is on 0/1 is important [unseal](https://developer.hashicorp.com/vault/docs/concepts/seal) the process.

```
kubectl -n vault exec vault-0 -- vault operator init -key-shares=1 -key-threshold=1 -format=json > vault-cluster-keys.json

kubectl -n vault exec vault-0 -- vault operator unseal <keys>


kubectl port-forward -n vault vault-0 8200:8200
```

```
WARNING! dev mode is enabled! In this mode, Vault runs entirely in-memory
and starts unsealed with a single unseal key. The root token is already
authenticated to the CLI, so you can immediately begin using Vault.

You may need to set the following environment variables:

    $ export VAULT_ADDR='http://[::]:8200'

The unseal key and root token are displayed below in case you want to
seal/unseal the Vault or re-authenticate.

Unseal Key: <keys>
Root Token: <root-keys>

Development mode should NOT be used in production installations!


```
