# Example: Ray Job

In this example, we use the `anyscale-cluster` plugin to start a small CPU-only cluster. We then submit a Ray Job based on the [Monte Carlo Pi](https://docs.ray.io/en/latest/ray-core/examples/monte_carlo_pi.html) example from Ray's docs.

## Steps

### Load Credentials

This example stores the Anyscale token required to create the cluster in an AWS Secretes Manager secret named `anyscale_cli_token`. We first load it's value into `ANYSCALE_CLI_TOKEN`, the variable the CLI expects.

```yaml
      - seek-oss/aws-sm#v2.3.1:
          env:
            ANYSCALE_CLI_TOKEN: "anyscale_cli_token"
```

### Start Cluster

Now we can start a cluster in Anyscale. This example optionally shows using a specific Ray version, `2.8.0`. The cluster environment and compute configuration names are added.

`cpu-test:1` is a BYOD cluster env which uses `anyscale/ray:2.8.0`

`small-amd-cpu-only` is an AWS compute configuration which only uses small `t3a.xlarge` instances.
```yaml
      - csivanich/anyscale-cluster#dev:
          image: anyscale/ray:2.8.0
          env-name: cpu-test:1
          compute-name: small-amd-cpu-only
```

### Submit Job

With the cluster started, we can submit a job using standard Ray commands. We pass through several supporting environment variables.

The example assumes the Ray `working-dir` is the local directory, which may not be true for you.


```yaml
      - docker#v5.8.0:
          image: anyscale/ray:2.8.0
          entrypoint: ray
          environment:
            - RAY_ADDRESS
            - ANYSCALE_CLI_TOKEN
            - ANYSCALE_HOST
          command:
            - job
            - submit
            - --working-dir=.
            - --
            - python
            - job.py
```
