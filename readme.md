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

`git clone` the contents of this folder to a just-genrated `STM32CubeMX` project.

If extension `Clangd` and `CMake Tools` has been installed, they should be working fine with `settings.json` containing the right paths of each tool. It's recommended to use `MSYS2` to install and manage the toolchain.

In VSCode's `Git Bash` terminal type 
`./f.sh`, and then `.elf` will be generated under `\build\debug`, then `Openocd` will flash it to STM32 if the corresponding hardware($e.g.$ `ST-LINK` or `DAPLINK`) is correctly connected to the device.
