# Getting Started With Helm

## Installing Helm

To install Helm quickly, run the following command:

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

For more installation options and details, check out the [Installing Helm](https://helm.sh/docs/intro/install/) guide in the Helm documentation.

## Finding Charts

To search for charts from different providers, you can use the `helm search hub` command. For example, to find a chart for the Drupal content management system (CMS), run:

```bash
helm search hub drupal
```

```
URL                                                     CHART VERSION   APP VERSION     DESCRIPTION                                       
https://artifacthub.io/packages/helm/bitnami-ak...      12.5.10         9.4.8           Drupal is one of the most versatile open source...
https://artifacthub.io/packages/helm/bitnami/dr...      16.1.8          10.2.0          Drupal is one of the most versatile open source...
https://artifacthub.io/packages/helm/cetic/drupal       0.1.0           1.16.0          Drupal is a free and open-source web content ma...
https://artifacthub.io/packages/helm/rock8s/drupal      0.0.1           latest          open source software you can use to create a be...

```

This will return a list of available charts along with their versions and descriptions.

You can adjust the column width for better readability by using the `--max-col-width` option. For example:


```bash
helm search hub drupal --max-col-width 65
```

```
URL                                                     CHART VERSION   APP VERSION     DESCRIPTION                                                      
https://artifacthub.io/packages/helm/bitnami-aks/drupal 12.5.10         9.4.8           Drupal is one of the most versatile open source content manage...
https://artifacthub.io/packages/helm/bitnami/drupal     16.1.8          10.2.0          Drupal is one of the most versatile open source content manage...
https://artifacthub.io/packages/helm/cetic/drupal       0.1.0           1.16.0          Drupal is a free and open-source web content management framew...
https://artifacthub.io/packages/helm/rock8s/drupal      0.0.1           latest          open source software you can use to create a beautiful website...
```

### Security tip:

When searching for charts, it's recommended to start with "official" charts or those from "verified publishers" for better quality and security. You can also examine the chart manifests using the `--dry-run` option with `helm install` to ensure their suitability.

## Adding a Repository

To add a repository, such as Bitnami, you can use the `helm repo add` command. For example:

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```

You can verify the repository has been added by running:

```bash
helm repo list
```

## Searching the Repository

To search for charts within a repository, you can use the `helm search repo` command. For example, to search for Drupal charts:

```bash
helm search repo drupal
```

You can also perform specific searches based on keywords, such as "open source" or "database".

To see the available versions for a specific chart, you can use the `--versions` option. For example:

```bash
helm search repo drupal --versions
```

To limit the output, you can pipe the command to `head`:

```bash
helm search repo drupal --versions | head -10
```

## Understanding Versions

In Helm, a *chart version* refers to the version of the Helm chart itself, while the *app version* represents the version of the application packaged in the chart. Multiple chart versions can have the same app version.