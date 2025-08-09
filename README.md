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

#Task 2

Spike Version:
```
Spike RISC-V ISA Simulator 1.1.1-dev
```
GCC Version:
```
Using built-in specs.
COLLECT_GCC=riscv64-unknown-elf-gcc
COLLECT_LTO_WRAPPER=/home/wyx_2/riscv_toolchain/riscv_gnu/libexec/gcc/riscv64-unknown-elf/15.1.0/lto-wrapper
Target: riscv64-unknown-elf
Configured with: /home/wyx_2/riscv_toolchain/riscv-gnu-toolchain/build/../gcc/configure --target=riscv64-unknown-elf --prefix=/home/wyx_2/riscv_toolchain/riscv_gnu --disable-shared --disable-threads --enable-languages=c,c++ --with-pkgversion= --with-system-zlib --enable-tls --with-newlib --with-sysroot=/home/wyx_2/riscv_toolchain/riscv_gnu/riscv64-unknown-elf --with-native-system-header-dir=/include --disable-libmudflap --disable-libssp --disable-libquadmath --disable-libgomp --disable-nls --disable-tm-clone-registry --src=../../gcc --enable-multilib --with-abi=lp64d --with-arch=rv64gc --with-isa-spec=20191213 'CFLAGS_FOR_TARGET=-Os    -mcmodel=medlow' 'CXXFLAGS_FOR_TARGET=-Os    -mcmodel=medlow'
Thread model: single
Supported LTO compression algorithms: zlib
gcc version 15.1.0 () 

```

Compilation Commands are as follows:
```
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E factorial.c -o factorial
spike pk ./factorial
riscv64-unknown-elf-gcc -O0 -S factorial.c -o factorial.s
gnome-screenshot -a
riscv64-unknown-elf-objdump -d ./factorial | sed -n '/<main>:/,/^$/p' | tee factorial_main_objdump.txt
gnome-screenshot -a
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E max_array.c -o max_array
spike pk ./max_array
gnome-screenshot -a
riscv64-unknown-elf-gcc -O0 -S max_array.c -o max_array.s
riscv64-unknown-elf-objdump -d ./max_array | sed -n '/<main>:/,/^$/p' | tee max_array_main_objdump.txt
gnome-screenshot -a
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E bitops.c -o bitops
spike pk ./bitops
gnome-screenshot -a
riscv64-unknown-elf-gcc -O0 -S bitops.c -o bitops.s
riscv64-unknown-elf-objdump -d ./bitops | sed -n '/<main>:/,/^$/p' | tee bitops_main_objdump.txt
gnome-screenshot -a
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 -DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" -DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E bubble_sort.c -o bubble_sort
spike pk ./bubble_sort
gnome-screenshot -a
riscv64-unknown-elf-gcc -O0 -S bubble_sort.c -o bubble_sort.s
riscv64-unknown-elf-objdump -d ./bubble_sort | sed -n '/<main>:/,/^$/p' | tee bubble_sort_main_objdump.txt
gnome-screenshot -a
```
ProofID/RunID is visible in each output screenshots
