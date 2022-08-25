you need cmake higher than the default cmake from apt.
i have included a deb file for both 32bit and 64bit rpiOS's. you can find them inside cmake folder.
install cmake before compiling or it will fail.

also it is recommended to make the swapfile larger, especially for 64bit. it tends to run out of memory while compiling. 

build instructions:
git clone https://github.com/foxhound311/Ocarina-rpi4.git
cd Ocarina-rpi4
git revert 6818247 -X ours --no-edit
sed libultraship/libultraship/color.h -i -e 's|#include "endianness.h"||g'
export CFLAGS="-O3 -march=armv8-a+crc -mtune=cortex-a72"
export CPPFLAGS="$CFLAGS"
export CXXFLAGS="$CFLAGS"
cmake -H. -Bbuild-cmake -GNinja \
-DNO_PULSE=ON \
-DUSE_OPENGLES=ON \
-DUSE_X11=OFF \
-DBUILD_OTR_GUI=OFF \
-DCMAKE_BUILD_TYPE:STRING=Release

cmake --build build-cmake --target ExtractAssets -j2
cmake --build build-cmake -j2
  

it takes about an hour to compile. please be patient.
