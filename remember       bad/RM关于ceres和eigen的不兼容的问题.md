# ceres,eigen多版本使用

## 安装多版本的eigen

 1、下载eigen3.2.5安装包，下载地址：Releases · libeigen / eigen · GitLab

 2、选好路径（随便），然后解压。进入解压出的eigen-3.2.5文件夹，创建build文件夹

3、进入/usr/local/include下，创建文件夹eigen340和eigen325，这是为了切换eigen版本，/usr/local/include下已经有一个eigen3文件夹，这是eigen3.4.0的。

4、进入在第2步中创建的build文件夹中编译并设置安装路径，将eigen3.2.5安装到第3步创建的eigen325文件夹中：

```shell	
cmake -DCMAKE_INSTALL_PREFIX=/usr/local/include/eigen325 ..
make -j8
sudo make install
```

切换eigen版本及使用
        将/usr/local/include下的eigen3放回eigen340文件夹中，将/usr/local/include/eigen325/include下的eigen3放到/usr/local/include上就完成了版本的切换。在/usr/local/include打开终端，输入：

    sudo mv eigen3 eigen325/include
    sudo mv eigen340/eigen3 .    

## 安装多版本的ceres 我已经安装了ceres2.1.0，现在安装ceres1.14.0。**注意：无论是安装还是使用，都需要把eigen版本切换到3.2.5。**

​    1、下载ceres1.14.0，选择安装地址（随便），然后下载并解压：

```shell
wget ceres-solver.org/ceres-solver-1.14.0.tar.gz
tar -zxvf ceres-solver-1.14.0.tar.gz
```

2、进入解压出的ceres-solver-1.14.0文件夹，创建build文件夹

3、进入/usr/local/include下，创建文件夹ceres_1.14.0

4、进入在第2步中创建的build文件夹中编译并设置安装路径，将ceres1.14.0安装到第3步创建的ceres_1.14.0文件夹中：

```HTML
cmake -DCMAKE_INSTALL_PREFIX=/usr/local/include/ceres_1.14.0 ..
make -j8
sudo make install
```

## 切换ceres版本及使用

 **使用ceres1.14.0时：**

​    首先确保eigen版本是3.2.5，然后CMakeList中：

```cobol
# Ceres
set(Ceres_DIR /usr/local/include/ceres_1.14.0/lib/cmake/Ceres)
find_package(Ceres 1.14.0 REQUIRED)
include_directories(${CERES_INCLUDE_DIRS})
```



