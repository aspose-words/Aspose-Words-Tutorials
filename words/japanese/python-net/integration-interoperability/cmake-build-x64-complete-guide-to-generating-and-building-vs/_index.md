---
category: general
date: 2026-07-16
description: cmake build x64 チュートリアルは、CMake を使用して Visual Studio 2022 のソリューションを生成し、64
  ビットホスト上で VS プロジェクトをビルドする方法を示します。ソースディレクトリの設定手順も含まれています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: ja
lastmod: 2026-07-16
og_description: cmake ビルド x64 の解説：ソースディレクトリの設定方法、Visual Studio 2022 ソリューションの生成方法、そして
  64 ビットホスト上で VS プロジェクトをコンパイルする方法を学びましょう。
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmakeでx64ビルド – VS 2022ソリューションを生成・ビルドするステップバイステップガイド
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
title: CMake ビルド x64 – VS 2022 プロジェクトの生成とビルド完全ガイド
url: /ja/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – VS 2022 プロジェクトの生成とビルド 完全ガイド

64 ビットの Visual Studio ソリューションを **CMake** で作成する方法で、髪の毛をむしりたくなることはありませんか？ あなたは一人ではありません。このチュートリアルでは、ソースディレクトリを設定し、Visual Studio 2022 用のジェネレータを実行し、最後に VS プロジェクトをビルドする **cmake build x64** ワークフローを、数行のシンプルな Bash コマンドで解説します。

ガイドの最後までに、任意のリポジトリに貼り付けられる再現可能なスクリプトと、必要に応じてカスタマイズできる基礎概念を習得できます。

---

## 学べること

- **set source directory** を正しく設定し、CMake が `CMakeLists.txt` の場所を認識できるようにする。  
- **cmake generate visual studio** – 正しいホストとアーキテクチャフラグで Visual Studio 2022 ジェネレータを呼び出す。  
- 生成されたソリューションを **cmake build x64** でビルドし、必要に応じて Release 構成を選択する。  
- 64 ビットマシンで **build vs project** を行う際の一般的な落とし穴を理解する。  

事前に CMake の高度な知識は不要です。ターミナルと最新の Visual Studio があれば始められます。

---

## 前提条件

| 要件 | 重要な理由 |
|------|------------|
| CMake ≥ 3.20 | 64 ビットビルドに使用する `-Thost=` と `-Ax64` フラグをサポートします。 |
| Visual Studio 2022 (Community, Professional, or Enterprise) | ジェネレータ `Visual Studio 17 2022` がこのバージョンを指します。 |
| Bash 互換シェル (Git Bash, WSL, PowerShell with `bash` alias) | スクリプトは可読性のため Bash 構文を使用しています。 |
| 有効な `CMakeLists.txt` を含むソースツリー | CMake はこれが無いとソリューションを生成できません。 |

これらが揃っていない場合は、まずインストールしてください。CMake は <https://cmake.org/download/>、VS 2022 は Microsoft のインストーラから入手できます。

---

## Step 1 – Set the Source and Build Directories (`set source directory`)

CMake を呼び出す前に、**どこ**にプロジェクトファイルがあるかを CMake に伝える必要があります。パスをハードコーディングするとスクリプトが壊れやすくなるため、プロジェクトごとに調整できる環境変数を使用します。

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Why this matters:**  
> CMake は *source directory*（`SRC_DIR`）をプロジェクトのルートとして扱います。*build directory*（`BUILD_DIR`）はすべての中間ファイル、キャッシュ、最終的な `.sln` が格納される場所です。これらを分離しておくことで、ソースツリーが汚染されず、`rm -rf "$BUILD_DIR"` で簡単にクリーンアップできます。

`YOUR_DIRECTORY` を任意の絶対パスまたは相対パスに置き換えてください。そのフォルダーに `CMakeLists.txt` が含まれていることを確認してください。

---

## Step 2 – Generate a Visual Studio 2022 Solution (`cmake generate visual studio`)

次に、CMake に **x64** をターゲットとした VS 2022 ソリューションを出力させます。重要なフラグは以下の通りです。

