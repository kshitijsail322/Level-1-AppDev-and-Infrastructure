# GSP004
## Run in cloudshell
```cmd
gcloud compute instances create gcelab --zone us-central1-c
gcloud compute disks create mydisk --size=200GB \
--zone us-central1-c
gcloud compute instances attach-disk gcelab --disk mydisk --zone us-central1-c
gcloud compute ssh gcelab --zone us-central1-c
```
```cmd
sudo mkdir /mnt/mydisk
sudo mkfs.ext4 -F -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1
sudo mount -o discard,defaults /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1 /mnt/mydisk
```
