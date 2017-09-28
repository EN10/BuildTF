Prebuilt Binaries:

https://github.com/lakshayg/tensorflow-build

Build:
    
    git clone https://github.com/tensorflow/tensorflow 
    cd tensorflow

Update:

    Git Pull

Bazel:

https://docs.bazel.build/versions/master/install-ubuntu.html#install-with-installer-ubuntu

https://github.com/bazelbuild/bazel/releases

    wget https://github.com/bazelbuild/bazel/releases/download/0.5.4/bazel-0.5.4-installer-linux-x86_64.sh
    
    sudo apt install pkg-config zip g++ zlib1g-dev unzip python
    
    chmod +x bazel-0.5.4-installer-linux-x86_64.sh
    ./bazel-0.5.4-installer-linux-x86_64.sh --user
    
    export PATH="$PATH:$HOME/bin"

Build Tensorflow:

    bazel build --config=opt --copt=-msse4.2 --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package
    
Ref:

https://github.com/EN10/TensorFlow-For-Poets