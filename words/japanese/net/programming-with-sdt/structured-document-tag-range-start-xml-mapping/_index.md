---
title: 構造化ドキュメントのタグ範囲の開始 XML マッピング
linktitle: 構造化ドキュメントのタグ範囲の開始 XML マッピング
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word で XML データを構造化ドキュメント タグに動的にバインドする方法を学びます。ステップ バイ ステップ ガイドに従ってください。
weight: 10
url: /ja/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 構造化ドキュメントのタグ範囲の開始 XML マッピング

## 導入

Word 文書に XML データを動的に挿入したいと思ったことはありませんか? 幸運です! Aspose.Words for .NET を使用すると、この作業が簡単になります。このチュートリアルでは、構造化されたドキュメントのタグ範囲開始 XML マッピングについて詳しく説明します。この機能を使用すると、カスタム XML パーツをコンテンツ コントロールにバインドして、ドキュメント コンテンツが XML データとシームレスに更新されるようにすることができます。ドキュメントを動的な傑作に変える準備ができました。

## 前提条件

コーディング部分に進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NETライブラリ: 最新バージョンであることを確認してください。ダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio または C# をサポートするその他の IDE。
3. C# の基礎知識: C# プログラミングに精通していることが必須です。
4. Word 文書: 作業に使用するサンプルの Word 文書。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、Aspose.Words for .NET で必要なすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## ステップ1: ドキュメントディレクトリを設定する

すべてのプロジェクトには基盤が必要ですね。ここでは、ドキュメント ディレクトリへのパスを設定します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: Word文書を読み込む

次に、Word 文書を読み込みます。これは、XML データを挿入する文書です。

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## ステップ3: カスタムXMLパーツを追加する

挿入するデータを含む XML パーツを作成し、それをドキュメントの CustomXmlPart コレクションに追加する必要があります。このカスタム XML パーツは、構造化ドキュメント タグのデータ ソースとして機能します。

### XML パーツの作成

まず、XML 部分の一意の ID を生成し、そのコンテンツを定義します。

```csharp
//データを含む XML パーツを構築し、それをドキュメントの CustomXmlPart コレクションに追加します。
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### XMLパーツのコンテンツを確認する

XML 部分が正しく追加されたことを確認するために、その内容を出力します。

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## ステップ4: 構造化ドキュメントタグを作成する

構造化ドキュメント タグ (SDT) は、XML パーツにバインドできるコンテンツ コントロールです。ここでは、カスタム XML パーツのコンテンツを表示する SDT を作成します。

まず、ドキュメント内の SDT 範囲の開始位置を見つけます。

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## ステップ5: SDTのXMLマッピングを設定する

ここで、XML 部分を SDT にバインドします。XML マッピングを設定することで、SDT に表示する XML データの部分を指定します。

 XPathは、表示したいXML部分の特定の要素を指します。ここでは、2番目の要素を指します。`<text>`要素内の`<root>`要素。

```csharp
// StructuredDocumentTagのマッピングを設定する
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを保存して変更内容を確認します。Word ドキュメントの SDT に、指定した XML コンテンツが表示されるようになります。

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、XML パーツを Word 文書内の構造化ドキュメント タグにマッピングできました。この強力な機能により、動的なデータ駆動型ドキュメントを簡単に作成できます。レポート、請求書、またはその他のドキュメント タイプを生成する場合でも、XML マッピングによりワークフローを大幅に効率化できます。

## よくある質問

### Word の構造化ドキュメント タグとは何ですか?
構造化ドキュメント タグ (コンテンツ コントロールとも呼ばれる) は、Word ドキュメント内の特定の種類のコンテンツを格納するコンテナーです。これらを使用して、データをバインドしたり、編集を制限したり、ドキュメント作成時にユーザーをガイドしたりできます。

### XML 部分のコンテンツを動的に更新するにはどうすればよいですか?
 XML部分の内容を更新するには、`xmlPartContent`文字列をドキュメントに追加する前に、新しいデータで文字列を更新して、`CustomXmlParts`コレクション。

### 同じドキュメント内の複数の XML パーツを異なる SDT にバインドできますか?
はい、同じドキュメント内の複数の XML パーツを異なる SDT にバインドできます。各 SDT には、独自の XML パーツと XPath マッピングを設定できます。

### 複雑な XML 構造を SDT にマップすることは可能ですか?
もちろんです! XML 部分内の目的の要素を正確に指す詳細な XPath 式を使用することで、複雑な XML 構造を SDT にマップできます。

### ドキュメントから XML 部分を削除するにはどうすればよいですか?
 XML部分を削除するには、`Remove`方法`CustomXmlParts`コレクション、渡す`xmlPartId`削除する XML 部分。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
