# TensorFlowGPU_Install_Instructions
TensorFlow is the most popular open-source machine learning framework. This guide will show you the steps required to install the framework on Nvidia GPU.
## Step 1
Go to System Settings->Software & Updates->Additional Drivers. Choose the Nvidia drivers(default is Nouveau). Reboot. 
Check if the Nouveau are loading or not.

`lsmod | grep nouveau`
## Step 2 - Install Cuda 9.0
### Install required packages.

`sudo apt-get install openjdk-8-jdk git python-dev python3-dev python-numpy python3-numpy build-essential python-pip python3-pip python-virtualenv swig python-wheel libcurl3-dev`  

### Install Cuda 9.0

`curl -O http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.0.176-1_amd64.deb`

Add the key

`sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub`

Install

`sudo dpkg -i ./cuda-repo-ubuntu1604_9.0.176-1_amd64.deb`

`sudo apt-get update`

`sudo apt-get install cuda-9-0`

#### Reboot.

## Step 3 - Check if Nvidia Driver is installed or not.

`nvidia-smi`

## Step 4 - Install cudann.

`wget https://s3.amazonaws.com/open-source-william-falcon/cudnn-9.0-linux-x64-v7.1.tgz`

`sudo tar -xzvf cudnn-9.0-linux-x64-v7.1.tgz`

`sudo cp cuda/include/cudnn.h /usr/local/cuda/include`

`sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64`

`sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*`

## Step 5 - Edit bashrc

`sudo vi ~/.bashrc`

Add the following lines.

> export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"

> export CUDA_HOME=/usr/local/cuda

Source bashrc file.

`source ~/.bashrc`

## Step 6 - Install TensorFlow.

`pip3 install tensorflow-gpu`
`
