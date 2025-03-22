# 1. Remote to K8s Master
## Option 1 - Remote via SSH forwarding
eval $(ssh-agent)
ssh-add hccnfpteam1-key-us-east-1.pem
ssh -A ubuntu@<Jump_Host_Public_IP>
ssh ubuntu@<K8S_Master_Private_IP>

## Option 2 - Remote via copy private key
scp -i hccnfpteam1-key-us-east-1.pem hccnfpteam1-key-us-east-1.pem ubuntu@<Jump_Host_Public_IP:~/
ssh -i hccnfpteam1-key-us-east-1.pem ubuntu@<Jump_Host_Public_IP>
ssh -i hccnfpteam1-key-us-east-1.pem ubuntu@<K8S_Master_Private_IP>

# 2. verify nodes
kubectl get nodes

kubectl label node k8s-wrk-1  node-role.kubernetes.io/worker=worker
