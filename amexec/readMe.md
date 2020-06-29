# amexec工具为模型推理工具

### 功能
输入.om模型和模型所需要的输入bin文件，输出模型的输出数据文件，支持多次推理（指对同一输入数据进行推理）。

模型必须是通过c7x版本的atc工具转换的om模型，输入bin文件需要符合模型的输入要求（支持模型多输入）

### 使用环境
Centos7.6或Ubuntu16.4 
必须按照《驱动和开发环境安装指南》装好C7x环境

### 获取
1. 下载压缩包方式获取。

   将 https://gitee.com/ascend/tools 仓中的脚本下载至服务器的任意目录。

   例如存放路径为：$HOME/AscendProjects/tools。

2. 命令行使用git命令方式获取。

   在命令行中：$HOME/AscendProjects目录下执行以下命令下载代码。

   **git clone https://gitee.com/ascend/tools.git**


### 使用方法
进入amexec目录
```
cd $HOME/AscendProjects/tools/amexec/
```
进入out目录
```
cd out
```
工具就在out目录下


工具为命令行的运行方式，例如
```
./amexec --model /home/HwHiAiUser/ljj/colorization.om --input /home/HwHiAiUser/ljj/colorization_input.bin --output /home/HwHiAiUser/ljj/AMEXEC/out/output1 --outfmt TXT --loop 2
```
需要注意的是这几个参数的顺序不能颠倒，outfmt与loop为可选参数，默认值分别有BIN、1。
如果有多个输入，需要用“，”隔开。
其他参数详情可使用--help查询。

### 编译
工具也支持源码编译，或者使用者需要添加或者修改代码，使用者重新编译
进入amexec目录
```
cd $HOME/AscendProjects/tools/amexec/
```
运行编译脚本
```
./build.sh
```
重新编译的工具在out目录下

## 注意事项
运行工具的用户在当前目录需要有创建目录以及执行工具的权限，使用前请自行检查。
dump、profiling以及动态多batch功能暂不支持。

## 参数说明

| 参数名   | 说明                            |
| -------- | ------------------------------- |
| --model  | 需要进行推理的om模型            |
| --input  | 模型需要的输入                  |
| --output | 推理数据输出路径                |
| --outfmt | 输出数据的格式，TXT或者BIN      |
| --loop   | 推理次数 [1,100]，可选参数默认1 |
| --help   | 工具使用帮助信                  |