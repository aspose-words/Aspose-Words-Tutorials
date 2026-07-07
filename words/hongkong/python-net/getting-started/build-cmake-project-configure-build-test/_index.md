---
category: general
date: 2026-07-06
description: 一步一步構建 CMake 專案。學習如何配置 CMake、如何構建 CMake，以及如何執行 CTest 以進行可靠的測試。
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: zh-hant
og_description: 快速且清晰地構建 CMake 專案。本指南說明如何配置 CMake、如何構建 CMake，以及如何執行 CTest。
og_title: 構建 CMake 專案：配置、構建與測試指南
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
title: 建構 CMake 專案：設定、建構與測試
url: /zh-hant/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建置 CMake 專案：設定、建置與測試

有沒有想過要 **build CMake project**，卻不想花上好幾個小時在 StackOverflow 上搜尋？你並不是唯一有這種感受的人。大多數開發者在從簡單的 `CMakeLists.txt` 轉向可重現的建置流程時，都會卡在同樣的地方。

在本教學中，我們會一步一步走過整個流程——*如何設定 CMake*、*如何建置 CMake*，以及 *如何執行 CTest*——讓你得到一個乾淨、可重複的建置，能在任何機器上執行。完成後，你會得到一個可直接複製貼上到自己儲存庫的範例，無需額外腳本。

## 前置條件 — 開始前需要的項目

在深入之前，請先確認你已具備：

- 最近的 CMake 版本（3.20 以上）——較舊的版本缺少我們將使用的某些旗標。
- 你的平台支援的 C++ 編譯器（gcc、clang、MSVC 等）。
- 能夠存取 `cmake` 與 `ctest` 的終端機或命令提示字元。
- （可選）Git，用來克隆範例儲存庫，若你想跟著原始碼操作的話。

如果缺少上述任一項，請立即安裝，否則稍後會遇到「command not found」之類的錯誤，真的很不爽。

## 第一步：設定 CMake 專案（Release 組態）

當你 *how to configure CMake* 時，第一件事就是告訴 CMake 原始碼所在位置以及建置產出要放在哪裡。`-S` 旗標指向來源目錄，`-B` 會建立一個獨立的建置資料夾，`-D CMAKE_BUILD_TYPE=Release` 則強制使用最佳化建置。

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**為什麼這很重要：** 將來源檔與建置檔分離（`out‑of‑source` 建置）可以避免意外修改原始碼，且日後清除建置目錄也非常簡單。`Release` 旗標同時會告訴編譯器啟用最佳化，這通常是最終二進位檔的需求。

> **小技巧：** 若需要 Debug 版來除錯，只要把 `Release` 換成 `Debug` 即可。指令本身不變——CMake 會自行處理其餘。

## 第二步：建置已設定好的專案

設定步驟產生了所有必要的 makefile 或 Visual Studio 專案檔後，就可以正式編譯程式碼了。`--build` 參數會抽象化底層建置工具（`make`、`ninja`、`MSBuild` 等），因此同一指令可在 Linux、macOS 與 Windows 上使用。

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**背後發生了什麼？** CMake 會讀取先前步驟產生的 `CMakeCache.txt`，判斷適合的建置工具，並以正確的旗標呼叫它。這就是 *how to build CMake* 的核心——你不必記得自己在用 `make` 還是 `ninja`；CMake 會幫你處理。

如果想在多核心機器上加速建置，可在指令後加入 `-- -j$(nproc)`（Linux/macOS）或 `-- /m`（Windows）：

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## 第三步：執行範例測試並顯示詳細輸出

測試是檢驗成果的關鍵。CMake 內建 `ctest`，它能自動偵測並執行 `CMakeLists.txt` 中透過 `add_test()` 加入的測試。若要執行測試並看到詳細輸出，先使用 `-E chdir` 進入建置目錄：

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**為什麼要加 `--verbose`？** 它會列印每個測試的指令列、退出代碼，以及測試本身輸出的任何訊息。學習 *how to run CTest* 時，這非常重要，因為它能清楚顯示背後的執行情況。

典型輸出如下：

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

若測試失敗，詳細日誌會包含失敗的指令與錯誤訊息，讓除錯速度大幅提升。

## 第四步：自動化整個工作流程（可選）

對於多數專案，你可能會想要一行指令就完成設定、建置與測試。只要寫一個簡單的 Bash（或 PowerShell）腳本即可：

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

將檔案存為 `run_all.sh`，賦予執行權限（`chmod +x run_all.sh`），就得到一條可重現的 **cmake build and test** 流程，隨時可以放入任何 CI 系統（GitHub Actions、GitLab CI、Azure Pipelines…隨你挑）。

## 邊緣案例與常見陷阱

| 情境 | 需要留意的地方 | 解決方式 |
|-----------|-------------------|-----|
| **找不到編譯器** | CMake 會中止並顯示 “No CMAKE_CXX_COMPILER could be found.” | 安裝編譯器（Ubuntu 上 `sudo apt install build-essential`，macOS 上 `xcode-select --install`）。 |
| **out‑of‑source 資料夾已存在** | 若資料夾內有舊檔，CMake 可能拒絕重新設定。 | 刪除 `build` 目錄（`rm -rf build`）或使用 `cmake --fresh`（CMake 3.24 以上）。 |
| **CTest 找不到測試** | 沒有呼叫 `add_test()`，或測試執行檔編譯失敗。 | 確認 `CMakeLists.txt` 中有 `add_test(NAME MyTest COMMAND MyTestExe)`，且目標能成功編譯。 |
| **平行建置時自訂指令競爭** | 某些自訂指令未標記 `DEPENDS`，導致不確定的失敗。 | 為自訂指令加入正確的 `add_custom_command(... DEPENDS ...)`。 |

了解這些細節，就能避免不穩定的建置，打造堅如磐石的 CI 流程。

## 視覺概覽（Alt text 包含主要關鍵字）

![顯示 CMake 專案設定、建置與測試流程的圖示](/images/cmake-workflow.png "建置 CMake 專案工作流程圖")

## 重點回顧 – 你學到了什麼

我們從最核心的問題出發：*how to build CMake project*。現在你已掌握如何使用乾淨的 out‑of‑source 方式 **configure CMake**、如何利用通用的 `--build` 旗標 **build CMake**，以及如何以 **verbose** 模式 **run CTest** 來驗證一切正常。你也得到一個即時可用的腳本，將三個步驟串起，形成完整的 **cmake build and test** 工作流程。

## 接下來要做什麼？

- **加入覆蓋率報告** – 整合 `gcov` 或 `llvm-cov`，讓 CTest 發布覆蓋率結果。
- **交叉編譯** – 探索 `-DCMAKE_TOOLCHAIN_FILE`，在嵌入式裝置上建置。
- **套件產出** – 使用 `cpack` 打包二進位檔以供發佈。
- **CI 整合** – 把腳本放入 GitHub Actions 工作流程，讓每次 Pull Request 都自動執行。

歡迎隨意嘗試不同的建置類型、加入更多測試，或把範例原始碼換成自己的專案。我們今天討論的模式適用於任何基於 CMake 的程式碼庫，無論是小工具還是大型多模組系統。

祝建置順利，願你的 CMake 建置永遠可重現！

## 你接下來該學什麼？

以下教學與本篇內容緊密相關，能在此基礎上延伸技術。每個資源都提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在自己的專案中探索不同的實作方式。

- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Display Aspose.Words Version in Python and .NET&#58; A Step-by-Step Guide](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}