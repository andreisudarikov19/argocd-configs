# Instructions to deploy `01-demo-app` in ArgoCD

This app is designed to create the simplest and most basic deployment scenario in ArgoCD.

1. Open your ArgoCD UI.

1. On the **Applications** page, in the top right corner click **CREATE**. You'll see the application creation form.

1. In the **GENERAL** section: 
    1. Under **Application Name**, specify `demo-app`.
    1. From the **Project name** dropdown, select `default`.

1. In the **SOURCE** section:
    1. Under **Repository URL**, paste the URL of the repository:

        ```url
        https://github.com/andreisudarikov19/argocd-configs.git
        ```

    1. Under **Path**, specify `./01-demo-app`.

1. In the **DESTINATION** section:
    1. From **Cluster URL** dropdown, select your Kubernetes cluster.

1. In the top left of the form, click **Create**.

    The application card will show your application as `Missing` and `Out Of Sync`.

1. On the application card, click **Sync**.

    This synchronizes the app configuration with the repo and deploys your application in a `Healthy` state.

