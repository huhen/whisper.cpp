## base for mod
```bash
# v1.5.4...v1.5.5(Mar 25, 2024)
git checkout 1558ec5
cmake -B build -DWHISPER_CUBLAS=1 -DGGML_CUDA_ARCHITECTURES=53
cmake --build build -j 4 --config Release

cp ./build/bin/* .
./main -f samples/jfk.wav -m models/ggml-small.bin
```

```bash
./models/download-ggml-model.sh small
```

```bash
./extra/bench-all.sh 4 0
```

## clang
```bash
rm -rf build
cmake -B build -DWHISPER_CUBLAS=1 -DGGML_CUDA_ARCHITECTURES=53 \
-D CMAKE_C_COMPILER=clang -D CMAKE_CXX_COMPILER=clang++ -D CMAKE_CUDA_COMPILER=clang++
cmake --build build -j 4 --config Release
```

/---------------------------------------/

## build CUDA version(clang 18)
```bash
# build the project
cmake -B build -D GGML_CUDA=1 -D CMAKE_CUDA_ARCHITECTURES="53" \
-D CMAKE_C_COMPILER=clang -D CMAKE_CXX_COMPILER=clang++ -D CMAKE_CUDA_COMPILER=clang++
cmake --build build -j 4 --config Release
```

## select gcc version
```bash
sudo update-alternatives --config gcc
sudo update-alternatives --config g++
```

## base for mod
```bash
# v1.6.2
git checkout c7b6988
cmake -B build -DWHISPER_CUDA=1 -DGGML_CUDA_ARCHITECTURES=53
cmake --build build -j 4 --config Release

cp ./build/bin/* .
./main -f samples/jfk.wav
```

## transcribe an audio file
```bash
./build/bin/whisper-cli -f samples/jfk.wav
```

## bench
```bash
./build/bin/whisper-bench -m ./models/ggml-small.en.bin -t 4
```

## download model
```bash
make -j base.en
```

## gcc-8.5.0 (support neon)
```bash
sudo apt-get install -y build-essential software-properties-common
sudo apt-get install -y libgmp-dev libmpfr-dev libmpc-dev
wget http://ftp.gnu.org/gnu/gcc/gcc-8.5.0/gcc-8.5.0.tar.gz
tar -xvzf gcc-8.5.0.tar.gz
cd gcc-8.5.0
./contrib/download_prerequisites
mkdir build && cd build
../configure --enable-languages=c,c++ --disable-multilib
make -j$(nproc)
sudo make install
sudo update-alternatives --install /usr/bin/gcc gcc /usr/local/bin/gcc 8
sudo update-alternatives --install /usr/bin/g++ g++ /usr/local/bin/g++ 8
```

## cmake-3.28.6
```bash
sudo apt-get remove --purge cmake
sudo apt-get install libssl-dev
wget https://cmake.org/files/v3.28/cmake-3.28.6.tar.gz
tar -xzvf cmake-3.28.6.tar.gz
cd cmake-3.28.6
./bootstrap
make -j$(nproc)
sudo make install
```

## fix link fs lib issue in gcc 8.5
```diff
diff --git a/ggml/CMakeLists.txt b/ggml/CMakeLists.txt
index c780077a..1df6924c 100644
--- a/ggml/CMakeLists.txt
+++ b/ggml/CMakeLists.txt
@@ -333,6 +333,8 @@ set(GGML_PUBLIC_HEADERS
     include/gguf.h)

 set_target_properties(ggml PROPERTIES PUBLIC_HEADER "${GGML_PUBLIC_HEADERS}")
+target_link_libraries(ggml PRIVATE stdc++fs)
+add_link_options(-Wl,--copy-dt-needed-entries)
 #if (GGML_METAL)
 #    set_target_properties(ggml PROPERTIES RESOURCE "${CMAKE_CURRENT_SOURCE_DIR}/src/ggml-metal.metal")
 #endif()
```

## FFmpeg support
```bash
# Debian/Ubuntu
sudo apt install libavcodec-dev libavformat-dev libavutil-dev
```

## build cpu version(gcc 8.5)
```bash
# build the project
cmake -B build -D WHISPER_FFMPEG=yes
cmake --build build -j 4 --config Release
```

## build CUDA version(nvcc 10.2)
For nvcc need refactor cuda code to c++14... may be future
```bash
# build the project
cmake -B build -D WHISPER_FFMPEG=yes -D GGML_CUDA=1 -D CMAKE_CUDA_ARCHITECTURES="53" -D CMAKE_CUDA_STANDARD=14
cmake --build build -j 4 --config Release
```

## build cpu version(clang 18)
```bash
# build the project
cmake -B build -D CMAKE_C_COMPILER=clang -D CMAKE_CXX_COMPILER=clang++
cmake --build build -j 4 --config Release
```