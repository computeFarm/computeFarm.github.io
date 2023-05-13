# Worker Descriptions

Each worker in a ComputeFarm must describe its unique collection of
capabilities.

These worker descriptions will be contained in YAML files.

```yaml
# The main `workers` dictionary of compute farm workers.
# One key per worker (one or more workers).
# Each key provides the name of a given worker.
workers:

  # The name of a given worker (no spaces)
  workerName: 

    # The (linux) platform/architecture provided by this worker.
    # aarch64 | amd64 
    platform: aarch64 

    # A list of the capabilities provided by a worker.
    # Typically this will be a list of the command line tools installed in
    # this worker's container.
    capabilities:
      - gcc
      - g++
      - cmake
      - ninja

```
