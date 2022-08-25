you need cmake higher than 3.18. i have included cmake 3.24 deb files inside the cmake folder. please install before compiling.
bigger swapfile is highly recommended. place your rom inside OTRExporter folder.

$ sudo apt install binutils gcc g++ patchelf p7zip-full python3 make curl git lld libsdl2-dev zlib1g-dev libbz2-dev libpng-dev libgles2-mesa-dev wget gpg imagemagick ninja-build   

32bit:

$ git clone https://github.com/foxhound311/Ocarina-rpi4

$ cd Ocarina-rpi4

$ git revert 6818247 -X ours --no-edit

$ sed libultraship/libultraship/color.h -i -e 's|#include "endianness.h"||g'

$ export CFLAGS="-O3 -march=armv8-a+crc -mtune=cortex-a72"
export CPPFLAGS="$CFLAGS"
export CXXFLAGS="$CFLAGS"
cmake -H. -Bbuild-cmake -GNinja \
-DNO_PULSE=ON \
-DUSE_OPENGLES=ON \
-DUSE_X11=OFF \
-DBUILD_OTR_GUI=OFF \
-DCMAKE_BUILD_TYPE:STRING=Release

$ cmake --build build-cmake --target ExtractAssets -j2

$ cmake --build build-cmake -j2



64bit:

$ git clone https://github.com/foxhound311/Ocarina-rpi4

$ cd Ocarina-rpi4

$ cmake -H. -Bbuild-cmake -GNinja \
-DNO_PULSE=ON \
-DUSE_OPENGLES=ON \
-DUSE_X11=OFF \
-DBUILD_OTR_GUI=OFF \
-DCMAKE_BUILD_TYPE:STRING=Release

$ cmake --build build-cmake --target ExtractAssets -j2

$ cmake --build build-cmake -j2

