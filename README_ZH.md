<p align="center">
<img src="https://i.imgur.com/exiipaG.png" width="1000px" />
<br>
<a href="https://discord.gg/pqEHdWDf8z"><img src="https://i.imgur.com/VMdA0q7.png" height="60px"/> </a>
<a href="https://www.nexusmods.com/skyrimspecialedition/mods/111491"><img src="https://i.imgur.com/STsBXT6.png" height="60px"/> </a>
<a href="https://ko-fi.com/cutleast"><img src="https://i.imgur.com/KcPrhK5.png" height="60px"/> </a>
<a href="https://trello.com/b/AA2KwhH8/sse-auto-translator"><img src="https://i.imgur.com/sIjqMOg.png" height="60px"/> </a>
<br>
</p>

# 描述

这个工具允许您以相对较少的努力翻译整个模组列表。它利用基于AI的语言检测功能自动识别您的模组列表中需要翻译的内容。
该工具会在Nexus Mods上搜索原始模组的可用翻译并下载它们（自动下载功能仅适用于Nexus Mods高级用户）。
SSE-AT在单个数据库中管理所有已安装的翻译，并使用Dynamic String Distributor SKSE插件将它们注入游戏，无需修改任何插件或在翻译过时的情况下"降级"原始插件。
此外，该工具还具有内置编辑器，用于自行创建和编辑翻译，并支持Google翻译和DeepL API。

# 使用方法

请参阅[文档](/doc/Instructions_en_US.md)。

# 功能

- 自动检测所需的翻译
- 自动检测并导入已安装的翻译
- 自动在Nexus Mods上扫描所需的翻译
- 通过SKSE实现版本独立的翻译
- 合并数据库，自动翻译完全由原版字符串或其他已安装翻译覆盖的插件
- 内置编辑器，用于创建和编辑翻译
  - 搜索和替换功能
  - 内置支持Google翻译（免费）和DeepL API（需要API密钥）
  - 导出功能，用于分享自己的翻译
- 导入功能，用于手动安装翻译
- 忽略列表功能，完全忽略被错误标记为"需要翻译"的插件
- 内置文档
- 深度扫描功能，查找不完整的翻译
- 启动对话框，便于设置和介绍
- 状态颜色，快速概览模组列表的翻译状态
- 支持Mod Organizer 2和Vortex
- 绑定到Nexus Mods上的"模组管理器下载"按钮，方便从Nexus Mods下载翻译（特别适用于免费用户）
  - 这需要在"翻译"选项卡中手动激活
  - 在设置中可使用"自动绑定"（实验性功能）
    - 启用此功能后，SSE-AT会在启动时自动链接到模组管理器下载，并在关闭时取消链接
    - 这是实验性功能，因为崩溃可能会阻止取消链接
