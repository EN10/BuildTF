Prebuilt Binaries:

https://github.com/lakshayg/tensorflow-build

Build:
    
    git clone https://github.com/tensorflow/tensorflow 
    cd tensorflow

Update:

    Git Pull

Bazel:

https://docs.bazel.build/versions/master/install-ubuntu.html#install-with-installer-ubuntu

    sudo apt-get install openjdk-8-jdk

    echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
    curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

    sudo apt-get update && sudo apt-get install bazel
    
    sudo apt-get upgrade bazel

Build Tensorflow:

    bazel build --config=opt --copt=-msse4.2 --copt=-mavx2 --copt=-mfma //tensorflow/tools/pip_package:build_pip_package
    
Ref:

https://github.com/EN10/TensorFlow-For-Poets