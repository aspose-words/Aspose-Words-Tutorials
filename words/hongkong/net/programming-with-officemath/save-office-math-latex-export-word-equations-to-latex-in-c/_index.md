---
category: general
date: 2026-04-21
description: 使用 Aspose.Words 快速儲存 Office 數學 LaTeX —— 同時學習如何一次性儲存 Word 純文字並匯出 Word
  方程式的 LaTeX。
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: zh-hant
og_description: 即時儲存 Office 數學 LaTeX；學習匯出 Word 方程式為 LaTeX，並使用 Aspose.Words 在 C# 中轉換
  Word 數學 LaTeX。
og_title: save office math latex – 將 Word 方程式匯出為 LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: 儲存 Office 數學 LaTeX – 在 C# 中將 Word 方程式匯出為 LaTeX
url: /zh-hant/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – 使用 Aspose.Words 將 Word 方程式匯出為 LaTeX

有沒有曾經需要從 `.docx` 檔案 **save office math latex** 但不知從何開始？你並不孤單，好消息是解決方案相當簡單。在本指南中，我們將逐步說明如何使用 Aspose.Words for .NET 匯出 Word 方程式 latex（甚至 MathML），同時示範如何 **save word plain text** 與數學內容一起保存。

我們會涵蓋你可能會想知道的所有內容：為什麼會選擇 LaTeX 而非其他格式、如何設定 `TxtSaveOptions`，以及如果需要 **convert word math latex** 成其他表示方式時該怎麼做。完成後，你將擁有一段可執行的程式碼片段，能將含有 Office Math 物件的 Word 文件轉成乾淨的 `.txt` 檔，內含 LaTeX（或 MathML）方程式。無需外部工具、無需手動複製貼上——只要乾淨的 C# 程式碼，隨時可放入任何專案。

## Prerequisites

- **Aspose.Words for .NET**（v23.10 或更新版本）。NuGet 套件名稱為 `Aspose.Words`。
- .NET 開發環境（Visual Studio、Rider，或安裝 C# 擴充功能的 VS Code）。
- 一個包含至少一個使用 Office Math 編輯器建立的方程式的 Word 檔（`.docx`）。
- 基本的 C# 語法認識——不需要高階技巧，只要會寫 `using` 陳述式即可。

如果以上條件都已符合，太好了——讓我們開始吧。

## Step 1 – Set up **save office math latex** options

首先要告訴 Aspose.Words 你希望如何呈現數學內容。`TxtSaveOptions` 類別有一個 `OfficeMathExportMode` 屬性，可接受三種值：`LaTeX`、`MathML` 或 `Text`。為了達成主要目標，我們選擇 `LaTeX`。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**為什麼這很重要：** 當你將 `OfficeMathExportMode` 設為 `LaTeX` 時，每個方程式都會被轉換成其原始 LaTeX 原始碼。之後可以使用任何 LaTeX 引擎編譯，取得像素級完美的排版，且不必重新手動輸入公式。

> **小技巧：** 若你需要 **convert word equations mathml**，只要把列舉值改成 `OfficeMathExportMode.MathML` 即可。其餘程式碼保持不變。

## Step 2 – Load the Word document (the **save word plain text** scenario)

接著，我們載入來源 `.docx`。無論你只想抽取純文字，或同時需要 LaTeX 方程式，這一步都相同。

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**這段程式碼在做什麼？** `Document` 建構子會將檔案讀入記憶體。使用 `GetChildNodes` 的快速檢查可以捕捉常見的邊緣情況——例如檔案根本不含方程式卻嘗試匯出 LaTeX。這是一個小小的保護機制，能避免之後得到空白輸出。

## Step 3 – **save office math latex** to a plain‑text file

現在終於要寫入檔案了。`Save` 方法會遵循先前設定的 `TxtSaveOptions`，因此產生的 `.txt` 會同時包含一般文字與每個方程式的 LaTeX 片段。

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

開啟 `Equations.txt` 後，你會看到類似以下的內容：

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

LaTeX 區塊會自動以 `\begin{equation}` … `\end{equation}` 包裹，讓它們直接可用於任何 LaTeX 文件中。

## Step 4 – Alternative: **convert word equations mathml** instead of LaTeX

如果你的下游工具鏈較偏好 MathML（例如在網頁上使用 MathJax 渲染方程式），只要切換匯出模式即可：

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

輸出現在會包含 XML 風格的 MathML 標籤，例如：

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

這就是在不自行撰寫解析器的情況下，快速 **convert word equations mathml** 的方法。

## Step 5 – Bonus: **save word plain text** while keeping equations separate

有時你只想要文件的純文字版本，且不想嵌入任何 LaTeX 或 MathML。可以將匯出模式改為 `Text`，再執行一次保存：

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

如此一來，你會同時得到三個檔案：

| File                         | Contents                               |
|------------------------------|----------------------------------------|
| `Equations.txt`              | 純文字 **+** LaTeX 方程式               |
| `EquationsMathML.txt`        | 純文字 **+** MathML 方程式              |
| `PlainDocument.txt`          | 完全純文字，已移除所有方程式標記        |

這個模式在需要將純文字送入搜尋索引，同時又要保留原始數學內容以供學術出版時，非常實用。

## Full Working Example (Copy‑Paste Ready)

以下是完整程式碼，你可以直接編譯執行。它示範了 **save office math latex**、**export word equations latex**、**convert word math latex** 與 **save word plain text**——全部集中在同一個腳本中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**預期結果：** 執行後，你會在 `C:\MyDocs` 中看到三個文字檔。開啟 `Equations.txt` 會看到 LaTeX 區塊；`EquationsMathML.txt` 會包含 MathML；`PlainDocument.txt` 則不含任何方程式標記。

## Common Questions & Edge Cases

- **如果只需要部份方程式的 LaTeX 該怎麼辦？**  
  使用 `OfficeMath` 節點 API 逐一遍歷每個方程式，利用 `MathConverter` 手動匯出，然後在想要的位置替換佔位文字。此方式可提供細緻的控制，但會多寫幾行程式碼。

- **這能在 .NET Core / .NET 5+ 上執行嗎？**  
  完全可以。Aspose.Words 是跨平台的，只要執行環境的版本符合套件需求，程式碼即可在 Windows、Linux 與 macOS 上運行。

- **我可以把 LaTeX 包裝器（`\begin{equation}`）改成其他形式嗎？**  
  可以。設定 `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` 後，調整 `txtOptions.MathExportSettings`（在較新版本中提供）即可自訂分隔符號。

- **處理超大型文件時會有效能問題嗎？**  
  程式庫會以串流方式輸出，因此記憶體使用量保持在合理範圍。但

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}