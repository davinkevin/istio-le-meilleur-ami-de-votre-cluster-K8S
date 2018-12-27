# Istio ⛵️, le meilleur ami de votre cluster K8S ❤️

Summary:
* Presentation slide
* **Our system are evolving**
    * "do-all-the-thing" app
    * Docker rising
    * We split our app to follow micro-services logic
    * But it's hard to maintain in production
    * Kubernetes solves some problems...
    * But not all... it's not its responsability
    * Istio rises 🤩
* Bingo 
    * Micro-services
    * Docker
    * Kubernetes
    * ...
* **Presentation**
    * Me, Myself and I
    * Stack-Labs
    * Open source
    * Work for someone with 🛰 and ✈ in TLS
* **History of Istio**
    * Who is behind istio
        * Lyft, IBM and Google
            * Release tweet of Istio
        * Release 0.1.0 > https://istio.io/blog/2017/0.1-announcement/
        * Huge modification during 0.x version (especially 0.7 to 0.8)
* **What is the main goal of Istio ?**
    * Writing reliable, loosely coupled, production-grade applications based on micro-services
    * Be technology agnostic
        * From application POV
        * From infrastructure POV 
    * Improve observability for dev and ops
        * Comparison between the monolith model and micro-services model
            * local call VS remote call
        * Distributed system requires distributed tools...
            * But our tools doesnt change
* **Architecture of istio**
    * Service Mesh
        * Description of Service Mesh
            * Additional layer between Infrastructure and Services 
    * Control Plane
        * Pilot
        * Mixer
        * Citadel
        * Galley
    * Data Plane
        * Envoy
            * auto-injection of envoy
* **K8S and Istio**
    * Responsibility of each one
    * Dev & Ops POV (vern diagram between K8S and Istio responsibility)
    * New objects available... more YAML files !
    * VirtualServices & Destination Rules
    * Service Entry & Gateway
* **Connect and Control**
    * New pattern of deployment
        * What was in K8S (Ingress|Service|Deployment|ReplicaSet|Pods)
        * What Istio add to this ❤️
    * Canary Deployment
        * Headers (routing & more)
        * https://youtu.be/pi-ABBZ1AIw?t=1184
    * Traffic mirroring
        * Follow the evolution without users on it
        * https://youtu.be/pi-ABBZ1AIw?t=1458
    * Blue/Green Deployment
        * Managing multi version in production
        * https://youtu.be/pi-ABBZ1AIw?t=1795
* **Observability**
    * Graphana
    * Zipkin
    * Jaeger & Open-Tracing
* **Security**
    * Security as a service
    * mTLS
    * JWT/OIDC + definitions
* **Envoy**
    * Supports many load-balancing algorithm
    * Fine tuning of retries and budget > https://istio.io/docs/concepts/traffic-management/#fine-tuning
* On GKE with ❤️!
    * Command line : 

```shell
gcloud beta container --project "istio-meilleur-ami-de-k8s" clusters create "istio-demo" --zone "europe-west1-b" --no-enable-basic-auth --cluster-version "1.11.5-gke.5" --machine-type "n1-standard-4" --image-type "COS" --disk-type "pd-ssd" --disk-size "100" --metadata disable-legacy-endpoints=true --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --preemptible --num-nodes "4" --enable-stackdriver-kubernetes --no-enable-ip-alias --network "projects/istio-meilleur-ami-de-k8s/global/networks/default" --subnetwork "projects/istio-meilleur-ami-de-k8s/regions/europe-west1/subnetworks/default" --enable-network-policy --enable-master-authorized-networks --addons HorizontalPodAutoscaling,HttpLoadBalancing,Istio --istio-config auth=NONE --enable-autoupgrade --enable-autorepair
```
