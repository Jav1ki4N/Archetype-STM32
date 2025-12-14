# Archetype-STM32
----
# 1. What is it?
The content of this folder is necessary files that configure components like `CMake` and `Openocd` and so on.

For now it's only verified under my current STM32 project structure, which is:

- `CMake` + `Ninja` for building
- `Openocd` for flashing
- `STM32CubeMX` for code generating.

----

# 2. How to use?

`git clone` the contents of this folder to a just-generated `STM32CubeMX` project.

Replace `STM32CubeMX` generated `CMakelists.txt` under root directory with `CMakelists.txt` in `\CMake_Portable`.

Edit `settings.json` in `\.vscode` to match your paths of tools.

If extension `Clangd` and `CMake Tools` has been installed, they should be working fine with `settings.json` containing the right paths of each tool. It's recommended to use `MSYS2` to install and manage the toolchain.

In VSCode's `Git Bash` terminal type 
`./f.sh`, and then `.elf` will be generated under `\build\debug`, then `Openocd` will flash it to STM32 if the corresponding hardware($e.g.$ `ST-LINK` or `DAPLINK`) is correctly connected to the device.

# 3. C++ Support

In `System.i4N` or whatever it's named after, there are two files specifically designed for `C++`, `cppmain.cpp` and `cppmain.h`.

To enable `C++`, simply include `cppmain.h` in `\Core\Src\main.c` and call function `cppmain()` in function `main()` of `\Core\Src\main.c`, however it should be called outside the while(1) loop to avoid dual infinite loop, which can cause serious errors.

After that, you can write your codes in `cppmain.c` instead of `main.c`, as all logics will ultimately be call in `main.c`.

For unknown reasons `c++` header files should have `.hpp` suffix instead of `.h` (which I always use) or `clangd` might fail to function properly.
