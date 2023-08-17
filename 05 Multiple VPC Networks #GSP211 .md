# GSP211
## Run in cloudshell (ZONE from Task 2, Step 3)
```cmd
export ZONE=
```
```cmd
gcloud compute networks create managementnet --subnet-mode=custom
gcloud compute networks subnets create managementsubnet-us --network=managementnet --region=us-east1 --range=10.130.0.0/20
gcloud compute networks subnets create managementsubnet-eu --network=managementnet --region=europe-west1 --range=172.20.0.0/20
gcloud compute firewall-rules create managementnet-allow-icmp-ssh-rdp --direction=INGRESS --priority=1000 --network=managementnet --action=ALLOW --rules=icmp,tcp:22,tcp:3389 --source-ranges=0.0.0.0/0
gcloud compute networks create privatenet --subnet-mode=custom
gcloud compute networks subnets create privatesubnet-us --network=privatenet --region=us-east1 --range=172.16.0.0/24
gcloud compute networks subnets create privatesubnet-eu --network=privatenet --region=europe-west1 --range=172.20.0.0/20
gcloud compute firewall-rules create privatenet-allow-icmp-ssh-rdp --direction=INGRESS --priority=1000 --network=privatenet --action=ALLOW --rules=icmp,tcp:22,tcp:3389 --source-ranges=0.0.0.0/0
gcloud compute instances create managementnet-us-vm --zone=$ZONE --machine-type=e2-micro --subnet=managementsubnet-us
gcloud compute instances create privatenet-us-vm --zone=$ZONE --machine-type=e2-micro --subnet=privatesubnet-us
gcloud compute instances create vm-appliance \
    --zone=$ZONE \
    --machine-type=e2-standard-4 \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=privatesubnet-us \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=managementsubnet-us \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=mynetwork
```
