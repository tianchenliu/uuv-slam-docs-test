TensorFlow 2 Installation
=============================

Install Anaconda (Optional)
----------------------------

Create a new virtual env: ::

    conda create -n env1 python=3.7

Remove an env: ::

    conda remove --name env1 --all

List all envs: ::

    conda env List
    conda info --envs

List packages installed: ::

    conda List


Install TensorFlow
--------------------

Run: ::

    pip install tensorflow

Verify installation: ::

    python -c "import tensorflow as tf; print(tf.__version__)"

GPU issue: if reporting missing library files, such as: ::

    'Could not load dynamic library '...'; dlerror: ...'

Install:

    - Nvidia driver
    - CUDA Toolkit v10.1
    - CuDNN 7.6.5

CuDNN files unzipped into <INSTALL_PATH>/NVIDIA GPU Computing Toolkit/CUDA/v10.1/ (default: C:/Program Files/)

Environment setup:

    - 'Edit the system environment variables'
    - Click 'Path'-->'Edit'
    - Add following paths: ::

        <INSTALL_PATH>/NVIDIA GPU Computing Toolkit/CUDA/v10.1/bin
        <INSTALL_PATH>/NVIDIA GPU Computing Toolkit/CUDA/v10.1/libnvvp
        <INSTALL_PATH>/NVIDIA GPU Computing Toolkit/CUDA/v10.1/extras/CUPTI/libx64
        # <INSTALL_PATH>/NVIDIA GPU Computing Toolkit/CUDA/v10.1/cuda/bin


For latest version (version >= 2.4.0), install: 

    - Nvidia driver > 450.x
    - CUDA Toolkit v11
    - CuDNN 8.0.4
    - Optional: TensorRT 6.0