- 更新功能，用于更新已下载的翻译
- 自动包含非插件文件，如界面翻译和Papyrus脚本（如果在用户设置中启用）
- 支持法语翻译网站[La Confrérie des Traducteurs](https://www.confrerie-des-traducteurs.fr)

# 限制

- 目前仅完全支持插件文件（.esp、.esm和.esl）
  - 非插件文件，如界面翻译（.txt）或Papyrus脚本（.pex），仅在用户设置中启用时才会从导入的翻译中提取和复制
- SSE-AT无法自动找到不在单独模组页面上和/或未在原始模组页面上链接（在"翻译"下）的翻译，除非它们在主列表中链接
  - 主列表是一种链接到未从原始模组常规翻译链接的翻译的方式，例如[Unofficial Skyrim Modder's Patch](https://www.nexusmods.com/skyrimspecialedition/mods/49616?tab=files)的德语翻译
  - 它们必须由志愿者维护，但到目前为止，只有一个小型的德语主列表
  - 如果您有兴趣为您的语言维护主列表，请通过上面链接的Discord服务器联系我们（@cutleast或@whusten）
- Vortex：SSE-AT和Vortex不能同时运行！
  - 这是Vortex数据库的限制，它一次只允许一个应用程序访问

# 常见问题

#### 我需要编辑任何ini文件吗？

- 确保在*Skyrim.ini*中将*[General]* > *sLanguage*设置为您想要的语言（例如*GERMAN*）
- 由于不支持声音，我还建议在同一ini文件中设置英语语音文件。只需转到*[Archive]*，在*sResourceArchiveList2*中将*Voices_xx0.bsa*替换为*Voices_en0.bsa*

#### SSE-AT将一个（或多个）插件检测为*需要翻译*，尽管它不包含可见的字符串。我该怎么做才能防止它再次检测？

- 您可以这样将其添加到忽略列表：右键单击插件 > "添加到忽略列表"
- 这将阻止SSE-AT完全包含它
- 您可以通过顶部过滤按钮旁边的"忽略列表"按钮查看和删除忽略列表中的插件

#### 我的游戏中仍有未翻译的字符串。我以为SSE-AT可以解决这个问题？

- SSE-AT只能下载Nexus Mods上可用的翻译，并为完全由已安装翻译（包括原版字符串）覆盖的模组自动创建翻译。
- 根据您想要的语言，Nexus Mods上可用的翻译数量会有所不同

#### 我发现了一个已安装翻译的模组中有未翻译的字符串。

- 在提交错误报告或问题之前，请确保原始翻译正常工作，并且这是SSE-AT的问题

#### [SSE-LD](https://www.nexusmods.com/skyrimspecialedition/mods/106185)怎么办？它会被下架或停止更新吗？

- 虽然SSE-AT能够像SSE-LD一样扫描插件文件（.esp、.esm、.esl），但它目前不支持Papyrus脚本（.pex）或MCM翻译（.txt）。
- SSE-LD暂时会保持在线，但除了一些错误修复外，不要期望有任何重大更新或更改。
- 一旦SSE-AT支持从翻译中提取非插件文件，SSE-LD将完全停止更新，GitHub仓库将被归档（但保持公开）。

#### 支持哪些语言？

- SSE-AT支持游戏和Nexus Mods支持的所有语言。
- 其他语言可能有效或无效。不提供对这些语言的支持。

# 贡献

## 1. 反馈（建议/问题）

如果您遇到问题/错误或有建议，请在上面的"Issues"选项卡下创建一个问题。

## 2. 代码贡献

### 1. 安装要求

1. 安装Python 3.11（确保将其添加到PATH！）
2. 克隆仓库
3. 在仓库文件夹中打开终端
4. 创建虚拟环境并通过运行以下命令激活它：
   `python -m venv .venv`
5. 输入以下命令安装所有要求：
   `pip install -r requirements.txt`

### 2. 从源代码执行

1. 在src文件夹中打开终端
2. 执行主文件
   `python app.py`

### 3. 编译和构建可执行文件

1. 在激活虚拟环境的情况下，从此仓库的根文件夹运行`build.bat`。
2. 可执行文件和所有依赖项都构建在main.dist文件夹中。

## 3. Beta测试

如果您有兴趣测试SSE-AT的预发布版本，请加入上面的Discord服务器。

## 4. 维护主列表
如果您有兴趣为您的语言维护主列表，请通过上面链接的Discord服务器联系我们（@cutleast或@whusten）！

# 致谢

- Qt by [The Qt Company Ltd](https://qt.io)
- [lingua-py](https://github.com/pemistahl/lingua-py) by [Peter M. Stahl](https://github.com/pemistahl)
- [Nuitka](https://github.com/Nuitka/Nuitka)
- [DynamicStringDistributor](https://github.com/SkyHorizon3/SSE-Dynamic-String-Distributor) by [SkyHorizon](https://github.com/SkyHorizon3)
- Icon by [Wuerfelhusten](https://nexusmods.com/users/122160268)
- Editor QoL Improvements by [FuchieSteph](https://github.com/FuchieSteph)
