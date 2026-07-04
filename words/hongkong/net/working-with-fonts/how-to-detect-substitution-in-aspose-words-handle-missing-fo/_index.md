---
category: general
date: 2026-04-24
description: 如何在 Aspose.Words 中使用 C# 檢測缺失字型的替代。此指南示範如何透過 FontSettings 警告可靠地處理缺失字型。
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: zh-hant
og_description: 如何在 Aspose.Words 中使用 C# 偵測缺失字型的取代。學習使用 FontSettings 警告來處理缺失字型。
og_title: 如何在 Aspose.Words 中偵測取代 – 完整指南
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: 如何在 Aspose.Words 中偵測字型取代 – 處理缺少字型
url: /zh-hant/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何偵測 Aspose.Words 中的字型替代 – 處理缺失字型

有沒有想過當文件嘗試使用伺服器上未安裝的字型時，**如何偵測字型替代**？這是常見的痛點，特別是在自動化流程中產生 PDF 或 Word 檔案時。好消息是 Aspose.Words 提供內建的掛鉤讓你即時發現此情況，同時你也可以**優雅地處理缺失字型**。

在本教學中，我們將逐步示範一個實務範例，說明如何透過 `FontSettings.Warning` 事件**偵測字型替代**，並解釋如何**處理缺失字型**而不會中斷處理流程。完成後，你將擁有可直接執行的程式碼片段、對每行程式碼意義的清晰理解，以及避免常見陷阱的幾個小技巧。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦可於 .NET Framework 上執行）
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）– 版本 23.11 或更新
- 一個參考了未安裝字型的範例文件（例如 `MissingFont.docx`）
- Visual Studio、VS Code 或任何你慣用的 C# IDE  

除了加入 NuGet 套件外，無需額外設定。

---

## 使用 FontSettings 偵測字型替代

The core of **how to detect substitution** lies in the `FontSettings.Warning` event.  When Aspose.Words can’t find a requested font, it raises a `WarningType.FontSubstitution` warning.  By subscribing to this event you get a real‑time notification, complete with the original font name and the font that was used as a fallback.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**為什麼這樣有效：**  
- `LoadOptions.FontSettings` 告訴 Aspose.Words 使用剛剛建立的 `FontSettings` 物件。  
- 訂閱 `Warning` 讓你在單一位置監控*所有*與字型相關的問題，而不僅限於缺失字型。  
- `WarningType.FontSubstitution` 篩選條件確保你只回應感興趣的特定情況——即 **偵測字型替代** 的核心。

### 預期輸出

使用上述程式碼執行一個參考不存在字型的文件時，會輸出類似以下內容：

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

如果文件僅使用已安裝的字型，控制台將保持沉默——這清楚表示 **偵測字型替代** 成功且沒有誤報。

---

## 優雅地處理缺失字型

偵測到字型替代只是解決問題的一半；你還需要一套策略來**處理缺失字型**，確保最終輸出如預期。以下提供三種實用方法，你可以自由組合使用。

### 1. 提供備用字型資料夾

Aspose.Words 可以搜尋額外的目錄以尋找字型。將其指向包含你常用字型的資料夾，可徹底降低發生字型替代的機會。

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**為什麼：** 當原始字型缺失時，Aspose.Words 會使用已知的備選字型集合，通常能產生更可預測的視覺結果。

### 2. 程式化取代缺失字型

如果需要完全掌控，你可以在偵測到缺失字型後，將其取代為指定的字型。

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**為什麼：** 這告訴引擎確切要使用的字型，讓你能遵循企業品牌或無障礙標準。

### 3. 記錄並中止（當字型替代不可接受時）

有時缺失字型代表文件對你的使用情境（例如法律表單）無效。在此情況下，你可以在發生字型替代時立即拋出例外。

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**為什麼：** 立即失敗可防止下游錯誤，例如表格錯位或簽章損毀。

---

## 完整範例 – 結合所有步驟

以下是一個可直接複製貼上的完整程式，示範 **偵測字型替代** *以及* 多種 **處理缺失字型** 的方式。可自行註解掉不需要的部分。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**預期結果：**  
- 如果 `MissingFont.docx` 參考了機器上不存在的字型，控制台會印出替代警告。  
- 儲存的 `Processed.docx` 會使用你設定的備用字型（或函式庫的預設字型）。  
- 除非你刻意在替代時中止，否則不會出現未處理的例外。

---

## 常見問題與邊緣情況

| 問題 | 回答 |
|----------|--------|
| *如果文件包含多個缺失字型會怎樣？* | 警告事件會對**每一次**替代觸發，因此會看到多行訊息。你可以將它們彙總成清單，以產生摘要報告。 |
| *這在 PDF 轉換時也適用嗎？* | 絕對可以。呼叫 `doc.Save("out.pdf")` 時會同樣遵守 `FontSettings`。字型替代警告仍會觸發，讓你驗證 PDF 的視覺一致性。 |
| *文件已載入後還能偵測字型替代嗎？* | 無法直接。警告會在**載入或儲存**期間拋出。若需載入後分析，請在載入階段將警告收集至集合中。 |
| *DOCX 中嵌入的自訂字型怎麼處理？* | 嵌入的字型被視為已存在，因此不會發生替代。若嵌入的字型損壞，Aspose.Words 仍會拋出警告，可同樣捕捉。 |
| *會有效能影響嗎？* | 影響極小。警告檢查本身負擔輕，主要成本在於載入文件本身。加入字型資料夾可能會稍微增加首次搜尋時間，但僅在首次載入時發生。 |

---

## 專業技巧與常見陷阱

- **專業技巧：** 指向包含大量字型的資料夾時，務必設定 `recursive: true`；否則子資料夾會被忽略。  
- **注意：** Linux 上的大小寫敏感。字型名稱在 Windows 為不區分大小寫，但在 Linux 卻區分，請使用正確的名稱或同時加入兩種變體。  
- **記得：** 若在容器環境執行，請確保字型資料夾已納入映像檔或於執行時掛載。  
- **小技巧：** 若需向最終使用者呈現摘要或記錄至監控系統，可將警告存入 `List<string>`。  

---

## 結論

我們已說明了在 Aspose.Words 中**偵測缺失字型的替代**的方法，展示了多種**處理缺失字型**的方式，並提供了一個完整、可直接執行的範例，可直接放入任何 .NET 專案。透過 `FontSettings.Warning` 事件，你能即時掌握字型問題，並藉由備用資料夾或明確的替代規則，確保輸出如你所預期。

準備好進一步了嗎？試著將解決方案擴充為自動將備用字型嵌入產生的 PDF，或將警告處理器掛接至集中式日誌服務，以支援大規模文件流水線。今天討論的模式——事件驅動偵測、優雅的備援以及明確的錯誤處理——同樣適用於其他 Aspose API，讓你能全面應對字型相關的挑戰。

對字型處理、PDF 轉換或 Aspose.Words 的技巧有更多疑問嗎？在下方留言吧，祝開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}