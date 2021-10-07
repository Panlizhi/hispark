
#### 基于YOLOV3的火焰监测
hispark主要是海思嵌入式大赛的相关参赛代码，

其中：

Taurus目录：是性别分类的相关AI插件代码补丁，以及一个训练好的性别分类的wk模型


### 1、Taurus代码补丁的验证

**这里请一定说明一下你是基于哪个hiopenais版本制作的patch**

* 步骤1：把hispark仓clone下来。
* 步骤2：按照QQ群提供的资料，在code目录下，重新搭建一份hiopenais_v1.1的环境(因为我的patch是基于hiopenais_v1.1制作的)。
* 步骤3：hispark/Taurus/patch/目录下的所有.patch文件都复制到code/hiopenais/patch/目录下。
* 步骤4：在code/hiopenais/目录下执行下面的命令，把patch补丁打入步骤2创建的hiopenais环境中。

```
patch -p1 < patch/0001.hiopenais_build.patch
patch -p1 < patch/0002.hiopenais_src.patch 
```

* 步骤5：进入code/hiopenais/build/目录下，执行下面的命令，重新编译hiopenais。

```
make rebuild && make plugs_rebuild && make boards_rebuild
```

* 步骤6：编译成功后，把code/hiopenais/output/目录下的所有文件都复制到SDK的文件系统中。
* 步骤7：hispark/Taurus/src/目录下的wk文件，复制到文件系统的hiopenais/plugs/目录下。
* 步骤8：在code/hiopenais/目录下执行 ./build.sh ext4来制作文件系统
* 步骤7：重新烧录镜像，验证功能。



