---
title: Word文件中的比較粒度
linktitle: Word文件中的比較粒度
second_title: Aspose.Words 文件處理 API
description: 了解 Aspose.Words for .NET 的 Word 文檔功能中的比較粒度，該功能允許逐個字元比較文檔，報告所做的更改。
weight: 10
url: /zh-hant/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word文件中的比較粒度

以下是解釋下面 C# 原始程式碼的逐步指南，該程式碼使用 Aspose.Words for .NET 的 Word 文件中的比較粒度功能。

## 第 1 步：簡介

Aspose.Words for .NET 的比較粒度功能可讓您在字元層級比較文件。這意味著將比較每個字元並相應地報告變化。

## 第2步：設定環境

在開始之前，您需要設定開發環境以使用 Aspose.Words for .NET。確保您已安裝 Aspose.Words 庫並擁有合適的 C# 專案來嵌入程式碼。

## 第 3 步：新增所需的程序集

若要使用 Aspose.Words for .NET 的比較粒度功能，您需要將必要的組件新增至專案。確保您的專案中有對 Aspose.Words 的正確引用。

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## 第 4 步：建立文檔

在此步驟中，我們將使用 DocumentBuilder 類別建立兩個文件。這些文件將用於比較。

```csharp
//建立文檔A。
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

//建立文檔B。
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## 第 5 步：配置比較選項

在此步驟中，我們將配置比較選項以指定比較粒度。這裡我們將使用字元級粒度。

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## 第六步：文件比較

現在讓我們使用 Document 類別的 Compare 方法來比較文件。變更將儲存在文件 A 中。

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

這`Compare`方法將文件 A 與文件 B 進行比較，並將變更儲存至文件 A。

## 結論

在本文中，我們探討了 Aspose.Words for .NET 的比較粒度功能。此功能可讓您在字元層級比較文件並報告變更。您可以使用這些知識在專案中執行詳細的文件比較。

### 使用 Aspose.Words for .NET 進行比較粒度的範例原始程式碼

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## 結論

在本教學中，我們探索了 Aspose.Words for .NET 的比較粒度功能。此功能可讓您在比較文件時指定詳細程度。透過選擇不同的粒度級別，您可以根據您的特定要求在字元、單字或區塊級別執行詳細比較。 Aspose.Words for .NET提供了靈活且強大的文件比較功能，可輕鬆識別不同粒度等級的文件中的差異。

### 常見問題解答

#### Q：在 Aspose.Words for .NET 中使用比較粒度的目的是什麼？

答：Aspose.Words for .NET 中的比較粒度可讓您在比較文件時指定詳細程度。透過此功能，您可以比較不同層級的文檔，例如字元級、單字級甚至區塊級。每個粒度等級在比較結果中提供不同等級的詳細資訊。

#### Q：如何在 Aspose.Words for .NET 中使用比較粒度？

答：若要在 Aspose.Words for .NET 中使用比較粒度，請依照下列步驟操作：
1. 使用 Aspose.Words 函式庫設定您的開發環境。
2. 透過引用 Aspose.Words 將必要的程式集新增到您的專案中。
3. 使用以下命令建立要比較的文檔`DocumentBuilder`班級。
4. 透過建立一個來配置比較選項`CompareOptions`對象並設定`Granularity`屬性達到所需的水平（例如，`Granularity.CharLevel`用於字元級比較）。
5. 使用`Compare`一個文檔上的方法，傳遞另一個文檔和`CompareOptions`對像作為參數。此方法將根據指定的粒度比較文檔，並將變更保存在第一個文檔中。

#### Q：Aspose.Words for .NET 中的比較粒度有哪些可用等級？

答：Aspose.Words for .NET 提供三個等級的比較粒度：
- `Granularity.CharLevel`：在字元層級比較文件。
- `Granularity.WordLevel`：在單字層級比較文件。
- `Granularity.BlockLevel`：在區塊層級比較文件。

#### Q：如何解讀字元級粒度的比較結果？

答：透過字元級粒度，分析比較文件中的每個字元是否有差異。比對結果將顯示單一字元層級的變化，包括新增、刪除和修改。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
