---
category: general
date: 2026-06-02
description: 學習如何在 C# 中使用可變字重字體，並以程式方式設定字重，同時變更字形寬度程式碼，以實現動態排版。
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: zh-hant
og_description: 在 C# 中使用可變字重字型，以程式方式設定字重並變更字形寬度程式碼，實現文件的動態排版。
og_title: 在 C# 中使用可變字重字體 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: 在 C# 中使用可變字重字體 – 完整程式設計指南
url: /zh-hant/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用可變字重字型 – 完整程式指南

是否曾在 .NET 專案中**使用可變字重字型**，卻不確定如何讓字重與字寬根據使用者輸入而變化？你並不孤單。在許多 UI 或報表情境下，你可能需要文字自動調整——例如輕量的標題在滑鼠懸停時變粗，或段落為了強調而擴寬。好消息是，使用 Aspose.Words 你可以**以程式方式設定字重**，甚至**即時變更字寬代碼**。

本教學將手把手示範如何載入可變字重字型、套用自訂字重，並調整字寬設定，全部以可直接複製貼上的 C# 程式碼呈現。完成後，你將擁有一個可執行的 console 應用程式，產生展示效果的 PDF。

---

## 需要的條件

- **Aspose.Words for .NET**（v23.12 或更新版本）。此函式庫完整支援可變字重字型。
- 一個資料夾，內含至少一個可變字重字型檔案，例如 *RobotoFlex‑Variable.ttf*。可從 Google Fonts 下載。
- .NET 6 SDK（或任何近期的 .NET 版本）以及你慣用的 IDE。
- 基本的 C# 知識——只需要幾行程式碼，沒有其他複雜需求。

就這樣。除了 Aspose.Words 之外不需要額外的 NuGet 套件，也不需要奇怪的設定檔。

---

![Use variable weight font example](https://example.com/variable-weight-sample.png "Use variable weight font demonstration")

*Alt text: screenshot showing use variable weight font in a generated PDF document.*

---

## 步驟 1：設定 FontSettings 並指向字型資料夾  

首先，Aspose.Words 必須知道你的可變字重字型放在哪裡。你需要建立一個 `FontSettings` 物件，並附加一個 `FolderFontSource`。`true` 參數表示同時搜尋子資料夾，若你將多個字型家族放在同一層非常方便。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**為什麼這很重要：** 若未註冊資料夾，Aspose.Words 會回退使用系統字型，並忽略自訂字型檔案中內嵌的可變字重資料。此步驟是後續所有操作的基礎。

---

## 步驟 2：將 FontSettings 套用到 Document  

接著建立一個新的 `Document`（或載入既有文件），並告訴它使用剛才設定好的 `FontSettings`。這個綁定讓每個之後加入的 `Run` 都能存取可變字重資料。

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

如果你已有範本——例如含有佔位符的 Word 檔——只要把 `new Document()` 換成 `new Document("Template.docx")` 即可。相同的 `FontSettings` 仍會套用。

---

## 步驟 3：加入使用可變字重字型的 Run  

`Run` 是 Aspose.Words 中最小的文字格式單位。我們會建立一個 `Run`，插入新段落，稍後再變更其字型屬性。

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

此時文字會以預設字型（通常是 Times New Roman）呈現。真正的魔法在於我們指派可變字重字型家族之後發生。

---

## 步驟 4：選取可變字重字型家族  

這裡才是真正**使用可變字重字型**的地方。將 `Font.Name` 設為字型檔內部定義的完整家族名稱。以 Roboto Flex 為例，名稱為 `"Roboto Flex"`。

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

若不確定家族名稱，可在字型檢視器中開啟 `.ttf` 檔，或使用 `fontSettings.GetFonts()` 方法列出所有可用家族。

---

## 步驟 5：以程式方式設定字重與字寬  

現在進入本教學的核心：**以程式方式設定字重**，以及**變更字寬代碼**。兩個屬性皆接受對應 OpenType 規範的整數值。

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**：100（Thin）→ 900（Black）。選擇任意可變字型支援的值。
- **FontStretch**：50（Ultra‑Condensed）→ 200（Ultra‑Expanded）。預設為 100（Normal）。

> **小技巧：** 並非所有可變字型都提供完整範圍。若設定了不支援的值，引擎會自動夾取至最近的可用字重或字寬。

---

## 步驟 6：儲存文件並驗證結果  

最後，將文件輸出為 PDF（或 DOCX），然後開啟檢視效果。PDF 是視覺驗證的好選擇，因為其渲染在各平台上保持一致。

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

開啟 *VariableWeightDemo.pdf* 後，你應該會看到「Variable‑weight text demo」這句文字以輕量、略為展寬的 Roboto Flex 呈現。將 `FontWeight` 改為 `700`、`FontStretch` 改為 `80` 後重新執行，即可看到文字變粗且更緊縮。

---

## 常見問題與特殊情況  

### 若字型根本沒有顯示該怎麼辦？

- **缺少 FontSettings**：請確認在加入任何文字之前已執行 `doc.FontSettings = fontSettings;`。
- **家族名稱錯誤**：使用 `fontSettings.GetFonts()` 列出所有偵測到的家族，並複製完整字串。
- **不支援的字重/字寬**：某些可變字型只支援 100‑900 範圍的子集。可使用 `run.Font.FontWeight = 400;` 作為安全備援。

### 可以在文件儲存後再變更字重嗎？

可以。`Run` 物件是可變的，只要在最終 `Save` 之前調整 `FontWeight` 或 `FontStretch` 即可。如果需要根據使用者互動即時切換字重，建議為每種狀態產生獨立的 Run。

### 這在 DOCX 輸出時也有效嗎？

絕對有效。可變字重的中繼資料會寫入底層 OpenXML，現代版的 Word 能正確解讀。但較舊的 Word 版本可能會忽略字寬設定。

---

## 完整範例程式  

以下是一個完整的 console 程式，你可以立即編譯執行。內含所有必要的 `using` 指令、錯誤處理與註解。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**預期輸出：** 主控台會印出儲存路徑，產生的 PDF 會以輕量、展寬的樣式顯示文字——正是我們剛設定的效果。

---

## 重點回顧  

我們說明了如何在 C# 中**使用可變字重字型**，示範了**以程式方式設定字重**，以及**變更字寬代碼**的完整步驟。流程很簡單：設定 `FontSettings`、將其附加到 `Document`、建立 `Run`、選取可變字重家族，最後調整 `FontWeight` 與 `FontStretch`。

---

## 接下來可以做什麼？

- **動態 UI 整合**：將相同邏輯嵌入 WinForms 或 WPF 應用，讓使用者透過滑桿自行調整字重/字寬。
- **多個 Run**：在同一段落內混合不同字重的 Run，打造豐富的排版層次。
- **進階軸向**：部分可變字型提供額外軸向（如斜體、光學尺寸）。可使用 `run.Font.FontStyle` 或探索 `FontVariationSettings` 取得更細緻的控制。
- **效能建議**：在大量文件處理時，將 `FontSettings` 實例快取起來，以免重複掃描資料夾。

盡情實驗吧——把 *Roboto Flex* 換成 *Inter Variable* 或其他 OpenType 可變字型，讓你的文件獲得全新視覺彈性。祝開發愉快！

## 下一步學習建議

以下教學與本指南緊密相關，能進一步深化你對 API 功能的掌握，並提供其他實作方式的範例程式碼與逐步說明。

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}