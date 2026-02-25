---
category: general
date: 2026-02-24
description: 使用 Aspose.Words C# 將 Word 轉換為 Markdown。可另存為 Markdown 或純文字，並將公式匯出為 LaTeX。
draft: false
keywords:
- convert word to markdown
- convert docx to txt
- how to save word as markdown
- save word as plain text
- convert word equations to latex
language: zh-hant
og_description: 使用 Aspose.Words C# 將 Word 轉換為 Markdown。學習如何儲存為 Markdown、純文字，並將方程式轉換為
  LaTeX。
og_title: 在 C# 中將 Word 轉換為 Markdown – 將方程式匯出為 LaTeX
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 將 Word 轉換為 Markdown（C#） – 匯出方程式為 LaTeX
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-word-to-markdown-in-c-export-equations-as-latex/
---

where appropriate.

Let's assemble.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 轉換為 Markdown – 完整步驟指南

有沒有想過如何 **將 Word 轉換為 Markdown**，同時不失去花了好幾小時輸入的精美數學公式？你並不是唯一有此困擾的人。許多開發者在需要一個乾淨的 Markdown 檔案 **以及** 能保留 LaTeX 公式的純文字版本時，常常卡住。

在本教學中，我們將逐步說明一個完整的 C# 解決方案，使用 Aspose.Words 來 **將 Word 轉換為 Markdown**、**將 docx 轉換為 txt**，甚至 **將 Word 公式轉換為 LaTeX**。完成後，你將擁有一段可重複使用的程式碼片段，能直接嵌入任何 .NET 專案。

> **小技巧：** 同樣的方法適用於 .NET 6、.NET 7，或傳統的 .NET Framework——只要確保引用正確的 Aspose.Words 套件版本即可。

## 所需環境與工具

- **Aspose.Words for .NET**（NuGet 套件 `Aspose.Words`）——負責繁重工作的函式庫。
- 一個 **.NET 開發環境**（Visual Studio、Rider，或安裝 C# 擴充功能的 VS Code）。
- 一個包含普通文字 *以及* Office Math 物件（即你想要轉成 LaTeX 的公式）的輸入 **.docx** 檔案。

不需要額外工具、不需手動複製貼上，絕對不使用第三方轉換器。

![將 Word 轉換為 Markdown 流程圖](image.png "顯示從 DOCX 到 Markdown 與 TXT，並保留 LaTeX 公式的流程圖")

## 步驟 1：載入來源 Word 文件  

我們首先要做的事是將 .docx 載入記憶體。Aspose.Words 只需一行程式碼即可完成。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document (replace the path with your own)
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**為何重要：** 載入文件會建立一個 `Document` 物件，讓我們能存取所有內部內容——文字、圖片，以及稍後會匯出為 LaTeX 的 Office Math 物件。

## 步驟 2：設定 Markdown 儲存選項  

Aspose.Words 能直接輸出 Markdown，但我們必須告訴它 *如何* 處理公式。將 `OfficeMathExportMode` 設為 `LaTeX` 即可解決。

```csharp
// Set up Markdown options – export equations as LaTeX
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

**這裡發生了什麼？** `OfficeMathExportMode` 列舉有多種值（`Image`、`MathML`、`LaTeX`）。選擇 `LaTeX` 後，我們確保 Word 檔中的任何公式都會以原生 LaTeX 片段的形式寫入產生的 `.md` 檔案。這正是你在 **將 Word 公式轉換為 LaTeX** 時所需要的。

## 步驟 3：將文件儲存為 Markdown  

現在我們真正寫出檔案。所有格式皆使用相同的 `doc.Save` 方法，只需傳入對應的選項物件。

```csharp
// Save as Markdown – this is the core of convert word to markdown
doc.Save("YOUR_DIRECTORY/output.md", mdOptions);
```

你會發現產生的 `output.md` 包含一般的 Markdown 語法，外加如下的 LaTeX 區塊：

```markdown
$$
\frac{a}{b} = c
$$
```

這就是在 **將 Word 儲存為 Markdown** 時，同時保留數學公式的神奇之處。

## 步驟 4：設定純文字（TXT）儲存選項  

如果你還需要一個簡單的 `.txt` 版本——例如快速預覽或供後續腳本使用——同樣以此方式設定 `TxtSaveOptions`。

```csharp
// Set up plain‑text options – keep equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

請注意我們重複使用相同的 `OfficeMathExportMode`。這保證在 **將 Word 儲存為純文字** 時，公式會以 LaTeX 字串呈現，而不會變成亂碼。

## 步驟 5：將文件儲存為純文字  

最後，寫出 `.txt` 檔案。

```csharp
// Save as plain text – this fulfills convert docx to txt with LaTeX equations
doc.Save("YOUR_DIRECTORY/output.txt", txtOptions);
```

開啟 `output.txt`，你會看到類似以下內容：

```
E = mc^2
\int_{a}^{b} f(x)\,dx
```

所有公式現在皆為 LaTeX，可直接嵌入 Jupyter Notebook 或任何支援 LaTeX 的工作流程中。

## 完整範例程式  

將上述步驟整合起來，以下是一個單一檔案程式，你可以直接執行（只需自行替換路徑）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}