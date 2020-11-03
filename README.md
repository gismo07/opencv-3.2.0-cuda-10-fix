# opencv-3.2.0-cuda-10-fix
Fix to build OpenCV 3.2.0 with newer CUDA versions.  
Based on: https://stackoverflow.com/questions/46584000/cmake-error-variables-are-set-to-notfound 

Tested on Ubuntu 18.04 with CUDA 10.2

## Apply fix
Get OpenCV and extra modules:
```shell
export CV_VERSION=3.2.0

git clone https://github.com/opencv/opencv.git -b $CV_VERSION &&\
git clone https://github.com/opencv/opencv_contrib.git -b $CV_VERSION
```

Get fix:
```shell
git clone https://github.com/gismo07/opencv-3.2.0-cuda-10-fix.git
```

Apply fix:
```shell
cp ./opencv-3.2.0-cuda-10-fix/FindCUDA.cmake ./opencv/cmake/FindCUDA.cmake
cp ./opencv-3.2.0-cuda-10-fix/OpenCVDetectCUDA.cmake ./opencv/cmake/OpenCVDetectCUDA.cmake 
sed -i "50i #include <cuda_fp16.h>" ./opencv/modules/cudev/include/opencv2/cudev/common.hpp 
```
