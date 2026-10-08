---
category: general
date: 2026-03-08
description: 自訂字型設定讓您可以設定字型、安心載入 Word 文件，並使用 Aspose.Words 處理缺少的字型。
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: zh-hant
og_description: 自訂字型設定可讓您設定字型、安心載入 Word 文件，並使用 Aspose.Words 處理缺失的字型。
og_title: C# 中的自訂字型設定 – 載入 Word 及處理缺少的字型
tags:
- Aspose.Words
- C#
- Font Management
title: C# 中的自訂字型設定 – 載入 Word 並處理缺失字型
url: /zh-hant/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# 中的自訂字型設定 – 載入 Word 並處理缺少的字型

有沒有想過當 Word 檔案引用了您未安裝的字型時，**custom font settings** 是如何運作的？這是一個常見的問題——您的文件在一台機器上顯示正常，但在另一台機器上卻突然所有段落都切換成備用字型。  

好消息是？使用 Aspose.Words 您可以 **set font settings**、**load Word document** 內容，並 **handle missing fonts**，一次搞定。以下您會看到一個完整、可直接執行的範例，示範如何操作，並說明每一步的原因。

## 您將學到的內容

* 建立 `LoadOptions` 物件並附加 `FontSettings` 實例。  
* 註冊警告回呼，以便查看哪些字型被替換。  
* 載入可能缺少字型的 DOCX 檔案，並將替換細節輸出至主控台。  

完成後，您就能自信地發佈 C# 應用程式，因為每個缺少字型的情況都會被記錄，之後可以加以處理。

> **先決條件：** 已透過 NuGet 安裝 Aspose.Words for .NET（v23.12 或更新版本），並具備基本的 C# 主控台應用程式知識。

---

## 自訂字型設定 – 設定 LoadOptions

您首先需要的是一個 `LoadOptions` 物件。它告訴 Aspose.Words 如何處理傳入的檔案。透過指派全新的 `FontSettings` 實例，我們為函式庫提供了一個搜尋自訂字型的場所。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**為什麼這很重要：**  
如果省略 `FontSettings`，Aspose.Words 會退回使用系統預設的字型集合。這表示任何缺少的字型都會被靜默替換，且您不會知道哪些字型被換掉。透過建立明確的 `FontSettings` 容器，您即可完整掌控字型搜尋過程。

---

## 在 LoadOptions 上設定字型設定

既然我們已有 `FontSettings` 物件，您可能會想知道要指向哪裡。通常會加入一個資料夾，裡面放置您隨應用程式一起發佈的字型：

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*如果您沒有私人資料夾，可以省略此區塊——Aspose.Words 仍會透過警告回呼報告缺少的字型。*

**Pro tip:** 如果您的字型分散在子資料夾中，請使用 `recursive: true` 旗標。這樣可免除手動逐一加入路徑的麻煩。

---

## 使用自訂字型設定載入 Word 文件

有了上述選項，載入文件變得非常簡單。`Document` 建構函式接受檔案路徑以及我們剛建立的 `LoadOptions`。

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**背後發生了什麼？**  
Aspose.Words 會解析 DOCX，檢查每個 `<w:font>` 參照，並參照您提供的 `FontSettings`。若找不到字型，會觸發 `FontSubstitution` 類型的警告。我們的自訂處理程式（如下所示）會捕捉這些警告。

---

## 使用警告回呼處理缺少的字型

`IWarningCallback` 介面讓您能對載入過程中出現的任何問題作出回應。實作它相當簡單：

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

當文件載入時，每個缺少的字型都會產生類似以下的訊息：

```
Font substituted: Arial -> Liberation Sans
```

**為什麼要記錄這些訊息：**  
在正式環境中，您可以將這些訊息重新導向至檔案或遙測系統，方便快速辨識需要捆綁或取得授權的字型。

---

## 完整範例程式

以下是一個獨立的主控台程式，將所有步驟整合在一起。將它複製貼上到新的 .NET Core 主控台專案中，然後按 **Run**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**預期輸出**（假設 `input.docx` 使用了您未安裝的字型）：

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

如果所有字型皆已存在，您只會看到最後的確認訊息。

---

## 常見問題與邊緣情況

| Question | Answer |
|----------|--------|
| **如果需要將缺少的字型嵌入 PDF 中，該怎麼做？** | 載入後，呼叫 `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";`，然後使用 `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;` 來啟用嵌入。 |
| **我可以抑制警告而不是記錄它們嗎？** | 可以——將 `loadOptions.WarningCallback = null;`，或實作回呼以忽略非字型相關的警告。 |
| **這適用於 `.doc` 與 `.rtf` 檔案嗎？** | 絕對可以。相同的 `LoadOptions` 物件適用於 Aspose.Words 支援的任何格式。 |
| **回呼是執行緒安全的嗎？** | 回呼會在載入文件的同一執行緒上執行，因此您可以安全地寫入主控台。若在多執行緒情境下，請使用並發集合或日誌框架。 |

---

## 專業提示與常見陷阱

* **Pro tip:** 如果您隨應用程式發佈的字型在目標機器上未安裝，請將其加入傳遞給 `SetFontsFolder` 的資料夾。這可確保渲染結果可預測。  
* **Watch out for licensing:** 某些字型在嵌入時需要商業授權。捆綁前務必確認字型的授權條款 (EULA)。  
* **Performance note:** 載入大量字型庫會減慢文件解析速度。請保持資料夾精簡——僅包含實際需要的字型。  
* **Edge case:** 當文件以 *PostScript 名稱* 而非字型族名稱引用字型時，只要字型檔案存在於搜尋路徑中，Aspose.Words 仍能正確解析。  

---

## 結論

您現在已掌握完整、可投入生產環境的 **custom font settings** 使用模式。透過設定 `LoadOptions`、註冊警告回呼，並視需要指向私人字型資料夾，您即可可靠地 **set font settings**、**load Word document** 內容。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}