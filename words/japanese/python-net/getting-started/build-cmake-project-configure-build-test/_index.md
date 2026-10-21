---
category: general
date: 2026-07-06
description: CMakeプロジェクトをステップバイステップで構築します。CMakeの設定方法、ビルド方法、そして信頼性の高いテストのためにCTestを実行する方法を学びましょう。
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: ja
og_description: 明確な手順でCMakeプロジェクトを迅速にビルドします。このガイドでは、CMakeの設定方法、CMakeのビルド方法、そしてCTestの実行方法を示します。
og_title: CMakeプロジェクトのビルド：設定、ビルド、テストガイド
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
title: CMakeプロジェクトのビルド：設定、ビルド、テスト
url: /ja/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CMake プロジェクトをビルド: 設定、ビルド、テスト

StackOverflow を何時間も探さずに **CMake プロジェクトをビルド** する方法を考えたことはありませんか？ あなただけではありません。ほとんどの開発者は、シンプルな `CMakeLists.txt` から再現可能なビルドパイプラインへ移行しようとすると同じ壁にぶつかります。

このチュートリアルでは、*CMake の設定方法*、*CMake のビルド方法*、そして *CTest の実行方法* の全プロセスを順に解説します。最終的に、どのマシンでも実行できるクリーンで再現可能なビルドが手に入ります。最後まで進めば、余計なスクリプトなしで自分のリポジトリにコピー＆ペーストできる動作例が得られます。

## Prerequisites — 開始前に必要なもの

作業を始める前に、以下が揃っていることを確認してください。

- 最近の CMake バージョン（3.20 以上） – 古いバージョンでは本チュートリアルで使用するフラグが利用できません。
- プラットフォームがサポートする C++ コンパイラ（gcc、clang、MSVC など）。
- `cmake` と `ctest` が使用できるターミナルまたはコマンドプロンプト。
- （任意）例のリポジトリをクローンしたい場合は Git。

これらが不足している場合は今すぐ入手してください。後で「command not found」エラーが出ると面倒です。

## Step 1: Configure the CMake Project (Release configuration)

*CMake の設定方法* の最初のステップは、ソースの場所とビルド成果物の出力先を CMake に伝えることです。`-S` フラグでソースディレクトリを指定し、`-B` で別のビルドフォルダを作成、`-D CMAKE_BUILD_TYPE=Release` で最適化ビルドを強制します。

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**なぜ重要か:** ソースとビルドファイルを分離した（*out‑of‑source* ビルド）ことで、ソースの誤変更を防ぎ、後でビルドディレクトリを簡単にクリーンにできます。`Release` フラグはコンパイラに最適化を有効にさせ、最終バイナリに通常求められる設定です。

> **プロのコツ:** デバッグ用ビルドが必要なときは `Release` を `Debug` に置き換えるだけです。同じコマンドで動作し、CMake が残りを処理します。

## Step 2: Build the Configured Project

設定ステップで生成された Makefile や Visual Studio プロジェクトファイルを使って、実際にコードをコンパイルします。`--build` オプションは基盤となるビルドツール（`make`、`ninja`、`MSBuild` など）を抽象化するため、Linux、macOS、Windows すべてで同じコマンドが使えます。

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**内部で何が起きているか？** CMake は前ステップで作成された `CMakeCache.txt` を読み取り、適切なビルドツールを判断し、正しいフラグで呼び出します。これが *CMake のビルド方法* の核心で、`make` か `ninja` かを覚えておく必要はありません。CMake が自動で処理します。

マルチコアマシンでビルドを高速化したい場合は、コマンドの後に `-- -j$(nproc)`（Linux/macOS）または `-- /m`（Windows）を付加してください。

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Step 3: Run the Example Tests with Detailed Output

テストは実際に動くかどうかを確認する重要な工程です。CMake には `ctest` が同梱されており、`add_test()` で登録されたテストを自動で検出・実行できます。テストを実行し、詳細な出力を得るには、まずビルドディレクトリに移動するための `-E chdir` ヘルパーを使います。

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**`--verbose` を使う理由:** 各テストのコマンドライン、終了コード、テスト自身が出力した内容がすべて表示されます。*CTest の実行方法* を学ぶ際に、裏で何が起きているかを正確に把握できるため必須です。

典型的な出力例は以下の通りです。

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

テストが失敗した場合でも、詳細ログに失敗したコマンドとエラーメッセージが含まれるため、デバッグが格段に速くなります。

## Step 4: Automate the Whole Workflow (Optional)

多くのプロジェクトでは、設定・ビルド・テストを一度のコマンドで実行したいものです。シンプルな Bash（または PowerShell）スクリプトで実現できます。

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

`run_all.sh` として保存し、実行権限を付与（`chmod +x run_all.sh`）すれば、**cmake ビルドとテスト** の再現可能なパイプラインが完成します。これを任意の CI システム（GitHub Actions、GitLab CI、Azure Pipelines など）に組み込めます。

## Edge Cases & Common Pitfalls

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Missing compiler** | CMake aborts with “No CMAKE_CXX_COMPILER could be found.” | Install a compiler (`sudo apt install build-essential` on Ubuntu, `xcode-select --install` on macOS). |
| **Out‑of‑source folder already exists** | CMake may refuse to reconfigure if the folder contains stale files. | Delete the `build` directory (`rm -rf build`) or run `cmake --fresh` (CMake 3.24+). |
| **CTest cannot find tests** | `add_test()` was never called or the test executable failed to compile. | Verify that `add_test(NAME MyTest COMMAND MyTestExe)` appears in `CMakeLists.txt` and that the target builds. |
| **Parallel builds race on custom commands** | Some custom commands are not marked as `DEPENDS`, leading to nondeterministic failures. | Add proper `add_custom_command(... DEPENDS ...)` entries. |

これらの細かいポイントを理解すれば、壊れやすいビルドと堅牢な CI パイプラインの差がはっきりします。

## Visual Overview (Alt text includes primary keyword)

![Diagram showing the flow of configuring, building, and testing a CMake project](/images/cmake-workflow.png "Build CMake Project workflow diagram")

## Recap – What You’ve Learned

最初の疑問は *CMake プロジェクトをどうビルドするか* でした。最後には、クリーンな out‑of‑source ビルドで **CMake を設定** し、汎用的な `--build` フラグで **CMake をビルド**、そして **CTest を詳細出力付きで実行** できるようになりました。また、3 つのステップをまとめたスクリプトも手に入れ、完全な **cmake ビルドとテスト** ワークフローを実現しています。

## What’s Next?

- **カバレッジレポートの追加** – `gcov` や `llvm-cov` を統合し、CTest が結果を公開できるようにする。  
- **クロスコンパイル** – 組み込みデバイス向けに `-DCMAKE_TOOLCHAIN_FILE` を活用する。  
- **パッケージ作成** – `cpack` を使ってバイナリを配布用にバンドルする。  
- **CI への統合** – スクリプトを GitHub Actions ワークフローに組み込み、プルリクエストごとに自動実行させる。

ビルドタイプを変えてみたり、テストを増やしたり、例のソースを自分のプロジェクトに差し替えてみたり、自由に実験してください。今回学んだパターンは、ユーティリティから大規模マルチモジュールシステムまで、あらゆる CMake ベースのコードベースに適用できます。

Happy building, and may your CMake builds always be reproducible!

## What Should You Learn Next?

以下のチュートリアルは、本ガイドで示したテクニックを応用できる関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、API 機能の習得や代替実装アプローチの探求に役立ちます。

- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Display Aspose.Words Version in Python and .NET&#58; A Step-by-Step Guide](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}