---
category: general
date: 2026-03-19
description: 使用 Aspose.Words 與可變字型建立 Word 文件。學習如何在 C# 中變更字型粗細、設定字型寬度，以及定義字型變體。
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: zh-hant
og_description: 使用 Aspose.Words 建立使用可變字型的 Word 文件。本教學示範如何載入字型、變更字型粗細、設定字型寬度，以及定義字型變化。
og_title: 使用可變字型製作 Word 文件 – 完整指南
tags:
- Aspose.Words
- C#
- Variable Font
title: 使用可變字型建立 Word 文件 – 指南
url: /zh-hant/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用可變字型建立 Word 文件 – 指南

有沒有曾經需要 **建立 Word 文件**，使用現代的可變字型，但不知從何開始？你並不孤單。在許多專案中——例如動態報告或品牌一致的手冊——能即時 **變更字型粗細** 真是個改變遊戲規則的功能。  

在本教學中，我們將逐步說明整個流程：從將可變字型載入 Aspose.Words、設定其粗細與寬度，最後儲存一個外觀完全符合設計的 DOCX。沒有模糊的說明，只有可直接放入 C# 專案的具體程式碼。

## 您將學到

- 如何使用 `FontSettings` **載入可變字型** 檔案到 Aspose.Words。
- **定義字型變化** 軸的語法，例如 `wght`（粗細）和 `wdth`（寬度）。
- 在單一 `Run` 上 **設定字型寬度** 與 **變更字型粗細** 的方法。
- 排除常見問題的技巧（缺少字形、資料夾路徑錯誤等）。
- 完整、可執行的範例，您可以直接複製貼上並立即測試。

> **前置條件**：.NET 6+（或 .NET Framework 4.6+）、透過 NuGet 安裝的 Aspose.Words for .NET，以及放置於本機 *Fonts* 資料夾的可變字型檔案，例如 *RobotoFlex.ttf*。

---

## 步驟 1 – 載入可變字型至 Aspose.Words

首先，我們必須告訴 Aspose.Words 在哪裡尋找自訂字型。`FontSettings` 類別負責這項重活。  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**為什麼這很重要**：如果未註冊資料夾，Aspose.Words 會退回使用系統字型，並忽略之後嘗試套用的任何 OpenType 變化資料。將其指向特定目錄即可確保每次執行程式時都能找到 *RobotoFlex*（或其他任何可變字型）。

> **小技巧**：若希望 Aspose 同時搜尋子資料夾，請將 `SetFontsFolder` 的第二個參數設為 `true`。當您依樣式或粗細分類字型時，這會很有幫助。

---

## 步驟 2 – 建立新文件並加入範例文字

現在字型引擎已知道要去哪裡尋找，我們建立一個空的 `Document`，並插入包含 `Run` 的段落。  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**發生了什麼**：`Run` 代表一段具有統一格式的連續文字。先建立它可將格式邏輯隔離——若日後需要對不同的 run 套用不同的變化軸，這樣的做法最為理想。

---

## 步驟 3 – 定義所需的變化軸（粗細與寬度）

可變字型會公開可於執行時調整的 *軸*。最常見的兩個是 `wght`（字型粗細）與 `wdth`（字型寬度）。Aspose.Words 以 `OpenTypeFontVariation` 集合來呈現這些軸。

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**為什麼是這些數值**：依 OpenType 規範，`wght` 的範圍為字型的最小至最大粗細（通常是 100–900）。**700** 的數值對應粗體外觀。`wdth` 的運作方式類似；**100** 代表預設（正常）寬度，低於 100 的數值會使字形變窄。

> **邊緣情況**：某些可變字型不支援特定軸。如果提供了不支援的標籤，Aspose 會靜默忽略。務必再次確認字型規格（通常位於 `.ttf` 或 `.otf` 檔案的中繼資料中）。

---

## 步驟 4 – 使用字型名稱將變化套用至 Run

