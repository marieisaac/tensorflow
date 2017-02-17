# Installation

Some minor fixes for standard installation

## Ubuntu 16.04, Cuda 8.0, Cudnn 5.1, Anaconda2, GTX1070

### CUDA

Install CUDA 8.0 from the .deb package: https://yangcha.github.io/GTX-1080/ (the Nvidia driver should be included there and you don't need the separate ppa step)

### Tensorflow

Install from sources:
https://www.tensorflow.org/install/install_sources (bazel build takes some time, e.g. ~814 seconds on i7-7700K)

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
