# Tools/packages you need to deploy a branch to the QA environment
All these tools should be installed by the `bin/k8s-prereqs.sh` script in this repo, but some need additional setup
## docker
## kubectl
Copy `cloud-hcs/.kube/config` to `~/.kube/config`
`kubectl completion` and follow the instructions for your shell (bash or zsh) as appropriate
Use `kubens qa` to switch to the QA namespace
## helm
## aws cli
In `~/.aws/credentials`, add a section
```
[exo]
aws_access_key_id = YOURACCESSKEYID
aws_secret_access_key = YOURSECRETACCESSKEY
``` 
with the actual values put in

## Deploying code to the QA environment
1. Check out the branch you want to QA (including the `cloud-nucleus` branch)
2. Run `bin/buildpush.sh qa qa exo` in `cloud-hcs` to build/deploy the code
3. Run `kubectl get pod` to list the active pods, then `kubectl delete pod cloud-hcs-$SOME_HASHES` to delete the active pod, to start it with the updated code
