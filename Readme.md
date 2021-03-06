# Dear ImGui: an interactive manual

Source for an online interactive manual for [Dear ImGui](https://github.com/ocornut/imgui).

Click on the image below to open it:

[![ImGui Manual](doc/images/link_manual.png)](https://pthom.github.io/imgui_manual_online/manual/imgui_manual.html)

See some demo videos with more explanations at https://pthom.github.io/imgui_manual_online.

---
This interactive manual was developed using [Hello ImGui](https://github.com/pthom/hello_imgui), which provided the emscripten port, as well as the assets embedding and image loading. [ImGuiManual.cpp](src/ImGuiManual.cpp) gives a good overview of [Hello Imgui API](https://github.com/pthom/hello_imgui/blob/master/src/hello_imgui/hello_imgui_api.md).

See also a [related demo for Implot](https://traineq.org/implot_demo/src/implot_demo.html), which also provides code navigation.

[I'd love to read your feedback!](https://github.com/pthom/imgui_manual/issues/1). 


# Test ImGui from your browser: no installation required!

This repository also enables you to get a feel of how easy it is to write ImGui applications by allowing you to write and run your own code in 3 minutes, *without even downloading or installing anything* : it runs on a dedicated cloud server on gitpod.io (which is free to use), so that you do not even need a compiler.

For example, you could write and run this code online:

````cpp
#include "playground.h"
void Playground() {
    static int counter = 0;
    if (ImGui::Button("Click me"))
        ++counter;
    ImGui::Text("counter=%i", counter);
}
````

Just click on the link below: 

[Open this repo in gitpod.io](https://gitpod.io/#https://github.com/pthom/imgui_manual)

More info: [demo on youtube](https://www.youtube.com/watch?v=FJgObNNmuzo&feature=youtu.be)


# Build instructions

First, init the submodules:
````
git submodule update --init --recursive
````


### Build instructions for emscripten

Install emscripten if not present

````
./external/hello_imgui/tools/emscripten/install_emscripten.sh
````

Build for emscripten using [tools/emscripten_build.sh](tools/emscripten_build.sh)
````
./tools/emscripten_build.sh
````

Launch a web server
````
python3 -m http.server
````

Then, browse to http://localhost:8000/src/imgui_manual.html

### Build instructions on desktop (linux, MacOS, Windows)

Init the submodules:
````
git submodule update --init --recursive
````

Install third parties via vcpkg (SDL)
````
python  external/hello_imgui/tools/vcpkg_install_third_parties.py
````

Run cmake, using vcpkg toolchain
````
mkdir build
cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=../external/hello_imgui/vcpkg/scripts/buildsystems/vcpkg.cmake
````

Build and run
````
make -j 4
./src/imgui_manual
````

---

_ETFM! (Enjoy The Fine Manual!)_
