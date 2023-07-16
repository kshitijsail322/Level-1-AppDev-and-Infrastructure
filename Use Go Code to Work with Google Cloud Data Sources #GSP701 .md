# GSP701
## Run in cloudshell
```cmd
export PROJECT_ID=$(gcloud info --format="value(config.project)")
git clone https://github.com/GoogleCloudPlatform/DIY-Tools.git
gcloud firestore import gs://$PROJECT_ID-firestore/prd-back
cd ~/DIY-Tools/gcp-data-drive/cmd/webserver
go build -mod=readonly -v -o gcp-data-drive
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
./gcp-data-drive
```
____
## Open a new cloudshell tab
### Copy the web preview url without `/?authuser=0`
```cmd
export PREVIEW_URL=
```
____
### after running this command open the green color highlited url in new tab
```cmd
export PROJECT_ID=$(gcloud info --format="value(config.project)")
echo $PREVIEW_URL/fs/$PROJECT_ID/symbols/product/symbol
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
echo -e "\033[32m$PREVIEW_URL/bq/$PROJECT_ID/publicviews/ca_zip_codes?authuser=0&environment_name=default\033[0m"
```
```cmd
cd ~/DIY-Tools/gcp-data-drive/cmd/webserver
gcloud app deploy app.yaml --project $PROJECT_ID -q
echo -e "\033[31mhttps://www.youtube.com/@CodingWithHardik\033[0m"
export TARGET_URL=https://$(gcloud app describe --format="value(defaultHostname)")
curl $TARGET_URL/fs/$PROJECT_ID/symbols/product/symbol
curl $TARGET_URL/fs/$PROJECT_ID/symbols/product/symbol/008888166900
curl $TARGET_URL/bq/$PROJECT_ID/publicviews/ca_zip_codes
```
____
