# C Showcase

A collection of C code examples for learning and quick reference. Each example demonstrates a different concept or technique in C programming.

![C](https://img.shields.io/badge/C-A8B9CC?logo=c&logoColor=white)

**English** · [中文](README.zh-CN.md)

## Examples

### Circular Queue

A straightforward implementation of a circular (ring) buffer using a fixed-size array. Demonstrates queue initialization, enqueue, dequeue, and boundary checks (empty/full).

```bash
gcc circular-queue.c -o circular-queue
./circular-queue
```

### LCOU Protocol (lcou)

A UDP-based custom protocol implementation featuring packet framing, checksum verification, and a command-handler callback model. Includes a client and server for testing.

- `src/lcou.h` / `src/lcou.c` — Protocol library (init, send, receive, checksum)
- `tests/server.c` — Server that listens for LCOU packets and dispatches commands
- `tests/client.c` — Client that sends LCOU packets and prints responses

```bash
# Compile server and client (Linux/macOS)
gcc src/lcou.c tests/server.c -o lcou-server
gcc src/lcou.c tests/client.c -o lcou-client

# Run server first, then client
./lcou-server
./lcou-client
```

### LeetCode Solutions

Solutions to selected LeetCode problems, each showcasing a different algorithmic technique.

| Problem | File | Techniques |
|---------|------|------------|
| [1. Two Sum](https://leetcode.com/problems/two-sum/) | `leetcode/1.两数之和.c` | Brute force, hash table (UTHash) |
| [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/) | `leetcode/160.相交链表.c` | Two-pointer comparison |
| [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/) | `leetcode/283.移动零.c` | Array shifting, two-pointer swap |

```bash
# Example: compile a LeetCode solution
gcc leetcode/1.两数之和.c -o two-sum
```

### MiniLisp

A Lisp interpreter written in approximately 1,000 lines of C. Supports integers, symbols, cons cells, closures, macros, and a copying garbage collector (Cheney's algorithm).

Based on [rui314/minilisp](https://github.com/rui314/minilisp).

```bash
cd minilisp
make
./minilisp    # Start the REPL
make test     # Run the test suite
```

See [`minilisp/README.md`](minilisp/README.md) for full language documentation.

### Shared Memory

A pair of programs demonstrating POSIX shared memory IPC. The writer creates a shared memory segment and writes data; the reader attaches, reads, and cleans up.

```bash
# Compile (Linux)
gcc shared-memory/write.c -o write
gcc shared-memory/read.c -o read

# Run writer first, then reader
./write
./read
```

## Requirements

- GCC or any C99-compatible compiler
- Linux or macOS (some examples use POSIX APIs such as `sys/ipc.h`, `sys/mman.h`)
- [UTHash](https://troydhanson.github.io/uthash/) (used in LeetCode hash table solution)

## License

This project does not currently include a license file.
