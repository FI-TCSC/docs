
================
Caffe
================

Installing and running Caffe 
============================

[[http://caffe.berkeleyvision.org/][Caffe]] is the other main option for running deep neural network code. Installing and running it is a bit more complicated. The following contains installation instructions for the normal Merope queue using CPU_ONLY mode (no GPU support) - NOTE: You need to fix the paths to your own directory structure and user name):

# Log to the queue you're planning to run the stuff
[kamarain@merope ~]$ srun --partition=normal --pty -J "Joni's caffe compilation session" --mem=1024 --ntasks=1 --time=4:00:00 /bin/bash -i
srun: job 875851 queued and waiting for resources
srun: job 875851 has been allocated resources
[kamarain@me8 ~]$

# Local boost compilation
# Download: http://www.boost.org/
[kamarain@me8 ~]$ cd /home/kamarain/Work/ext/boost_1_56_0
[kamarain@me8 ~]$ ./bootstrap.sh
[kamarain@me8 boost_1_56_0]$ ./b2 --with-system --build-dir=./build --prefix=./install install

# Local gflags
# Download: https://github.com/schuhschuh/gflags
[kamarain@me8 gflags]$ cd /home/kamarain/Work/ext/gflags
[kamarain@me8 gflags]$ mkdir build; cd build
[kamarain@me8 build]$ module load cmake/2.8.12.2
[kamarain@me8 build]$ cmake ..
[kamarain@me8 build]$ ccmake ..
CMAKE_INSTALL_PREFIX             /home/kamarain/Work/ext/gflags/build/install
generate & exit
[kamarain@me8 build]$ make install

# Local glog
# Download: https://code.google.com/p/google-glog/
[kamarain@me8 build]$ cd /home/kamarain/Work/ext/glog-0.3.3
[kamarain@me8 glog-0.3.3]$ ./configure --prefix=/home/kamarain/Work/ext/glog-0.3.3/install
[kamarain@me8 glog-0.3.3]$ make install

# Local protobuf
# Download: https://code.google.com/p/protobuf/
[kamarain@me8 glog-0.3.3]$ cd /home/kamarain/Work/ext/protobuf
[kamarain@me8 protobuf]$ ./configure --prefix=/home/kamarain/Work/ext/protobuf/install --exec-prefix=/home/kamarain/Work/ext/protobuf/install
[kamarain@me8 protobuf]$ make install

# Local leveldb
# Download: https://code.google.com/p/leveldb/
[kamarain@me8 protobuf]$ cd /home/kamarain/Work/ext/leveldb
[kamarain@me8 leveldb]$ make

# Local OpenCV
# Download: http://opencv.org/
[kamarain@me8 leveldb]$ cd /home/kamarain/Work/ext/opencv-2.4.4
[kamarain@me8 opencv-2.4.4]$ mkdir build; cd build
[kamarain@me8 build]$ cmake ..
[kamarain@me8 build]$ ccmake ..
CMAKE_INSTALL_PREFIX             /home/kamarain/Work/ext/opencv-2.4.4/build/in
generate & exit
[kamarain@me8 build]$ make
[kamarain@me8 build]$ make install

# Local OpenCV WITH Python
# Do exactly like above except the cmake step:

cmake -DPYTHON_EXECUTABLE=/cvmfs/fgi.csc.fi/apps/sl6/python/2.7.3/bin/python -DPYTHON_LIBRARIES=/cvmfs/fgi.csc.fi/apps/sl6/python/2.7.3/lib/libpython2.7.so -DPYTHON_LIBRARY=/cvmfs/fgi.csc.fi/apps/sl6/python/2.7.3/lib/libpython2.7.so -DPYTHON_INCLUDE_DIR=/cvmfs/fgi.csc.fi/apps/sl6/python/2.7.3/include/python2.7 ..

# Local mdb
# GIT: git clone git@gitorious.org:mdb/mdb.git
[kamarain@me8 build]$ cd /home/kamarain/Work/ext/mdb/libraries/liblmdb
[kamarain@me8 liblmdb]$ make

# Local hdf5
# Download: ftp://ftp.hdfgroup.uiuc.edu/pub/outgoing/hdf5/snapshots 
[kamarain@me8 liblmdb]$ cd /home/kamarain/Work/ext/hdf5-1.9.195
[kamarain@me8 hdf5-1.9.195]$ ./configure --prefix=/home/kamarain/Work/ext/hdf5-1.9.195/install


# Finally, compile caffe
[kamarain@me8 ~]$ export PATH=$PATH:/home/kamarain/Work/ext/protobuf/install/bin/
[kamarain@me8 ~]$ cd /home/kamarain/Work/ext/caffe
[kamarain@me8 ~]$ ln -s /usr/lib64/libsnappy.so.1 libsnappy.so
[kamarain@me8 ~]$ ln -s /usr/lib64/atlas/libcblas.so.3 libcblas.so
[kamarain@me8 ~]$ ln -s /usr/lib64/atlas/libatlas.so.3 libatlas.so
edit Makefile.config:
CPU_ONLY := 1
INCLUDE_DIRS := \
              /home/kamarain/Work/ext/boost_1_56_0/install/include \
              /home/kamarain/Work/ext/gflags/build/install/include \
              /home/kamarain/Work/ext/glog-0.3.3/install/include \
              /home/kamarain/Work/ext/protobuf/install/include \
              /home/kamarain/Work/ext/ATLAS3.10.0/include \
              /home/kamarain/Work/ext/leveldb/include \
              /home/kamarain/Work/ext/opencv-2.4.4/build/install/include \
              /home/kamarain/Work/ext/hdf5-1.9.195/install/include \
              /home/kamarain/Work/ext/mdb/libraries/liblmdb
LIBRARY_DIRS := /home/kamarain/Work/ext/boost_1_56_0/install/lib \
             /home/kamarain/Work/ext/gflags/build/install/lib \
             /home/kamarain/Work/ext/glog-0.3.3/install/lib \
              /home/kamarain/Work/ext/protobuf/install/lib \
              /home/kamarain/Work/ext/leveldb/ \
              /home/kamarain/Work/ext/opencv-2.4.4/build/install/lib \
              /home/kamarain/Work/ext/hdf5-1.9.195/install/lib \
              /home/kamarain/Work/ext/mdb/libraries/liblmdb \
              /home/kamarain/Work/ext/caffe
[kamarain@me8 caffe]$ make
[kamarain@me8 caffe]$ export LD_LIBRARY_PATH=/home/kamarain/Work/ext/boost_1_56_0/install/lib:/home/kamarain/Work/ext/gflags/build/install/lib:/home/kamarain/Work/ext/glog-0.3.3/install/lib:/home/kamarain/Work/ext/protobuf/install/lib:/home/kamarain/Work/ext/leveldb/:/home/kamarain/Work/ext/opencv-2.4.4/build/install/lib:/home/kamarain/Work/ext/hdf5-1.9.195/install/lib:/home/kamarain/Work/ext/mdb/libraries/liblmdb:/home/kamarain/Work/ext/caffe
[kamarain@me8 caffe]$ cd build/tools
[kamarain@me8 caffe]$ ./caffe

## Ready to use the network !! ## 
