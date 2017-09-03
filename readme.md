# Docker image for crosscompiling kernels targeting i686-elf
## Description
A docker image containing a cross-compiler for compiling kernels for i686-elf, based on the osdev tutorials:
http://wiki.osdev.org/GCC_Cross-Compiler and http://wiki.osdev.org/Bare_Bones_with_NASM

The toolchain uses Binutils 2.29 and GCC 7.2.0, both of which you'll need to download separately and paste into the toolchain folder before building this image.

It also contains GRUB2 to build bootable iso images using grub-mkrescue.

## Building
Add binutils-2.29.tar.gz and gcc-7.2.0.targ.gz to the toolchain folder
Build using: docker-compose-build

## Usage

Run the docker, mounting the folders with your project folder as a volume.

Use nasm, i686-elf-gcc and i686-elf g++ to compile and link your sources.
Use grub-mkrescue to build a bootable iso.
Preferably automate those tasks in a script, which you can place with your project folder, for example: build.sh

```
docker run --rm -v /project/path/on/host:/path/on/container jdesmedt/crosscompile-i686-elf /path/on/container/build.sh
```

On windows, from a powershell command or script:
```
docker run --rm -v ${PWD}:/path/on/container jdesmedt/crosscompile-i686-elf /path/on/container/build.sh
```

## Environment variables
* $PREFIX /opt/cross
* $TARGET i686-elf
* $PATH /opt/cross/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin