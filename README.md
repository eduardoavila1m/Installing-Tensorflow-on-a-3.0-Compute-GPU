# Installing Tensorflow on a 3.0 Compute GPU - OS Windows 10

## Hardware Set Up

GTX 770M GPU

Intel Core I7-4700HQ

## NVIDIA Drivers

This step is crucial to get Tensorflow working on GPU other whise the Libraries wont compile. Each GPU has its own driver. 

## CUDA Toolkit - 10.1.105_418.96

To install CUDA toolkit is very important to choose the correct version. The version needs to correspont to the one that was used when the tensorflow library was build from source files to be ompatible with 3.0 compute capability graphic cards. A table with the specific Tensorflow version, CUDA Toolkit version and CuDNN version can be found at the following link:

https://github.com/fo40225/tensorflow-windows-wheel

Is very important to note that this does not follow the recomendations found at the Tensorflow official website. So, do not install anything in advanced before reviewing the specific versions.

The Cuda Toolkit version that corresponds with tensorflow 1.13.1 is 10.1.105_418.96. It can be downloaded from: https://developer.nvidia.com/cuda-10.1-download-archive-base?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal .


### Tensorflow 1.13.1

The cuda Toolkit Version that works with tensorflow 1.13.1 can be downloaded from the following link.

https://developer.nvidia.com/cuda-10.1-download-archive-base?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal

## CuDNN

The CuDNN library 


## Tensor-Flow Version Compatibility Table

https://www.tensorflow.org/install/source_windows#gpu

