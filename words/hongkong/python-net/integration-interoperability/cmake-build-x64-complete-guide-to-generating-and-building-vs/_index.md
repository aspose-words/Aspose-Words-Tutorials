---
category: general
date: 2026-07-16
description: cmake build x64 教學示範如何使用 CMake 產生 Visual Studio 2022 解決方案，並在 64 位元主機上建置
  VS 專案。包括設定來源目錄的步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: zh-hant
lastmod: 2026-07-16
og_description: cmake 構建 x64 說明：了解如何設定來源目錄、產生 Visual Studio 2022 解決方案，並在 64 位元主機上編譯
  VS 專案。
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake 構建 x64 – 逐步指南：生成與建置 VS 2022 解決方案
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
title: cmake 建置 x64 – 生成與建置 VS 2022 專案的完整指南
url: /zh-hant/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – 完整指南：產生與建置 VS 2022 專案

有沒有想過 **how to use CMake** 來產生 64 位元的 Visual Studio 解決方案，而不至於抓狂？你並不孤單。在本教學中，我們將逐步說明一個 **cmake build x64** 工作流程，設定來源目錄、為 Visual Studio 2022 執行產生器，最後建置 VS 專案——全部只需幾條簡潔的 Bash 指令。

完成本指南後，你將擁有一個可重複使用的腳本，能直接放入任何儲存庫，同時對背後概念有扎實的了解，讓你能依需求自行調整。

---

## 你將學會

- **Set source directory** 正確設定，使 CMake 知道你的 `CMakeLists.txt` 位於何處。  
- **cmake generate visual studio** – 使用正確的主機與架構旗標呼叫 Visual Studio 2022 產生器。  
- 對產生的解決方案執行 **cmake build x64**，可選擇 Release 組態。  
- 了解在 64 位元機器上嘗試 **build vs project** 時常見的陷阱。  

不需要事先掌握 CMake 魔法，只要有終端機與最近的 Visual Studio 安裝即可。

---

## 前置條件

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | 支援用於 64 位元建置的 `-Thost=` 與 `-Ax64` 旗標。 |
| Visual Studio 2022 (Community, Professional, or Enterprise) | 產生器 `Visual Studio 17 2022` 會指向此版本。 |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | 以下腳本使用 Bash 語法以提升可讀性。 |
| Source tree containing a valid `CMakeLists.txt` | 若無此檔案，CMake 無法產生解決方案。 |

若缺少上述任一項，請先安裝——CMake 可從 <https://cmake.org/download/> 下載，VS 2022 則透過 Microsoft 安裝程式取得。

---

## 第一步 – 設定來源與建置目錄 (`set source directory`)

在呼叫 CMake 之前，需要告訴它 **在哪裡** 找到專案檔案。硬編碼路徑會使腳本脆弱，因此我們將使用環境變數，讓你可以依專案自行調整。

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **為什麼這很重要：**  
> CMake 將 *source directory*（`SRC_DIR`）視為專案根目錄。*build directory*（`BUILD_DIR`）則是放置所有中間檔案、快取以及最終 `.sln` 的位置。將兩者分離可避免汙染來源樹，且清理變得簡單（`rm -rf "$BUILD_DIR"`）。

你可以將 `YOUR_DIRECTORY` 替換為任意絕對或相對路徑；只要確保該資料夾內有 `CMakeLists.txt` 即可。

---

## 第二步 – 產生 Visual Studio 2022 解決方案 (`cmake generate visual studio`)

現在我們請 CMake 產生一個針對 **x64** 的 VS 2022 解決方案。關鍵旗標如下：

- `-G "Visual Studio 17 2022"` – 選擇 VS 2022 產生器。  
- `-Thost=x64` – 告訴 CMake *host*（IDE）以 64 位元程序執行。  
- `-Ax64` – 強制產生的專案以 x64 架構建置。

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **底層發生了什麼？**  
> CMake 從 `$SRC_DIR` 讀取 `CMakeLists.txt`，解析所有 `add_executable()` 與 `add_library()` 呼叫，接著在 `$BUILD_DIR` 內建立 `.sln` 檔案以及一系列 `.vcxproj` 檔案。這些專案檔現在可於 Visual Studio 開啟，或以指令列方式建置。  

如果執行指令後看到長串設定訊息，最後以 `-- Configuring done` 與 `-- Generating done` 結束，代表你已成功完成 **cmake generate visual studio** 步驟。

---

## 第三步 – 建置產生的解決方案 (`cmake build x64`)

解決方案已就緒，接下來的合乎邏輯的步驟是編譯它。CMake 可為你驅動建置，背後委派給 MSBuild。

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **為什麼使用 `--config Release`？**  
> Visual Studio 專案支援多種組態（Debug、Release、RelWithDebInfo 等）。指定 `Release` 可確保二進位檔針對正式環境進行最佳化，且產生的 `.exe` 或 `.dll` 會位於建置樹中的 `Release/` 目錄下。  

若你偏好 Debug 組態，只需將 `Release` 換成 `Debug`。指令的運作方式相同，證明 **how to use CMake** 在不同組態下僅是切換此旗標而已。

---

## 第四步 – 驗證建置 (`build vs project` sanity check)

成功編譯後應會產生可執行檔或函式庫。讓我們確認它是否存在：

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **常見陷阱：**  
> - 忘記在修改 `CMakeLists.txt` 後執行產生器步驟，會導致此檢查失敗。  
> - 混用 32 位元與 64 位元工具鏈可能造成連結錯誤；務必保持 `-Ax64` 一致。  
> - 若看到 “MSB3073” 錯誤，通常表示後置建置步驟（如複製資源）失敗——請檢查輸出以尋找線索。

---

## 第五步 – 清理與重新執行（迭代 `cmake build x64`）

開發過程中常需要從頭重新建置。最乾淨的方式是刪除建置資料夾後重新開始：

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **提示：**  
> 將 `-DCMAKE_BUILD_TYPE=Release` 加入產生器指令對於像 Visual Studio 這類多組態產生器是可選的，但在切換到單組態產生器（如 Ninja）時會很方便。

---

## 第六步 – 擴充腳本（進階 `cmake generate visual studio` 情境）

如果你的專案位於子目錄，或需要傳遞自訂定義呢？CMake 可透過 `-D` 參數達成：

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

現在產生的 VS 解決方案會定義 `MyFeature_ENABLED` 巨集，且安裝目標會將檔案放置於 `/opt/myapp`。這展示了 **how to use CMake** 超越基本三步流程的彈性。

---

## 預期輸出

當你從頭到尾執行完整腳本時，終端機應顯示類似以下內容：

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

若發生任何錯誤，CMake 會輸出指向 `CMakeLists.txt` 中問題行或缺少 SDK 元件的錯誤訊息——非常適合快速除錯。

---

## 結論

我們已說明完成 **cmake build x64** 所需的全部內容：設定來源目錄、呼叫 **cmake generate visual studio** 步驟、編譯產生的 **build vs project**，以及驗證輸出。此腳本簡潔、可移植，且可直接整合至 CI 流程或本機開發工作流程。

接下來，你可以探索：

- 使用 `ctest` 加入單元測試執行。  
- 轉換至 Ninja 產生器以加速增量建置（`-G Ninja`）。  
- 使用 CMake 預設 (`CMakePresets.json`) 來儲存我們剛才輸入的旗標。

盡情實驗、故意弄壞再重新建置——畢竟這是最快學會有效使用 CMake 的方式。祝建置順利！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在此處示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [建立表格](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [建立帶樣式的表格](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [建立帶邊框的表格](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}