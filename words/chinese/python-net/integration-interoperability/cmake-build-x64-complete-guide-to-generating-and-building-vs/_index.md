---
category: general
date: 2026-07-16
description: cmake build x64 教程展示了如何使用 CMake 生成 Visual Studio 2022 解决方案并在 64 位主机上构建
  VS 项目。包括设置源目录的步骤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: zh
lastmod: 2026-07-16
og_description: cmake 构建 x64 详解：学习如何设置源目录、生成 Visual Studio 2022 解决方案，以及在 64 位主机上编译
  VS 项目。
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake 构建 x64 – 生成并构建 VS 2022 解决方案的分步指南
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
url: /zh/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – 完整指南：生成并构建 VS 2022 项目

是否曾经想过 **如何使用 CMake** 来生成 64 位的 Visual Studio 解决方案，却不想抓狂？你并不孤单。在本教程中，我们将演示一个 **cmake build x64** 工作流，设置源码目录，运行 Visual Studio 2022 的生成器，最后构建 VS 项目——全部只需几条简洁的 Bash 命令。

阅读完本指南后，你将拥有一个可复用的脚本，能够直接放入任意仓库，同时对背后的概念有深入理解，便于根据自己的需求进行调整。

---

## 你将学到

- 正确 **设置源码目录**，让 CMake 知道 `CMakeLists.txt` 所在位置。  
- **cmake generate visual studio** – 使用正确的主机和架构标志调用 Visual Studio 2022 生成器。  
- 对生成的解决方案执行 **cmake build x64**，可选地指定 Release 配置。  
- 理解在 64 位机器上 **build vs project** 时常见的陷阱。  

无需事先掌握 CMake 高级技巧，只需一个终端和最近的 Visual Studio 安装即可。

---

## 前置条件

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | 支持用于 64 位构建的 `-Thost=` 和 `-Ax64` 标志。 |
| Visual Studio 2022（Community、Professional 或 Enterprise） | 生成器 `Visual Studio 17 2022` 指向此版本。 |
| 支持 Bash 的终端（Git Bash、WSL、带 `bash` 别名的 PowerShell） | 以下脚本使用 Bash 语法，便于阅读。 |
| 包含有效 `CMakeLists.txt` 的源码树 | 没有此文件 CMake 无法生成解决方案。 |

如果缺少上述任意项，请先安装——CMake 可从 <https://cmake.org/download/> 下载，VS 2022 可通过 Microsoft 安装程序获取。

---

## 第 1 步 – 设置源码和构建目录（`set source directory`）

在调用 CMake 之前，需要告诉它 **在哪里** 查找项目文件。硬编码路径会导致脚本脆弱，因此我们使用可以按项目自行调整的环境变量。

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **为什么重要：**  
> CMake 将 *源码目录*（`SRC_DIR`）视为项目根目录。*构建目录*（`BUILD_DIR`）则存放所有中间文件、缓存以及最终的 `.sln`。将两者分离可以避免污染源码树，并且清理工作变得非常简单（`rm -rf "$BUILD_DIR"`）。

你可以将 `YOUR_DIRECTORY` 替换为任意绝对或相对路径，只要该文件夹中包含 `CMakeLists.txt` 即可。

---

## 第 2 步 – 生成 Visual Studio 2022 解决方案（`cmake generate visual studio`）

现在让 CMake 生成一个面向 **x64** 的 VS 2022 解决方案。关键标志如下：

- `-G "Visual Studio 17 2022"` – 选择 VS 2022 生成器。  
- `-Thost=x64` – 告诉 CMake IDE（主机）以 64 位进程运行。  
- `-Ax64` – 强制生成的项目面向 x64 架构。

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **内部发生了什么？**  
> CMake 从 `$SRC_DIR` 读取 `CMakeLists.txt`，解析所有 `add_executable()` 与 `add_library()` 调用，然后在 `$BUILD_DIR` 中创建 `.sln` 文件以及一系列 `.vcxproj` 文件。这些项目文件即可在 Visual Studio 中打开，或通过命令行构建。

如果运行该命令后看到一长串配置信息，以 `-- Configuring done` 和 `-- Generating done` 结尾，说明已成功完成 **cmake generate visual studio** 步骤。

---

## 第 3 步 – 构建生成的解决方案（`cmake build x64`）

解决方案已经就绪，接下来自然是编译它。CMake 可以为你驱动构建，内部调用 MSBuild。

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **为何使用 `--config Release`？**  
> Visual Studio 项目支持多种配置（Debug、Release、RelWithDebInfo 等）。指定 `Release` 可确保生成的二进制文件已针对生产环境进行优化，并且生成的 `.exe` 或 `.dll` 会位于构建树中的 `Release/` 目录下。

如果想要 Debug 构建，只需将 `Release` 替换为 `Debug`。命令的工作方式相同，说明 **how to use CMake** 在不同配置之间的切换仅是更换此标志而已。

---

## 第 4 步 – 验证构建（`build vs project` 健全性检查）

一次成功的编译应当留下可执行文件或库。让我们确认它们是否存在：

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **常见陷阱：**  
> - 修改 `CMakeLists.txt` 后忘记重新运行生成器步骤，会导致此检查失败。  
> - 混用 32 位和 64 位工具链会引发链接错误；请始终保持 `-Ax64` 一致。  
> - 若出现 “MSB3073” 错误，通常意味着某个后期构建步骤（如复制资源）失败——检查输出以获取线索。

---

## 第 5 步 – 清理并重新运行（迭代 `cmake build x64`）

在开发过程中，你经常需要从头开始重新构建。最干净的方式是删除构建文件夹后重新开始：

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **小贴士：**  
> 为多配置生成器（如 Visual Studio）添加 `-DCMAKE_BUILD_TYPE=Release` 是可选的，但在切换到单配置生成器（如 Ninja）时会非常有用。

---

## 第 6 步 – 扩展脚本（高级 `cmake generate visual studio` 场景）

如果项目位于子目录，或需要传递自定义定义，该怎么办？CMake 允许使用 `-D` 参数：

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

现在生成的 VS 解决方案将定义 `MyFeature_ENABLED` 宏，且 install 目标会将文件放置到 `/opt/myapp` 下。这展示了 **how to use CMake** 超越基础三步流程的灵活性。

---

## 预期输出

完整运行脚本后，终端应显示类似如下内容：

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

若出现问题，CMake 会输出指向 `CMakeLists.txt` 中出错行或缺失 SDK 组件的错误信息——非常适合快速调试。

---

## 结论

我们已经覆盖了执行 **cmake build x64** 所需的全部内容：设置源码目录、调用 **cmake generate visual studio**、编译得到的 **build vs project**，以及验证输出。该脚本简洁、可移植，适合集成到 CI 流水线或本地开发工作流中。

接下来，你可以探索：

- 使用 `ctest` 添加单元测试执行。  
- 切换到 Ninja 生成器以获得更快的增量构建（`-G Ninja`）。  
- 使用 CMake 预设（`CMakePresets.json`）来保存我们刚才输入的标志。

尽情实验、故意出错，然后再重建——这正是快速掌握 **how to use CMake** 的最佳方式。祝构建愉快！

## 接下来你应该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助你在自己的项目中进一步掌握 API 功能并探索替代实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}