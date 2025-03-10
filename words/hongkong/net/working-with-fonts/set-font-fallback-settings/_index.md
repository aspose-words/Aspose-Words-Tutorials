---
title: 設定字體回退設定
linktitle: 設定字體回退設定
second_title: Aspose.Words 文件處理 API
description: 了解如何在 Aspose.Words for .NET 中設定字體後備設定。此綜合指南可確保文件中的所有字元都能正確顯示。
weight: 10
url: /zh-hant/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體回退設定

## 介紹

當處理包含不同文字元素（例如不同語言或特殊字元）的文件時，請確保這些元素正確顯示至關重要。 Aspose.Words for .NET 提供了一個名為「字體回退設定」的強大功能，該功能有助於在原始字體不支援某些字元時定義替換字體的規則。在本指南中，我們將透過逐步教學來探索如何使用 Aspose.Words for .NET 設定字體回退設定。

## 先決條件

在深入學習本教程之前，請確保您具備以下先決條件：

- C#基礎：熟悉C#程式語言和.NET架構。
-  Aspose.Words for .NET：從以下位置下載並安裝[下載連結](https://releases.aspose.com/words/net/).
- 開發環境：用於編寫和執行程式碼的 Visual Studio 等設定。
- 範例文件：有一個範例文件（例如，`Rendering.docx`）準備測試。
- 字型回退規則 XML：準備定義字型回退規則的 XML 檔案。

## 導入命名空間

要使用Aspose.Words，您需要匯入必要的命名空間。這允許存取文件處理所需的各種類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## 第 1 步：定義文檔目錄

首先，定義儲存文件的目錄。這對於查找和處理文件至關重要。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：載入文檔

將文件載入到 Aspose.Words 中`Document`目的。此步驟可讓您以程式設計方式處理文件。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟 3：配置字型設定

創建一個新的`FontSettings`物件並從 XML 檔案載入字體後備設定。此 XML 檔案包含字型後備規則。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## 步驟 4：將字型設定套用到文檔

分配已配置的`FontSettings`到文檔。這可確保在呈現文件時套用字型後備規則。

```csharp
doc.FontSettings = fontSettings;
```

## 第 5 步：儲存文檔

最後，儲存文件。儲存作業期間將使用字體後備設置，以確保正確的字體替換。

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

透過執行以下步驟，您可以在 Aspose.Words for .NET 中有效地設定和使用字體回退設定。這可以確保您的文件正確顯示所有字符，即使原始字體不支援某些字符。實施這些設定將大大提高文件的品質和可讀性。

## 常見問題解答

### Q1：什麼是字體回退？

字體後備功能允許在原始字體不支援某些字元時替換字體，從而確保所有文字元素的正確顯示。

### Q2：我可以指定多種後備字體嗎？

是的，您可以在 XML 規則中指定多種後備字型。 Aspose.Words 將按照指定的順序檢查每種字體，直到找到支援該字元的字體。

### Q3：哪裡可以下載 Aspose.Words for .NET？

您可以從[Aspose下載頁面](https://releases.aspose.com/words/net/).

### 問題 4：如何建立字體後備規則的 XML 檔案？

可以使用任何文字編輯器建立 XML 檔案。它應遵循本教程提供的範例中所示的結構。

### Q5：Aspose.Words 有支援嗎？

是的，您可以在[Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
