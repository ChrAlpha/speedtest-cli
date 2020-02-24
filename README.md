# speedtest-cli

一个基于 speedtest.net 测试网络带宽的命令行工具。

[![Latest Version](https://camo.githubusercontent.com/be317f03ffa0d70577d68256fc29e1c753362222/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f7370656564746573742d636c692e737667) ](https://pypi.python.org/pypi/speedtest-cli/)[![Travis](https://camo.githubusercontent.com/d52442b7e8d875afe3b6d22f4982d01e00f4fdf3/68747470733a2f2f696d672e736869656c64732e696f2f7472617669732f736976656c2f7370656564746573742d636c692e737667) ](https://pypi.python.org/pypi/speedtest-cli/)[![License](https://camo.githubusercontent.com/9cf3d6fe433a71d5727b9b8c5104ef8171f3916e/68747470733a2f2f696d672e736869656c64732e696f2f707970692f6c2f7370656564746573742d636c692e737667) ](https://pypi.python.org/pypi/speedtest-cli/) 

## Versions 版本要求

speedtest-cli 良好地运行在 Pythin 2.4-3.7 上。

[![Versions](https://camo.githubusercontent.com/f31a76b4d003567f4c64a3530129b0a44af71940/68747470733a2f2f696d672e736869656c64732e696f2f707970692f707976657273696f6e732f7370656564746573742d636c692e737667) ](https://pypi.python.org/pypi/speedtest-cli/) 

## Installation 安装

### 使用 pip / easy_install 安装

```
pip install speedtest-cli
```

或

```
easy_install speedtest-cli
```

### 基于 Github 安装

```
pip install git+https://github.com/sivel/speedtest-cli.git
```

或

```
git clone https://github.com/sivel/speedtest-cli.git
cd speedtest-cli
python setup.py install
```

### 直接下载源

```
wget -O speedtest-cli https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py
chmod +x speedtest-cli
```

或

```
curl -Lo speedtest-cli https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py
chmod +x speedtest-cli
```

## Usage 使用

```
$ speedtest-cli -h
usage: speedtest-cli [-h] [--no-download] [--no-upload] [--single] [--bytes]
                     [--share] [--simple] [--csv]
                     [--csv-delimiter CSV_DELIMITER] [--csv-header] [--json]
                     [--list] [--server SERVER] [--exclude EXCLUDE]
                     [--mini MINI] [--source SOURCE] [--timeout TIMEOUT]
                     [--secure] [--no-pre-allocate] [--version]

Command line interface for testing internet bandwidth using speedtest.net.
--------------------------------------------------------------------------
https://github.com/sivel/speedtest-cli

optional arguments:
-h, --help            使用帮助
--no-download         不进行下载性能测试
--no-upload           不进行上传性能测试
--single              使用单线程而非多线程
--bytes               使用 bytes 而非 bits 作为单位
--share               将测试结果生成一个以图片形式的分享连接（不受 --csv, --bytes 影响）
--simple              去重冗长的结果，仅显示基本信息
--csv                 去重冗长的结果，仅显示基本信息（不受 --bytes 影响，使用 bits 作为单位）
--csv-delimiter CSV_DELIMITER
                      自定义 CSV 模式中的分界符（默认 ", "）
--csv-header          答应 CSV 标头
--json                去重冗长的结果，仅以 JSON 格式显示基本信息（不受 --bytes 影响，使用 bits 作为单位）
--list                按距离排序展现 speedtest.net 服务器列表
--server SERVER       指定测试服务器 ID ，可指定多个 
--exclude EXCLUDE     排除测试服务器 ID ，可排除多个
--mini MINI           调用 Speedtest Mini 服务（URL）
--source SOURCE       绑定源 IP 地址
--timeout TIMEOUT     设定超时时间，以秒为单位，默认为 10
--secure              使用 HTTPS 连接测试而非 HTTP
--no-pre-allocate     不要预分配上传数据。 默认启用该预分配，以提高上传性能。为了支持内存不足的系统，请使用此选项来避免出现 MemoryError
--version             查看当前 speedtest-cli 版本
```

## Python API

关于 Python API 使用方法请参考：[wiki](https://github.com/sivel/speedtest-cli/wiki) 

## Inconsistency

It is not a goal of this application to be a reliable latency reporting tool.

Latency reported by this tool should not be relied on as a value indicative of ICMP style latency. It is a relative value used for determining the lowest latency server for performing the actual speed test against.

There is the potential for this tool to report results inconsistent with Speedtest.net. There are several concepts to be aware of that factor into the potential inconsistency:

1. Speedtest.net has migrated to using pure socket tests instead of HTTP based tests
2. This application is written in Python
3. Different versions of Python will execute certain parts of the code faster than others
4. CPU and Memory capacity and speed will play a large part in inconsistency between Speedtest.net and even other machines on the same network

Issues relating to inconsistencies will be closed as wontfix and without additional reason or context.