# Build Tensorflow

* [Build Tensorflow](https://www.tensorflow.org/install/install_sources#clone_the_tensorflow_repository)

### Pip Install
Tested on cs50.io:  
`sudo pip install -U pip`  
`sudo pip install tensorflow`

### Prebuilt Binaries:

* [EN10 - 1.4.0rc0](https://github.com/EN10/BuildTF/blob/master/tensorflow-1.4.0rc0-cp27-none-linux_x86_64.whl)  
Built in Docker: `docker pull ubuntu:trusty`

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

On Docker Trusty:

    apt update
    apt install git software-properties-common python-software-properties curl

On Ubuntu 14.04 LTS you'll have to use a PPA:
    
    sudo add-apt-repository ppa:webupd8team/java
    sudo apt update && sudo apt-get install oracle-java8-installer

    echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
    curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

    sudo apt update && sudo apt-get install bazel
    sudo apt upgrade bazel

### Build Tensorflow:

    sudo apt install python-numpy python-dev python-pip python-wheel
    
    ./configure

    bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package

May be required in Docker:

    sudo apt update
    sudo apt upgrade
    sudo apt install oracle-java8-set-default

**Performance :** `SSE4.1 SSE4.2 AVX AVX2 FMA`  

    bazel build --config=opt --copt=-msse4.2 --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package

Compiles 3,436 files?
    
Error:

Killed non-responsive server process  
    
    bazel --batch build --config=opt --copt=-msse4.2 --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package
    
Python Configuration Error: 'PYTHON_BIN_PATH' environment variable is not set  
    
    ./configure

Build a `.whl` file:
    
    bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg

### Install Tensorflow

    sudo pip install --ignore-installed --upgrade tensorflow-1.4.0-cp27-none-linux_x86_64.whl

### Test Build

    python run.py

### Working Builds

* [codenvy](https://github.com/mind/wheels/releases/download/tf1.3-cpu/tensorflow-1.3.0-cp27-cp27mu-linux_x86_64.whl)

Ref:

* https://github.com/EN10/TensorFlow-For-Poets