OpenCV Installation
========================

From the Ubuntu Repository
******************************************

1. Installation ::

    sudo apt update
    sudo apt install python3-opencv


2. Verify ::

    python3 -c "import cv2; print(cv2.__version__)"


From Source
******************************************

1. Install dependencies ::

    sudo apt install build-essential cmake git pkg-config libgtk-3-dev \
    libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
    libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev \
    gfortran openexr libatlas-base-dev python3-dev python3-numpy \
    libtbb2 libtbb-dev libdc1394-22-dev

2. Clone repos ::

    mkdir ~/opencv_build && cd ~/opencv_build
    git clone https://github.com/opencv/opencv.git
    git clone https://github.com/opencv/opencv_contrib.git

3. Create a temporary build directory ::

    cd ~/opencv_build/opencv
    mkdir build && cd build

Set up build with CMake ::
    
    cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_GENERATE_PKGCONFIG=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON ..

4. Start the compilation process ::

    make -j8

If you do not know the number of cores your processor, you can find it by typing nproc

5. Install OpenCV ::

    sudo make install

6. Verify ::

    pkg-config --modversion opencv4
    python3 -c "import cv2; print(cv2.__version__)"