現在我們將變化資料綁定到實際文字。`FontInfo` 類別保存字型族名稱與軸集合。

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**說明**：設定 `FontInfo` 後，我們繞過一般的 `Font.Name` 屬性，直接向引擎提供完整的字型設定。這是唯一能告訴 Aspose.Words 使用帶有自訂軸的可變字型的方法。

> **常見錯誤**：忘記與字型檔案內的精確族名稱相符（本例為 `RobotoFlex`）。拼寫錯誤會導致 Aspose 退回使用預設字型，變化設定將遺失。

---

## 步驟 5 – 儲存文件並驗證結果

最後，將文件寫入磁碟。產生的 DOCX 會包含可變字型指令，Microsoft Word（2016 版以上）能正確呈現。

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

在 Word 中開啟產生的檔案，選取文字，並檢視 **字型** 對話框。您應該會看到列出 *Roboto Flex*，且文字會比周圍內容更粗——正是我們設定的 `wght = 700` 所要求的效果。

> **驗證提示**：若文字看起來未變化，請再次確認字型檔案確實支援 `wght` 軸。有些「可變」字型只提供 `ital`（斜體）或 `opsz`（光學尺寸）。

---

## 可選：加入更多變化 – 動態變更寬度

如果想要在另一段落 *設定不同的字型寬度*，只需使用新的 `OpenTypeFontVariation` 集合重複步驟 3‑4 即可。

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

現在您有兩個 run——一個粗體，一個稍寬——同時示範了 **變更字型粗細** 與 **設定字型寬度** 在同一文件中的應用。

---

## 完整可執行範例

將以下程式碼片段複製到新的主控台應用程式（`Program.cs`）中並執行。確保 `Fonts` 資料夾內有 `RobotoFlex.ttf`（或您偏好的任何可變字型）。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**預期輸出**：一個 `VariableFont.docx` 檔案，裡面的「Variable‑weight text」文字因 `wght = 700` 軸而呈現粗體，同時保留預設寬度。

---

## 常見問題與邊緣情況

| Question | Answer |
|----------|--------|
| *如果找不到字型怎麼辦？* | 確認資料夾路徑是否正確，確保檔名相符且程式具有讀取權限。您也可以呼叫 `fontSettings.GetFonts()` 來列出已偵測的字型。 |
| *我可以將多個 run 結合使用不同的變化嗎？* | 當然可以。每個 `Run` 都可以攜帶自己的 `FontInfo`。只要對每個 run 重複步驟 3‑4 即可。 |
| *舊版 Word 支援可變字型嗎？* | Word 2016（Build 16.0.8001）已加入基本支援。若目標為較舊版本，文件會退回使用最接近的靜態字型實例。 |
| *設定的軸數量有限制嗎？* | 您可以設定字型所定義的任意軸數。常見標籤包括 `wght`、`wdth`、`ital`、`opsz`、`GRAD`。提供不支援的標籤則不會產生任何效果。 |
| *如何偵錯缺少的字形？* | 使用 `FontSettings.GetFontSources()` 檢查已載入的字型，並利用 `FontInfo.HasGlyph(char)` 測試個別字元是否有字形。 |

---

## 結論

只需幾個步驟，我們就示範了 **如何建立使用可變字型的 Word 文件**，讓您能 **變更字型粗細**、**設定字型寬度**、**載入可變字型** 檔案，並 **定義字型變化** 軸——全部透過 Aspose.Words for .NET 完成。  

核心概念相當簡單：註冊字型資料夾、描述所需的軸、將其附加到 `Run`，最後儲存。之後您可以將此技巧擴展至整個章節、表格，甚至程式化產生品牌專屬的報告。  

**下一步**：嘗試將 `RobotoFlex` 換成其他可變字型、實驗 `ital`（斜體）軸，或使用 Aspose.PDF 產生相同文件的 PDF 版。相同的流程仍適用——載入、定義、套用、儲存。  

祝程式開發順利，盡情體驗可變字型為您的 Word 自動化專案帶來的彈性！  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}