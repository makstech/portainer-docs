# Add an Ingress using a manifest

There are two ways to add a new ingress: [manually by using a form](add.md) or automatically by using a manifest. This article explains how to add an ingress using a manifest.

{% hint style="info" %}
Manifests aren't just for Ingresses - you can also deploy namespaces, ConfigMaps, secrets and volumes using a manifest.
{% endhint %}

From the menu select **Ingresses** then click **Create from manifest**.

<figure><img src="../../../.gitbook/assets/2.16-ingress-manifest.gif" alt=""><figcaption></figcaption></figure>

Select the namespace for your deployment, define a name for your Ingress, and then choose the build method from the options provided.

{% hint style="info" %}
If you want to use namespaces specified in your manifest to define the namespace(s) you wish to deploy to, you can leave **Namespace** set to `default` and toggle on the **Use namespace(s) specified from manifest** option.
{% endhint %}

<figure><img src="../../../.gitbook/assets/2.15-kubernetes_applications_add_manifest_namespace.png" alt=""><figcaption></figcaption></figure>

## Option 1: Git Repository

From **Deployment type** select either **Kubernetes** or **Compose** (depending on the format of the manifest) then enter the details of your Git repo.

{% hint style="warning" %}
Portainer uses Kompose to convert a Compose manifest to a Kubernetes-compliant manifest. This functionality is planned for deprecation in an upcoming release.
{% endhint %}

| Field/Option          | Overview                                                                                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Authentication        | Toggle this on if your repository requires authentication.                                                                                                                |
| Git Credentials       | If the **Authentication** toggle is enabled and you have [configured Git credentials](../../account-settings.md#git-credentials), you can select them from this dropdown. |
| Username              | Enter your Git username.                                                                                                                                                  |
| Personal Access Token | Enter your personal access token or password.                                                                                                                             |
| Save credential       | Check this option to save the credentials entered above for future use under the name provided in the **credential name** field.                                          |

<figure><img src="../../../.gitbook/assets/2.16-stacks-add-gitcreds.png" alt=""><figcaption></figcaption></figure>

| Field/Option         | Overview                                                                                                                                                                                          |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Repository URL       | Enter the repository URL. If you have enabled Authentication above the credentials will be used to access the repository. The below options will be populated by what is found in the repository. |
| Repository reference | Select the reference to use when deploying the stack (for example, the branch).                                                                                                                   |
| Manifest path        | When using the Kubernetes deployment type, enter the path to your manifest file relative to the root of your repository.                                                                          |
| Compose path         | When using the Compose deployment type, enter the path to your compose file relative to the root of your repository.                                                                              |
| Additional paths     | Click **add file** to define additional manifests or compose files to process as part of the deployment.                                                                                          |

<figure><img src="../../../.gitbook/assets/2.16-applications-manifest-gitdetails.png" alt=""><figcaption></figcaption></figure>

### Automatic updates

Enabling Automatic updates gives Portainer the ability to update your application automatically, either by polling the repository at a defined interval for changes or by using a webhook to trigger an update.

{% hint style="info" %}
For more detail on how automatic updates function under the hood, have a look at [this knowledge base article](https://portal.portainer.io/knowledge/how-do-automatic-updates-for-stacks-applications-work).
{% endhint %}

{% hint style="warning" %}
If your application is configured for automatic updates and you make changes locally, these changes will be overridden by the application definition in the Git repository. Bear this in mind when making configuration changes.
{% endhint %}

| Field/Option   | Overview                                                                                                                            |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Mechanism      | Choose from **Polling** or **Webhook**.                                                                                             |
| Fetch interval | When using the **Polling** method, choose how often you wish to check the Git repository for updates to your application.           |
| Webhook        | When using the **Webhook** method, this displays the webhook URL to use. Click **Copy link** to copy the webhook to your clipboard. |

<figure><img src="../../../.gitbook/assets/2.15-k8s-applications-manifest-autoupdates-polling.png" alt=""><figcaption><p>Automatic updates using the polling mechanism</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/2.15-k8s-applications-manifest-autoupdates-webhook.png" alt=""><figcaption><p>Automatic updates using the webhook mechanism</p></figcaption></figure>

| Field/Option       | Overview                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Force Redeployment | <p>Enable this setting to force the redeployment of your application at the specified interval (or when the webhook is triggered), overwriting any changes that have been made in the local environment, even if there has been no update to the application in Git. This is useful if you want to ensure that your Git repository is the source of truth for your applications and are happy with the local application being replaced.</p><p></p><p>If this option is left disabled, automatic updates will only trigger if Portainer detects a change in the remote Git repository.</p> |

<figure><img src="../../../.gitbook/assets/2.15-kubernetes_applications_add_manifest_force_deploy.png" alt=""><figcaption></figcaption></figure>

When you're ready, click **Deploy**.

## Option 2: Web editor

From **Deployment type** select either **Kubernetes** or **Compose** (depending on the format of the manifest) then write or paste in your Kubernetes manifest.&#x20;

{% hint style="warning" %}
Portainer uses Kompose to convert a Compose manifest to a Kubernetes-compliant manifest. This functionality is planned for deprecation in an upcoming release.
{% endhint %}

<figure><img src="../../../.gitbook/assets/2.16-k8s-ingress-manifest-webeditor.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can search within the web editor at any time by pressing `Ctrl-F` (or `Cmd-F` on Mac).
{% endhint %}

When you're ready, click **Deploy**. &#x20;

## Option 3: URL

From **Deployment type** select either **Kubernetes** or **Compose** (depending on the format of the manifest) then enter the **URL** to your manifest file.

{% hint style="warning" %}
Portainer uses Kompose to convert a Compose manifest to a Kubernetes-compliant manifest. This functionality is planned for deprecation in an upcoming release.
{% endhint %}

<figure><img src="../../../.gitbook/assets/2.15-kubernetes_applications_add_manifest_url.png" alt=""><figcaption></figcaption></figure>

When you're ready, click **Deploy**.

## Option 4: Custom template

From the **Template** dropdown, select the custom template to use. As an optional step, you can edit the template before deploying the application. If you have no custom templates you will be given a link to the [Custom Templates](../templates/) section.

<figure><img src="../../../.gitbook/assets/2.16-k8s-ingress-manifest-template.png" alt=""><figcaption></figcaption></figure>

When you're ready, click **Deploy**.
