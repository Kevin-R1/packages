# packages手动上传整合包

     git clone https://github.com/Kevin-R1/packages.git package/Kevin-R1
     make menuconfig

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
