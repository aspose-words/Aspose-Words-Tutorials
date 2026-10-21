---
category: general
date: 2026-07-06
description: 一步一步构建 CMake 项目。学习如何配置 CMake、如何构建 CMake，以及如何运行 CTest 进行可靠的测试。
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: zh
og_description: 快速构建 CMake 项目，步骤清晰。本指南展示了如何配置 CMake、如何构建 CMake，以及如何运行 CTest。
og_title: 构建 CMake 项目：配置、构建与测试指南
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 构建 CMake 项目：配置、构建与测试
url: /zh/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 构建 CMake 项目：配置、构建与测试

是否曾经想过 **构建 CMake 项目** 却要在 StackOverflow 上耗费数小时寻找答案？你并不是唯一的遇到这种情况的人。大多数开发者在尝试从一个简单的 `CMakeLists.txt` 转向可复现的构建流水线时，都会卡在同一个坑。

在本教程中，我们将完整演示整个过程——*如何配置 CMake*、*如何构建 CMake*、以及 *如何运行 CTest*——让你得到一个干净、可重复的构建，能够在任何机器上运行。结束时，你将拥有一个可以直接复制粘贴到自己仓库的完整示例，无需额外脚本。

## 前置条件 — 开始之前需要准备的内容

在深入之前，请确保你已经具备：

- 最近的 CMake 版本（3.20 或更新）——旧版本缺少我们将使用的一些标志。
- 你的平台支持的 C++ 编译器（gcc、clang、MSVC 等）。
- 能够访问 `cmake` 和 `ctest` 的终端或命令提示符。
- （可选）Git，用于克隆示例仓库，以便与你的源码保持一致。

如果缺少上述任意项，请立即安装，否则后续会出现 “command not found” 错误，十分烦人。

## 第一步：配置 CMake 项目（Release 配置）

当你 *how to configure CMake* 时，首先要告诉 CMake 源码所在位置以及构建产物的输出目录。`-S` 标志指向源码目录，`-B` 用于创建独立的构建文件夹，`-D CMAKE_BUILD_TYPE=Release` 强制使用优化构建。

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**为什么这很重要：** 将源码与构建文件分离（`out‑of‑source` 构建）可以防止意外修改源码，并且以后清理构建目录也非常简单。`Release` 标志还会让编译器开启优化，这通常是最终二进制文件所需要的。

> **小技巧：** 如果需要调试构建，只需将 `Release` 换成 `Debug`。同一条命令即可——CMake 会自行处理其余工作。

## 第二步：构建已配置的项目

配置步骤生成了所有必要的 Makefile 或 Visual Studio 项目文件后，你就可以真正编译代码了。`--build` 选项会抽象底层构建工具（`make`、`ninja`、`MSBuild` 等），因此同一条命令可在 Linux、macOS 和 Windows 上通用。

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**内部到底发生了什么？** CMake 读取上一步生成的 `CMakeCache.txt`，确定合适的构建工具，并使用正确的标志调用它。这就是 *how to build CMake* 的核心——你不必记住是使用 `make` 还是 `ninja`，CMake 会为你完成。

如果想在多核机器上加速构建，可在命令后添加 `-- -j$(nproc)`（Linux/macOS）或 `-- /m`（Windows）：

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## 第三步：运行示例测试并显示详细输出

测试是检验成果的关键环节。CMake 自带 `ctest`，它可以发现并运行通过 `add_test()` 添加到 `CMakeLists.txt` 的任何测试。要执行测试并查看详细输出，先使用 `-E chdir` 辅助命令切换到构建目录：

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**为什么要使用 `--verbose`？** 它会打印每个测试的命令行、退出码以及测试本身输出的所有信息。这在学习 *how to run CTest* 时尤为重要，因为它能清晰展示背后发生的每一步。

典型输出如下：

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

如果某个测试失败，详细日志会包含失败的命令及错误信息，从而大幅加快调试速度。

## 第四步：自动化完整工作流（可选）

对于多数项目，你可能希望只用一行命令完成配置、构建和测试。可以使用下面的 Bash（或 PowerShell）脚本实现：

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

将其保存为 `run_all.sh`，赋予可执行权限（`chmod +x run_all.sh`），即可得到一个可复现的 **cmake build and test** 流水线，随时可以放入任何 CI 系统（GitHub Actions、GitLab CI、Azure Pipelines 等）。

## 边缘情况与常见陷阱

| 情况 | 需要注意的点 | 解决方案 |
|-----------|-------------------|-----|
| **缺少编译器** | CMake 会报错 “No CMAKE_CXX_COMPILER could be found.” | 安装编译器（Ubuntu 上 `sudo apt install build-essential`，macOS 上 `xcode-select --install`）。 |
| **out‑of‑source 文件夹已存在** | 如果文件夹中残留旧文件，CMake 可能拒绝重新配置。 | 删除 `build` 目录（`rm -rf build`）或使用 `cmake --fresh`（CMake 3.24+）。 |
| **CTest 找不到测试** | 未调用 `add_test()` 或测试可执行文件编译失败。 | 确认 `CMakeLists.txt` 中出现 `add_test(NAME MyTest COMMAND MyTestExe)`，并且目标能够成功构建。 |
| **并行构建时自定义命令竞争** | 某些自定义命令未标记 `DEPENDS`，导致不确定性失败。 | 为自定义命令添加正确的 `add_custom_command(... DEPENDS ...)`。 |

掌握这些细节，才能让构建从“偶发”变为“稳如磐石”的 CI 流水线。

## 可视化概览（Alt 文本包含主要关键词）

![展示配置、构建和测试 CMake 项目流程的图示](/images/cmake-workflow.png "Build CMake Project workflow diagram")

## 小结 – 你学到了什么

我们从核心问题出发：*how to build CMake project*。现在，你已经掌握了如何使用干净的 out‑of‑source 方式 **配置 CMake**，如何通过通用的 `--build` 标志 **构建 CMake**，以及如何使用 **verbose** 模式 **运行 CTest** 来验证一切是否正常。你还拥有一个即插即用的脚本，将三步串联起来，形成完整的 **cmake build and test** 工作流。

## 接下来该做什么？

- **添加覆盖率报告** – 集成 `gcov` 或 `llvm-cov`，让 CTest 发布结果。
- **交叉编译** – 探索 `-DCMAKE_TOOLCHAIN_FILE`，在嵌入式设备上构建。
- **生成软件包** – 使用 `cpack` 打包二进制文件以供分发。
- **CI 集成** – 将脚本复制到 GitHub Actions 工作流中，让每次 Pull Request 都自动运行。

随意尝试不同的构建类型，添加更多测试，或将示例源码替换为自己的项目。我们今天覆盖的模式适用于任何基于 CMake 的代码库，无论是小工具还是大型多模块系统。

祝构建愉快，愿你的 CMake 构建始终可复现！

## 接下来应该学习什么？

以下教程与本指南紧密相关，进一步扩展了本篇中演示的技巧。每个资源都提供完整可运行的代码示例以及逐步解释，帮助你掌握更多 API 功能，并在自己的项目中探索替代实现方式。

- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Display Aspose.Words Version in Python and .NET&#58; A Step-by-Step Guide](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}