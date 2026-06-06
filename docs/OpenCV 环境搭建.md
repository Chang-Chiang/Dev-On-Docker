# OpenCV 环境搭建

## 目录

- [OpenCV安装：使用包管理器安装](#使用包管理器安装)
- [OpenCV安装：从源码安装](#从源码安装)
- [测试程序](#测试程序)
- [参考](#参考)

## 使用包管理器安装

- 更新包

  ```shell
  sudo apt update
  sudo apt upgrade
  ```

- 安装 opencv 库

  ```shell
  sudo apt install libopencv-dev
  ```

- 查看 opencv 版本

  ```shell
  pkg-config --modversion opencv4  
  4.6.0
  ```

- 配置环境变量

  ```shell
  cd /usr/local/lib
  sudo mkdir pkgconfig
  cd pkgconfig
  sudo touch opencv.pc
  ```

  - 编辑 opencv.pc 文件

    ```
    prefix=/usr/local
    exec_prefix=${prefix}
    includedir=${prefix}/include
    libdir=${exec_prefix}/lib
    
    Name: opencv
    Description: The opencv library
    Version:4.6.0
    Cflags: -I${includedir}/opencv4
    Libs: -L${libdir} -lopencv_shape -lopencv_stitching -lopencv_objdetect -lopencv_superres -lopencv_videostab -lopencv_calib3d -lopencv_features2d -lopencv_highgui -lopencv_videoio -lopencv_imgcodecs -lopencv_video -lopencv_photo -lopencv_ml -lopencv_imgproc -lopencv_flann  -lopencv_core
    ~                                               
    ```

  - 配置文件导入环境变量

    ```shell
    export  PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
    ```

- 编写测试代码

  官网代码

  https://github.com/opencv/opencv/tree/4.x/samples/cpp/example_cmake

- g++ 编译

  ```shell
  g++ HelloOpenCV.cpp -o HelloOpenCV.o -c -Wall -I/usr/local/include/opencv4
  g++ example.o -o opencv_example -L/usr/local/lib -lopencv_shape -lopencv_stitching -lopencv_objdetect -lopencv_superres -lopencv_videostab -lopencv_calib3d -lopencv_features2d -lopencv_highgui -lopencv_videoio -lopencv_imgcodecs -lopencv_video -lopencv_photo -lopencv_ml -lopencv_imgproc -lopencv_flann -lopencv_core
  ```

  

## 从源码安装

## 参考

- https://blog.csdn.net/whitephantom1/article/details/136406214
- https://cloud.baidu.com/article/2917407
- https://blog.csdn.net/PecoHe/article/details/97476135