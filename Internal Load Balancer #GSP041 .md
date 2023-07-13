# GSP041
## Run in cloudshell
```cmd
sudo apt-get install -y virtualenv
python3 -m venv venv
source venv/bin/activate
curl -O -L https://github.com/CodingWithHardik/Level-1-AppDev-and-Infrastructure/blob/master/sh%20files/backend.sh
gcloud compute instance-templates create primecalc \
--metadata-from-file startup-script=backend.sh \
--no-address --tags backend
gcloud compute firewall-rules create http --network default --allow=tcp:80 \
--source-ranges 10.128.0.0/20 --target-tags backend
gcloud compute instance-groups managed create backend \
--size 3 \
--template primecalc \
--zone us-central1-f
gcloud compute instance-groups managed set-autoscaling backend \
--target-cpu-utilization 0.8 --min-num-replicas 3 \
--max-num-replicas 10 --zone us-central1-f
gcloud compute health-checks create http ilb-health --request-path /2
gcloud compute backend-services create prime-service \
--load-balancing-scheme internal --region us-central1 \
--protocol tcp --health-checks ilb-health
gcloud compute backend-services add-backend prime-service \
--instance-group backend --instance-group-zone us-central1-f \
--region us-central1
gcloud compute forwarding-rules create prime-lb \
--load-balancing-scheme internal \
--ports 80 --network default \
--region us-central1 --address 10.128.10.10 \
--backend-service prime-service
curl -O -L https://github.com/CodingWithHardik/Level-1-AppDev-and-Infrastructure/blob/master/sh%20files/frontend.sh
gcloud compute instances create frontend --zone us-central1-b \
--metadata-from-file startup-script=frontend.sh \
--tags frontend
gcloud compute firewall-rules create http2 --network default --allow=tcp:80 \
--source-ranges 0.0.0.0/0 --target-tags frontend
```