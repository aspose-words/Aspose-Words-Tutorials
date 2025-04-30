---
"description": "Aspose.Words for .NET を使用して、XMLデータをWordの構造化ドキュメントタグに動的にバインドする方法を学びましょう。ステップバイステップのガイドに従ってください。"
"linktitle": "構造化ドキュメントのタグ範囲開始 XML マッピング"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "構造化ドキュメントのタグ範囲開始 XML マッピング"
"url": "/ja/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 構造化ドキュメントのタグ範囲開始 XML マッピング

## 導入

Word文書にXMLデータを動的に挿入したいと思ったことはありませんか？そんな時、Aspose.Words for .NETが役立ちます！Aspose.Words for .NETを使えば、この作業はあっという間に完了します。このチュートリアルでは、構造化文書のタグ範囲開始XMLマッピングについて詳しく解説します。この機能を使うと、カスタムXMLパーツをコンテンツコントロールにバインドできるため、XMLデータに合わせて文書のコンテンツがシームレスに更新されます。さあ、あなたの文書をダイナミックな傑作へと昇華させましょう。

## 前提条件

コーディング部分に進む前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NETライブラリ：最新バージョンであることを確認してください。ダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
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

すべてのプロジェクトには基盤が必要ですよね？ここでは、ドキュメントディレクトリへのパスを設定します。

```csharp
// ドキュメントディレクトリへのパス 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: Word文書を読み込む

次に、Word文書を読み込みます。この文書にXMLデータを挿入します。

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## ステップ3: カスタムXMLパーツを追加する

挿入したいデータを含むXMLパーツを作成し、ドキュメントのCustomXmlPartコレクションに追加する必要があります。このカスタムXMLパーツは、構造化ドキュメントタグのデータソースとして機能します。

### XMLパーツの作成

まず、XML 部分に一意の ID を生成し、そのコンテンツを定義します。

```csharp
// データを含む XML パーツを構築し、それをドキュメントの CustomXmlPart コレクションに追加します。
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### XMLパーツの内容を確認する

XML 部分が正しく追加されたことを確認するために、その内容を出力します。

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## ステップ4: 構造化ドキュメントタグを作成する

構造化ドキュメントタグ（SDT）は、XMLパーツにバインドできるコンテンツコントロールです。ここでは、カスタムXMLパーツのコンテンツを表示するSDTを作成します。

まず、ドキュメント内の SDT 範囲の開始位置を見つけます。

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## ステップ5: SDTのXMLマッピングを設定する

さて、XML部分をSDTにバインドしましょう。XMLマッピングを設定することで、SDTに表示するXMLデータの部分を指定します。

XPathは、XML部分内の表示したい特定の要素を指します。ここでは、2番目の要素を指します。 `<text>` 要素内の `<root>` 要素。

```csharp
// StructuredDocumentTagのマッピングを設定する
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを保存して変更内容を確認します。Word文書のSDTに、指定したXMLコンテンツが表示されるようになります。

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## 結論

これで完了です！Aspose.Words for .NET を使用して、XML パーツを Word 文書内の構造化ドキュメントタグにマッピングできました。この強力な機能により、動的でデータドリブンなドキュメントを簡単に作成できます。レポート、請求書、その他のドキュメントを作成する場合でも、XML マッピングはワークフローを大幅に効率化します。

## よくある質問

### Word の構造化文書タグとは何ですか?
構造化文書タグ（コンテンツコントロールとも呼ばれます）は、Word文書内の特定の種類のコンテンツを格納するコンテナです。データのバインド、編集の制限、文書作成時のユーザーガイドなどに使用できます。

### XML 部分のコンテンツを動的に更新するにはどうすればよいですか?
XML部分の内容を更新するには、 `xmlPartContent` ドキュメントに追加する前に文字列を更新してください。新しいデータで文字列を更新し、 `CustomXmlParts` コレクション。

### 同じドキュメント内の複数の XML パーツを異なる SDT にバインドできますか?
はい、同じドキュメント内の複数のXMLパーツを異なるSDTにバインドできます。各SDTには、独自のXMLパーツとXPathマッピングを設定できます。

### 複雑な XML 構造を SDT にマップすることは可能ですか?
もちろんです！XML 部分内の目的の要素を正確に指し示す詳細な XPath 式を使用することで、複雑な XML 構造を SDT にマップできます。

### ドキュメントから XML 部分を削除するにはどうすればよいですか?
XML部分を削除するには、 `Remove` 方法 `CustomXmlParts` コレクションを渡す `xmlPartId` 削除する XML 部分の。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}