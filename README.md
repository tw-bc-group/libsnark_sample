# ZK-SANRK 示例

## quick run

1. 拉取zksanrk代码

```
git submodule update --init --recursive
```

2. 安装zksnark依赖

ubuntu 18.04及以上：
```
sudo apt install build-essential cmake git libgmp3-dev libprocps-dev python3-markdown libboost-program-options-dev libssl-dev python3 pkg-config
```
其他os：
参考zksnark库[官方文档](https://github.com/scipr-lab/libsnark#build-instructions)

3. 编译

```
mkdir build; cd build; cmake ..; make
```
编译后，会在`build/merkle`下生成`merkle`二进制文件

4. 初始化配置

```
cd ./merkle; ./merkle setup
```

5. 生成证明

```
./merkle prove [data1] [data2] [data3] [data4] [data5] [data6] [data7] [data8] [index]
```
生成后，命令行会输出root的值，copy下来，在验证时使用

6. 验证证明

```
./merkle [root]
```
