---
category: general
date: 2026-03-06
description: 如何將 Word 文件中的方程式轉換為 LaTeX 標記並儲存為純文字。了解如何匯出數學式、將 Word 另存為文字檔等更多技巧。
draft: false
keywords:
- how to convert equations
- how to export math
- save word as text
- how to save txt
- save docx as txt
language: zh-hant
og_description: 如何將 Word 文件中的方程式轉換為 LaTeX 標記並儲存為純文字。本指南將示範如何匯出數學式、將 Word 儲存為文字檔等操作。
og_title: 如何將 Word 中的方程式轉換為 LaTeX – 儲存為 TXT
tags:
- Aspose.Words
- C#
- LaTeX
- Document Conversion
title: 如何將 Word 中的方程式轉換為 LaTeX – 儲存為 TXT
url: /zh-hant/net/programming-with-officemath/how-to-convert-equations-in-word-to-latex-save-as-txt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何將 Word 中的方程式轉換為 LaTeX – 儲存為 TXT

將 Word 文件中的方程式轉換為 LaTeX 標記是處理科學論文、電子學習內容或任何連接 Microsoft Office 與 LaTeX 工作流程的開發人員常見需求。是否曾經在複製複雜的 Office Math 區塊時，結果卻出現亂碼？你並不孤單。

在本教學中，我們將逐步說明一個完整、可直接執行的解決方案，該方案能夠 **匯出數學** 從 `.docx` 檔案，將其轉換為乾淨的 LaTeX，然後 **將結果儲存為純文字** (`.txt`)。完成後，你將了解如何 **匯出數學**、**將 Word 儲存為文字**，甚至如何 **將 docx 儲存為 txt** 以供後續處理。

## 你將學到什麼

- 為何 Aspose.Words 是方程式轉換的可靠選擇。
- 如何設定 `TxtSaveOptions` 以輸出 LaTeX 而非原始 Unicode。
- 可直接放入任何 .NET 專案的完整 C# 程式碼。
- 邊緣案例處理（例如，文件中沒有方程式、較舊的 Aspose 版本）。
- 實用技巧，避免在大量批次轉換時的陷阱。

### 前置條件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later (or .NET Framework 4.7+) | Aspose.Words for .NET 同時支援兩者。 |
| Aspose.Words for .NET NuGet package (≥ 23.9) | 較新版本包含 `OfficeMathExportMode.LaTeX` 列舉。 |
| A Word file (`.docx`) that contains Office Math objects | 轉換僅適用於實際的方程式物件。 |
| Visual Studio, VS Code, or any C# IDE you like | 不需要額外的工具。 |

如果尚未加入 Aspose.Words，請執行以下指令：

```bash
dotnet add package Aspose.Words
```

就這樣——不需要額外搜尋 DLL。

![如何轉換方程式範例](/images/convert-equations.png "如何轉換方程式說明")

## 步驟式實作

以下我們將流程分為三個清晰的階段。每個階段都有自己的 H2 標題，讓你可以直接跳到需要的部分。

### 如何轉換方程式：載入來源文件

首先，我們需要將 Word 檔案載入記憶體。`Document` 類別抽象化整個 `.docx` 包，讓我們能存取每個段落、表格，以及最重要的 Office Math 物件。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains Office Math equations
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – is there any math at all?
bool hasMath = document.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("⚠️ No equations found. The output file will be empty.");
}
```

**為何這很重要：**  
如果跳過健全性檢查且文件中沒有方程式，你將得到一個空的 `.txt`，浪費 I/O 時間。`GetChildNodes` 呼叫成本低，且能提供清晰的診斷訊息。

### 如何匯出數學：設定文字儲存選項

Aspose.Words 讓你控制在儲存為純文字時 Office Math 的呈現方式。將 `OfficeMathExportMode` 設為 `LaTeX` 後，函式庫會將每個方程式轉換為正確的 LaTeX 語法，而非預設的 Unicode 表示。

```csharp
// Set up text save options to export Office Math as LaTeX markup
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Optional: preserve line breaks for readability
    PreserveTableLayout = true,
    Encoding = Encoding.UTF8
};
```

**為何這很重要：**  
預設的匯出 (`OfficeMathExportMode.Text`) 會得到類似 “∫ f(x)dx” 的結果，雖在 PDF 中看起來不錯，但會破壞許多 LaTeX 工作流程。切換為 `LaTeX` 後會得到 `\int f(x)\,dx`，可直接放入 `.tex` 檔案。

### 如何儲存 TXT：將含 LaTeX 的文字寫入磁碟

現在選項已設定好，我們只需呼叫 `Save`。此方法會遵循我們傳入的 `TxtSaveOptions`，因此產生的檔案會包含原始 LaTeX，並與任何周圍的純文字內容交錯。

```csharp
// Save the document as a plain‑text file using the configured options
string outputPath = "YOUR_DIRECTORY/output.txt";
document.Save(outputPath, txtSaveOptions);

