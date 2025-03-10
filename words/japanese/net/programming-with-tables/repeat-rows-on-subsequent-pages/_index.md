---
title: 後続のページで行を繰り返す
linktitle: 後続のページで行を繰り返す
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、テーブル ヘッダー行を繰り返した Word 文書を作成する方法を学びます。このガイドに従って、プロフェッショナルで洗練された文書を作成してください。
weight: 10
url: /ja/net/programming-with-tables/repeat-rows-on-subsequent-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 後続のページで行を繰り返す

## 導入

Word 文書をプログラムで作成するのは、特に複数のページにわたって書式を維持する必要がある場合は、困難な作業になることがあります。Word で表を作成しようとして、ヘッダー行が後続のページで繰り返されないことに気づいたことはありませんか? 心配はいりません! Aspose.Words for .NET を使用すると、表のヘッダーが各ページで繰り返されるように簡単に設定でき、文書にプロフェッショナルで洗練された外観を与えることができます。このチュートリアルでは、簡単なコード例と詳細な説明を使用して、これを実現する手順を説明します。さっそく始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: ダウンロードできます[ここ](https://releases.aspose.com/words/net/).
2. .NET Framework がマシンにインストールされています。
3. Visual Studio または .NET 開発をサポートするその他の IDE。
4. C# プログラミングの基本的な理解。

続行する前に、Aspose.Words for .NET がインストールされ、開発環境が設定されていることを確認してください。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートする必要があります。C# ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

これらの名前空間には、Word 文書や表を操作するために必要なクラスとメソッドが含まれます。

## ステップ1: ドキュメントを初期化する

まず、新しいWord文書を作成し、`DocumentBuilder`テーブルを構築します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このコードは新しいドキュメントを初期化し、`DocumentBuilder`ドキュメント構造の構築に役立つオブジェクトです。

## ステップ2: テーブルを開始し、ヘッダー行を定義する

次に、テーブルを開始し、後続のページで繰り返すヘッダー行を定義します。

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

ここで、新しいテーブルを開始し、`HeadingFormat`財産に`true`行がヘッダーであることを示すため、およびセルの配置と幅を定義します。

## ステップ3: テーブルにデータ行を追加する

ここで、テーブルに複数のデータ行を追加します。これらの行は後続のページで繰り返されません。

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

このループは、各行に2つの列を含む50行のデータをテーブルに挿入します。`HeadingFormat`に設定されています`false`これらの行はヘッダー行ではないため、

## ステップ4: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

これにより、ドキュメントが指定された名前でドキュメント ディレクトリに保存されます。

## 結論

これで完了です。Aspose.Words for .NET を使用すると、数行のコードだけで、後続のページにヘッダー行が繰り返される表を含む Word 文書を作成できます。これにより、文書の読みやすさが向上するだけでなく、一貫性のあるプロフェッショナルな外観が保証されます。さあ、プロジェクトでこれを試してみてください。

## よくある質問

### ヘッダー行をさらにカスタマイズできますか?
はい、プロパティを変更することで、ヘッダー行に追加の書式を適用できます。`ParagraphFormat`, `RowFormat` 、 そして`CellFormat`.

### テーブルに列を追加することは可能ですか?
もちろんです！セルを挿入することで、必要な数の列を追加できます。`InsertCell`方法。

### 後続のページで他の行を繰り返すにはどうすればよいですか?
任意の行を繰り返すには、`RowFormat.HeadingFormat`財産に`true`その特定の行に対して。

### この方法はドキュメント内の既存の表にも使用できますか?
はい、既存のテーブルにアクセスして変更することができます。`Document`オブジェクトを作成し、同様の書式を適用します。

### Aspose.Words for .NET では他にどのようなテーブル書式設定オプションが利用できますか?
 Aspose.Words for .NET は、セルの結合、境界線の設定、表の配置など、幅広い表の書式設定オプションを提供します。[ドキュメント](https://reference.aspose.com/words/net/)詳細についてはこちらをご覧ください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
