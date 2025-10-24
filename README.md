# Build and install llama.cpp for CUDA and cuBLAS.

The script `install-llama.cpp-cuda` is intended to be run on
Fedora 42. It builds llama.cpp against CUDA Toolkit and Intel OneAPI
HPC Toolkit. `llama-server`, `llama-cli`, et al. and their shared
libraries are installed (properly) under */usr/local*.

To run the llama.cpp commands, add Intel oneAPI library paths to
LD_LIBRARY_PATH, e.g.,

```
: ${ONEAPI_ROOT:='/opt/intel/oneapi'}
source ${ONEAPI_ROOT}/setvars.sh
llama-server ...
```

The `asdf` version manager is installed as necessary to provide a
local Python v3.11. Shell init files (e.g., ~/.bashrc,
~/.bash_profile) are not modified. To benefit from `asdf`, add to
them:

```
: ${ASDF_DATA_DIR:="${HOME}/.asdf"}

export PATH=${ASDF_DATA_DIR}/shims:${PATH}:${HOME}/bin
```

NB: The latest CUDA Toolkit (currently 13.0) and Intel OneAPI HPC
Toolkit (currently 2025.3) are installed and used to build llama.cpp.
To build vLLM, CUDA Toolkit 12.9 might be required. That's okay - CUDA
Toolkits 13.0 and 12.9 can coexist.

NB: The NVIDIA Ampere architecture (CUDA GPU Compute Capability 8.6)
is hardcoded in the script `install-llama.cpp-cuda`.  To change this,
refer to NVIDIA's [CUDA GPUs](https://developer.nvidia.com/cuda-gpus)
page and update the line:

```
    -DCMAKE_CUDA_ARCHITECTURES="86"
```

to reflect your GPU's Compute Capability. Several architectures can be
added as a semicolon-separated list (e.g., "86;89").
