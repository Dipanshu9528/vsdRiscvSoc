# Task 1
The following commands were executed in sequence starting from home directory:

```
mkdir riscv_toolchain && cd riscv_toolchain
mkdir riscv_gnu
git clone https://github.com/riscv-collab/riscv-gnu-toolchain.git
cd riscv-gnu-toolchain
mkdir build && cd build
echo 'export PATH="$HOME/riscv_toolchain/riscv_gnu/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
../configure --prefix=/home/wyx_2/riscv_toolchain/riscv_gnu --enable-multilib
make
cd ../..
git clone https://github.com/riscv-software-src/riscv-isa-sim.git
cd riscv-isa-sim
mkdir build && cd build
../configure --prefix=/home/wyx_2/riscv_toolchain/riscv_gnu
make
sudo make install
cd ../..
git clone https://github.com/riscv-software-src/riscv-pk.git
cd riscv-pk
mkdir build && cd build
../configure --prefix=/home/wyx_2/riscv_toolchain/riscv_gnu --host=riscv64-unknown-elf
make
make install
```

Compilation command:
```
riscv64-unknown-elf-gcc -O2 -Wall -march=rv64imac -mabi=lp64 -DUSERNAME="$(id -un)" -DHOSTNAME="$(hostname -s)" unique_test.c -o unique_test
```

Compilation Results are as follows:
```
RISC-V Uniqueness Check
User: wyx_2
Host: wyx-Precision-3680-2
UniqueID: 0xee2082017962e432
GCC_VLEN: 6

```
