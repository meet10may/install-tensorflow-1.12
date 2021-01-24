# Install-tensorflow-1.12 with CUDA 9.0

This will allow you to install tensorflow-1.12 in Ubuntu 16.04. Please note, that CUDA version and driver need to be compatibile. Check the compatiility in [stackoverflow post](https://stackoverflow.com/questions/30820513/what-is-the-correct-version-of-cuda-for-my-nvidia-driver/30820690#30820690) for more detail.

Assuming that nvidia drivers are not installed.

``ADD iMAGE``

Install NVIDIA drivers. 

``sudo apt-get update``

``sudo apt-get install nvidia-384 nvidia-modprobe``

``ADD IMAGE``

This will install the CUDA driver 384. 
``ADD IMAGE``

Install CUDA 9.0
``mkdir ~/nvidia-install ; cd ~/nvidia-install``

``wget -c https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda_9.0.176_384.81_linux-run``
``chmod +x cuda_9.0.176_384.81_linux-run``
``./cuda_9.0.176_384.81_linux-run --extract=$HOME/nvidia-install``
``sudo ./cuda-linux.9.0.176-22781540.run``

Add paths to ~/.bashrc file
``export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}``
``export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}``
``export CUDA_HOME=/usr/local/cuda``

Update bashrc file
``source ~/.bashrc``
``sudo ldconfig``

Download runtime and developer library deb's from https://developer.nvidia.com/rdp/cudnn-download. You may have to register yourself, but it is free and straightforward. Download two files,`libcudnn7_7.4.1.5-1+cuda9.0_amd64.deb` and `libcudnn7-dev_7.4.1.5-1+cuda9.0_amd64.deb`

``sudo dpkg -i libcudnn7_7.4.1.5-1+cuda9.0_amd64.deb``
``sudo dpkg -i libcudnn7-dev_7.4.1.5-1+cuda9.0_amd64.deb``

By now you should have installed the CUDA 9.0. If you are ready to install tensorflow 1.12.

Create a new conda environment and install tensorflow 1.12
``conda create -name tf-1.12 python=3.6``
``source activate tf-1.12``
``pip install tensorflow-gpu==1.12``

Test the installation
``python3 -c "import tensorflow as tf; print(tf.__version__)"``

Your installation must be successful!
