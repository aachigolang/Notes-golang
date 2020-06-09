### Useful links

https://codelabs.developers.google.com/codelabs/cloud-hello-istio/index.html?index=..%2F..index#0
https://github.com/GoogleCloudPlatform/gke-istio-gce-demo


### install gcloud on ubuntu

https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu


echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -

sudo apt-get update && sudo apt-get install google-cloud-sdk


### initialize SDK with gcloud

### Gcloud compunenets

gcloud components list

│                  
                                Components                                          │
├───────────────┬───────────────────────────────────────────────┬──────────────────────────┬───────────┤
│     Status    │                         Name                  │            ID            │    Size   │
├───────────────┼───────────────────────────────────────────────┼──────────────────────────┼───────────┤
│ Installed     │ App Engine Go Extensions                      │ app-engine-go            │  97.7 MiB │
│ Installed     │ Cloud Bigtable Command Line Tool              │ cbt                      │   4.0 MiB │
│ Installed     │ Cloud Bigtable Emulator                       │ bigtable                 │   3.8 MiB │
│ Installed     │ Cloud Datalab Command Line Tool               │ datalab                  │   < 1 MiB │
│ Installed     │ Cloud Datastore Emulator                      │ cloud-datastore-emulator │  17.8 MiB │
│ Installed     │ Cloud Datastore Emulator (Legacy)             │ gcd-emulator             │  38.1 MiB │
│ Installed     │ Cloud Pub/Sub Emulator                        │ pubsub-emulator          │  33.2 MiB │
│ Installed     │ Emulator Reverse Proxy                        │ emulator-reverse-proxy   │  14.5 MiB │
│ Installed     │ Google Cloud Build Local Builder              │ cloud-build-local        │   4.4 MiB │
│ Installed     │ gcloud app Java Extensions                    │ app-engine-java          │ 118.9 MiB │
│ Installed     │ gcloud app PHP Extensions                     │ app-engine-php           │  21.9 MiB │
│ Installed     │ gcloud app Python Extensions (Extra Libraries)│ app-engine-python-extras │  27.8 MiB │
│ Installed     │ kubectl                                       │ kubectl                  │  12.2 MiB │
│ Installed     │ BigQuery Command Line Tool                    │ bq                       │   < 1 MiB │
│ Installed     │ Cloud SDK Core Libraries                      │ core                     │   7.2 MiB │
│ Installed     │ Cloud Storage Command Line Tool               │ gsutil                   │   3.3 MiB │
│ Installed     │ gcloud Alpha Commands                         │ alpha                    │   < 1 MiB │
│ Installed     │ gcloud Beta Commands                          │ beta                     │   < 1 MiB │
│ Installed     │ gcloud app Python Extensions                  │ app-engine-python        │   6.1 MiB 


### Create K8 cluster on GKE

https://cloud.google.com/kubernetes-engine/docs/how-to/creating-a-cluster


### Setting up istion on GKE

post installation checkup

gcloud version
gcloud components install kubectl
gcloud config set project project-id
gcloud config set compute/zone compute-zone

gcloud beta container clusters create CLUSTER_NAME \
    --addons=Istio --istio-config=auth=MTLS_STRICT \
    --cluster-version=CLUSTER_VERSION \
    --machine-type=n1-standard-2 \
    --num-nodes=4


Security options

Strict mTLS
Permissive mTLS:

### Verify Istio setup

gcloud container clusters list
gcloud container clusters get-credentials CLUSTER_NAME

kubectl get service -n istio-system
kubectl get pods -n istio-system