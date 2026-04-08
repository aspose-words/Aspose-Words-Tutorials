---
category: general
date: 2026-01-05
description: 如何快速擷取字型並處理缺失字型（使用 Aspose.Words）。了解一步一步的解決方案，附完整 C# 程式碼。
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: zh-hant
og_description: 如何在 Aspose.Words 中捕捉字型並處理缺失的字型。請參考此詳細指南，以獲得可靠的 C# 實作。
og_title: 如何在 Aspose.Words 中擷取字型 – 完整教學
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何在 Aspose.Words 中捕獲字型 – 完整指南
url: /zh-hant/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中捕獲字型 – 完整指南

有沒有想過在使用 Aspose.Words 載入 Word 文件時 **如何捕獲字型**？你並不是唯一有此疑問的人。缺少字型可能導致細微的版面錯位，若沒有適當的警告，你可能直到最終的 PDF 看起來不對勁才發現。於本教學中，我們將完整示範如何 **捕獲字型** **and** 處理缺失的字型，確保輸出保持像素完美。

我們將逐步說明一個真實情境、設定警告回呼，並提供可直接執行的 C# 範例。完成後，你將了解此作法的重要性、如何實作，以及當字型在環境中消失時需要留意的事項。

## 你將學到什麼

- 如何設定 **LoadOptions** 以監聽與字型相關的警告。  
- **IWarningCallback** 與 **WarningInfo** 在 Aspose.Words 中的角色。  
- 實用技巧，協助排除問題與記錄缺失的字型。  
- 完整、獨立的程式碼範例，可直接貼到 Visual Studio 並立即執行。  

**先決條件：** .NET 6+（或 .NET Framework 4.7.2+）、透過 NuGet 安裝的 Aspose.Words for .NET，以及對 C# 的基本了解。無需其他函式庫。

---

## 步驟 1：設定 Load Options 以捕獲字型

我們首先需要一個 **LoadOptions** 實例。此物件告訴 Aspose.Words 在讀取文件時的行為方式。透過指派自訂的 **IWarningCallback**，我們可以攔截載入過程中發生的任何字型替換警告。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**為什麼這很重要：**  
Aspose.Words 會悄悄將缺失的字型替換為預設字型，除非你要求告知。透過插入回呼，我們在載入時 **捕獲字型** 資訊，讓我們有機會記錄、替換，甚至中止操作。

> **專業提示：** 若一次處理多個文件，請將 `loadOptions` 保持為可重複使用的變數。這可避免一遍又一遍重新建立相同的回呼。

---

## 步驟 2：使用已設定的選項載入文件

現在回呼已設定完畢，我們載入文件。**Document** 建構式接受檔案路徑以及剛剛設定好的 **LoadOptions**。

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

若有任何字型缺失，Aspose.Words 會發出警告，`FontWarningCollector` 會接收到該警告。文件本身仍會載入，但你將清楚記錄哪些字型被替換。

---

## 步驟 3：實作 FontWarningCollector – 處理缺失的字型

**捕獲字型** 的核心在於 `FontWarningCollector` 類別。它實作 `IWarningCallback`，僅過濾 `WarningType.FontSubstitution` 事件。

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**說明：**  
- `info.Type` 告訴我們警告的類別。透過檢查 `FontSubstitution`，我們 **處理缺失的字型**，而不會讓輸出被不相關的訊息（例如已棄用功能）所淹沒。  
- `info.Description` 包含可供人閱讀的訊息，例如「字型 'Comic Sans MS' 已被替換為 'Arial'」。這正是你審核字型清單所需的資料。

> **注意：** 若在關鍵字型缺失時需要停止處理，請在 `if` 區塊內拋出例外，而非僅列印訊息。

---

## 步驟 4：驗證輸出 – 期待的結果

在主控台或 IDE 中執行程式。每當缺少字型時，你會看到類似以下的行：

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

若所有字型皆存在，回呼將保持沉默，文件亦會順利載入。此時你可以放心地繼續儲存、轉換或列印文件，確信已 **捕獲字型** 資訊。

---

## 步驟 5：完整可執行範例（全部組合）

以下是完整、可直接複製貼上的程式。它包含 using 指令、回呼實作，以及示範將載入的文件儲存為 PDF 的小範例。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**執行程式碼：**  
1. 建立新的主控台專案 (`dotnet new console -n FontCaptureDemo`)。  
2. 新增 Aspose.Words 套件 (`dotnet add package Aspose.Words`)。  
3. 用上述程式碼取代產生的 `Program.cs`。  
4. 放置一個故意引用你未安裝字型（例如 “Papyrus”）的 DOCX。  
5. 執行 (`dotnet run`)。觀察主控台的替換訊息，然後開啟 `output.pdf` 以驗證版面配置。

---

## 常見問題與邊緣情況

### 如果之後需要缺失字型的清單該怎麼辦？

將訊息儲存在 `FontWarningCollector` 內的 `List<string>`，並透過屬性公開。如此即可在處理大量文件後將清單寫入日誌檔案。

### 這對加密或受密碼保護的檔案有效嗎？

可以，但必須透過 `LoadOptions.Password` 提供密碼。文件解密後，警告回呼的行為相同。

### 我可以用自訂的備援字型取代缺失的字型嗎？

當然可以。在 `Warning` 方法內，你可以呼叫 `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`。這可確保替換是確定性的。

### 這會影響效能嗎？

開銷極小——基本上每個警告只會呼叫一次方法。在成千上萬文件的批次處理中，影響可忽略不計，遠低於載入每個檔案的 I/O 成本。

---

## 結論

我們已說明了在 Aspose.Words 中 **如何捕獲字型**，示範了使用乾淨的警告回呼 **處理缺失字型**，並提供完整可執行的範例。將此模式套用於文件處理流程後，你將不會再因靜默的字型替換而感到意外。

準備好進一步了嗎？試著擴充收集器以寫入 JSON 日誌、整合至監控儀表板，或自動將缺失字型嵌入輸出 PDF。可能性無窮，而你已擁有堅實的基礎。

祝開發愉快！ 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}