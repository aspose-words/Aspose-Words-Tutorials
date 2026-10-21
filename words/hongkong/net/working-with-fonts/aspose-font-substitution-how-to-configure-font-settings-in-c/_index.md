---
category: general
date: 2026-03-27
description: Aspose 字體替換變得簡單：學習如何設定字體、捕捉警告，以及在 .NET 應用程式中處理缺失的字體。
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: zh-hant
og_description: 透過配置字型設定與使用警告回呼處理缺失字型，精通 Aspose 字型取代。完整 C# 指南。
og_title: Aspose 字體置換 – 在 C# 中配置字體設定
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose 字型取代 – 如何在 C# 中設定字型
url: /zh-hant/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – 完整指南：設定字體設定

有沒有遇過文件突然把自訂字體換成通用字體？那就是 **aspose font substitution** 在發揮作用——將缺少的字體替換為最接近的匹配字體。這很方便，但如果你需要*精確*知道被換掉的是哪一個字體，就必須使用函式庫的警告機制，並自行設定字體設定。

在本教學中，我們將示範一個真實情境：載入一個引用了你未安裝字體的 DOCX，捕捉字體替換事件，並在主控台印出友善訊息。完成後，你將能熟練 **configure font settings**、設定 **Aspose.Words warning callback**，以及將範例延伸至任何工作流程。

> **你需要的環境**  
> • .NET 6+（或 .NET Framework 4.7.2+）  
> • Aspose.Words for .NET（最新 NuGet）  
> • 一個引用了缺少字體的 DOCX（此處稱為 `MissingFont.docx`）  

讓我們開始吧。

---

## Step 1: 安裝 Aspose.Words 並準備專案

在撰寫任何程式碼之前，先確定已參考 Aspose.Words 套件：

```bash
dotnet add package Aspose.Words
```

> **專業提示**：使用最新的穩定版；截至 2026 年 3 月，版本為 23.11.0。較新版本會改進字體匹配演算法，並加入更多警告類型。

建立一個新的 Console 應用程式（或將程式碼放入現有專案），並加入一般的 `using` 指示詞：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

這些命名空間讓我們可以存取 `Document`、`LoadOptions` 以及相關的字體類別。

---

## Step 2: 使用 LoadOptions 設定 Font Settings

**aspose font substitution** 控制的核心在 `LoadOptions.FontSettings`。只要提供一個空的 `FontSettings` 物件，即可讓 Aspose 使用預設搜尋路徑，並透過警告回呼報告任何替換。

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

為什麼不直接使用預設？因為只有在 `FontSettings` 屬性非 null 時，才能掛接警告回呼（下一步）。這一行程式碼為我們提供了介入替換流程的切入點，同時不會改變實際的字體搜尋行為。

---

## Step 3: 附加 Warning Callback 以捕捉替換

Aspose.Words 實作了 `IWarningCallback` 介面。每當發生值得注意的事件（例如缺少字體）時，系統會呼叫我們的 `Warning` 方法。我們將實作一個簡易處理器，過濾 `WarningType.FontSubstitution`，並將說明印出。

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

以下是處理器本身：

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **為什麼這很重要** – 若未設定回呼，Aspose 會悄悄替換字體，你永遠不會知道實際使用了哪一個。回呼讓整個過程透明化，對於合規報告或除錯排版問題都相當關鍵。

---

## Step 4: 使用已設定的 Options 載入文件

現在終於可以載入文件，並傳入先前準備好的 `loadOptions`。如果來源檔案引用了未安裝的字體，我們的處理器就會被觸發。

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

將 `YOUR_DIRECTORY` 替換為 `MissingFont.docx` 所在的實際路徑。執行程式後，你應該會看到類似以下的輸出：

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

這行訊息會精確告訴你缺少哪個字體，以及 Aspose 選擇的備用字體。

---

## Step 5: （可選）微調字體搜尋路徑

如果公司有私有字體資料夾，可以在回退至系統字體之前，先告訴 Aspose 去哪裡找。這是 **configure font settings** 的進階用法：

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

將 `recursive: true` 設為 true，表示 Aspose 也會掃描子資料夾。如此一來，程式會優先使用你的私有字體，降低不必要的替換機會。

---

## Full Working Example

把所有步驟整合起來，以下是一個完整、可直接執行的範例程式：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**預期輸出**（當遇到缺少字體時）：

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

若所有字體皆已安裝，程式將靜默執行（不會有警告），仍會產生 PDF。

---

## Common Questions & Edge Cases

### 如果我要徹底*阻止*字體替換，該怎麼做？

將 `FontSettings.SubstitutionSettings` 設為 `null`，或使用 `FontSettings.FontSubstitutionSettings` 來控制行為。例如：

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

如此一來，Aspose 會拋出例外而非悄悄替換，你可以自行捕捉並處理。

### 這個機制能用在其他檔案格式嗎（例如 .doc、.rtf）？

當然可以。相同的 `LoadOptions` 物件可傳給任何接受檔案路徑的 `Document` 建構子。警告回呼會對所有依賴字體的格式觸發。

### 我能取得*精確*的備用字體名稱嗎？

可以。`info.Description` 文字同時包含缺少的字體與替代字體。若需要程式化取得名稱，可自行解析字串，或在較新版本中直接使用 `FontInfo` 物件。

### 在多執行緒環境下會怎樣？

`FontSettings` **不是**執行緒安全的。每個執行緒應建立自己的 `LoadOptions`（以及各自的 `FontSettings`），或以 lock 保護存取。

---

## Conclusion

我們已完整說明如何在 C# 應用程式中掌握 **aspose font substitution** 與 **configure font settings**：

1. 安裝 Aspose.Words 並加入必要的 `using` 陳述式。  
2. 建立帶有全新 `FontSettings` 的 `LoadOptions`。  
3. 附加自訂的 `IWarningCallback` 以顯示替換事件。  
4. 載入文件，讓回呼報告任何缺少的字體。  
5. （可選）擴充搜尋路徑或完全停用替換。

有了這套模式，你可以為合規需求記錄缺字體、在 UI 中提醒使用者，或在發佈前自動嵌入備用字體。接下來，你或許想探索 **Aspose.Words font substitution policies**，或將此工作流程整合至更大的文件處理管線。

祝程式開發順利，願你的文件永遠以正確的字體呈現！  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}