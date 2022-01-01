# iTXTech MCL Installer

`iTX Technologies Mirai Console Loader Installer` ，支持自动下载`Java`
运行时和 [iTXTech Mirai Console Loader](https://github.com/iTXTech/mirai-console-loader) 。

## 获取`mcl-installer`

1. 前往 [Release](https://github.com/iTXTech/mcl-installer/releases) 选择对应操作系统和架构下载可执行文件
2. 文件命名格式为 `mcl-installer-版本-操作系统-架构`，例如`mcl-installer-1.0.2-windows-x86.exe`，`mcl-installer-1.0.2-linux-amd64`
   ，`mcl-installer-1.0.2-macos-amd64`等
2. 运行 `mcl-installer`

### 以`Linux`和`macOS`为例

* 自动构建的二进制文件采用了 `upx` 进行压缩，所以暂时不能在 `WSL` 和 `macOS Big Sur` 下运行。
* 如要在以上环境运行，可以 [手动构建](#构建-mcl-installer) 。

```bash
$ cd 你想要安装 iTXTech MCL 的目录
$ curl -LJO https://github.com/iTXTech/mcl-installer/releases/download/v1.0.3/mcl-installer-1.0.3-linux-amd64 # 如果是macOS，就将链接中的 linux 修改为 macos
$ chmod +x mcl-installer-1.0.3-linux-amd64
$ ./mcl-installer-1.0.3-linux-amd64
```

### 以`Windows`为例

下载 `mcl-installer-版本-windows-amd64.exe` 到想要安装 `iTXTech MCL` 的目录中执行。

## 运行 `mcl-installer`

**如果您是新手，且没有特殊需求，一路回车就能进行安装了。**

```
Would you like to install Java? (Y/N, default: Y)
是否安装Java，如果上面的检测结果输出的Java版本大于11即可，可输入N跳过安装，否则必须安装Java

Java version (8-15, default: 11): 选择Java版本安装，默认为Java 11
JRE or JDK (1: JRE, 2: JDK, default: JRE): 选择JRE还是JDK安装，默认为JRE
Binary Architecture (default: x64): 选择架构安装，默认x64
如果操作系统为Windows并且需要使用 mirai-native，请选择 x32（而不是i386等其他名字）

The latest stable version of iTXTech MCL is x.x.x 获取最新MCL并询问是否下载
Would you like to download it? (Y/N, default: Y) Y：下载，N：取消
```

## 构建 `mcl-installer`

* `mcl-installer` 使用 [rust](https://www.rust-lang.org/) 编写，需要调用 `cargo` 构建。

```bash
$ git clone https://github.com/iTXTech/mcl-installer.git
$ cd mcl-installer
# native-tls => 使用系统的 OpenSSL，rustls => 使用 rustls。
# --release 用于构建优化过的二进制文件，如需要进行调试请去除该参数。
$ cargo build --features native-tls --release
$ cd target/release
$ strip mcl-installer # strip 可减小可执行文件大小
$ upx --best --lzma mcl-installer # 使用 upx 压缩可进一步缩小可执行文件大小
```

## 开源许可证

    Copyright (C) 2021 iTX Technologies

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as
    published by the Free Software Foundation, either version 3 of the
    License, or (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.

    You should have received a copy of the GNU Affero General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
