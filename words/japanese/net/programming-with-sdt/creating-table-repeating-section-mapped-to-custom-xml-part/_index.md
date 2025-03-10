---
title: カスタム XML パーツにマップされたテーブル繰り返しセクションの作成
linktitle: カスタム XML パーツにマップされたテーブル繰り返しセクションの作成
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書内の CustomXmlPart にマップされた繰り返しセクションを含むテーブルを作成する方法を学習します。
weight: 10
url: /ja/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# カスタム XML パーツにマップされたテーブル繰り返しセクションの作成

## 導入

このチュートリアルでは、Aspose.Words for .NET を使用して、カスタム XML パーツにマップされた繰り返しセクションを含むテーブルを作成するプロセスについて説明します。これは、構造化データに基づいてドキュメントを動的に生成する場合に特に便利です。

## 前提条件

始める前に、以下のものを用意してください。
1.  Aspose.Words for .NETライブラリがインストールされています。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).
2. C# と XML の基本的な理解。

## 名前空間のインポート

プロジェクトに必要な名前空間を必ず含めてください。

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## ステップ 1: Document と DocumentBuilder を初期化する

まず、新しいドキュメントを作成し、`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: カスタムXMLパーツを追加する

ドキュメントにカスタム XML パーツを追加します。この XML には、テーブルにマップするデータが含まれています。

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## ステップ3: テーブル構造を作成する

次に、`DocumentBuilder`テーブルヘッダーを作成するには:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## ステップ4: 繰り返しセクションを作成する

作成する`StructuredDocumentTag`(SDT) を繰り返しセクションに作成し、XML データにマップします。

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## ステップ5: 繰り返しセクションアイテムを作成する

繰り返しセクション アイテムの SDT を作成し、それを繰り返しセクションに追加します。

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## ステップ 6: XML データをテーブル セルにマップする

タイトルと著者の SDT を作成し、それらを XML データにマップして、行に追加します。

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## ステップ7: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## 結論

これらの手順に従うことで、Aspose.Words for .NET を使用して、カスタム XML パーツにマップされた繰り返しセクションを含むテーブルを正常に作成できました。これにより、構造化データに基づく動的なコンテンツ生成が可能になり、ドキュメント作成がより柔軟かつ強力になります。

## よくある質問

### StructuredDocumentTag (SDT) とは何ですか?
SDT (コンテンツ コントロールとも呼ばれます) は、構造化データを格納するために使用されるドキュメント内の境界領域です。

### カスタム XML 部分で他のデータ型を使用できますか?
はい、カスタム XML パーツを任意のデータ型で構造化し、それに応じてマップすることができます。

### 繰り返しセクションに行を追加するにはどうすればよいですか?
繰り返しセクションは、マップされた XML パス内の各項目の行構造を自動的に複製します。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
