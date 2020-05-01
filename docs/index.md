# 总述

## 版权声明

本项目为 2019 年秋季学期起清华大学计算机系开设的《计算机网络原理》课程的实验框架。
**未经作者授权，禁止用作任何其他用途，包括且不限于在其他课程或者其他学校中使用。**
作者保留一切追究侵权责任的权利。

这里是 2020 年网络原理课程原理课程实验采用的框架。它有以下的设计目标：

1. 降低难度，把与底层打交道的部分抽象成通用的接口，减少学习底层 API 的负担
2. 复用代码，在一个平台上编写的程序可以直接用于其他平台
3. 方便测试，提供文件读写 PCAP 的后端，可以直接用数据进行黑箱测试

实验的目标是完成一个具有以下功能的路由器：

1. 转发：收到一个路过的 IP 包，通过查表得到下一棒（特别地，如果目的地址直接可达，下一棒就是目的地址），然后“接力”给下一棒。
2. 路由：通过 RIP 协议，学习到网络的拓扑信息用于转发，使得网络可以连通。

如果你参加的是联合实验，请阅读 `Router-Lab-Joint` 仓库下的 README。

请仔细阅读**所有的文档**，在问问题时，请把所有的 **暗号** 按顺序连在一起重复一遍然后再说你的问题。

本文档默认你已经在软件工程、编译原理、程序设计训练等课程中已经学习到了足够的 Git 、Make 、SSH 、Python3 和 Linux 的使用知识。如果你用的是 Windows 系统，你可以 WSL/虚拟机/下发的树莓派上进行以下所有相关的操作。无论你电脑是用的是什么系统，最终都需要在树莓派的 Linux 上运行路由器。

如果你运行的是 Debian 系列发行版（包括 Ubuntu、Raspbian），你可以一把梭地安装所有可能需要的依赖：

```bash
sudo apt install git make cmake python3 python3-pip libpcap-dev libreadline-dev libncurses-dev wireshark tshark iproute2 g++
pip3 install pyshark
```

其他发行版也有类似的包管理器安装方法。