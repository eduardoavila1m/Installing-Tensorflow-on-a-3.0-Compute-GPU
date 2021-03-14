# Installing Tensorflow on a 3.0 Compute GPU - OS Windows 10

## Hardware Set Up

GTX 770M GPU

Intel Core I7-4700HQ

## NVIDIA Drivers

This step is crucial to get Tensorflow working on GPU other whise the Libraries wont compile. Each GPU has its own driver.

Navigate to the following web site

https://www.nvidia.com/en-gb/geforce/drivers/

Select the parameters of the specific graphics card. For GeForce GTX 770M the following parameters are the following.

Product Type: GeForce

Product Series: GeForce 700M Series (Notebook)

Product: GeForce GTX 770M

Operating System: Windows 10 64-bit

Download Type: Game Ready Driver

Dwonload Driver Version: 425.31 - Release Date (2019 April 11)

## CUDA Toolkit - 10.1.105_418.96

To install CUDA toolkit is very important to choose the correct version. The version needs to correspont to the one that was used when the tensorflow library was build from source files to be ompatible with 3.0 compute capability graphic cards. A table with the specific Tensorflow version, CUDA Toolkit version and CuDNN version can be found at the following link:

https://github.com/fo40225/tensorflow-windows-wheel

Is very important to note that this does not follow the recomendations found at the Tensorflow official website. So, do not install anything in advanced before reviewing the specific versions.

The Cuda Toolkit version that corresponds with tensorflow 1.13.1 is CUDA Toolkit 10.1 released on (Feb 2019), version 10.1.105_418.96. It can be downloaded from: https://developer.nvidia.com/cuda-10.1-download-archive-base?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal .

If a different version s required, the specific version can be found on NVIDIA CUDA Toolkin Archive. 

https://developer.nvidia.com/cuda-toolkit-archive

## CuDNN - 7.5.0.56

### Download CuDNN

The CuDNN library that works with this precompiled version of tensorflow is also very specific. Download cuDNN v7.5.0 released on (Feb 25, 2019), for CUDA 10.1 at the following link: https://developer.nvidia.com/rdp/cudnn-archive#a-collapse751-101.

If a different version of CuDNN is required it can be found at NVIDIA CuDNN Archive.

https://developer.nvidia.com/rdp/cudnn-archive

### install Library *.dll files 

Copy <cuDNN directory>\cuda\bin\*.dll to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vxx.x\bin
  
Copy <cuDNN directory>\cuda\include\*.h to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vxx.x\include
  
Copy <cuDNN directory>\cuda\lib\x64\*.lib to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vxx.x\lib\x64
  
### Update environmental variables
  
Open Control Panel > System and Security > System > Advanced System Settings.

Click Environment Variables at the bottom of the window.

In the new window and in the System variables pane, select the Path variable and click Edit in the System variables pane.

![image](https://user-images.githubusercontent.com/38021152/111083959-2d3ae880-8508-11eb-9d62-3101a460ddfd.png)

You should see two CUDA entries already listed

![image](https://user-images.githubusercontent.com/38021152/111083973-4479d600-8508-11eb-804c-051de0b234b9.png)

If you do not see these listed, add the following directories to this Path list (where vxx.x is your CUDA version number):

    C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vxx.x\bin
    C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\vxx.x\libnvvp

Click OK on the three pop-up windows to close out of the System Properties.


## Tensorflow 1.13.1 - Pre-built wheel file

Tensorflow library can not be installed directly from pip or conda. A pre-built tensorflow wheel specifiaclly for graphic cards with 3.0 compute capability is required. The wheel file of this version can be found in: https://github.com/fo40225/tensorflow-windows-wheel/blob/master/1.13.1/py37/GPU/cuda101cudnn75avx2/tensorflow_gpu-1.13.1-cp37-cp37m-win_amd64.7z.001  (NOTE: If this link is not found any more a copy of the wheel file has been saved in the external hard-drive.)

Is important to take into consideration that the CPU must suport AVX2. Intel core I7-4700HQ supports AVX2.

## Install Tensorflow

### Create new environment

conda create -n tensorflow-gpu python=3.7

### Install the library

navigate to the directory containing teh whell file.

conda activate tensorflow-gpu

pip install --ignore-installed --upgrade tensorflow_gpu-1.13.1-cp37-cp37m-win_amd64.whl

## Testing Tensorflow

import tensorflow as tf

from tensorflow.python.client import device_lib

print (tf.__version__)

print(tf.test.is_built_with_cuda())

device_lib.list_local_devices()

## For GPUs with 3.5 Compute Capability or Higher

### Pre Build Tensorflow Wheel Files

Specific official prebuild wheel files for pip install can be found in the following table at link:

https://www.tensorflow.org/install/pip#package-location

### Tensor-Flow Version Compatibility Table

https://www.tensorflow.org/install/source_windows#gpu

## References

https://shawnhymel.com/1961/how-to-install-tensorflow-with-gpu-support-on-windows/

https://medium.com/@naarkie/using-tensorflow-gpu-on-a-compute-3-0-graphics-card-in-windows-4184f4228fe9

