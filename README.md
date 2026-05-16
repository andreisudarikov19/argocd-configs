# ArgoCD configurations for learning and testing

This repository contains app configuration for my ArgoCD testing cluster.

Repository address for quick copying:

```url
https://github.com/andreisudarikov19/argocd-configs.git
```

<details>
    <summary>How to install and use ArgoCD on minikube</summary>

To install ArgoCD on minikube for experiments on a local machine:

1. Manually create a namespace for ArgoCD to run in:

    ```sh
    kubectl create ns argocd
    ```

    It's important that you name the namespace *exactly* `argocd`, otherwise it won't work.

1. Apply the manifest from the ArgoCD GutHub installation repo:

    ```sh
    kubectl apply \
        -n argocd \
        -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.8/manifests/install.yaml
    ```

1. Check that everything is `RUNNING`:

    ```sh
    kubect get all \
        -n argocd
    ```

1. Create a new terminal or tab in your terminal emulator and port-forward the ArgoCD UI:

    ```sh
    kubectl port-forward svc/argocd-server \
        -n argocd 8080:443
    ```

    You can now access the ArgoCD UI on your local machine at `localhost:8080`.

1. Get the admin password value to log into the UI:

    ```sh
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d; echo
    ```

</details>


## App naming conventions in ArgoCD

* Capital lettters are not allowed.


## Notes on behavior

* When specifying a config location in the repository, start with `./` for root directory.

* While ArgoCD can create namespaces automatically, it **won't** delete them in this case.

    > Thus, to avoid hassle with manual search and deletion of namespaces, provide a namespace manifest with every app, so that ArgoCD can clean up after itself.
