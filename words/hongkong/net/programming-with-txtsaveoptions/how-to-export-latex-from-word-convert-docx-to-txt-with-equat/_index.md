---
category: general
date: 2026-03-21
description: 學習如何透過將 Word DOCX 轉換為 TXT 來匯出 LaTeX，並保留方程式。一步一步的 C# 指南，教你從 Word 匯出方程式。
draft: false
keywords:
- how to export latex
- convert docx to txt
- export equations from word
- save docx as txt
- convert word equations latex
language: zh-hant
og_description: 如何從 Word 匯出 LaTeX？本教學示範如何使用 C# 將 DOCX 轉換為 TXT，同時保留方程式為 LaTeX。
og_title: 如何從 Word 匯出 LaTeX – 快速 DOCX 轉 TXT 教學
tags:
- C#
- Aspose.Words
- LaTeX
- DOCX
- Text Export
title: 如何從 Word 匯出 LaTeX – 將 DOCX 轉換為含方程式的 TXT
url: /zh-hant/net/programming-with-txtsaveoptions/how-to-export-latex-from-word-convert-docx-to-txt-with-equat/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何從 Word 匯出 LaTeX – 將 DOCX 轉換為含公式的 TXT

有沒有想過 **如何從 Word 文件匯出 LaTeX** 而不必手動複製每個公式？你並不是唯一的。大多數開發者在需要將公式從 *.docx* 中抽取並輸入到支援 LaTeX 的流程時，都會卡住。  

好消息是？只要幾行 C# 程式碼加上正確的儲存選項，你就可以 **convert docx to txt**，並將每個 Office Math 公式轉換為乾淨的 LaTeX。本文將逐步說明每個步驟、解釋各設定的原因，並展示你可以在幾秒內驗證的最終結果。

## 本教學涵蓋內容

我們會先說明前置條件（只需要 Aspose.Words for .NET 函式庫）。接著深入三步驟流程：

1. 載入來源 *.docx* 檔案。
2. 設定 `TxtSaveOptions` 以將 Office Math 匯出為 LaTeX。
3. 將文件儲存為純文字檔。

完成後，你將了解 **如何匯出 LaTeX**，熟悉 **從 Word 匯出公式**，並擁有可在任何 C# 專案中直接使用的可重複使用程式碼片段。  

*為什麼在乎？* 如果你產生科學報告、作業或任何之後會以 LaTeX 編譯的內容，自動化此匯出可節省數小時的複製貼上，並消除格式錯誤。

## 前置條件

- .NET 6.0 或更新版本（程式碼同樣適用於 .NET Core 與 .NET Framework）。
- Aspose.Words for .NET（免費試用或授權版）。透過 NuGet 安裝：

```bash
dotnet add package Aspose.Words
```

- 包含至少一個 Office Math 公式的 Word 文件（`input.docx`）。

> **專業提示：** 若手頭沒有 DOCX，請建立一個新的 Word 檔，透過 *Insert → Equation* 插入公式，並儲存為 `input.docx`。

## 步驟 1：載入欲匯出的來源文件

首先，我們需要一個指向欲轉換檔案的 `Document` 實例。`Document` 類別抽象化整個 Word 檔，讓我們能存取段落、表格，以及最重要的 Office Math 物件。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source DOCX file
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **為什麼這很重要：** 載入檔案會在記憶體中建立可供儲存引擎遍歷的表示。若沒有此物件，就無法匯出，後續的設定也不會產生任何效果。

## 步驟 2：設定文字儲存選項以將 Office Math 匯出為 LaTeX

魔法就在 `TxtSaveOptions` 中。預設情況下，儲存為純文字會去除所有非文字內容，包括公式。將 `OfficeMathExportMode` 設為 `LaTeX`，即告訴 Aspose 將每個 Office Math 節點轉換為相應的 LaTeX。

