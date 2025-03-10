---
title: Word文書にブックマークを作成する
linktitle: Word文書にブックマークを作成する
second_title: Aspose.Words ドキュメント処理 API
description: この詳細なステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書にブックマークを作成する方法を学習します。文書のナビゲーションと整理に最適です。
weight: 10
url: /ja/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word文書にブックマークを作成する

## 導入

Word 文書にブックマークを作成すると、特に大きな文書を楽々とナビゲートしたい場合には、状況が一変する可能性があります。今日は、Aspose.Words for .NET を使用してブックマークを作成するプロセスについて説明します。このチュートリアルでは、プロセスの各部分を理解できるように、手順を追って説明します。それでは、早速始めましょう。

## 前提条件

始める前に、次のものを用意する必要があります。

1.  Aspose.Words for .NETライブラリ: ダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の .NET 開発環境。
3. C# の基礎知識: 基本的な C# プログラミング概念を理解していること。

## 名前空間のインポート

Aspose.Words for .NET を使用するには、必要な名前空間をインポートする必要があります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントとDocumentBuilderを設定する

ドキュメントを初期化する

まず、新しいドキュメントを作成し、`DocumentBuilder`これは、ドキュメントにコンテンツとブックマークを追加するための開始点です。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

説明:`Document`オブジェクトはキャンバスです。`DocumentBuilder`ペンのようなもので、ドキュメントにコンテンツを書き込んだり、ブックマークを作成したりできます。

## ステップ2: メインブックマークを作成する

メインブックマークの開始と終了

ブックマークを作成するには、開始点と終了点を指定する必要があります。ここでは、「My Bookmark」という名前のブックマークを作成します。

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

説明:`StartBookmark`メソッドはブックマークの始まりを示し、`Writeln`ブックマーク内にテキストを追加します。

## ステップ3: ネストされたブックマークを作成する

メインブックマーク内にネストされたブックマークを追加する

ブックマークを他のブックマークの中にネストすることができます。ここでは、「マイブックマーク」内に「ネストされたブックマーク」を追加します。

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

説明: ブックマークをネストすると、より構造化された階層的なコンテンツ編成が可能になります。`EndBookmark`メソッドは現在のブックマークを閉じます。

## ステップ4: ネストされたブックマークの外側にテキストを追加する

コンテンツの追加を続ける

ネストされたブックマークの後は、メインのブックマーク内にさらにコンテンツを追加し続けることができます。

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

説明: これにより、メインのブックマークにネストされたブックマークと追加のテキストの両方が含まれるようになります。

## ステップ5: PDF保存オプションを設定する

ブックマークのPDF保存オプションを設定する

ドキュメントを PDF として保存するときに、ブックマークを含めるオプションを設定できます。

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

説明:`PdfSaveOptions`クラスを使用すると、ドキュメントをPDFとして保存する方法を指定できます。`BookmarksOutlineLevels`プロパティは、PDF 内のブックマークの階層を定義します。

## ステップ6: ドキュメントを保存する

文書をPDFとして保存する

最後に、指定したオプションでドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

説明:`Save`メソッドは、指定された形式と場所でドキュメントを保存します。これで、PDF には作成したブックマークが含まれるようになります。

## 結論

Aspose.Words for .NET を使用して Word 文書にブックマークを作成するのは簡単で、文書のナビゲーションと整理に非常に役立ちます。レポートの生成、電子書籍の作成、または大きな文書の管理など、ブックマークがあれば作業が簡単になります。このチュートリアルで説明されている手順に従えば、ブックマーク付きの PDF がすぐに作成されます。

## よくある質問

### 異なるレベルで複数のブックマークを作成できますか?

もちろんです! ドキュメントを PDF として保存するときに、必要な数のブックマークを作成し、その階層レベルを定義できます。

### ブックマークのテキストを更新するにはどうすればよいですか?

ブックマークに移動するには、`DocumentBuilder.MoveToBookmark`その後、テキストを更新します。

### ブックマークを削除することは可能ですか?

はい、ブックマークを削除するには、`Bookmarks.Remove`ブックマークの名前を指定してメソッドを実行します。

### PDF 以外の形式でブックマークを作成できますか?

はい、Aspose.Words は、DOCX、HTML、EPUB など、さまざまな形式のブックマークをサポートしています。

### ブックマークが PDF に正しく表示されるようにするにはどうすればよいですか?

必ず定義してください`BookmarksOutlineLevels`適切に`PdfSaveOptions`これにより、ブックマークが PDF のアウトラインに含まれるようになります。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
