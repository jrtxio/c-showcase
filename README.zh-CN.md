# C Showcase

C 语言代码示例合集，用于学习和快速参考。每个示例演示 C 语言编程中不同的概念或技术。

![C](https://img.shields.io/badge/C-A8B9CC?logo=c&logoColor=white) [![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

[English](README.md) · **中文**

## 功能特性

- **数据结构** —— 循环（环形）缓冲区队列，含入队 / 出队和边界检查
- **自定义协议** —— 基于 UDP 的 LCOU 协议，包含数据包帧封装、校验和验证以及回调模型
- **算法练习** —— LeetCode 题解，展示不同算法技巧（哈希表、双指针）
- **语言解释器** —— MiniLisp，用约 1,000 行 C 实现的 Lisp 解释器，支持闭包、宏和垃圾回收
- **IPC** —— POSIX 共享内存程序，用于进程间通信

## 环境要求

| 依赖 | 用途 / 版本 |
|------|------------|
| 编译器 | GCC 或任何兼容 C99 的编译器 |
| 平台 | Linux 或 macOS（部分示例使用了 POSIX API，如 `sys/ipc.h`、`sys/mman.h`） |
| [UTHash](https://troydhanson.github.io/uthash/) | 用于 LeetCode 哈希表题解 |

## 分类

| 示例 | 说明 | 主题 |
|------|------|------|
| 循环队列 | 循环（环形）缓冲区队列，含入队 / 出队和空 / 满检查 | 数据结构 |
| LCOU 协议 | 基于 UDP 的自定义协议，包含数据包帧封装、校验和验证以及命令处理回调模型 | 网络、协议 |
| LeetCode 题解 | 精选 LeetCode 题目的 C 语言解答（见下文） | 算法 |
| MiniLisp | 用约 1,000 行 C 实现的 Lisp 解释器；支持闭包、宏和复制式 GC（Cheney 算法）。基于 [rui314/minilisp](https://github.com/rui314/minilisp) | 解释器 |
| 共享内存 | POSIX 共享内存 IPC 程序对：写入端创建段，读取端挂载并读取 | IPC |

## 使用方法

### 1. 克隆

```bash
git clone https://github.com/turinglambdaai/c-showcase.git
cd c-showcase
```

### 2. 构建并运行示例

### 循环队列

```bash
gcc circular-queue.c -o circular-queue
./circular-queue
```

### LCOU 协议（lcou）

基于 UDP 的自定义协议实现，包含数据包帧封装、校验和验证以及命令处理回调模型。附带 client 和 server 用于测试。

- `src/lcou.h` / `src/lcou.c` —— 协议库（初始化、发送、接收、校验和）
- `tests/server.c` —— 监听 LCOU 数据包并分发命令的服务端
- `tests/client.c` —— 发送 LCOU 数据包并打印响应的客户端

```bash
# 编译 server 和 client（Linux/macOS）
gcc src/lcou.c tests/server.c -o lcou-server
gcc src/lcou.c tests/client.c -o lcou-client

# 先启动 server，再运行 client
./lcou-server
./lcou-client
```

### LeetCode 题解

精选 LeetCode 题目的 C 语言解答，每道题展示不同的算法技巧。

| 题目 | 文件 | 技巧 |
|------|------|------|
| [1. 两数之和](https://leetcode.com/problems/two-sum/) | `leetcode/1.两数之和.c` | 暴力枚举、哈希表（UTHash） |
| [160. 相交链表](https://leetcode.com/problems/intersection-of-two-linked-lists/) | `leetcode/160.相交链表.c` | 双指针比较 |
| [283. 移动零](https://leetcode.com/problems/move-zeroes/) | `leetcode/283.移动零.c` | 数组移位、双指针交换 |

```bash
# 示例：编译 LeetCode 题解
gcc leetcode/1.两数之和.c -o two-sum
```

### MiniLisp

用约 1,000 行 C 语言实现的 Lisp 解释器。支持整数、符号、cons 单元、闭包、宏以及复制式垃圾回收（Cheney 算法）。

基于 [rui314/minilisp](https://github.com/rui314/minilisp)。

```bash
cd minilisp
make
./minilisp    # 启动 REPL
make test     # 运行测试套件
```

完整的语言文档见 [`minilisp/README.md`](minilisp/README.md)。

### 共享内存

一对演示 POSIX 共享内存 IPC 的程序。写入端创建共享内存段并写入数据；读取端挂载、读取并清理。

```bash
# 编译（Linux）
gcc shared-memory/write.c -o write
gcc shared-memory/read.c -o read

# 先运行写入端，再运行读取端
./write
./read
```

## 项目结构

```
c-showcase/
├── circular-queue/   # 循环（环形）缓冲区队列
├── lcou/             # LCOU UDP 协议库及测试
├── leetcode/         # LeetCode C 题解
├── minilisp/         # 用约 1,000 行 C 实现的 Lisp 解释器
└── shared-memory/    # POSIX 共享内存 IPC 程序
```

## 许可证

基于 [MIT License](LICENSE) 开源。
