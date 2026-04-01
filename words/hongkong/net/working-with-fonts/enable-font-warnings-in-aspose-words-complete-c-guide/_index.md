---
category: general
date: 2026-04-01
description: 在使用 Aspose.Words 載入 Word 檔案時啟用字型警告。了解如何使用 C# 的 LoadOptions 與字型設定來捕捉字型替換事件。
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: zh-hant
og_description: 在使用 Aspose.Words 載入 Word 文件時啟用字型警告。本教學示範如何在 C# 中捕捉字型替換事件。
og_title: 在 Aspose.Words 中啟用字型警告 – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Font Management
title: 在 Aspose.Words 中啟用字型警告 – 完整 C# 指南
url: /zh-hant/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words 中啟用字型警告 – 完整 C# 指南

有沒有想過為什麼在程式化載入 Word 文件後，文件的外觀會突然變得不同？**啟用字型警告** 後，你會立即知道 Aspose.Words 何時將缺失的字型替換為備用字型。在本教學中，我們將逐步示範一個實作範例，不僅捕捉這些替換，還會說明*為什麼*會發生。

我們會涵蓋讓你快速上手所需的一切：必備的 NuGet 套件、精確的 `LoadOptions` 設定，以及能清楚顯示被替換字型的整潔主控台輸出。完成後，你將擁有一套穩固且可重複使用的 **C# 文件處理** 範本，適用於任何版本的 Aspose.Words。

## 你將學會

- 如何建立可追蹤字型變更的 `LoadOptions` 實例。  
- `SubstitutionWarning` 事件的用途以及如何註冊。  
- 完整且可執行的程式碼範例，能將清晰的警告輸出至主控台。  
- 處理邊緣案例的技巧，例如僅包含標準字型的文件。

不需要事先使用 Aspose.Words 的經驗——只要對 C# 與 .NET 有基本了解即可。

---

![啟用字型警告圖示說明缺少字型被替換時的事件流程](placeholder-image.png "啟用字型警告圖示")

*替代文字：顯示缺少字型被替換時事件流程的啟用字型警告圖示。*

## 步驟 1：設定 LoadOptions 並啟用字型警告

首先，你需要一個 `LoadOptions` 物件。此容器告訴 Aspose.Words 如何處理即將載入的檔案。透過指派全新的 `FontSettings` 實例，即可開啟與字型相關的事件。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**為什麼這很重要：**  
如果省略 `FontSettings` 的指派，Aspose.Words 仍會替換缺失的字型，但你不會收到任何通知。警告機制位於 `FontSettings` 內部，因此初始化它對於我們的目標是*關鍵*的。

> **小技巧：** 你也可以使用 `SetFontsFolder` 將 `FontSettings` 指向自訂的字型資料夾。這樣可以減少出現的警告數量，因為 Aspose.Words 能實際找到缺失的字型。

## 步驟 2：訂閱 SubstitutionWarning 事件（字型替換）

現在 `FontSettings` 物件已存在，我們將其 `SubstitutionWarning` 事件掛勾起來。每當 Aspose.Words 將請求的字型替換為其他字型時，該事件會**每次**觸發。

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**為什麼這很重要：**  
若沒有此監聽器，你將無法看到替換過程。主控台輸出提供快速的稽核紀錄，對於自動化建置或在合規性要求高的產業產生 PDF 時特別有用。

> **常見問題：** *如果我想要抑制警告該怎麼辦？*  
> 只要解除註冊處理程序或設定 `FontSettings.SubstitutionWarning += null;` 即可。然而，保留警告通常是最安全的做法，因為靜默的替換可能導致版面錯位。

## 步驟 3：使用已設定的選項載入文件（C# 文件處理）

警告系統就緒後，載入文件變得相當簡單。將 `LoadOptions` 實例傳入 `Document` 建構函式，Aspose.Words 會自行處理其餘步驟。

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**為什麼這很重要：**  
`LoadOptions` 物件是原始檔案與警告基礎設施之間的橋樑。如果省略它，文件會靜默載入，任何缺失的字型都會在未留下痕跡的情況下被替換。

> **邊緣案例：** 有些文件會嵌入所需的字型檔案。在此情況下不會出現警告，因為 Aspose.Words 能找到嵌入的字型。上述程式碼仍然可運作，只是主控台輸出會是空的。

## 步驟 4：驗證輸出與常見陷阱

從命令提示字元或 IDE 的除錯器執行程式。若來源文件包含機器上未安裝（或自訂字型資料夾中不存在）的字型，你會看到類似以下的行：

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

如果沒有任何輸出，可能是：

1. 所有字型皆已找到，**或**  
2. `SubstitutionWarning` 處理程序未正確掛勾（請再次檢查步驟 2）。

### 為什麼會發生字型替換？

- **缺少系統字型：** 作業系統未安裝請求的字型。  
- **不支援的字型格式：** Aspose.Words 能讀取 TrueType 與 OpenType，但不支援所有專有格式。  
- **授權限制：** 某些商業字型會阻止嵌入，迫使使用備用字型。

了解*原因*有助於你決定是將缺失的字型隨應用程式一起發佈，還是調整文件的樣式。

## 加分：控制備用字型

如果你希望所有缺失的字型都回退至特定字型族（例如 “Calibri”），可以設定全域的替換規則：

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

此時主控台仍會發出警告，但視覺結果在所有缺失字型上會保持一致。

---

## 重點回顧

- **啟用字型警告**：透過建立帶有全新 `FontSettings` 的 `LoadOptions`。  
- 掛勾 `SubstitutionWarning` 事件，以即時取得字型被替換的警示。  
- 使用已設定的選項載入文件，必要時另存為 PDF 以觀察視覺效果。  
- 診斷替換發生的原因，並在需要時強制使用特定的備用字型。

你剛為 **Aspose.Words** 工作流程加入了一層安全網，防止靜默的版面變更。接下來，你可以探索如 `DefaultFontName` 等 **字型設定**，或深入 **文件渲染** 選項，以微調 PDF 輸出。

---

### 接下來可以嘗試什麼？

- **探索其他 FontSettings 功能**：`SetFontsFolder`、`LoadFontSources` 與 `DefaultFontName`。  
- **將警告與日誌框架結合**（如 Serilog、NLog）以實現生產等級的診斷。  
- **嘗試不同的文件格式**（`.doc`、`.rtf`、`.html`），觀察各自如何處理缺失字型。

有任何問題或特殊情境嗎？在下方留言，我們一起討論，祝程式開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}