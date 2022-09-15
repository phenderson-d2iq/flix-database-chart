# Flix Database

This chart will deploy a Flix Database instance in Kubernetes.

## TL;DR;

```console
$ helm install flix-db flix-database/flix-database
```

> **Warning**: This is meant for testing only and is not a fully production ready Flix Database instance. It comes with no backup solution.

## Introduction

This chart installs a set of Flix Databases using your current configuration.

## Installing the Chart

To install the chart with the release name `flix-db`:

```console
$ helm install flix-database/flix-database --name flix-db
```

You must pass in values.

## Uninstalling the Chart

To uninstall/delete the `flix-db` deployment:

```console
$ helm delete flix-db
```

The command removes all the Kubernetes components associated with the chart and
deletes the release.

## Configuration

The following table lists the required values needed for the chart:

| Parameter                       | Description                                                                 | Required |
|:--------------------------------|:----------------------------------------------------------------------------|:---------|
| `mysqlDatabase.rootDBpassword`  | Password for the root MySQL User                                            | Yes |
| `mysqlDatabase.dbUser`          | User for the Flix Application                                               | Yes |
| `mysqlDatabase.dbPassword`      | Password for the Flix DB User                                               | Yes |
| `mysql_db_pvc.storageClassName` | StorageClass to use for MySQL backend                                       | Yes |
| `mysql_db_pvc.size`             | Size of MySQL DB                                                            | Yes |
| `flix.config`                   | This will be the basic Flix config to get a server running (license server) | Yes |


## Example format of flix.config:

The following is a example of how to format you current flix config in the values.yaml:

```
flix:
  config:
    floating_license_hostname: 20.98.109.175
    floating_license_port: 4101
    shared_storage: true
``` 

---

## Full values.yaml example:

```
mysqlDatabase:
  rootDBpassword: "JyXiP7JofmBer9"
  dbUser: "flix"
  dbPassword: "qGQGSLu6BM3hth"

mysql_db_pvc:
  storageClassName: ebs-sc
  size: 50Gi

# Flix Specific configurations:
# config - This is the configuration for your Flix Instance. Make sure its in proper yaml format. See commented out example at bottom of page.
flix:
  config:
    floating_license_hostname: 20.98.109.175
    floating_license_port: 4101
    shared_storage: true
```