Console.WriteLine($"✅ Conversion complete! LaTeX saved to: {outputPath}");
```

**預期輸出：**  
在任何編輯器中開啟 `output.txt`，你會看到類似以下內容：

```
Here is a simple equation:
\int_{0}^{\infty} e^{-x^2} \,dx = \frac{\sqrt{\pi}}{2}
And a second one:
E = mc^{2}
```

周圍的句子保持不變，而每個 Office Math 區塊則變成乾淨的 LaTeX。

## 處理常見的邊緣案例

| Situation | What to Do |
|-----------|------------|
| **文件不含方程式** | 上述的健全性檢查已經會警告你。你可以選擇跳過儲存或寫入佔位行。 |
| **較舊的 Aspose.Words 版本 (< 22.9)** | `OfficeMathExportMode.LaTeX` 不可用。升級 NuGet 套件或回退至 `OfficeMathExportMode.Text`，並手動後處理 Unicode。 |
| **大量批次轉換（數百個檔案）** | 將邏輯包在 `foreach` 迴圈中，重複使用單一 `TxtSaveOptions` 實例，並考慮非同步 I/O（`await document.SaveAsync`）。 |
| **含自訂字型或符號的方程式** | LaTeX 會保留數學語意，但視覺樣式（顏色、大小）會遺失——這在純文字工作流程中是預期的。 |
| **需要 PDF 而非 TXT** | 將 `TxtSaveOptions` 換成 `PdfSaveOptions`；相同的 `OfficeMathExportMode` 也適用於 PDF。 |

**小技巧：** 在處理大量檔案時，將成功與失敗皆記錄至 CSV。如此即可快速找出未包含任何數學或拋出例外的文件。

## 完整可執行範例（即貼即用）

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class EquationConverter
{
    static void Main()
    {
        // 1️⃣ Load the source .docx
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Verify that the document actually has Office Math objects
        bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
        if (!hasMath)
        {
            Console.WriteLine("⚠️ No equations found in the source document.");
        }

        // 3️⃣ Configure save options to export LaTeX
        TxtSaveOptions options = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true,
            Encoding = Encoding.UTF8
        };

        // 4️⃣ Save as plain‑text (.txt)
        string outputPath = "YOUR_DIRECTORY/output.txt";
        doc.Save(outputPath, options);

        Console.WriteLine($"✅ Done! LaTeX equations saved to \"{outputPath}\"");
    }
}
```

執行程式（如果使用主控台專案則執行 `dotnet run`），即可得到整潔的 `.txt` 檔案，適用於任何 LaTeX 工作流程。

## 常見問與答

**Q: 這能用於 `.doc`（較舊的二進位格式）嗎？**  
A: 可以，Aspose.Words 同時抽象化 `.doc` 與 `.docx`。只要將 `Document` 指向 `.doc` 檔案，即可使用相同的 `OfficeMathExportMode.LaTeX`。

**Q: 如果需要保留原始 Word 的樣式該怎麼辦？**  
A: 純文字無法保留樣式。若需保留樣式，可考慮儲存為 HTML（`HtmlSaveOptions`）或 PDF（`PdfSaveOptions`）。LaTeX 匯出仍保持不變。

**Q: 能直接轉換為 `.tex` 檔案嗎？**  
A: 雖非即時支援，但你可以在儲存後將 `.txt` 重新命名為 `.tex`，或自行在輸出前加上最小的 LaTeX 前置碼。

## 結論

現在你已掌握一套完整、端到端的流程，能夠 **將 Word 文件中的方程式轉換為 LaTeX** 並 **將 Word 儲存為文字**，且不會遺失任何數學意義。透過將 `TxtSaveOptions` 設定為使用 `OfficeMathExportMode.LaTeX`，即可取得乾淨的標記，與任何 LaTeX 處理器皆相容。

接下來，你可能想探索 **如何匯出數學** 為其他格式（HTML、Markdown），或自動化 **將 docx 儲存為 txt** 以處理大量科學論文。相同的模式——載入、設定、儲存——適用於所有情境，歡迎自行嘗試。

還有其他想了解的情境嗎？在下方留言或於 GitHub 上私訊我。祝轉換順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}