# Creating Charts

## Hello NGINX

A Helm chart consists of two main components: the **Chart.yaml** file and at least one **template** file.

The Chart.yaml file contains metadata about the chart. Here's an example:

```yaml
apiVersion: v2
name: hello-nginx
version: 0.1.0
```

Notes:
- The Chart.yaml file provides information about the chart.
- Every chart must have a version number following the Semantic Versioning 2 standard.

The templates directory contains one or more template files that generate Kubernetes manifest files when combined with values. Here's an example of a pod.yaml template file:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: {{ .Chart.Name }}-{{ .Release.Name }}
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

Notes:
- The pod.yaml template uses the Go Template syntax.
- In the example, `{{ .Chart.Name }}-{{ .Release.Name }}` is replaced with values from the Chart.yaml file and the release name.

To install the chart, use the following command:

```bash
helm install minimal-release hello-nginx
```

To view the deployed resources, run:

```bash
kubectl get all,pvc,secret,cm
helm ls
helm get manifest minimal-release
```


## Helm create command

To create a new chart using the Helm create command, run:

```
helm create -h
```

References:
* [Charts](https://helm.sh/docs/topics/charts/) documentation.
* Best practices: [General Conventions](https://helm.sh/docs/chart_best_practices/conventions/)
* Best practices: [Values](https://helm.sh/docs/chart_best_practices/values/)
* Best practices: [Templates](https://helm.sh/docs/chart_best_practices/templates/)
* Chart template guide [Getting Started](https://helm.sh/docs/chart_template_guide/getting_started/)

```
helm create sample-chart
```