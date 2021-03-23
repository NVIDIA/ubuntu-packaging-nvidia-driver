# ubuntu packaging nvidia driver

[![License](https://img.shields.io/badge/License-GPL%202.0-blue.svg)](https://opensource.org/licenses/GPL-2.0)
[![Contributing](https://img.shields.io/badge/Contributing-Developer%20Certificate%20of%20Origin-violet)](https://developercertificate.org)

## Overview

Packaging templates for `Ubuntu` based Linux distros to build NVIDIA driver packages.

The `main` branch contains this README. The `control` and `.install` files can be found in the appropriate [16.04](../../tree/16.04), [18.04](../../tree/18.04), and [20.04](../../tree/20.04) branches.

## Table of Contents

- [Overview](#Overview)
- [Deliverables](#Deliverables)
- [Prerequisites](#Prerequisites)
  * [Clone this git repository](#Clone-this-git-repository)
  * [Download a NVIDIA driver runfile](#Download-a-NVIDIA-driver-runfile)
  * [Install build dependencies](#Install-build-dependencies)
- [Related](#Related)
  * [NVIDIA modprobe](#NVIDIA-modprobe)
  * [NVIDIA settings](#NVIDIA-settings)
- [See also](#See-also)
  * [RHEL driver](#RHEL-driver)
  * [SUSE driver](#SUSE-driver)
- [Contributing](#Contributing)


## Deliverables

This repo contains the template files used to build the following **DEB** packages:

> *note:* `flavor` is the first `.` delimited field in the driver version, ex: `460` in `460.32.03`

* **Ubuntu 18.04** or **Ubuntu 20.04**
 ```shell
 - libnvidia-cfg1-${flavor}
 - libnvidia-common-${flavor}
 - libnvidia-compute-${flavor}
 - libnvidia-decode-${flavor}
 - libnvidia-encode-${flavor}
 - libnvidia-extra-${flavor}
 - libnvidia-fbc1-${flavor}
 - libnvidia-gl-${flavor}
 - libnvidia-ifr1-${flavor}
 - nvidia-compute-utils-${flavor}
 - nvidia-dkms-${flavor}
 - nvidia-driver-${flavor}
 - nvidia-headless-${flavor}
 - nvidia-headless-no-dkms-${flavor}
 - nvidia-kernel-common-${flavor}
 - nvidia-kernel-source-${flavor}
 - nvidia-utils-${flavor}
 - xserver-xorg-video-nvidia-${flavor}
 ```

* **Ubuntu 16.04**
 ```shell
 - libcuda1-${flavor}
 - nvidia-libopencl1-${flavor}
 - nvidia-opencl-icd-${flavor}
 - nvidia-${flavor}
 - nvidia-${flavor}-dev
 ```

* **Additional GRID packages**
 ```shell
 - libnvidia-grid-${flavor}
 - nvidia-grid-utils-${flavor}
 ```

## Prerequisites

### Clone this git repository:

Supported branches: `16.04`, `18.04` & `20.04`

```shell
git clone -b ${branch} https://github.com/NVIDIA/ubuntu-packaging-nvidia-driver
> ex: git clone -b 18.04 https://github.com/NVIDIA/ubuntu-packaging-nvidia-driver
```

### Download a NVIDIA driver runfile:

* **TRD** location: [https://us.download.nvidia.com/tesla/](https://us.download.nvidia.com/tesla/) (not browsable)

  *ex:* [https://us.download.nvidia.com/tesla/460.32.03/NVIDIA-Linux-x86_64-460.32.03.run](https://us.download.nvidia.com/tesla/460.32.03/NVIDIA-Linux-x86_64-460.32.03.run)

* **UDA** location: [https://download.nvidia.com/XFree86/Linux-x86_64/](https://download.nvidia.com/XFree86/Linux-x86_64/)

  *ex:* [https://us.download.nvidia.com/XFree86/Linux-x86_64/460.56/NVIDIA-Linux-x86_64-460.56.run](https://us.download.nvidia.com/XFree86/Linux-x86_64/460.56/NVIDIA-Linux-x86_64-460.56.run)

* **CUDA** runfiles: `cuda_${toolkit}_${driver}_linux.run` are not compatible.

  However a NVIDIA driver runfile can be extracted intact from a CUDA runfile:
  ```shell
  sh cuda_${toolkit}_${driver}_linux.run --tar mxvf
  > ex: sh cuda_11.2.1_460.32.03_linux.run --tar mxvf

  ls builds/NVIDIA-Linux-${arch}-${driver}.run
  > ex: ls builds/NVIDIA-Linux-x86_460.32.03.run
  ```

### Install build dependencies
> *note:* these are only needed for building not installation

```shell
# Packaging
apt-get install debhelper devscripts dpkg-dev
```

## Related

- nvidia-modprobe
  * [https://github.com/NVIDIA/ubuntu-packaging-nvidia-modprobe](https://github.com/NVIDIA/ubuntu-packaging-nvidia-modprobe)

- nvidia-settings
  * [https://github.com/NVIDIA/ubuntu-packaging-nvidia-settings](https://github.com/NVIDIA/ubuntu-packaging-nvidia-settings)


## See also

- nvidia-graphics-drivers
  * [https://github.com/tseliot/nvidia-graphics-drivers](https://github.com/tseliot/nvidia-graphics-drivers)

### RHEL driver

  * [https://github.com/NVIDIA/yum-packaging-nvidia-driver](https://github.com/NVIDIA/yum-packaging-nvidia-driver)

### SUSE driver

  * [https://github.com/NVIDIA/zypper-packaging-nvidia-driver](https://github.com/NVIDIA/zypper-packaging-nvidia-driver)


## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)
