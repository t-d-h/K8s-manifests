Simple vault server with one instance config and auto unseal script
---
How to use:
1. Change all namespace in the manifest to your
2. Apply configmap.yaml and vault-rbac.yaml
3. Edit nodeAffinity in init-job.yaml and apply the manifest.
It is the a one time job auto install vault at node's hostpath: /mnt/kubernetes/vault.
Then the pod will be cleaned by itself
4. Get yournode:/mnt/kubernetes/vault/init.txt, it will look like the example init.txt file.
5. Replace those unseal_keys_b64 to vault-secret.yaml, then apply it
6. Apply vault-deployment.yaml, you are done. Next time, when ever vault start, it will took those 3 unseal key to unseal it seft.
You can edit Service config (in vault-deployment.yaml) to fit your needs.

Node: you can backup /mnt/kubernetes/vault to some where, in case you want to restore, you just need to start vault to the node which has that data.