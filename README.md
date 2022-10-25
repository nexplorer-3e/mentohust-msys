# MentoHUST-OpenWrt-ipk

`MentoHUST` msys2 build to make it run on Windows.

## 特点

- 修复了原MentoHUST在shell下由于libiconv库编译或工作不正常导致的反馈信息乱码问题
- 去除了libiconv库的依赖，加入了轻量级的strnormalize库，GBK to UTF-8转换良好
- 去除configure等冗余文件，仅保留核心src源码文件
- ./src/Makefile中使用通配符`*`指代libpcap版本，通用性更强
- 无需手动配置环境变量，无需使用automake和configure生成所需Makefile
- 重新完全手动编写./和./src/目录下的Makefile，保证编译的有效性
- 无`--disable-notify --disable-encodepass`等配置，保证原汁原味
- 无手动`#define NO_DYLOAD`补丁，使用动态加载库函数，ipk包更小，并且更容易编译

### 需要的工具 requirements

- To run `mentohust`, install one of WinPcap providers (WinPcap, Win10Pcap, Npcap, etc.)
- Msys2 (need `msys-2.0.dll` to provide `pthreads`, etc.)
- WinPcap SDK (see ./WinPcap_Devpack)

## PreCompile

(WIP)

## Compile

Invoke in MSYS2 shell: (Mingw64 shell is not supported by present)

```bash
cd src && make # you may want to speed up build by appending `-j` parameter.
mkdir ../bin && cp mentohust.exe ../bin && cd ../bin # WIP
cp /usr/bin/msys-2.0.dll .
```

you may need to edit `CFLAGS` in `src/Makefile`. Default is `-Wall -O2`.

## Install

[Win10Pcap](https://www.win10pcap.org/download/) works on my machine. Origin WinPcap should works too.

Npcap have not been tested. You may need to install its "winpcap compatibility layer" during installation guide.

## Usage

(WIP) run in cmd.exe: `mentohust -h`

安装好后可以立即使用，配置文件在`/etc/mentohust.conf`，可以自行编辑。

最后，可以将mentohust添加到开机启动，怎么弄不用我多说了吧。

## 已知问题

- Need `-DNO_DYLOAD` to load libpcap.
- There is no dhclient on windows.
- You may not able to invoke `mentohust.exe` in ConEmu. run in `cmd.exe` instead.

- mentohust未能智能识别路由器WAN口对应的网卡，请手动在mentohust.conf的末尾DHCP脚本中添加自己WAN口对应的网卡。最终脚本类似`udhcpc -i eth1`
- 暂未加入init.d目录的mentohust脚本，可能下个版本加入。
- 后续可能加入只有一个Makefile，通过自动从git下载源码进行编译的版本

## License

(WIP to attach a gpl-2.0 doc)

- MentoHUST: GPL-2.0
- WinPcap SDK: GPL-2.0
- Win10Pcap: GPL-2.0