```csharp
// Step 2: Set up save options for LaTeX export
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag ensures every equation becomes LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **底層發生了什麼？** Aspose 會解析 Office Math XML，將運算子映射為 LaTeX 指令，並將結果寫入文字串流。`OfficeMathExportMode` 列舉還提供 `Unicode` 與 `MathML`——可依你的下游工具鏈選擇合適的模式。

## 步驟 3：使用設定好的選項將文件儲存為純文字檔

現在我們將轉換後的內容寫入磁碟。副檔名 `.txt` 表示純文字格式，但因為已設定相應選項，檔案中會在原有公式位置混合一般文字與 LaTeX 片段。

```csharp
// Step 3: Export the document to a TXT file with LaTeX equations
doc.Save(@"YOUR_DIRECTORY\Equations.txt", txtSaveOptions);
```

### 預期輸出

在任何編輯器中開啟 `Equations.txt`。你應該會看到類似以下內容：

```
This is a sample paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

如果 LaTeX 如上所示，即表示你已成功 **save docx as txt** 並保留了公式。

## 常見變化與邊緣情況

### 批次轉換多個檔案

如果需要處理一個資料夾中的多個 DOCX 檔，可將這三個步驟包在 `foreach` 迴圈中：

```csharp
string[] files = Directory.GetFiles(@"YOUR_DIRECTORY", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtSaveOptions);
}
```

### 處理非公式內容

`TxtSaveOptions` 也允許你控制換行、編碼，以及是否保留隱藏文字。例如，強制使用 UTF‑8：

```csharp
txtSaveOptions.Encoding = Encoding.UTF8;
```

### 匯出至其他文字格式

如果你偏好 Markdown 而非純 TXT，只需更改副檔名，並視需要微調選項：

```csharp
doc.Save(@"YOUR_DIRECTORY\Equations.md", txtSaveOptions);
```

LaTeX 區塊會保持完整，Markdown 處理器（如 Pandoc）之後即可渲染。

## 完整、可執行範例

以下是完整程式碼，你可以直接複製貼上到 Console 應用程式中。它包含所有必要的 `using` 陳述式、錯誤處理，以及說明每一行的註解。

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\Equations.txt";

            try
            {
                // 1️⃣ Load the Word document
                Document doc = new Document(inputPath);

                // 2️⃣ Prepare save options – this is where we tell Aspose to export equations as LaTeX
                TxtSaveOptions saveOptions = new TxtSaveOptions
                {
                    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                    Encoding = Encoding.UTF8          // Ensure Unicode characters survive
                };

                // 3️⃣ Perform the export
                doc.Save(outputPath, saveOptions);

                Console.WriteLine($"✅ Success! LaTeX‑rich text file created at: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Oops – something went wrong: {ex.Message}");
            }
        }
    }
}
```

執行程式，開啟產生的 `Equations.txt`，即可看到每個公式皆以 LaTeX 呈現——可直接供 LaTeX 編譯器或科學出版工作流程使用。

## 常見問答

**這在較舊版本的 Aspose.Words 上可用嗎？**  
是的。`OfficeMathExportMode` 屬性自 19.8 版起即已存在。若你使用較舊的版本，請升級至至少該版本。

**如果我的 DOCX 含有圖片怎麼辦？**  
純文字匯出會依設計捨棄圖片。若同時需要圖片與 LaTeX，可考慮匯出為 HTML（`HtmlSaveOptions`），再後處理 HTML 以提取 LaTeX 區塊。

**能直接匯出為 `.tex` 檔嗎？**  
Aspose 並未提供原生的 `.tex` 寫入器，但匯出後可將 `.txt` 更名為 `.tex`——LaTeX 程式碼相同。只需自行手動加入文件結構（前置、`\begin{document}`）即可。

## 結論

現在你已了解如何 **如何匯出 LaTeX** 從 Word 檔案，透過 **convert docx to txt** 同時保留所有公式。這段三步驟的 C# 片段——載入、設定、儲存——涵蓋了 **從 Word 匯出公式** 的核心，且相同模式可套用於批次處理或其他輸出格式。  

準備好接受下一個挑戰了嗎？試試對多語言文件執行 **save docx as txt**，或探索使用 `pdflatex` 等工具將這些 LaTeX 片段轉換為 PDF。結合 Aspose.Words 與完善的 LaTeX 工作流程，無所不能。

---

![顯示流程的圖示：DOCX → Aspose.Words → 含 LaTeX 公式的 TXT](https://example.com/flow-diagram.png "如何匯出 latex 流程圖")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}