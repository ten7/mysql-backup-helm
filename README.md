# mysql-backup-helm

A helm chart to backup your MySQL or MariaDB database to an S3 bucket or SFTP from Kubernetes

## How it works

This chart provisions a cronjob which runs the [`ten7/mysql_backup`](https://hub.docker.com/repository/docker/ten7/mysql-backup) container. It uses the [`s3cmd`](https://s3tools.org) command to synchronize with one or more "remotes". Each remote can be either an S3 bucket, or an SFTP server.

## Features

* Synchronizes from multiple sources to multiple targets.
* Does not require persistent storage to function.
* Has no persistent container, or a cronjob.
* Supports multiple S3 and SFTP destinations.
* Can be installed multiple times in the same namespace, with different schedules, allowing you to make hourly/daily/weekly/monthly backups.

## Requirements

* Connection and credentials for source database servers.
* Connection and credentials for target S3 and/or SFTP providers.

## Installation

```shell
helm repo add mysql-backup https://ten7.github.io/mysql-backup-helm/
helm repo update
helm upgrade --install mysql-backup mysql-backup/mysql-backup --namespace=my-namespace -f path/to/my-values.yml
```

## Configuration

For a full list of values, see [values.yaml](https://raw.githubusercontent.com/ten7/mysql-backup-helm/main/charts/mysql-backup/values.yaml).

## License

MySQL Backup is licensed under GPLv3. See [LICENSE](https://raw.githubusercontent.com/ten7/mysql-backup-helm/main/LICENSE) for the complete language.
