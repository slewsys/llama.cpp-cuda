# Build and install llama.cpp for CUDA and cuBLAS.

These scripts are intended to be run on Fedora 42. They build and
install the **llama.cpp** LLM inference suite with support for Nvidia
CUDA and Intel oneAPI (HPC) Toolkits. `llama-server`, `llama-cli`, et
al. and their shared libraries are installed (properly) under
*/usr/local*.

[Nvidia CUDA Toolkit](https://developer.nvidia.com/cuda/toolkit)
and
[Intel oneAPI HPC Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/hpc-toolkit.html)
are installed as needed along with
[asdf](https://asdf-vm.com/)
version manager to provide a local Python and golang. Shell init files
(e.g., *~/.bashrc*, *~/.bash_profile*) are **not** modified. To benefit
from `asdf`, add its install directory (*${HOME}/bin*) and
shims path (*${HOME}/.asdf/shims*) to the shell init files, e.g.:

```
: ${ASDF_DATA_DIR:="${HOME}/.asdf"}

export PATH=${ASDF_DATA_DIR}/shims:${PATH}:${HOME}/bin
```
