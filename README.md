Prebuilt Binaries:

https://github.com/lakshayg/tensorflow-build

Build:
    
    git clone https://github.com/tensorflow/tensorflow 
    cd tensorflow

Update:

    Git Pull

Build Tensorflow:

    bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
    
Ref:

https://github.com/EN10/TensorFlow-For-Poets