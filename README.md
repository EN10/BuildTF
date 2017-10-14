# Build Tensorflow

* [Build Tensorflow](https://www.tensorflow.org/install/install_sources#clone_the_tensorflow_repository)

### Pip Install
Tested on cs50.io:  
`sudo pip install -U pip`  
`sudo pip install tensorflow`

### Prebuilt Binaries:

* [lakshayg](https://github.com/lakshayg/tensorflow-build)

* [mind](https://github.com/mind/wheels)

### Repo:
    
    git clone https://github.com/tensorflow/tensorflow 
    cd tensorflow

Update:

    git pull

### Bazel:

[Install Bazel](https://docs.bazel.build/versions/master/install-ubuntu.html#install-with-installer-ubuntu)

    sudo apt-get install openjdk-8-jdk

    echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
    curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

    sudo apt-get update && sudo apt-get install bazel
    sudo apt-get upgrade bazel

### Build Tensorflow:

    ./configure

    bazel build --config=opt --copt=-msse4.2 --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package

Compiles 3,415 files?
    
Error:

Killed non-responsive server process  
    
    bazel --batch build --config=opt --copt=-msse4.2 --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package
    
Python Configuration Error: 'PYTHON_BIN_PATH' environment variable is not set  
    
    ./configure

Build a `.whl` file:
    
    bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg

### Install Tensorflow

    sudo pip install --ignore-installed --upgrade tensorflow-1.3.0-cp27-cp27mu-linux_x86_64.whl

### Working Builds#

* [codenvy](https://github.com/mind/wheels/releases/download/tf1.3-cpu/tensorflow-1.3.0-cp27-cp27mu-linux_x86_64.whl)

Ref:

* https://github.com/EN10/TensorFlow-For-Poets

