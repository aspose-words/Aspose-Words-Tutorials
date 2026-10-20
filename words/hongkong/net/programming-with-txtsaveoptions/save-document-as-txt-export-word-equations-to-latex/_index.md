---
category: general
date: 2026-03-01
description: 使用 Aspose.Words 將文件儲存為含 LaTeX 方程式的 TXT。了解如何將 Word 轉換為 LaTeX，輕鬆匯出方程式。
draft: false
keywords:
- save document as txt
- convert word to latex
- how to save txt
- how to export equations
- export equations to latex
language: zh-hant
og_description: 使用 Aspose.Words 將文件另存為含 LaTeX 方程式的 TXT。了解如何將 Word 轉換為 LaTeX，輕鬆匯出方程式。
og_title: 將文件另存為 TXT – 匯出 Word 方程式為 LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Text Export
title: 將文件另存為 TXT – 匯出 Word 方程式至 LaTeX
url: /zh-hant/net/programming-with-txtsaveoptions/save-document-as-txt-export-word-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將文件另存為 TXT – 匯出 Word 方程式為 LaTeX

是否曾想 **將文件另存為 txt**，卻擔心美觀的 Word 方程式會消失？你並非唯一遇到此問題的人。許多開發者在嘗試從含有 Office Math 物件的 .docx 取出純文字時，都會卡在這裡。好消息是：使用 Aspose.Words，你可以 **將文件另存為 txt**，同時保留每個方程式的乾淨 LaTeX 語法。

在本教學中，我們將一步步示範如何將 Word 檔案轉換為含 LaTeX 格式方程式的純文字檔。過程中會說明「如何匯出方程式」、展示 **如何程式化儲存 txt**，甚至涵蓋「將 Word 轉換為 LaTeX」的做法，適合需要在學術論文中使用數學式的朋友。沒有多餘的說明——只提供完整、可直接執行的解決方案，讓你隨時在任何 .NET 專案中使用。

## 你將學會什麼

- 從全新 .NET 主控台應用程式開始，最終產生一個 `Equations.txt`，裡面全是 LaTeX。
- 為何 `OfficeMathExportMode.LaTeX` 是保留數學式的最佳選擇。
- 處理多個方程式、複雜版面與常見問題（例如缺字型）的技巧。
- 一段可直接複製、貼上、執行的完整程式碼範例。

> **先決條件清單**  
> - .NET 6.0 或更新版本（亦可使用 .NET Framework 4.8，但版本越新越好）。  
> - Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）。  
> - 一份至少包含一個方程式的 Word 文件（以下稱為 `Sample.docx`）。  

如果你已備妥上述條件，讓我們開始吧。

![將文件另存為 txt 範例](image.png "將文件另存為 txt 範例")

## Step 1 – 安裝 Aspose.Words 並建立主控台專案

首先，打開你慣用的 IDE（Visual Studio、Rider，或甚至 VS Code），新建一個主控台專案：

```bash
dotnet new console -n TxtExportDemo
cd TxtExportDemo
dotnet add package Aspose.Words
```

這行指令會把最新的 Aspose.Words 二進位檔加入專案檔。依我所見，使用最新版（目前為 24.10）可避免多項與 Office Math 相關的隱藏錯誤。

## Step 2 – 載入 Word 文件

接下來，我們需要一個代表欲轉換 .docx 的 `Document` 物件。`using` 陳述式可確保檔案在使用完畢後正確釋放。

```csharp
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the source Word file – make sure the path is correct.
        Document doc = new Document(@"C:\Path\To\Sample.docx");
        // The rest of the code follows…
    }
}
```

為何要這樣載入？`Document` 會解析整個 OpenXML 包，提供圖片、表格，且最關鍵的是能取得包含方程式的 `OfficeMath` 節點。若不先載入文件，就無法匯出任何內容。

## Step 3 – 設定 TXT 儲存選項以 LaTeX 方式匯出方程式

這是本教學的核心。預設的純文字儲存會去除除原始字元之外的所有內容。將 `OfficeMathExportMode` 設為 `LaTeX` 後，Aspose.Words 會把每個 `OfficeMath` 節點替換成其 LaTeX 表示。

