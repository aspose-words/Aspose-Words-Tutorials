---
category: general
date: 2026-04-24
description: 將文件儲存為 txt，並使用 Aspose.Words 將 Word 轉換為 LaTeX。快速學習如何將 Word 數學方程式匯出為 LaTeX。
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: zh-hant
og_description: 使用 C# 將文件另存為 txt，並將 Word 方程式轉換為 LaTeX。完整逐步教學與程式碼。
og_title: 將文件另存為 TXT – 匯出 Word 數學式至 LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: 將文件另存為 TXT – 在 C# 中將 Word 數學公式匯出為 LaTeX
url: /zh-hant/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將文件另存為 TXT – 匯出 Word 數學公式為 LaTeX（C#）

有沒有曾經需要 **save document as txt**，同時又想保留精美的公式？你並不是唯一的使用者。Word 內建的「另存為純文字」會直接捨棄 Office Math，留下難以辨識的亂碼。若能保留公式，且以乾淨的 LaTeX 形式輸出，會怎樣？

在本教學中，我們將一步步說明如何使用 Aspose.Words for .NET，將 Word 轉換成可直接使用 LaTeX 的文字檔。完成後，你會得到一個 `.txt` 檔案，裡面的每個公式都以正確的 LaTeX 標記呈現，隨時可以貼到論文或 Markdown 檔中。全程不需要外部轉換工具，也不必手動複製貼上，只要幾行 C# 程式碼即可。

## 你將學會

- 如何使用 Aspose.Words 載入 `.docx` 檔案。  
- 設定 `TxtSaveOptions`，讓 Office Math 以 LaTeX 匯出。  
- 將結果儲存為純文字檔，任何編輯器都能開啟。  
- 處理內嵌與顯示公式的特殊情況，並提供批次處理多個文件的快速技巧。

### 前置條件

- .NET 6.0 或更新版本（亦支援 .NET Framework 4.6 以上）。  
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）。  
- 一份至少包含一個公式（Office Math 物件）的 Word 文件。

---

## 步驟 1：安裝 Aspose.Words 並建立專案

首先，將函式庫加入專案。於解決方案資料夾的終端機執行：

```bash
dotnet add package Aspose.Words
```

> **小技巧：** 若使用 Visual Studio，NuGet 套件管理員 UI 也同樣方便——搜尋「Aspose.Words」後點選「Install」即可。

接著建立一個新的 Console 應用程式（或將程式碼放入既有專案）。需要的 `using` 指示如下：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

這些指示會把 `Document` 類別與 `TxtSaveOptions` 型別匯入至程式範圍。

## 步驟 2：載入來源文件

我們必須讓 Aspose.Words 指向包含公式的 Word 檔案。將 `YOUR_DIRECTORY/input.docx` 替換成你電腦上的實際路徑。

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **為什麼這很重要：** 載入文件後，Aspose.Words 才能完整存取內部的 Office Math 物件；若僅使用簡易的文字匯出器，這些物件將無法被偵測。

## 步驟 3：設定 TxtSaveOptions 以匯出 LaTeX

魔法發生在 `TxtSaveOptions` 物件內。將 `OfficeMathExportMode` 設為 `LaTeX`，即可將每個公式轉換為對應的 LaTeX 代碼。

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **如果需要 MathML 呢？** 只要把 `OfficeMathExportMode` 改成 `MathML` 即可。相同的 API 也支援其他輸出格式。

## 步驟 4：將文件另存為純文字

現在把結果寫入檔案。產生的 `Math.txt` 會包含普通文字以及每個公式的 LaTeX 片段。

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

執行程式後，產生的檔案大致如下：

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

可見內嵌公式使用 `$…$` 包圍，而顯示公式則以 `\[` 與 `\]` 包起。這是 LaTeX 的標準慣例，Aspose.Words 會自動處理。

## 步驟 5：驗證輸出（可選）

若想確認 LaTeX 是否正確，可將 `.txt` 交給 `pdflatex` 或線上渲染服務（如 Overleaf）編譯。文字應能順利編譯，且公式會與 Word 中的呈現完全相同。

```bash
pdflatex Math.txt
```

若出現 “Undefined control sequence” 錯誤，請確保在嵌入更大 LaTeX 文件時已在前置區加入所需的套件（例如 `amsmath`）。

## 常見變化處理

### 批次轉換資料夾內的多個檔案

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### 處理內嵌與顯示公式的差異

Aspose.Words 會自動依 Word 中的版面判斷公式類型。若需強制指定樣式，可在輸出後自行後處理：

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### 匯出至其他格式

若目標不是 LaTeX，只要切換匯出模式即可：

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

或改用 `HtmlSaveOptions`，將 MathML 直接嵌入 HTML。

---

## 完整範例程式

以下提供可直接執行的完整程式碼。將其複製貼上至 .NET Console 專案的 `Program.cs`。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

執行程式（`dotnet run`），開啟 `Math.txt`，即可看到 Word 內容與 LaTeX 公式完整保留。

---

## 常見問答

**Q: 這能處理舊版 .doc 檔嗎？**  
A: 能——Aspose.Words 能開啟舊版 `.doc`，但較複雜的公式可能會以影像形式儲存。此時匯出器會以佔位註解取代。

**Q: 若公式包含自訂符號該怎麼辦？**  
A: Aspose.Words 會將大多數 Office Math 符號對應到標準 LaTeX 指令。若真的有自訂符號，可能需要手動編輯產生的 LaTeX。

**Q: 輸出檔案的編碼是 UTF‑8 嗎？**  
A: 預設情況下，`TxtSaveOptions` 會以 UTF‑8 寫入，適用於大多數語言與符號。

---

## 結論

現在你已掌握 **save document as txt** 的技巧，且能在檔案中保留每個公式的乾淨 LaTeX 標記。此方法讓你 **convert Word to LaTeX** 完全不依賴第三方工具，且可從單一檔案擴展至整個資料夾。接下來，你可以探索 **convert word equations to LaTeX** 的批次處理，或深入研究 **export word math latex** 於 HTML 或 Markdown 工作流程中的應用。

盡情實驗吧——替換 `OfficeMathExportMode` 為 MathML、調整換行處理，或將此程式碼片段整合至更大的文件產生流程中。祝開發順利，願你的公式永遠正確渲染！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}