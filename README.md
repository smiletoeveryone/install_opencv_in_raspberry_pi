# install_opencv_in_raspberry_pi
![](https://github.com/smiletoeveryone/install_opencv_in_raspberry_pi/blob/master/cv_version.jpg)

1st section
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo reboot

$ sudo apt-get install build-essential cmake pkg-config

$ sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev

$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
$ sudo apt-get install libxvidcore-dev libx264-dev

$ sudo apt-get install libgtk2.0-dev

$ sudo apt-get install libatlas-base-dev gfortran

$ sudo apt-get install python2.7-dev python3-dev

2nd section - downloading opencv

$ wget -O opencv-3.2.0.zip https://sourceforge.net/projects/opencvlibrary/files/opencv-unix/3.2.0/opencv-3.2.0.zip/download

$ unzip opencv-3.2.0.zip

$ cd opencv-3.2.0

3rd section setup the environment for python

$ wget https://bootstrap.pypa.io/get-pip.py

$ sudo python get-pip.py

$ sudo pip install virtualenv virtualenvwrapper

$ sudo rm -rf ~/.cache/pip

$ vim ~/.profile ### add the 3 lines below in the end of the file

virtualenv and virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
$ source ~/.profile

#creat a virtual env that name is “cv” for python
$ mkvirtualenv cv -p python2
$ mkvirtualenv cv -p python3

check the steps above you are doing right
$ workon cv

$ pip install numpy

compile and install opencv
$ workon cv

$ cd ~/opencv-3.2.0/

$ mkdir build

$ cd build

$ cmake -D CMAKE_BUILD_TYPE=RELEASE \

-D CMAKE_INSTALL_PREFIX=/usr/local \

-D INSTALL_PYTHON_EXAMPLES=ON \

-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.2.0/modules \

-D BUILD_EXAMPLES=ON ..
$ make -j4

if you could not compile sucesssfully, please try again
$ make clean

$ make

for python2.7
$ cd ~/.virtualenvs/cv/lib/python2.7/site-packages/

$ sduo ln -s /usr/local/lib/python2.7/site-packages/cv2.so cv2.so

for python3
$ cd ~/.virtualenvs/cv/lib/python3.4/site-packages/

$ sudo ln -s /usr/local/lib/python3.7/site-packages/cv2.so cv2.so

4th section
test and check your opencv version
$ source ~/.profile

$ workon cv

$ python

>>> import cv2

>>> cv2.__version__
