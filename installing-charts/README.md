# Working with Charts

For a complete list of options available when installing a Helm chart:

```bash
helm install -h | less
```

## Phases of a Helm Intallation

Helm follows a series of 5 stages during the installation process:

1. Chart Loading: The chart is loaded into Helm.
2. Value Parsing: The values specified for the chart are parsed.
3. Template Execution: The templates within the chart are executed.
4. YAML Rendering: The executed templates are rendered into YAML files.
5. Kubernetes Deployment: The rendered YAML files are sent to Kubernetes for deployment.
6. The initial four stages primarily involve local data processing, where Helm operates on the same computer where the helm command is executed.

However, in the final stage, Helm transmits the processed data to Kubernetes. Subsequently, Helm and Kubernetes engage in bidirectional communication until the release is either accepted or rejected.

## Installing Drupal

References:
* [Bitnami Drupal](https://artifacthub.io/packages/helm/bitnami/drupal) on Artifact Hub.
* [Drupal packaged by Bitnami](https://bitnami.com/stack/drupal/helm) documentation
* [Drupal packaged by Bitnami](https://github.com/bitnami/charts/tree/master/bitnami/drupal/) GitHub repo.

An option to install the chart is by utilizing the following command, which deploys the chart with default values and generates a unique release name:

```bash
helm install bitnami/drupal --generate-name
```

Nevertheless, for the sake of consistency across subsequent commands, it is advisable to install the chart using a designated release name such as hello-helm. This ensures that the provided commands remain universally applicable.

```bash
helm install hello-helm bitnami/drupal
```

Get a list of installed helm releases:

```bash
helm ls
```

To see what resources the chart created:

```bash
kubectl get all,pvc,secret,cm
```

Please take note of the service type being `LoadBalancer`. To establish an external IP address for the service, open a separate terminal and execute the command minikube tunnel. Once the tunnel is successfully established, the service should acquire an `external IP address`.

```bash
kubectl get svc
```

Copy the IP address into your browser. 

## Getting More Information

Find out what information is available:

```bash
helm get -h
```

After installing the chart, Helm provides detailed notes regarding the installation. To revisit these notes, you can execute the following command:

```bash
helm get notes hello-helm
```

The notes provided by Helm contain instructions on how to obtain the username and password required for logging into the active Drupal website.

Additionally, Helm allows us to inspect the manifests it generated and submitted to Kubernetes by executing the following command:

```bash
helm get manifest hello-helm | less
```

To see what values were supplied when Helm installed our chart:

```bash
helm get values hello-helm
```

We can get all information about our release including computed values based on the chart configuration:

```bash
helm get all hello-helm | less
```

## Release Names and Namespaces

Release names must be unique within a namespace:

```bash
helm install hello-helm bitnami/drupal
```

But we can install multiple releases in the same namespaces if they have different names:

```bash
helm install hello-drupal bitnami/drupal
```
To see what we have now:
```bash
helm ls
```
and:
```bash
kubectl get all,pvc,secret,cm
```

In Helm, Well written templates include the release name in the resource name.

We can reuse a release name in different namespaces:

```bash
kubectl create ns foo
helm install hello-helm bitnami/drupal --namespace foo
```

To see what we have now:
```bash
helm ls --all-namespaces
```
and:
```bash
kubectl get all,pvc,secret,cm
kubectl get all,pvc,secret,cm --namespace foo
```


## Uninstalling a Chart

To get the list of installed charts:
```bash
helm ls --all-namespaces
```

To uninstall the chart we created in the `foo` namespace:

```bash
helm uninstall hello-helm --namespace foo
```

We can delete the releases in our current namespace as follows:

```bash
helm uninstall hello-helm
helm uninstall hello-drupal
```