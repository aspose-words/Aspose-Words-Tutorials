---
category: general
date: 2025-12-29
description: 了解如何在使用 Aspose.Words 將 Word 轉換為 PNG 時設定 DPI。本分步教學亦涵蓋高解析度 PNG 匯出與影像解析度設定。
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: zh-hant
og_description: 使用 Aspose.Words 將 Word 轉換為 PNG 時，如何設定 DPI。遵循本指南以實現高解析度 PNG 匯出與影像解析度控制。
og_title: 將 Word 轉換為 PNG 時如何設定 DPI – 完整 C# 教學
tags:
- Aspose.Words
- C#
- Image Export
title: 將 Word 轉換為 PNG 時如何設定 DPI – 完整 C# 指南
url: /zh-hant/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在將 Word 轉換為 PNG 時設定 DPI – 完整 C# 指南

有沒有想過在將 Word 文件轉換為 PNG 時**如何設定 DPI**？也許你需要在簡報中使用清晰的螢幕截圖，或是要產生必須在 300 dpi 下保持銳利的可列印資產。無論哪種情況，你都來對地方了。在本教學中，我們將示範如何使用 Aspose.Words 將多頁 `.docx` 轉換為高解析度 PNG 圖片，並且會告訴你如何正確設定影像解析度，避免輸出模糊。

我們還會提供 **convert word to png**、**save word as png** 的技巧，並且在不費吹灰之力的情況下完成 **high resolution png export**。不需要外部文件，只要一個自包含、可直接在 Visual Studio 中複製貼上的可執行範例。

---

## 需要的環境

- **Aspose.Words for .NET**（最新版本，例如 24.9）。  
- .NET 6+（或 .NET Framework 4.7.2+）– 任何近期的執行環境皆可。  
- 想要轉換成 PNG 的 Word 檔案（`MultiPage.docx`）。  
- 開發環境 – Visual Studio、Rider 或 VS Code 都可以。

就是這樣。除了 Aspose.Words 之外不需要其他 NuGet 套件。

## 步驟 1：載入 Word 文件

首先，我們需要在記憶體中取得 Word 檔案的表示。`Document` 類別會為我們完成這件事。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **為什麼這很重要：** 載入文件後，我們即可取得其 `PageCount`，稍後在指示 Aspose 匯出 **所有頁面** 為 PNG 時會用到它。

## 步驟 2：使用 DPI 設定配置 ImageSaveOptions

現在我們告訴 Aspose 我們需要 PNG 輸出 *且* 指定 DPI。`ImageHorizontalResolution` 與 `ImageVerticalResolution` 這兩個屬性就是關鍵所在。

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **專業提示：** 300 dpi 是列印就緒圖形的事實標準。如果只需要螢幕顯示品質，96 dpi 可大幅減少檔案大小。

## 步驟 3：將所有頁面儲存為單一拼貼 PNG（或分別檔案）

Aspose 允許你將每一頁合併成一個巨大的拼貼 PNG **或** 為每頁寫入單獨的檔案。以下範例示範 *單一拼貼* 的方式，但我們加入的 `PageSavingCallback` 已確保如果切換 `ExportImagesAsSeparateFiles` 旗標，會產生分別的檔案。

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

如果你偏好每頁一個檔案，只需設定：

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

而回呼函式會負責為每個 `Page_#.png` 命名。

## 步驟 4：驗證輸出

執行程式碼後，使用任何圖像檢視器開啟 `Pages.png`（或產生的 `Page_#.png` 檔案）。你應該會看到與原始 Word 頁面版面相符的清晰高解析度影像。

- **解析度檢查：** 右鍵 → 屬性 → 詳細資訊 → Horizontal DPI / Vertical DPI → 應顯示 **300**。  
- **尺寸檢查：** 在 300 dpi 下，典型的 A4 頁面（8.27 in × 11.69 in）大約為 2481 × 3508 像素 – 完美列印。

## 常見陷阱與避免方法

| 問題 | 為何會發生 | 解決方案 |
|-------|----------------|-----|
| **影像模糊** | DPI 保持預設值 (96) | 明確設定 `ImageHorizontalResolution` **以及** `ImageVerticalResolution`。 |
| **缺少頁面** | `PageSet` 只涵蓋了部分頁面 | 使用 `new PageSet(0, multiPageDoc.PageCount - 1)` 以包含所有頁面。 |
| **檔名衝突** | 未設定回呼函式 | 提供產生唯一名稱的 `PageSavingCallback`。 |
| **檔案過大** | 不必要的 600 dpi 或更高 | 選擇仍能滿足品質需求的最低 DPI。 |
| **記憶體不足錯誤**（大型文件） | 匯出巨大的拼貼 PNG | 改為 `ExportImagesAsSeparateFiles = true`，將每頁分別寫入。 |

## 進階：匯出不同類型的 PNG

有時你需要 **透明背景** 或 **不同的色彩深度**。Aspose.Words 透過 `ImageSaveOptions` 中的 `PngOptions` 支援這些調整。

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

你也可以將此與上述 DPI 設定結合，取得適用於網路與列印的 **high resolution png export**。

## 完整範例程式

以下是完整、可直接複製貼上的程式。只需將 `YOUR_DIRECTORY` 替換為你機器上的實際路徑。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

執行程式後，你將得到每頁的 **high resolution PNG export**，且每張圖片的 DPI 均為你設定的精確值。

## 常見問答

**Q: 這能適用於較舊的 `.doc` 檔案嗎？**  
A: 絕對可以。Aspose.Words 抽象化了格式，因此相同程式碼可處理 `.doc`、`.docx`、`.rtf`，甚至 `.odt`。

**Q: 我可以匯出為 JPEG 而不是 PNG 嗎？**  
A: 可以 – 只要將 `SaveFormat.Png` 改為 `SaveFormat.Jpeg`，並在需要時調整 `JpegOptions`。

**Q: 如果需要 600 dpi 以製作大型海報怎麼辦？**  
A: 設定 `ImageHorizontalResolution = 600` 與 `ImageVerticalResolution = 600`。同時留意記憶體使用情況；較大的 DPI 會快速增加像素尺寸。

**Q: 有沒有方法批次處理多個 Word 檔案？**  
A: 可將上述邏輯包在 `foreach (var file in Directory.GetFiles(folder, "*.docx"))` 迴圈中。記得釋放每個 `Document` 實例，或重複使用單一 `ImageSaveOptions` 物件以提升效能。

## 結論

我們已說明如何在使用 Aspose.Words **convert Word to PNG** 時 **設定 DPI**，探討 **high resolution PNG export** 的細節，並提供可直接執行的程式碼範例，讓你能 **save word as png** 並精確控制影像解析度。透過調整 `ImageHorizontalResolution`、`ImageVerticalResolution`，以及可選的 `PngOptions`，即可自信地產生列印就緒的圖形或輕量的網頁資產。

接下來的步驟？試著變換不同的 DPI 值、改用分別檔案匯出，或將此工作流程與 PDF 轉 PNG 管線結合，以處理更廣泛的文件。相同原則同樣適用於 **set image resolution png** 其他格式，讓你現在能應對各種影像匯出情境。

祝程式開發順利，願你的 PNG 永遠銳利如刀！

![將 Word 轉換為 PNG 時設定 DPI 的範例輸出](/images/how-to-set-dpi-word-to-png.png "設定 DPI")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}