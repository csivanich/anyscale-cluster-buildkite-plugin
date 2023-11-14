# anyscale-cluster-buildkite-plugin

A Buildkite plugin to run an Anyscale Ray cluster

Starts the Ray cluster on Anyscale before running command(s), then terminates cluster after.

# Properties

| Name | Description | Required |
|------|-------------|----------|
| cloud-name | Cloud name to create cluster with | NO default: org default Cloud |
| compute-file | Compute configuration to use, will be created from file | NO default: org default compute config |
| compute-name | Compute configuration to use by name | NO default: org default compute config |
| debug | Increase plugin verbosity | NO default: `unset` | 
| docker-cmd | Command to use for Docker | NO default: `docker` | 
| env-name | Cluster environment ot use by name | YES |
| idle-timeout | May not do anything. Time to allow cluster to idle before auto-termination | NO default: `10` |
| image | Docker image to run `anyscale` from within | NO default: `anyscale/ray:2.8.0` | 
| name | Name to give the cluster | NO default: `buildkite-<PIPELINE SLUG>-<BUILD NUMBER>-<RETRY NUMBER>` | 
| project-id | Project to create cluster with by id | NO default: no project |
| project-name | Project to create cluster with by name | NO default: no project |
