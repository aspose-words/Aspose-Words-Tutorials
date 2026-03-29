---
category: general
date: 2026-03-28
description: 如何在使用 Aspose.Words 載入 DOCX 時捕捉警告，並取得缺少字型的警告訊息。學習有效處理缺字型問題。
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: zh-hant
og_description: 如何在使用 Aspose.Words 載入 DOCX 時捕捉警告、取得警告訊息，並以實作範例處理缺少字型。
og_title: 如何在 Aspose.Words 中捕捉警告 — 完整 C# 教程
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何捕捉 Aspose.Words 警告 – 完整 C# 指南
url: /zh-hant/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中捕獲警告 – 完整 C# 教學

有沒有想過 **如何捕獲** 在使用 Aspose.Words 載入 Word 文件時彈出的警告？也許你看到字體奇怪的變化，想要確切知道原因。簡而言之，你可以掛接庫的警告系統，**取得警告訊息**，甚至在字體缺失破壞版面之前 **處理缺少的字體**。

在本教學中，我們將示範一個實務情境：載入 DOCX、收集引擎產生的每一個警告，並印出任何字體替換的詳細資訊。完成後，你將擁有可直接執行的程式碼範例，了解每一步背後的「為什麼」，並知道如何將此方法延伸到自己的專案。

## 你將學會

- 如何設定 `LoadOptions` 讓警告自動被捕獲。  
- 從 `WarningInfoCollection` **取得警告訊息** 的確切方式。  
- 如何透過 `WarningType.FontSubstitution` 標誌辨識並回應 **缺少的字體**。  
- 解決邊緣案例的技巧，例如含有嵌入字體或自訂字體資料夾的文件。  

不需要額外參考資料——所有內容都在此。

---

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦支援 .NET Framework 4.7+）。  
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）。  
- 一個範例 DOCX（`input.docx`），其字體可能缺失或使用未安裝於本機的字體。  

就這些。如果你已熟悉 C# 與 Visual Studio，只要複製貼上程式碼即可立即執行。

---

## 步驟 1：準備 Load Options 與警告回呼

當你呼叫 `new Document(path, loadOptions)` 時，Aspose.Words 會先解析檔案。解析過程中可能遇到缺少字體、未支援功能或已棄用的標記。要捕捉這些事件，需要一個 **警告回呼** 物件。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**為什麼這很重要：** 若沒有回呼，Aspose.Words 只會把警告靜默寫入主控台（或直接丟棄），讓你無法得知可能影響版面的字體替換。提供專屬的 `WarningInfoCollection` 後，你即可完整掌握所有資訊。

> **小技巧：** 若你只在意與字體相關的警告，之後可以自行過濾——但先收集 *全部* 警告能為未來的問題提供安全網。

---

## 步驟 2：使用已設定好的選項載入文件

回呼準備好之後，載入檔案。`Document` 建構子會自動在發現問題時呼叫回呼。

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**底層發生了什麼？** Aspose.Words 會解析 Open XML、解析樣式，並嘗試將每個字體參照對應到系統已安裝的字體。若找不到匹配，就會產生 `WarningInfo`，類型為 `FontSubstitution`。

---

## 步驟 3：取得並檢查收集到的警告

載入完成後，`warningCollector` 已包含所有發生的警告。現在把它們取出，並聚焦於字體替換訊息。

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**範例輸出**（你的主控台可能會顯示類似以下內容）：

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

如果想要 *全部* 警告，只需移除 `if` 判斷或對每筆條目列印 `warning.Type`。

---

## 步驟 4：處理缺少的字體 – 不只是記錄

捕獲警告固然有用，但通常你還需要以程式方式 **處理缺少的字體**。以下提供兩種常見策略：

### 4.1 以特定備援字體取代缺失字體

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

現在任何缺少的字體都會被換成 *Calibri*，而不是庫的預設備援字體。

### 4.2 動態嵌入替代字體

若你有自訂字體檔（例如 `MyFallback.ttf`），可以在執行時註冊：

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

當你需要將特定企業字體隨應用程式一起發佈時，這個方法非常方便。

> **邊緣案例：** 若文件已嵌入所需字體，系統的替換規則會被忽略。此時，對該字體的警告集合會是空的，這正是你想要的結果。

---

## 步驟 5：完整可執行範例（直接複製貼上）

以下是一個自包含的程式，示範從頭到尾的所有步驟。只要把 `YOUR_DIRECTORY/input.docx` 改成測試檔案的實際路徑即可。

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**預期結果**

- 主控台會列印每筆字體替換警告，前面加上警告表情符號以提升可見度。  
- 輸出 DOCX（`output.docx`）會在偵測到缺失字體的地方使用 *Calibri*。  
- 不會拋出未處理的例外——警告系統會優雅地處理任何未知字體。

---

## 常見問題與解答

**Q: 這能否用於由 Word 產生的 PDF？**  
A: 能。Aspose.Words 把 PDF 視為另一種輸出格式。警告捕獲發生在 *載入* 階段，與最終匯出無關。

**Q: 若我要捕獲 **所有** 文件操作（儲存、轉換等）的警告，該怎麼做？**  
A: 在文件實例化後，將同一個 `WarningInfoCollection` 指派給 `Document.WarningCallback`。之後的每個操作都會把新條目推入同一集合。

**Q: 警告回呼會影響效能嗎？**  
A: 影響極小。集合只負責儲存物件；除非在緊密迴圈中處理上千筆警告，否則不會感受到明顯的慢速。

**Q: 我要如何過濾掉我不在乎的警告？**  
A: 實作繼承自 `IWarningCallback` 的自訂類別，並在 `Warning` 方法內自行篩選。內建的 `WarningInfoCollection` 只負責儲存，不會過濾。

---

## 專業技巧與常見陷阱

- **小技巧：** 常檢查 `Warning.Description`——它會包含缺失的字體名稱，幫助你決定是否要將該字體隨應用程式一起發佈。  
- **注意嵌入字體：** 若來源 DOCX 已嵌入所需字體，即使本機未安裝，Aspose.Words 也不會發出替換警告。  
- **執行緒安全性：**`WarningInfoCollection` 並非執行緒安全。若同時載入多個文件，請為每個執行緒分配獨立的集合。  
- **版本檢查：** 警告 API 從 Aspose.Words 20.8 起已穩定。確保使用較新版本，以免遺漏較新的警告類型。

---

## 結論

我們已說明 **如何捕獲 Aspose.Words 的警告**，示範 **取得警告訊息** 的方法，並提供實用的 **缺少字體處理** 方案（備援字體或自訂字體資料夾）。完整範例可直接放入任何 .NET 專案，且概念可擴展至更大型的自動化流程。

接下來，你可以探索：

- 使用 `Document.WarningCallback` 在 **儲存** 操作期間捕獲警告。  
- 將警告寫入檔案或遙測系統，以供正式環境監控。  
- 擴充回呼，讓缺失字體自動以品牌專屬字體取代。

盡情實驗吧——換掉備援字體、批次處理更多文件，或將警告收集器整合至 CI 流程，以標記字體相關的回歸問題。祝程式開發順利，願你的文件永遠如你所預期般呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}