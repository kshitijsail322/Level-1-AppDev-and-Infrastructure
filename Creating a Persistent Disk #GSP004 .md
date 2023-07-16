# GSP004
## Run in cloudshell
```cmd
export ZONE=
```
```cmd
gcloud compute instances create gcelab --zone $ZONE
gcloud compute disks create mydisk --size=200GB \
--zone $ZONE
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
gcloud compute instances attach-disk gcelab --disk mydisk --zone $ZONE
gcloud compute ssh gcelab --zone $ZONE
```
```cmd
sudo mkdir /mnt/mydisk
sudo mkfs.ext4 -F -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
sudo mount -o discard,defaults /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1 /mnt/mydisk
```
