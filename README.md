# anyscale-cluster-buildkite-plugin

A Buildkite plugin to run an Anyscale Ray cluster

Starts the Ray cluster on Anyscale before running command(s), then terminates cluster after.

# Properties

| Name | Description | Required |
|------|-------------|----------|
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_CLOUD_NAME | Cloud name to create cluster with | NO default: org default Cloud |
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_COMPUTE_FILE | Compute configuration to use, will be created from file | NO default: org default compute config |
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_COMPUTE_NAME | Compute configuration to use by name | NO default: org default compute config |
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_DEBUG | Increase plugin verbosity | NO default: `unset` | 
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_DOCKER_CMD | Command to use for Docker | NO default: `docker` | 
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_ENV_NAME | Cluster environment ot use by name | YES |
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_IDLE_TIMEOUT | May not do anything. Time to allow cluster to idle before auto-termination | NO default: `10` |
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_IMAGE | Docker image to run `anyscale` from within | NO default: `anyscale/ray:2.8.0` | 
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_NAME | Name to give the cluster | NO default: `buildkite-<PIPELINE SLUG>-<BUILD NUMBER>-<RETRY NUMBER>` | 
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_PROJECT_ID | Project to create cluster with by id | NO default: no project |
| BUILDKITE_PLUGIN_ANYSCALE_CLUSTER_PROJECT_NAME | Project to create cluster with by name | NO default: no project |
