# Kubernetes_dev_environment_from_scratch

- 64bit Ubuntu 20.04 VirtualBox 환경
- Install Docker, Kubectl
- K3s
  - 쿠버네티스 클러스터 구축 쉬움
  - 경량화
  - Helm, Kustomize, CSI Pluugin
  ```
  wget https://get.helm.sh/helm-v3.7.1-linux-amd64.tar.gz
  ```
  ```
  wget https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize%2Fv3.10.0/kustomize_v3.10.0_linux_amd64.tar.gz
  ```
  ```
  kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/v0.0.20/deploy/local-path-storage.yaml
  ```
  
- Setup Components
  - Kubeflow
    <details>
    <summary> Cert-manager, Istio, Dex, OIDC AuthService, Kubeflow Namespace, Kubeflow Roles, Kubeflow Istio Resources, Kubeflow Pipelines, Katib, Central Dashboard, Admission Webhook, Notebooks & Jupyter Web App, Profiles + KKFAM, Volumnes Web App, Training Operator, User Namespace </summary>
    
    ```
    kustomize build common/cert-manager/cert-manager/base | kubectl apply -f -
    ```
    ```
    kustomize build common/cert-manager/kubeflow-issuer/base | kubectl apply -f -
    ```
    ```
    kustomize build common/istio-1-9/istio-crds/base | kubectl apply -f -
    ```
    ```
    kustomize build common/istio-1-9/istio-namespace/base | kubectl apply -f -
    ```
    ```
    kustomize build common/istio-1-9/istio-install/base | kubectl apply -f -
    ```
    ```
    kustomize build common/dex/overlays/istio | kubectl apply -f -
    ```
    ```
    kustomize build common/oidc-authservice/base | kubectl apply -f -
    ```
    ```
    kustomize build common/kubeflow-namespace/base | kubectl apply -f -
    ```
    ```
    kustomize build common/kubeflow-roles/base | kubectl apply -f -
    ```
    ```
    kustomize build common/istio-1-9/kubeflow-istio-resources/base | kubectl apply -f -
    ```
    ```
    kustomize build apps/pipeline/upstream/env/platform-agnostic-multi-user | kubectl apply -f -
    ```
    ```
    kustomize build apps/katib/upstream/installs/katib-with-kubeflow | kubectl apply -f -
    ```
    ```
    kustomize build apps/centraldashboard/upstream/overlays/istio | kubectl apply -f -
    ```
    ```
    kustomize build apps/admission-webhook/upstream/overlays/cert-manager | kubectl apply -f -
    ```
    ```
    kustomize build apps/jupyter/notebook-controller/upstream/overlays/kubeflow | kubectl apply -f -
    ```
    ```
    kustomize build apps/profiles/upstream/overlays/kubeflow | kubectl apply -f -
    ```
    ```
    kustomize build apps/volumes-web-app/upstream/overlays/istio | kubectl apply -f -
    ```
    ```
    kustomize build apps/tensorboard/tensorboards-web-app/upstream/overlays/istio | kubectl apply -f -
    ```
    ```
    kustomize build apps/tensorboard/tensorboard-controller/upstream/overlays/kubeflow | kubectl apply -f -
    ```
    ```
    kustomize build apps/training-operator/upstream/overlays/kubeflow | kubectl apply -f -
    ```
    ```
    kustomize build common/user-namespace/base | kubectl apply -f -
    ```
    
    </details>
![image](https://user-images.githubusercontent.com/121914727/233456983-e5419070-19a5-4b01-b95b-d5048320f07e.png)

    
  
  
