# hpl-2.3 for RISCV
## Qemu
'''

qemu-system-riscv64 \\

-cpu rv64,v=true,vlen=256,vext_spec=v1.0 \\

-machine virt -nographic -m 16G -smp 8 \\

-bios /usr/lib/riscv64-linux-gnu/opensbi/generic/fw_jump.elf \\

-kernel /usr/lib/u-boot/qemu-riscv64_smode/uboot.elf \\

-device virtio-net-device,netdev=eth0 -netdev user,id=eth0,hostfwd=tcp::2222-:22 \\

-drive file=ubuntu-22.04.1-preinstalled-server-riscv64+unmatched.img,format=raw,if=virtio

'''

## gcc 12
'''

git clone https://github.com/riscv/riscv-gnu-toolchain -b rvv-next

cd riscv-gcc

git checkout -b riscv-gcc-rvv-next

git pull

./configure --prefix=/opt/riscv

make linux

'''

##  OpenMPI 4.1.4
'''

wget https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.4.tar.gz

export PATH=/opt/riscv/bin:$PATH

mkdir build

../configure --prefix=/home/ubuntu/hpl/install

make -j 8 all

make install

'''

##  OpenBlas
'''

git clone https://github.com/xianyi/OpenBLAS.git

make TARGET=RISCV64_GENERIC

make PREFIX=~/hpl/out install

'''

## HPL
'''

make arch=Linux_RISCV

export LD_LIBRARY_PATH=~/hpl/install/lib

export PATH=~/hpl/install/bin:$PATH

cd bin/Linux_RISCV/

mpirun -n 4 ./xhpl

'''
