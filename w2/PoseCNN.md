## problems

### 1

```
Traceback (most recent call last):
  File "/home/lcy/FURP/Pointnet_Pointnet2_pytorch/test_partseg.py", line 167, in <module>
    main(args)
  File "/home/lcy/FURP/Pointnet_Pointnet2_pytorch/test_partseg.py", line 153, in main
    np.array(total_correct_class) / np.array(total_seen_class, dtype=np.float))
                                                                     ^^^^^^^^
  File "/home/lcy/envmc1/lib/python3.12/site-packages/numpy/__init__.py", line 324, in __getattr__
    raise AttributeError(__former_attrs__[attr])
AttributeError: module 'numpy' has no attribute 'float'.
`np.float` was a deprecated alias for the builtin `float`. To avoid this error in existing code, use `float` by itself. Doing this will not modify any behavior and is safe. If you specifically wanted the numpy scalar type, use `np.float64` here.
The aliases was originally deprecated in NumPy 1.20; for more details and guidance see the original release note at:
    https://numpy.org/devdocs/release/1.20.0-notes.html#deprecations. Did you mean: 'cfloat'?
```
fix: np.float => float

### 2
```
from distutils.core import setup
from distutils.extension import Extension
```

fix: `from setuptools import setup, Extension`

### 3

```        extra_compile_args={'gcc': ["-Wno-unused-function"],
                            'nvcc': ['-arch=sm_35',
                                     '--ptxas-options=-v',
                                     '-c',
                                     '--compiler-options',
                                     "'-fPIC'"]},

```

fix:`sm_35`=>`sm_89`

### 4

/usr/local/include/eigen3
/usr/include/eigen3

kinect_fusion/kfusion.cpp:1281:10: fatal error: numpy/arrayobject.h: No such file or directory
 1281 | #include "numpy/arrayobject.h"
      |          ^~~~~~~~~~~~~~~~~~~~~
compilation terminated.
error: command '/usr/bin/x86_64-linux-gnu-gcc' failed with exit code 1

`'/usr/local/include/eigen3'`=>`'/usr/include/eigen3'`


### 5

/home/lcy/envmc1/lib/python3.12/site-packages/tensorflow/include/absl/base/policy_checks.h:79:2: error: #error "C++ versions less than C++14 are not supported."

fix 1 : ~~`pip install tensorflow==1.2.0`~~

fix 2 : ~~`pip install tensorflow-1.2.0-cp36-cp36m-manylinux1_x86_64`~~

fix 3: install old version of tensorflow(not finished)
```npm install -g @bazel/bazelisk
export GIT_SSL_NO_VERIFY=1
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
git checkout v1.2.1
```
  - issue: `ERROR: Config value 'cuda' is not defined in any .rc file`

  - fix 4: install old version of barzel

    - issue:`E: Unable to locate package bazel-0.4.5
E: Couldn't find any package by glob 'bazel-0.4.5'`
