# hpl-2.3 for RISCV
## Qemu
## gcc 12
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
