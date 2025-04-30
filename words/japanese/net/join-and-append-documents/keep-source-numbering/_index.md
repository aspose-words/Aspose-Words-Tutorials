---
"description": "Aspose.Words for .NET を使用して、書式設定を維持しながらドキュメントをインポートする方法を学びます。コード例を使ったステップバイステップのガイドです。"
"linktitle": "ソース番号を維持する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "ソース番号を維持する"
"url": "/ja/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ソース番号を維持する

## 導入

Aspose.Words for .NETを使用する場合、書式を保持しながらあるソースから別のソースにドキュメントをインポートすることは、 `NodeImporter` クラス。このチュートリアルでは、プロセスを段階的に説明します。

## 前提条件

始める前に、次のものがあることを確認してください。
- Visual Studio がマシンにインストールされています。
- Aspose.Words for .NET がインストールされていること。インストールされていない場合は、こちらからダウンロードしてください。 [ここ](https://releases。aspose.com/words/net/).
- C# および .NET プログラミングの基礎知識。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間を含めます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## ステップ1: プロジェクトの設定

まず、Visual Studio で新しい C# プロジェクトを作成し、NuGet パッケージ マネージャーを使用して Aspose.Words をインストールします。

## ステップ2: ドキュメントの初期化
ソースのインスタンスを作成する（`srcDoc`）と目的地（`dstDoc`) 文書。

```csharp
// ドキュメントディレクトリへのパス 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## ステップ3: インポートオプションを設定する
番号付き段落を含むソースの書式を維持するためのインポート オプションを設定します。

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## ステップ4: 段落をインポートする
ソース ドキュメント内の段落を反復処理し、宛先ドキュメントにインポートします。

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## ステップ5: ドキュメントを保存する
結合したドキュメントを目的の場所に保存します。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## 結論

結論として、Aspose.Words for .NETを使用して書式を保持しながらドキュメントをインポートすることは、 `NodeImporter` クラス。このメソッドにより、ドキュメントの元の外観と構造がシームレスに維持されます。

## よくある質問

### 異なる書式スタイルのドキュメントをインポートできますか?
はい、 `NodeImporter` クラスは、さまざまな書式設定スタイルを持つドキュメントのインポートをサポートします。

### ドキュメントに複雑な表や画像が含まれている場合はどうなりますか?
Aspose.Words for .NET は、インポート操作中にテーブルや画像などの複雑な構造を処理します。

### Aspose.Words は .NET のすべてのバージョンと互換性がありますか?
Aspose.Words は、シームレスな統合のために .NET Framework および .NET Core バージョンをサポートしています。

### ドキュメントのインポート中にエラーが発生した場合、どうすれば処理できますか?
インポート プロセス中に発生する可能性のある例外を処理するには、try-catch ブロックを使用します。

### Aspose.Words for .NET の詳細なドキュメントはどこで入手できますか?
訪問 [ドキュメント](https://reference.aspose.com/words/net/) 包括的なガイドと API リファレンスについては、こちらをご覧ください。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}