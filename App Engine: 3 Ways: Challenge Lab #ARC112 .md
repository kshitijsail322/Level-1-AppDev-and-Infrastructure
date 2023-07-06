# ARC112
```cmd
export MESSAGE=
```
```cmd
gcloud services enable appengine.googleapis.com
git clone https://github.com/GoogleCloudPlatform/python-docs-samples.git
cd python-docs-samples/appengine/standard_python3/hello_world
gcloud app deploy
rm -f main.py
cat > main.py << EOF

# Copyright 2018 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# [START gae_python38_app]
# [START gae_python3_app]
from flask import Flask


# If `entrypoint` is not defined in app.yaml, App Engine will look for an app
# called `app` in `main.py`.
app = Flask(__name__)


@app.route("/")
def hello():
    """Return a friendly HTTP greeting.

    Returns:
        A string with the words 'Hello World!'.
    """
    return "$MESSAGE"


if __name__ == "__main__":
    # This is used when running locally only. When deploying to Google App
    # Engine, a webserver process such as Gunicorn will serve the app. You
    # can configure startup instructions by adding `entrypoint` to app.yaml.
    app.run(host="127.0.0.1", port=8080, debug=True)
# [END gae_python3_app]
# [END gae_python38_app]
EOF
gcloud app deploy
```
____
# REGIONS
`1` *=>* `asia-east1`<br>
`2` *=>* `asia-northeast1`<br>
`3` *=>* `asia-south1`<br>
`4` *=>* `asia-southeast1`<br>
`5` *=>* `australia-southeast1`<br>
`6` *=>* `europe-central2`<br>
`7` *=>* `europe-west`<br>
`8` *=>* `europe-west2`<br>
`9` *=>* `europe-west3`<br>
`10` *=>* `us-central`<br>
`11` *=>* `us-east1`<br>
`12` *=>* `us-east4`<br>
`13` *=>* `us-west1`<br>
`14` *=>* `us-west2`<br>
`15` *=>* `us-west3`<br>
`16` *=>* `us-west4`<br>
`17` *=>* `cancel`