```csharp
// Step 3: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This converts every equation into LaTeX syntax.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

**為什麼選 LaTeX？** LaTeX 是科學出版的通用語言。之後把產生的 `.txt` 檔匯入支援 `$…$` 的 LaTeX 編輯器或 Markdown 處理器時，方程式會完美呈現。若你偏好 MathML 或純 Unicode，Aspose.Words 也支援，只要改變列舉值即可。

## Step 4 – 將文件儲存為純文字檔

設定完選項後，儲存只需要一行程式碼。檔名可自行決定，我們使用 `Equations.txt` 以保持清晰。

```csharp
// Step 4: Save the document as a plain‑text file with the configured options
doc.Save(@"C:\Path\To\Equations.txt", txtSaveOptions);
```

執行程式後會產生一個 `Equations.txt`，內容大致如下：

```
This is a sample paragraph.

The quadratic formula is given by:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

Another equation:
\[
E = mc^2
\]
```

請注意 `\[` … `\]` 分隔符——這是 LaTeX 的「顯示數學」標記，多數編輯器會自動辨識。

## Step 5 – 驗證輸出（若顯示異常該怎麼辦）

在任意文字編輯器中開啟產生的檔案。若看到原始的 LaTeX 字串，代表成功。若方程式變成亂碼，請檢查以下兩點：

1. **OfficeMathExportMode** – 確認已設定為 `LaTeX`。  
2. **文件版本** – 舊版 .doc 檔有時會以專有格式儲存方程式，請先轉成 .docx。

快速驗證方法是把內容貼到線上 LaTeX 渲染器（如 Overleaf），若方程式正確顯示，即表示成功。

## Step 6 – 邊緣情況與進階技巧

### 同段落內的多個方程式

當多個 `OfficeMath` 物件相鄰時，Aspose.Words 會在每個 LaTeX 區塊之間插入空格。若需要更緊密的控制（例如以逗號分隔的內嵌方程式），可在產生的 txt 檔後處理：

```csharp
string txt = File.ReadAllText(@"C:\Path\To\Equations.txt");
txt = txt.Replace(@"\] \[", @"\]\,\[" ); // adds a thin space between display blocks
File.WriteAllText(@"C:\Path\To\Equations.txt", txt);
```

### 保留非數學的格式

純文字無法保留粗體或斜體，但可指示 Aspose.Words 加入 Markdown 標記：

```csharp
txtSaveOptions.AdditionalExportOptions = TxtExportOptions.Markdown;
```

此時粗體會顯示為 `**bold**`，斜體則為 `_italic_`。若之後要將檔案導入靜態網站產生器，這非常有用。

### 匯出至其他數學格式

若下游工具偏好 MathML，只需切換：

```csharp
txtSaveOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
```

其餘流程保持不變——說明了只要改一行程式碼，就能 **將 Word 轉換為 LaTeX** 或其他格式。

## 常見問題

**Q: 這在 .NET Core 上可用嗎？**  
A: 完全可以。Aspose.Words 支援跨平台，程式碼在 Windows、Linux 或 macOS 上皆可執行。

**Q: 若 Word 檔案有密碼保護該怎麼辦？**  
A: 使用包含密碼的 `LoadOptions` 載入，之後照常處理。

```csharp
LoadOptions loadOpts = new LoadOptions { Password = "mySecret" };
Document protectedDoc = new Document(@"C:\Path\Protected.docx", loadOpts);
```

**Q: 能只匯出方程式，跳過一般文字嗎？**  
A: 可以。遍歷 `doc.GetChildNodes(NodeType.OfficeMath, true)`，將每個節點的 LaTeX 手動寫入檔案。這是一種在不需要正文時 **匯出方程式為 LaTeX** 的好方法。

## 重點回顧 – 一次完成將文件另存為含 LaTeX 方程式的 TXT

我們從一個簡單問題開始：*如何在保留數學式的同時將 Word 檔案另存為 txt？* 只要安裝 Aspose.Words、載入文件、以 `OfficeMathExportMode.LaTeX` 設定 `TxtSaveOptions`，再呼叫 `doc.Save`，即可得到可靠的管線，既 **將文件另存為 txt** 又 **匯出方程式為 LaTeX**。

接下來，你可以：

- **將 Word 轉換為 LaTeX**，完成整篇手稿的轉換。  
- 使用產生的 txt 作為支援 LaTeX 的靜態網站生成器的輸入。  
- 擴充腳本以批次處理整個資料夾的 Word 檔案。  

試著執行、調整匯出模式，讓純文字 LaTeX 檔案為你的下一篇研究論文或文件專案分擔繁重工作。

---

*祝開發順利，願你的方程式永遠渲染得漂亮！*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}