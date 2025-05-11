# nvsmifs

A (user-)friendly wrapper to `nvidia-smi` forked from https://github.com/pmav99 to include fan speed and power_draw support.

It can be used to filter the GPUs based on resource usage (e.g. to choose the least utilized GPU on a multi-GPU system).

## Usage

### CLI

```
nvsmifs --help
nvsmifs ls --help
nvsmifs ps --help
```

### As a library

```
import nvsmifs

nvsmifs.get_gpus()
nvsmifs.get_available_gpus()
nvsmifs.get_gpu_processes()
nvsmifs.get
```

## Easy Function

```
import nvsmifs

# Get all GPUs

def gpu_info():
    for gpu in nvsmifs.get_gpus():
        if gpu.display_active == 'Enabled':
            gpu_info =f"{gpu.id} {gpu.power_draw} {gpu.name} {gpu.temperature} {gpu.fan_speed} {gpu.gpu_util}"
            print(gpu_info)
gpu_info()
```

## Prerequisites

- An nvidia GPU
- `nvidia-smi`
- Python 2.7 or 3.6+

## Installation

### pipx

The recommended installation method is [pipx](https://github.com/pipxproject/pipx).
More specifically, you can install `nvsmifs` for your user with:

``` shell
pipx install nvsmifs
```

The above command will create a virtual environment in `~/.local/pipx/venvs/nvsmifs` and
add the `nvsmifs` executable in `~/.local/bin`.

### pip

Alternatively you can use good old `pip` but this is more fragile than `pipx`:

```
pip install --user nvsmifs
```
