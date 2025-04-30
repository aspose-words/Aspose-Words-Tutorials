---
"description": "了解如何在 Aspose.Words for .NET 中設定字體後備設定。本綜合指南可確保您的文件中的所有字元均正確顯示。"
"linktitle": "設定字體回退設定"
"second_title": "Aspose.Words文件處理API"
"title": "設定字體回退設定"
"url": "/zh-hant/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體回退設定

## 介紹

當處理包含多種文字元素（例如不同語言或特殊字元）的文件時，請確保這些元素正確顯示至關重要。 Aspose.Words for .NET 提供了一個強大的功能，稱為“字體回退設定”，當原始字體不支援某些字元時，它有助於定義替換字體的規則。在本指南中，我們將透過逐步教學探討如何使用 Aspose.Words for .NET 設定字體後備設定。

## 先決條件

在深入學習本教程之前，請確保您已滿足以下先決條件：

- C#基礎：熟悉C#程式語言和.NET架構。
- Aspose.Words for .NET：從下載並安裝 [下載連結](https://releases。aspose.com/words/net/).
- 開發環境：像 Visual Studio 這樣的設置，用於編寫和運行程式碼。
- 範例文件：提供範例文件（例如， `Rendering.docx`）準備進行測試。
- 字體後備規則 XML：準備一個定義字體後備規則的 XML 檔案。

## 導入命名空間

若要使用 Aspose.Words，您需要匯入必要的命名空間。這允許存取文件處理所需的各種類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## 步驟1：定義文檔目錄

首先，定義儲存文件的目錄。這對於定位和處理您的文件至關重要。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟 2：載入文檔

將您的文件載入到 Aspose.Words `Document` 目的。此步驟可讓您以程式設計方式處理文件。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟3：配置字體設定

創建新的 `FontSettings` 物件並從 XML 檔案載入字體回退設定。該 XML 檔案包含字型回退規則。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## 步驟 4：將字型設定套用至文檔

分配已配置的 `FontSettings` 到文檔中。這可確保在呈現文件時套用字型回退規則。

```csharp
doc.FontSettings = fontSettings;
```

## 步驟5：儲存文檔

最後，儲存文件。儲存操作期間將使用字體回退設定來確保正確的字體替換。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML 檔案：字型後備規則

以下是定義字體後備規則的 XML 檔案的範例：

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## 結論

遵循這些步驟，您可以有效地設定和使用 Aspose.Words for .NET 中的字體回退設定。這可確保您的文件正確顯示所有字符，即使原始字體不支援某些字符。實施這些設定將大大提高文件的品質和可讀性。

## 常見問題解答

### Q1：什麼是字體回退？

字體回退功能允許在原始字體不支援某些字元時替換字體，以確保所有文字元素的正確顯示。

### 問題2：我可以指定多個後備字體嗎？

是的，您可以在 XML 規則中指定多個後備字型。 Aspose.Words 將按照指定的順序檢查每種字體，直到找到支援該字元的字體。

### 問題3：哪裡可以下載 Aspose.Words for .NET？

您可以從 [Aspose下載頁面](https://releases。aspose.com/words/net/).

### Q4：如何建立字體後備規則的 XML 檔案？

可以使用任何文字編輯器建立 XML 檔案。它應該遵循本教程提供的範例中所示的結構。

### 問題5：是否支援Aspose.Words？

是的，您可以在 [Aspose.Words 支援論壇](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}