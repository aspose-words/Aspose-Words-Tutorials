---
category: general
date: 2026-05-29
description: 學習如何在 Aspose.Words 中設定 FontSettings，並優雅地處理缺失字型。提供完整程式碼與最佳實踐的逐步指南。
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: zh-hant
og_description: 如何在 Aspose.Words 中設定 FontSettings 並快速處理缺失字型。請參考本指南，獲得完整且可執行的解決方案。
og_title: 如何設定字型設定 – 處理缺失字型
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: 如何設定 FontSettings – 處理缺失字型
url: /zh-hant/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何設定 FontSettings – 處理缺失字型

有沒有想過 **如何設定 FontSettings**，卻在使用 Aspose.Words 時突然遇到文件引用了你系統中未安裝的字型？這是個常見的問題，尤其是在伺服器上只安裝了最小字型集，卻要處理客戶提供的檔案。好消息是，你可以捕捉這些缺口，**處理缺失字型**，而不會讓應用程式當機或產生醜陋的 PDF。

在本教學中，我們將示範一個真實情境：載入一個要求「Calibri」的 DOCX，而你的 Linux 容器只提供「DejaVu Sans」。你將看到如何設定 FontSettings、訂閱字型替換警告，並提供備援字型，使文件能如作者預期般正確呈現。沒有冗長說明——只提供你今天即可直接使用的程式碼。

## 前置條件

- .NET 6.0 或更新版本（在 .NET Framework 4.7+ 上 API 行為相同）
- Aspose.Words for .NET 23.10 或更新版本（NuGet 套件名稱為 `Aspose.Words`）
- 基本的 C# 開發環境（Visual Studio、Rider 或 VS Code）

如果你已具備上述條件，讓我們開始吧。

## 步驟 1：建立 FontSettings 並監聽替換事件

解決方案的核心是 `FontSettings` 物件。透過將處理函式掛到其 `FontSubstitutionWarning` 事件，你可以即時取得每次 Aspose.Words 必須替換缺失字型的報告。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**為什麼這很重要：**  
當引擎找不到 *Calibri* 時，可能會悄悄退回使用 *Arial*。透過監聽警告，你可以保留透明的稽核紀錄——對除錯或合規報告都相當有幫助。

> **小技巧：** 若在 CI 伺服器上執行，請將輸出導向日誌檔，方便在批次執行後檢視哪些字型缺失。

## 步驟 2：將 FontSettings 套用至 LoadOptions

`LoadOptions` 是控制文件解析方式的入口。將剛才設定好的 `FontSettings` 指派給它，之後的每一次 `Document` 載入都會遵循我們的替換邏輯。

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**背後發生了什麼？**  
在 `Document` 建構子執行時，Aspose.Words 會讀取 DOCX 的 XML、解析字型參照，若找不到字型就會觸發先前設定的警告。若沒有這個掛鉤，你根本不會知道替換已發生。

## 步驟 3：載入文件並（可選）定義備援字型資料夾

現在終於把檔案載入記憶體。如果你已有備援字型資料夾（例如隨應用程式一起部署的 OpenType 字型目錄），請告訴 `FontSettings` 去哪裡找。這一步是可選的，但通常是處理缺失字型最乾淨的方式。

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**邊緣案例提醒：**  
若文件內嵌了自訂字型（以二進位串流形式），Aspose.Words 會自動使用它——不需要替換。警告只會在 *缺少* 系統字型時觸發。

### 驗證結果

載入後，你可能想將文件另存為 PDF 或 Word，以確認版面是否正確。

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

執行程式時，主控台會輸出類似以下的行：

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

只要看到這些訊息，就代表你已成功 **處理缺失字型**，且清楚知道發生了哪些替換。

## 步驟 4：進階 – 自訂字型替換規則（可選）

有時你需要確定的映射，例如永遠將 *Times New Roman* 替換為 *Liberation Serif*。這可以透過 `FontSettings.SubstitutionTable` 來達成。

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**為什麼要這樣做？**  
明確的規則讓你掌控排版，確保在產出 PDF 時保持品牌字體一致性，特別是製作行銷素材時。

## 常見陷阱與避免方式

| 陷阱 | 症狀 | 解決方法 |
|------|------|----------|
| **沒有警告輸出** | 你以為字型沒問題，但文件顯示異常。 | 確保在載入文件 **之前** 已掛載 `FontSubstitutionWarning`。 |
| **備援資料夾未被掃描** | 替換仍回退到系統預設字型。 | 呼叫 `SetFontsFolder(path, true)`，第二個參數 `true` 代表遞迴子資料夾。 |
| **大量批次時效能下降** | 載入 1 萬份文件變慢。 | 將單一 `FontSettings` 實例快取起來，重複使用；避免每次都重新建立。 |
| **內嵌字型被忽略** | 你預期使用自訂內嵌字型，卻仍發生替換。 | 確認原始 DOCX 確實內嵌了字型（在 Word 中檢查：檔案 → 資訊 → 字型）。 |

## 完整範例程式

以下是可直接複製貼上的完整程式碼，示範從事件處理到最終 PDF 儲存的全部步驟。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**預期的主控台輸出**（範例）：

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

執行程式，開啟 `Output.pdf`，你會看到文字已使用備援字型呈現——不會出現缺字方塊，也不會當機。

## 結論

現在你已掌握在 Aspose.Words 中 **設定 FontSettings** 並優雅 **處理缺失字型** 的完整生產模式。透過掛載 `FontSubstitutionWarning` 事件、指向備援字型目錄，必要時再定義明確的替換規則，你即可在自動化文件流程中獲得完整的可見性與排版控制。

接下來可以嘗試加入品牌專屬的自訂字型集合，或探索 `FontSourceBase` API 從資料庫或雲端儲存載入字型。原理相同——只要把不同的來源接到 `FontSettings` 即可。

對於右至左腳本或 Emoji 字型等邊緣案例有疑問嗎？歡迎在下方留言，祝開發順利！

## 接下來該學什麼？

- [如何在 Aspose.Words 中擷取字型 – 完整指南](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [如何在 Aspose.Words 中偵測字型 – 處理警告與設定](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [如何載入 DOCX 並偵測缺失字型 – 完整 C# 教學](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}