# abc-decompiler

abc-decompiler 基于 [jadx](https://github.com/skylot/jadx/) 和 [abcde](https://github.com/Yricky/abcde/tree/main) 实现的鸿蒙 [abc/方舟字节码](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V5/arkts-bytecode-fundamentals-V5#%E6%9C%AF%E8%AF%AD%E5%92%8C%E7%BA%A6%E6%9D%9F) 的反编译工具.

目前还在开发中，欢迎有兴趣的兄弟一起讨论、研究.

![qq.png](qq.png)

## #1 使用方法

下载或者编译 jar 包，然后运行把 hap 文件解压缩，将其中的 modules.abc 字节码文件拖入工具

![img.png](img.png)


## #2 进展与计划

分析了方舟的字节码，有很大部分与 DEX 字节码语义相近，且 jadx 比较成熟，于是基于 jadx 实现反编译器。

目前的进展：
- 修改输入部分代码，可以拖入 abc 文件分析
- 实现了部分字节码，目前实现指令 122 条，字节码总数：[282 条](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V5/arkts-bytecode-fundamentals-V5#%E6%9C%AF%E8%AF%AD%E5%92%8C%E7%BA%A6%E6%9D%9F).

计划：
- 先补齐字节码，让代码能看.
- 开发 abc 的反编译优化模块（在 jadx 中为 Pass），优化代码显示，让代码好看.
- 实现数据流分析，自动化漏洞挖掘.


## #3 关键代码路径

字节码解析: [jadx-core/src/main/java/jadx/core/dex/instructions/InsnDecoder.java](./jadx-core/src/main/java/jadx/core/dex/instructions/InsnDecoder.java)

jadx 自带的 Pass: [jadx-core/src/main/java/jadx/core/dex/visitors](./jadx-core/src/main/java/jadx/core/dex/visitors)


## #4 编译

需要编译 patch 过的 [abcde](https://github.com/ohos-decompiler/abcde) 库（增加导出了一个接口）

