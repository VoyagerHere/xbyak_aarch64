sudo apt update
sudo apt install -y git cmake build-essential gcc-aarch64-linux-gnu g++-aarch64-linux-gnu
sudo apt install gcc-aarch64-linux-gnu
sudo apt install g++-aarch64-linux-gnu

mkdir build && cd build

cmake .. \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=aarch64 \
  -DCMAKE_C_COMPILER=aarch64-linux-gnu-gcc \
  -DCMAKE_CXX_COMPILER=aarch64-linux-gnu-g++ \
  -DCMAKE_BUILD_TYPE=Release

make -j$(nproc)


sudo apt install qemu-user
qemu-aarch64 ./binary
sudo make install