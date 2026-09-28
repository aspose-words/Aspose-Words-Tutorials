---
category: general
date: 2026-02-13
description: 快速在 C# 中將 PNG 轉換為 Base64 – 學習如何對圖片進行 Base64 編碼、在 HTML 中嵌入 Base64 圖片，以及在
  Web 專案中將串流複製至記憶體。
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: zh-hant
og_description: 快速在 C# 中將 PNG 轉換為 Base64。本教學示範如何對圖像進行 Base64 編碼、在 HTML 中嵌入 Base64
  圖像，以及將串流複製至記憶體。
og_title: 在 C# 中將 PNG 轉換為 Base64 – 完整指南
tags:
- C#
- image-processing
- data-uri
title: 在 C# 中將 PNG 轉換為 Base64 – 完整指南
url: /zh-hant/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 轉換 PNG 為 Base64（C# 完整指南）

曾經需要 **convert PNG to Base64** 但不知從何開始嗎？你並不孤單；許多開發者在嘗試直接將圖像嵌入 HTML 或 CSS 時都會碰到這個問題。好消息是，只要掌握正確步驟，解決方案其實相當簡單。

在本教學中，我們將逐步示範一個完整且可執行的範例，該範例會 **base64 encode image** 資料，示範如何透過 data‑URI **embed image html base64**，並說明最佳的 **copy stream to memory** 方法以避免資源洩漏。完成後，你將擁有一段可重複使用的程式碼片段，能直接放入任何 .NET 專案中。

## 你將學到什麼

- 如何以不區分大小寫的方式驗證檔案副檔名。  
- 使用 `MemoryStream` 將 **image stream to base64** 轉換的最安全模式。  
- 建立瀏覽器可辨識的正確 data‑URI。  
- 清理原始串流，讓應用程式保持精簡。  

不需要任何外部函式庫——只要使用 .NET 隨附的 BCL 類別即可。只要你熟悉 C# 基礎，且專案已具備檔案上傳處理功能，就可以直接開始。

---

![從 PNG 檔案到 Base64 data‑URI 流程圖 – convert png to base64](https://example.com/convert-png-to-base64-diagram.png "convert png to base64 範例")

## 轉換 PNG 為 Base64 – 步驟說明

以下我們將流程分為五個邏輯步驟。每個標題對應拼圖的一塊，讓你（以及 AI 助手）能輕鬆找到所需的具體部分。

### 步驟 1：驗證資源是否為 PNG（不區分大小寫）

在浪費記憶體之前，我們先確認傳入的檔案確實為 PNG。`StringComparison.OrdinalIgnoreCase` 旗標可處理大小寫混合的副檔名。

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*為何重要：* 嘗試將非圖像（或 JPEG）編碼為 PNG 可能會損壞輸出，並導致之後嵌入的 data‑URI 無法正常工作。

### 步驟 2：將串流複製到記憶體

傳入的 `Stream`（可能來自上傳處理程式）需要完整讀取。使用 `using var` 陳述式可自動釋放緩衝區，確保 **copy stream to memory** 的過程保持乾淨。

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*專業提示：* 若處理非常大的檔案，建議使用 `CopyToAsync` 並設定合理的緩衝大小，以避免阻塞執行緒。

### 步驟 3：將影像進行 Base64 編碼

現在影像位元組已位於 `memory` 中，我們可以將它們轉換為 Base64 字串。這就是 **base64 encode image** 的核心。

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*發生了什麼？* `Convert.ToBase64String` 會接受位元組陣列，並回傳瀏覽器可解碼回二進位資料的文字表示。

### 步驟 4：為 HTML/CSS 建立 Data‑URI

Data‑URI 允許你直接在標記中嵌入影像，省去額外的 HTTP 請求。其格式為 `data:[<mediatype>][;base64],<data>`。

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

當你稍後在 `<img src="...">` 標籤中渲染 `args.ResourceFilePath` 時，瀏覽器會即時顯示 PNG。

### 步驟 5：釋放原始串流

由於影像已由 data‑URI 表示，原始的 `Stream` 已不再需要。將其設為 `null` 可協助垃圾回收機制回收底層的 socket 或檔案句柄。

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*邊緣情況：* 若稍後仍需原始檔案（例如儲存至磁碟），可跳過此步驟，並在其他地方保留參考。

---

## 完整可執行範例

將所有部件組合起來，即可得到一個緊湊的方法，能貼入任何處理上傳資源的類別中。

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**預期輸出：** `ProcessPng` 執行後，`args.ResourceFilePath` 會包含類似以下的字串：

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

現在你可以直接將該字串放入 `<img>` 標籤中：

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

影像會即時顯示，且不產生任何額外的網路流量。

---

## 常見問題與邊緣情況

### 如果 PNG 檔案很大怎麼辦？

大型影像會因整個檔案被載入 `MemoryStream` 而導致記憶體使用激增。對於超過數 MB 的檔案，建議以分塊方式串流進行 Base64 轉換，或在編碼前先調整影像大小。

### 我可以將其改為非同步嗎？

當然可以。將 `CopyTo` 換成 `CopyToAsync`，並將方法標記為 `async Task`。這樣在 I/O 完成期間，ASP.NET 請求執行緒即可保持空閒。

```csharp
await args.Stream.CopyToAsync(memory);
```

### 這能用於其他影像格式嗎？

程式碼本身與格式無關；只需要在 data‑URI 中調整 MIME 類型（`image/jpeg`、`image/gif` 等），並相應修改副檔名檢查即可。

### 我要如何優雅地處理錯誤？

將整段程式碼包在 `try/catch` 中並記錄例外。若在 Web API 中，則回傳 400 Bad Request 並附上友善的錯誤訊息。

---

## 結論

現在你已掌握在 C# 中 **convert PNG to Base64** 的完整流程。教學涵蓋了驗證檔案類型、安全地將串流複製到記憶體、執行 **base64 encode image**、構建正確的 **embed image html base64** data‑URI，以及清理資源。

接下來你可以探索即時影像縮放、快取產生的 data‑URI，或甚至產生 SVG 佔位圖。無論選擇何種方式，上述模式都將成為在任何需要將 **image stream to base64** 並直接嵌入標記的情境下的堅實基礎。

對此工作流程有自己的變化嗎？或許你正使用 WebAssembly 或 Blazor——歡迎在留言中分享你的實驗。祝編程愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}