# Installation

Some minor fixes for standard installation

## Ubuntu 16.04, Cuda 8.0, Cudnn 5.1, Anaconda2, GTX1070

### CUDA

Install CUDA 8.0 from the .deb package: https://yangcha.github.io/GTX-1080/ (the Nvidia driver should be included there and you don't need the separate ppa step).

#### Make sure that CUDA works

By for example compiling the CUDA samples and running the deviceQuery `./deviceQuery` which should for example return something like that with GTX1070:

```
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "GeForce GTX 1070"
  CUDA Driver Version / Runtime Version          8.0 / 8.0
  CUDA Capability Major/Minor version number:    6.1
  Total amount of global memory:                 8113 MBytes (8506769408 bytes)
  (15) Multiprocessors, (128) CUDA Cores/MP:     1920 CUDA Cores
  GPU Max Clock rate:                            1683 MHz (1.68 GHz)
  Memory Clock rate:                             4004 Mhz
  Memory Bus Width:                              256-bit
  L2 Cache Size:                                 2097152 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384)
  Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 1 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 8.0, CUDA Runtime Version = 8.0, NumDevs = 1, Device0 = GeForce GTX 1070
Result = PASS
```

or 1080ti

```
Device 0: "GeForce GTX 1080 Ti"
  CUDA Driver Version / Runtime Version          8.0 / 8.0
  CUDA Capability Major/Minor version number:    6.1
  Total amount of global memory:                 11164 MBytes (11706630144 bytes)
  (28) Multiprocessors, (128) CUDA Cores/MP:     3584 CUDA Cores
  GPU Max Clock rate:                            1633 MHz (1.63 GHz)
  Memory Clock rate:                             5505 Mhz
  Memory Bus Width:                              352-bit
  L2 Cache Size:                                 2883584 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384)
  Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 1 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 8.0, CUDA Runtime Version = 8.0, NumDevs = 1, Device0 = GeForce GTX 1080 Ti
Result = PASS

```

or with low-cost GT 730 

```
Device 0: "GeForce GT 730"
  CUDA Driver Version / Runtime Version          8.0 / 8.0
  CUDA Capability Major/Minor version number:    3.5
  Total amount of global memory:                 2001 MBytes (2098462720 bytes)
  ( 2) Multiprocessors, (192) CUDA Cores/MP:     384 CUDA Cores
  GPU Max Clock rate:                            902 MHz (0.90 GHz)
  Memory Clock rate:                             900 Mhz
  Memory Bus Width:                              64-bit
  L2 Cache Size:                                 524288 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65536), 3D=(4096, 4096, 4096)
  Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 1 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 1 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 8.0, CUDA Runtime Version = 8.0, NumDevs = 1, Device0 = GeForce GT 730
Result = PASS
```


If `Result = FAIL` you will start getting weird errors in TensorFlow pointing to missing `ImportError: libnvidia-fatbinaryloader.so`, `'CUDA driver version is insufficient for CUDA runtime version`, etc.

### Tensorflow

Install from sources:
https://www.tensorflow.org/install/install_sources (bazel build takes some time, e.g. ~*814 seconds* on Intel i7-7700K, and ~*3000 seconds* on AMD A8-7600)

```bash
./configure 
bazel build --config=opt --config=cuda //tensorflow/tools/pip_package:build_pip_package 
bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
~/anaconda2/bin/pip install /tmp/tensorflow_pkg/tensorflow-1.0.0-cp27-cp27mu-linux_x86_64.whl 
```
**NOTE!** Now install without `sudo` and if your `pip`s must match to the Python version that you used (now this example uis with Python2.7 from Anaconda, the Python3.6 being default for pip).

#### Issues

When trying `python2` and `import tensorflow as tf`

```bash
ImportError: anaconda2/bin/../lib/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by anaconda2/lib/python2.7/site-packages/tensorflow/python/_pywrap_tensorflow.so)
```

The GCC's shipped with Anaconda and Ubuntu 16.04 are not exactly the same as discussed there: http://askubuntu.com/questions/575505/glibcxx-3-4-20-not-found-how-to-fix-this-error

```bash
strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep CXXABI_1.3.8
CXXABI_1.3.8
```

Compare to (with no CXXABI_1.3.8)

```bash
strings anaconda2/bin/../lib/libstdc++.so.6 | grep CXXABI_1.3.8
```

So you have to link the GCC of system lib in Anaconda, as followed:

```bash
cd ~/anaconda2/lib
mv -vf libstdc++.so.6 libstdc++.so.6.old
ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 ./libstdc++.so.6
```
