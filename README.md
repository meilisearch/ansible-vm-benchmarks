# ansible-vm-benchmarks
Ansible Playbook to index datasets on several typology of Instance
on a specific Meilisearch version/commit.

## Prerequisites
### Ansible
Ansible needs to be installed only locally.

### Benchmark Instances
To be able to run benchmarks on instances, you need to be able to connect to the Instances via ssh.
All the instances needs to run on the same OS.

### Compilation
The Meilisearch specified version needs to be compiled on one of the benchmark Instance.
`rust` and `git` have to be installed on this instance.

Meilisearch repository has to be cloned on this instance.

This Instance will be assigned as the compilation instance.

### Datasets
No dataset is provided, they only need to be present locally.

**Format:** `json`

#### Batched datasets
To run a batched indexing,
the dataset only needs to be chunked in several `json` files in the same directory.

## Configuration

### `host` file
A host file describing the instances is needed to run the script.
An example is provided in this repository: `host.example`

### `config.yaml` file
A config file is needed in the current directory to run the script.
An example is provided in this repository: `config.example.yaml`

## Run
`ansible-playbook -v -i <HOST_FILE_PATH> benchmark-meilisearch.yaml`

the results of the benchmark is put into a local `results` directory.
If one of the file is empty it means that the indexing crashed/failed/be killed.

## Warning
This script is not meant to be used in production, it is just a manual tool.