- `-G "Visual Studio 17 2022"` – VS 2022 ジェネレータを選択。  
- `-Thost=x64` – CMake に *host*（IDE）が 64 ビットプロセスとして実行されることを伝える。  
- `-Ax64` – 生成されるプロジェクトを x64 アーキテクチャ向けに強制。

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **What happens under the hood?**  
> CMake は `$SRC_DIR` から `CMakeLists.txt` を読み取り、`add_executable()` や `add_library()` の呼び出しを解決した上で、`.sln` ファイルと一連の `.vcxproj` ファイルを `$BUILD_DIR` 内に作成します。これらのプロジェクトファイルは Visual Studio で開くことも、コマンドラインからビルドすることも可能です。

コマンド実行後に `-- Configuring done` と `-- Generating done` で終わる長い設定メッセージが表示されたら、**cmake generate visual studio** が正常に完了しています。

---

## Step 3 – Build the Generated Solution (`cmake build x64`)

ソリューションが生成されたら、次はコンパイルです。CMake がビルドを駆動し、内部で MSBuild を呼び出します。

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Why use `--config Release`?**  
> Visual Studio のプロジェクトは複数の構成（Debug、Release、RelWithDebInfo など）をサポートします。`Release` を指定すると、バイナリが本番向けに最適化され、生成された `.exe` や `.dll` がビルドツリー内の `Release/` ディレクトリに配置されます。

Debug ビルドが必要な場合は `Release` を `Debug` に置き換えてください。コマンドの挙動は同じで、**how to use CMake** の構成切替はフラグを変えるだけです。

---

## Step 4 – Verify the Build (`build vs project` sanity check)

ビルドが成功すると、実行可能ファイルまたはライブラリが生成されます。存在を確認しましょう。

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Common pitfalls:**  
> - `CMakeLists.txt` を変更した後にジェネレータステップを実行し忘れると、このチェックは失敗します。  
> - 32 ビットと 64 ビットのツールチェーンを混在させるとリンカエラーが発生します。`-Ax64` は常に一貫させてください。  
> - “MSB3073” エラーが出た場合、ポストビルドステップ（リソースコピーなど）が失敗していることが多いので、出力を確認して原因を特定してください。

---

## Step 5 – Clean Up and Re‑run (Iterating on a `cmake build x64`)

開発中はしばしばゼロからビルドし直す必要があります。最もシンプルな方法はビルドフォルダーを削除してやり直すことです。

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tip:**  
> マルチコンフィグジェネレータ（Visual Studio など）では `-DCMAKE_BUILD_TYPE=Release` は必須ではありませんが、Ninja のようなシングルコンフィグジェネレータに切り替える際には便利です。

---

## Step 6 – Extending the Script (Advanced `cmake generate visual studio` scenarios)

プロジェクトがサブディレクトリにある場合や、カスタム定義を渡したい場合はどうしますか？ CMake は `-D` 引数でそれらを受け取れます。

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

これで生成された VS ソリューションには `MyFeature_ENABLED` マクロが定義され、インストールターゲットは `/opt/myapp` 配下にファイルを配置します。**how to use CMake** の基本的な 3 ステップを超えた柔軟性を示す例です。

---

## Expected Output

スクリプトを最初から最後まで実行すると、ターミナルには次のような出力が表示されます。

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

何か問題が起きた場合、CMake は `CMakeLists.txt` の該当行や不足している SDK コンポーネントを指摘するエラーメッセージを出します。デバッグが非常に容易です。

---

## Conclusion

**cmake build x64** を実行するために必要なすべてを網羅しました：ソースディレクトリの設定、**cmake generate visual studio** ステップの呼び出し、生成された **build vs project** のコンパイル、そして出力の検証です。スクリプトはコンパクトでポータブル、CI パイプラインやローカル開発フローへの組み込みもすぐにできます。

次に試すべきこと：

- `ctest` でユニットテストを実行する。  
- Ninja ジェネレータ（`-G Ninja`）に切り替えてインクリメンタルビルドを高速化する。  
- `CMakePresets.json` を使って、ここで入力したフラグをプリセットとして保存する。

ぜひ実験し、失敗し、再ビルドしてください。これが CMake を効果的に使いこなす最速の学習方法です。Happy building!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには動作するコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}