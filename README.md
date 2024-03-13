# Kargo SaaS Demo

Simple Demo for Kargo SaaS on AKP

* Create GitHub PAT
* Create AKP Argo CD instance
* Add a cluster called "mykind"
* Create AKP Kargo instance
  * Attach it to your AKP Argo CD instance.
    * Set as default shard
    * Set as Self-hosted Kargo Agent (if you want)
      * (optional) ^ If you set Self-hosted Kargo Agent, you need to install the agent on the managed cluster
* Login to your Argo CD instance: `argocd login --grpc-web --username=admin christian.cd.akuity.cloud`
* Login to Kargo SaaS instance: `kargo login --admin https://christian.kargo.akuity.cloud`
* Load Repo creds for Argo CD: `argocd repo add https://github.com/christianh814/kargo-saas-demo --type git --username not-used --password $KARGO_GH_PAT`
* Load [PAT creds for Kargo](https://kargo.akuity.io/how-to-guides/managing-credentials#credentials-as-kubernetes-secret-resources): `kargo create -f ~/workspace/kargo/kargo-saas-demo.yaml` # the `namespace` is the Kargo `Project` name
* Create AppSet: `argocd appset create  argocd/appset.yaml`
* Create Kargo things: `kargo create -f kargo/just-kargo-things.yaml`
