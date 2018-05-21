# Concourse Org Pipeline Helm Chart

Installing this chart will set a pipeline in a specified Concourse installation,
which deploys the Analytics Platform Control Panel frontend webapp when a Github
release is created.


## Installing the Chart

To install the chart:

```bash
helm install mojanalytics/cpfrontend-pipeline \
  --values /path/to/chart/configs/cpfrontend-pipeline.yaml
```

## Configuration

| Parameter  | Description     | Default |
| ---------- | --------------- | ------- |
| concourse.externalURL | The same value as for the Concourse Helm chart | "" |
| concourse.password | Basic authentication password for Concourse | "" |
| concourse.team | Concourse team name | `main` |
| concourse.username | Basic authentication username for Concourse | "" |
| github.accessToken | Github personal access token for API | "" |
| github.webhookToken | Access token for Github webhook calling Concourse
resource | "" |
| kubernetes.apiUrl | Kubernetes cluster API URL | "" |
| kubernetes.caCert | Kubernetes cluster CA certificate for API access | "" |
| kubernetes.token | Kubernetes token for API access | "" |
