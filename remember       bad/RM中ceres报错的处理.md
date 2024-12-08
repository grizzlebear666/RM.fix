# Ubuntu22.04 安装ceres-solver，cmake编译报错有tbb_stddef.h

## Eigie3.4.0，ceres版本为2.0.0（如果是ceres1.14，[Eigen](https://so.csdn.net/so/search?q=Eigen&spm=1001.2101.3001.7020)版本要是3.30以下）[Ceres安装步骤】

安装环境

```shell	
sudo apt-get install liblapack-dev libsuitesparse-dev libcxsparse3 libgflags-dev libgoogle-glog-dev libgtest-dev
```

## 解决方案

1.根据报错信息中找到该文件夹下：

```shell	
/usr/include/tbb
```

2.在该目录下打开终端，按步骤输入以下命令

```
1.sudo touch tbb_stddef.h
2.sudo gedit tbb_stddef.h
```

3.将该链接下的文档复制到打开的文件中[link](https://blog.csdn.net/cpu077/article/details/128187694?ops_request_misc=%7B%22request%5Fid%22%3A%22167757787116800213063911%22%2C%22scm%22%3A%2220140713.130102334.pc%5Fall.%22%7D&request_id=167757787116800213063911&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-128187694-null-null.142^v73^wechat_v2,201^v4^add_ask,239^v2^insert_chatgpt&utm_term=tbb文件缺少tbb_stddef.h&spm=1018.2226.3001.4187)
4.保存
5.重新运行

```shell
cmake  ..
make -j4
sudo make install
```

