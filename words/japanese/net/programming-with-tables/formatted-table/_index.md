---
title: フォーマットされた表
linktitle: フォーマットされた表
second_title: Aspose.Words ドキュメント処理 API
description: この詳細なステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書で表を作成し、書式設定する方法を学習します。
weight: 10
url: /ja/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォーマットされた表

## 導入

プログラムを使用して Word 文書に表を作成し、書式設定するのは困難な作業のように思えるかもしれませんが、Aspose.Words for .NET を使用すると、簡単かつ管理しやすくなります。このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書に書式設定された表を作成する方法について説明します。環境の設定から、美しく書式設定された表を含む文書の保存まで、すべてをカバーします。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NETライブラリ: ダウンロードはこちらから[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio のような IDE。
3. .NET Framework: マシンに .NET Framework がインストールされていることを確認します。

## 名前空間のインポート

実際のコードを書く前に、必要な名前空間をインポートする必要があります。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメントを保存するパスを定義する必要があります。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントを保存する実際のパスを入力します。

## ステップ 2: ドキュメントと DocumentBuilder を初期化する

ここで、新しいドキュメントと DocumentBuilder オブジェクトを初期化します。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

の`DocumentBuilder`ドキュメント構築のプロセスを簡素化するヘルパー クラスです。

## ステップ3: テーブルを開始する

次に、`StartTable`方法。

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

表を開始するにはセルを挿入する必要があります。

## ステップ4: 表全体の書式設定を適用する

表全体に影響する書式を適用できます。たとえば、左インデントを設定するには、次のようにします。

```csharp
table.LeftIndent = 20.0;
```

## ステップ5: ヘッダー行の書式を設定する

ヘッダー行の高さ、配置、その他のプロパティを設定します。

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

このステップでは、背景色、フォント サイズ、配置を設定して、ヘッダー行を目立たせます。

## ステップ6: 追加のヘッダーセルを挿入する

ヘッダー行にさらにセルを挿入します。

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## ステップ7: 本文の行をフォーマットする

ヘッダーを設定したら、表の本文をフォーマットします。

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## ステップ8: 本文の行を挿入する

コンテンツを含む本文行を挿入します。

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

追加の行についても繰り返します。

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## ステップ9: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

これにより、フォーマットされた表を含む Word 文書が作成され、保存されます。

## 結論

これで完了です。これらの手順に従うと、Aspose.Words for .NET を使用して Word 文書内に適切にフォーマットされた表を作成できます。この強力なライブラリを使用すると、Word 文書をプログラムで簡単に操作できるため、時間と労力を節約できます。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、Word 文書をプログラムで作成、編集、変換するための強力なライブラリです。

### 行ごとに異なる色を使用できますか?
はい、色を含むさまざまな書式を、異なる行またはセルに適用できます。

### Aspose.Words for .NET は無料ですか?
 Aspose.Words for .NETは有料のライブラリですが、[無料トライアル](https://releases.aspose.com/).

### Aspose.Words for .NET のサポートを受けるにはどうすればよいですか?
サポートを受けるには[Aspose コミュニティ フォーラム](https://forum.aspose.com/c/words/8).

### Aspose.Words for .NET を使用して他の種類のドキュメントを作成できますか?
はい、Aspose.Words for .NET は、PDF、HTML、TXT など、さまざまなドキュメント形式をサポートしています。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
