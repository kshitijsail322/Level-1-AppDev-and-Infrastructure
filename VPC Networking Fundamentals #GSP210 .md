# GSP210
## Run in cloudshell
### Copy the zone from task 2 where the instance create steps are shown
```cmd
export ZONE=
```
```cmd
gcloud compute networks create mynetwork \
--project=$DEVSHELL_PROJECT_ID \
--subnet-mode=auto --mtu=1460 \
--bgp-routing-mode=regional
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
gcloud compute instances create mynet-us-vm \
--project=$DEVSHELL_PROJECT_ID \
--zone=$ZONE --machine-type=e2-micro \
--network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=mynetwork \
--metadata=enable-oslogin=true \
--maintenance-policy=MIGRATE \
--provisioning-model=STANDARD \
--create-disk=auto-delete=yes,boot=yes,device-name=mynet-us-vm,image=projects/debian-cloud/global/images/debian-11-bullseye-v20230509,mode=rw,size=10,type=projects/$DEVSHELL_PROJECT_ID/zones/$ZONE/diskTypes/pd-balanced \
--no-shielded-secure-boot \
--shielded-vtpm \
--shielded-integrity-monitoring \
--labels=goog-ec-src=vm_add-gcloud \
--reservation-affinity=any
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
gcloud compute instances create mynet-eu-vm \
--project=$DEVSHELL_PROJECT_ID \
--zone=europe-west1-b \
--machine-type=e2-micro \
--network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=mynetwork \
--metadata=enable-oslogin=true \
--maintenance-policy=MIGRATE \
--provisioning-model=STANDARD \
--create-disk=auto-delete=yes,boot=yes,device-name=mynet-eu-vm,image=projects/debian-cloud/global/images/debian-11-bullseye-v20230509,mode=rw,size=10,type=projects/$DEVSHELL_PROJECT_ID/zones/europe-west1-b/diskTypes/pd-balanced \
--no-shielded-secure-boot \
--shielded-vtpm \
--shielded-integrity-monitoring \
--labels=goog-ec-src=vm_add-gcloud \
--reservation-affinity=any
```
____
