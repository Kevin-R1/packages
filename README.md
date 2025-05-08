# packages

     git clone https://github.com/Kevin-R1/packages.git package/Kevin-R1
     make menuconfig
## 编译命令
- 首先装好 Linux 系统，推荐 Debian 或 Ubuntu LTS

- 安装编译依赖
bash
     sudo apt update -y
     sudo apt full-upgrade -y
     sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
     bzip2 ccache clang cmake cpio curl device-tree-compiler flex gawk gcc-multilib g++-multilib gettext \
     genisoimage git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libfuse-dev libglib2.0-dev \
     libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libpython3-dev \
     libreadline-dev libssl-dev libtool llvm lrzsz msmtp ninja-build p7zip p7zip-full patch pkgconf \
     python3 python3-pyelftools python3-setuptools qemu-utils rsync scons squashfs-tools subversion \
     swig texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev
  
## 下载源代码，更新 feeds 并选择配置以lede为模板！！！

     git clone https://github.com/coolsnowwolf/lede
     cd lede
     ./scripts/feeds update -a
     ./scripts/feeds install -a
     make menuconfig

## 下载 dl 库，编译固件 （-j 后面是线程数，第一次编译推荐用单线程）

     make download -j8
     make V=s -j1

## 二次编译：

     cd lede
     git pull
     ./scripts/feeds update -a
     ./scripts/feeds install -a
     make defconfig
     make download -j8
     make V=s -j$(nproc)
## 如果需要重新配置：

     rm -rf .config
     make menuconfig
     make V=s -j$(nproc)
