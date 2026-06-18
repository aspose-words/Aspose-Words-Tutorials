---
category: general
date: 2026-06-17
description: 使用此一步一步的教學，協助 .NET 開發人員在 Aspose.Words 中處理字型替換，並快速偵測缺失的字型。
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: zh-hant
og_description: 處理 Aspose.Words 中的字型替換，並學習如何在文件中偵測缺失的字型，提供清晰的程式碼範例。
og_title: 處理 Aspose.Words 中的字型替換 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: 處理 Aspose.Words 中的字型替換 – 完整程式設計指南
url: /zh-hant/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words 中處理字體替換 – 完整程式設計指南

有沒有想過當 Word 文件引用了伺服器上未安裝的字體時，如何**處理字體替換**？你並不孤單。在許多實際應用中——例如發票產生器或自動化報告服務——缺少字體會導致靜默的替代，破壞版面配置。

好消息是 Aspose.Words 為你提供了內建的警告系統，讓你**偵測缺少的字體**並依需求做出回應。在本教學中，我們將示範如何註冊警告處理程式、載入文件，並取得你需要關注的字體替換事件。最後，你還會看到如何以乾淨、可投入生產的程式碼回答「**如何偵測缺少的字體**？」這個經典問題。

## 本教學涵蓋內容

* 設定 Aspose.Words 於每一次字體替換時發出警告。  
* 在自訂處理程式中捕捉這些警告，以便記錄、取代或中止。  
* 使用捕捉到的資料在文件儲存或呈現前**偵測缺少的字體**。  
* 排除邊緣案例的技巧——例如當替代字體被靜默選取時。  
* 完整、可執行的範例，可直接放入任何 .NET 主控台應用程式。

> **先決條件** – 需要最近的 .NET SDK（6.0 以上皆可），有效的 Aspose.Words for .NET 授權（或臨時評估金鑰），以及一個刻意引用未安裝字體的範例 DOCX。無需其他第三方函式庫。

---

## ## 使用自訂警告處理程式處理字體替換

Aspose.Words 每當找不到請求的字體時，會拋出 `WarningInfo` 物件。預設情況下這些警告會被忽略，這也是為什麼你常常不會注意到字體被替換。要**處理字體替換**，只需要將預設的警告處理程式換成真正會執行動作的自訂處理程式。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### 為什麼這樣做有效

* `FontSettings.DefaultWarningHandler` 是全域靜態屬性——設定一次後，**所有** 在當前 AppDomain 中的 Aspose.Words 操作都會使用你的委派。  
* `WarningInfoCollectionHandler` 會收到包含 `WarningType` 與可讀性說明 `Description` 的 `WarningInfo` 物件。以 `WarningType.FontSubstitution` 為條件過濾，即可只看到你關心的事件。  
* 呼叫 `doc.Save` 會強制函式庫解析所有字體，屆時警告即會觸發。若只想檢查文件而不儲存，可改為呼叫 `doc.UpdatePageLayout()`。

**預期的主控台輸出**（假設缺少的字體是 “Papyrus”）：

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

那一行即是程式庫**偵測到缺少字體**並選擇了替代字體的證明。

---

## ## 在渲染前偵測缺少的字體

有時若必需的字體缺失，你可能需要徹底停止處理——例如品牌指南要求使用特定排版。可以擴充警告處理程式，將所有缺字訊息收集到清單中，之後再自行決定。

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### 如何回答「如何偵測缺少的字體」

* `missingFonts` 清單充當每一次替換事件的帳本。  
* 在 `UpdatePageLayout` 之後，你可以檢查此清單，決定是繼續、記錄，或拋出例外。  
* 這套模式對任何輸出格式（PDF、HTML、影像）皆適用，因為警告系統與格式無關。

---

## ## 進階技巧：以特定字體取代缺少的字體

如果公司有必須使用的字體，你可以指示 Aspose.Words 自動將任何缺少的字體換成你的備用字體。當你希望文件在未經手動後處理的情況下仍能保持可接受的外觀時，這非常實用。

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

將上述程式碼**放在**載入文件之前。現在無論缺少哪個字體，都會被換成 “Calibri”（若 Calibri 不在則換成 “Arial”）。仍會收到警告，但文件會以你指定的字體呈現。

---

## ## 常見陷阱與避免方法

| 陷阱 | 為何會發生 | 解決方案 |
|------|------------|----------|
| **警告在第一次呼叫後消失** | 靜態的 `DefaultWarningHandler` 後續被程式覆寫。 | 在應用程式啟動時**只設定一次**，或保留參考並在需要變更時重新指派。 |
| **只報告第一個缺少的字體** | 某些 API 會批次警告，需要呼叫 `UpdatePageLayout` 或 `Save` 以刷新佇列。 | 強制執行版面更新或以目標格式儲存，以確保所有警告被觸發。 |
| **即使中止仍發生替換** | 警告處理程式在字體已被替換之後才執行。 | 讓處理程式**先記錄**，再拋出例外以阻止後續處理。 |
| **Linux 容器缺少字體** | Linux 通常沒有 Windows 的字體目錄，導致大量替換。 | 將必要字體掛載至容器，或使用 `FontSettings.SetFontsFolder` 指向自訂字體資料夾。 |

---

## ## 在 Web API 情境下偵測字體替換

若透過 ASP.NET Core 提供文件服務，你可能不想在主控台寫入訊息。改為收集警告，並將其作為 HTTP 回應的一部份回傳。

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

現在 API **偵測缺少的字體**，並在產生任何 PDF 之前回傳清晰的 JSON 內容。這正是「如何偵測缺少的字體」在生產等級服務中的實作範例。

---

## ## 測試你的實作

1. **建立測試 DOCX**，引用一個你確定機器上沒有的字體（例如在最小化 Docker 映像中使用 “Comic Sans MS”）。  
2. 執行主控台應用程式或 API 端點。  
3. 確認主控台（或 HTTP 回應）列出字體替換警告。  
4. （可選）開啟產生的 PDF，檢查字體屬性——Aspose.Words 應顯示你設定的備用字體。

如果看到警告卻 PDF 仍使用非預期字體，請再次檢查 `SubstitutionSettings` 的順序；第一個符合的設定會被採用。

---

## ## 結論

我們已完整說明如何在 Aspose.Words 中**處理字體替換**，從註冊警告處理程式到程式化**偵測缺少的字體**，甚至以公司字體取代。透過內建的警告系統，你可以完整掌握每一次「找不到字體」的事件，直接回應每位開發者在自動化文件產生時常問的「**如何偵測缺少的字體**？」問題。

接下來可以嘗試結合 **動態字體載入** (`FontSettings.SetFontsFolder`) 以即時支援使用者上傳的字體，或將警告處理程式擴充為寫入 Serilog 等集中式日誌服務。字體處理越完整，文件流水線的可靠性就越高。

遇到棘手的字體替換情境嗎？在下方留言，我們一起排除問題。祝開發順利！

## 接下來該學什麼？

以下教學與本指南示範的技巧密切相關，能幫助你進一步掌握 API 功能並探索其他實作方式：

- [如何在 Aspose.Words 中偵測字體 – 處理警告與設定](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [在 Aspose.Words 中啟用字體替換警告 – 完整指南](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [如何載入 DOCX 並偵測缺少字體 – 完整 C# 指南](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}