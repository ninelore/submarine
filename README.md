<!-- <img align="left" style="vertical-align: middle" width="120" height="120" alt="Skiff Icon" src="data/icons/app.svg"> -->

# Submarine

An experimental bootloader for depthcharge.

###

<!-- [![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0) -->

## 📕 Explainer
Submarine provides a minimal Linux environmemt that lives in a small partition (16mb) on the disk. We use this environment to bootstrap a full Linux system (or a different system if you're brave.)

Additional documention can be found on Fyra Developer (under construction!)


## 📦 Builds

We offer prebuilt versions of the images per each commit:

- [Latest build](https://github.com/FyraLabs/submarine/blob/main/.github/workflows/build.yml)

## 🛠️ Dependencies

Please make sure you have these dependencies first before building.

```bash
make
gcc
flex
bison
elfutils-devel
parted
vboot-utils
golang
xz
bc
```

Additionally, you'll need to install u-root. To install the latest version:

```bash
go install github.com/u-root/u-root@latest
```

## 🏗️ Building

Simply clone this repo with submodules, so pass `--recurse-submodules` to `git clone`, then:

```bash
make -j$(nproc)
```

The build output is located in `build/`.
For testing, an image is built at `build/submarine.bin` which you can directly flash onto an external drive.
So, for example, replace `/dev/sda` with the device file of the external drive:

```bash
sudo dd if=build/submarine.bin of=/dev/sda
```

## 🗒️ Todos

- improve makefile