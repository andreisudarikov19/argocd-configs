# ArgoCD configurations for learning and testing

This repository contains app configuration for my ArgoCD testing cluster.

<details>
    <summary>How to install ArgoCD on minikube</summary>

To install ArgoCD in minikube for your experiments on a local machine:

1. Manually create a namespace for ArgoCD to run in:

    ```sh
    kubectl create ns argocd
    ```

    It's important that you name the namespace *exactly* `argocd`, otherwise it won't work.

1. Apply the manifest from the ArgoCD GutHub installation repo:

    ```sh
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.8/manifests/install.yaml
    ```

1. Check that everything is `RUNNING`:

    ```sh
    kubect get all -n argocd
    ```

1. Create a new terminal or tab in your terminal emulator and port-forward the ArgoCD UI:

    ```sh
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    ```

    You can now access the ArgoCD UI on your local machine at `localhost:8080`.

1. Get the admin password value to log into the UI:

    ```sh
    kubectl get secret argocd-initial-admin-secret -n argocd -o yaml # | yq
    ```

    The password is under `data:password`.

</details>
