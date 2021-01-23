### FROM https://gist.github.com/automata/09fd4e1e64118dda4a79559898dd5022

# install-tensorflow-1.12
sudo apt-get install nvidia-384 nvidia-modprobe

## Get URL from https://developer.nvidia.com/cuda-downloads
mkdir ~/nvidia-install ; cd ~/nvidia-install
wget -c https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda_9.0.176_384.81_linux-run
chmod +x cuda_9.0.176_384.81_linux-run
./cuda_9.0.176_384.81_linux-run --extract=$HOME/nvidia-install
sudo ./cuda-linux.9.0.176-22781540.run
Add to ~/.bashrc:
   
   export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
   export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
   export CUDA_HOME=/usr/local/cuda
source ~/.bashrc
sudo ldconfig

### Download runtime and developer library deb's from https://developer.nvidia.com/rdp/cudnn-download
sudo dpkg -i libcudnn7_7.4.1.5-1+cuda9.0_amd64.deb
sudo dpkg -i libcudnn7-dev_7.4.1.5-1+cuda9.0_amd64.deb

### Install Anaconda
### Create conda environment

### pip install tensorflow-gpu==1.12
