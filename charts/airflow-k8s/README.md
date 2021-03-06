# Airflow Helm Chart

Run Airflow on Kubernetes, tasks are executed as new pods.


## Install/Upgrade the Chart

Run:

```bash
$ helm upgrade --install airflow charts/airflow-k8s --namespace airflow -f chart-env-config/ENV/airflow-k8s.yml
```

Airflow will be available at <https://airflow.tools.ENV.mojanalytics.xyz>.

**NOTE**: Change the environment config file to deploy in a different environment
          (the URL will change accordingly)


## Configuration

| Parameter           | Description     | Default.    |
| ------------------- | --------------- | ----------- |
| `airflow.admin.username` | Airflow admin username | `""` |
| `airflow.admin.password` | Airflow admin password | `""` |
| `airflow.auth.type`         | Type of authentication to use. Can be `"AUTH_DB"` which will allow you to login using username/password for a user in the DB or `"AUTH_OID"` which will allow you to login using OIDC. | `"AUTH_DB"` |
| `airflow.auth.oauth.*` | OAuth configuration, required only when `airflow.auth.type` is `"AUTH_OID"` | |
| `airflow.config.core.parallelism` | Airflow configuration determining how many tasks it will run at the same time | `32` |
| `airflow.volumes.dags.nfsServer` | Host of the NFS server where DAGs will be stored. | `""` |
| `airflow.volumes.dags.path` | Path on the NFS server where DAGs will be stored. | `"/dags"` |
| `airflow.volumes.logs.nfsServer` | Host of the NFS server where logs will be stored. | `""` |
| `airflow.volumes.logs.path` | Path on the NFS server where DAGs will be stored. | `"/logs"` |
| `gitSync.interval`| Number of seconds between DAGs syncing from Git repository | `180` (3 minutes) |
| `gitSync.repository`| Git repository with the DAGs. This needs to be public | `"https://github.com/ministryofjustice/analytics-platform-airflow-example-dags"` |
| `gitSync.branch`| Branch to use when syncing the Git repository with the DAGs | `master` |
| `postgres.host`     | (required)      | `""`        |
| `postgres.port`     |                 | `5432`      |
| `postgres.user`     | (required)      | `"airflow"` |
| `postgres.password` | (required)      | `""`        |
| `postgres.db`       | (required)      | `"airflow"` |
| `redis.password`    | password for redis-server (required)      | `"airflow"` |
