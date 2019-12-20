# intake-server
A helm chart for deploying Intake server as a kubernetes service

## Chart details

This chart will deploy one pod running the intake server, and a service that exposes the intake


## Installation

To install the Intake server helm chart:

```
git clone https://github.com/informatics-lab/intake-server.git
helm install --name catalog-server ./intake-server
```

Note that there's currently a bug in Intake that means you cannot use the name 'intake' in the server name.
This is fixed in an upcoming release of Intake.

To upgrade an existing installation:

```
helm upgrade --install catalog-server ./catalog-server
```

To delete an existing installation:

```
helm delete catalog-server
```


## Configuration Options

The table below shows configurable options for the Intake server helm chart:

| Parameter                                     | Description                                     | Default Value                                           |
| --------------------------------------------- | ------------------------------------------------| --------------------------------------------------------|
| `global.imagePullSecrets`                     | Global Docker registry secret names as an array | `[]`                                                    |
| `containers.volumeMounts.value`               | Extra volume mounts to add to the server-running container | `[]`                                         |
| `extraEnv.catalogPath.value`                  | Path to the Intake catalog file to be served    | `""`                                                    |
| `extraEnv.serverPort.value`                   | Port the intake server runs on                  | 5000                                                    |
| `extraVolumes`                                | Definitions of extra volumes to be added to the server  | `[]`                                            |
| `service.port`                                | Service port; must match `extraEnv.ServerPort.value` | 5000                                               |
| `resources`                                   | Hardware resource requests / limits             | `{}`                                                    |
| `nodeSelector`                                | Node labels for pod assignment                  | `{}`                                                    |
| `tolerations`                                 | Node tolerations for pod assignment             | `[]`                                                    |
| `affinity`                                    | Node affinity for pod assignment                | `{}`                                                    |