# javaenv
受rbenv和tfenv启发的Java版本管理器。 javaenv管理您已安装的Java版本，并允许将项目的Java版本保持在版本控制之下。
该脚本采用python3编写的，轻松安装

## 为什么不使用jEnv？
jEnv是具有相似目标的出色工具。但是，我希望javaenv管理Java环境的整个生命周期，包括安装，以简化某些工作流程。

## 支持
javaenv支持Linux和Mac OSX。对Windows的支持应该可行，但不在我的计划之列。

# 安装
## 使用git
git clone https://github.com/protocol7/javaenv.git〜/ .javaenv
javaenv是一个自包含脚本，需要Python 3.3或更高版本才能运行。

为了方便起见，将javaenv添加到$ PATH中，例如使用：

ln -s〜/ .javaenv / javaenv / usr / local / bin
填充Java命令行工具：

ln -s〜/ .javaenv / javaenv / usr / local / bin / java
ln -s〜/ .javaenv / javaenv / usr / local / bin / javac
...
这将允许您自动切换Java，javac和其他工具的版本，例如：

$ cd my-java-project
$ cat .javaversion
openjdk-11.0.2
$ javac-版本
javac 11.0.2
# 用法
## versions
作为命令行参数或.javaversion文件提供的版本的格式为<distribution>-<version>。支持的发行版是：

采用openjdk
Corretto
OpenJDK
甲骨文
有效版本为，例如，openjdk-11.0.2。

该版本可以用于某些命令，而对于.javaversion文件，该发行版不包括发行版，在这种情况下，openjdk被用作默认版本。因此，有效版本也可以是例如11.0.2。

## .javaversion
如果没有为命令提供版本，或者在调用Java命令行实用程序时，将从当前目录中名为.javaversion的文件中读取该版本。该文件应仅包含上面定义的版本，例如：

回声'openjdk-11.0.2'> .javaversion
建议将.javaversion保留在源代码的版本控制下。这使贡献者可以轻松地安装和使用正确的Java版本。

## jjavaenv install [version]
安装JDK的版本。要安装的版本可以提供给命令，也可以从.javaversion文件中读取。如果已经安装了该版本，则为空操作。因此，当使用javaenv在项目上开始工作时，您只需运行即可进行全部设置：

javaenv安装
## javaenv uninstall version
卸载特定版本。版本必须包含发行版名称。

## javaenv list
列出本地安装的版本

## javaenv list-remote
列出所有可用于安装的版本。

## javaenv home [version]
打印活动版本的JAVA_HOME的值。该版本可以提供给命令，也可以从.javaversion文件中读取。该命令对于使用JAVA_HOME的工具很有用，例如Maven。

export JAVA_HOME=$(javaenv home)

# 验证安装
下载安装文件时，javaenv将验证预期的SHA256 / MD6哈希。请注意，预期的哈希存储在javaenv命令本身中，因此这需要您信任javaenv安装。

# TODO
添加对自动调整Java命令行工具的支持
添加所有已发布且仍可用的版本
添加对构建Docker映像的支持
添加对构建Docker映像的支持原文
添加对构建Docker映像的支持
添加直接支持以设置Maven的Java版本
[长期]不再需要Python


# 翻译原文
https://github.com/protocol7/javaenv
