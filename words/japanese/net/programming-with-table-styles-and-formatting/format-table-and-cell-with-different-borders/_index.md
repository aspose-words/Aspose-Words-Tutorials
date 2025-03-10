---
title: 表とセルを異なる境界線で書式設定する
linktitle: 表とセルを異なる境界線で書式設定する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、さまざまな境界線で表とセルを書式設定する方法を学びます。カスタマイズされた表のスタイルとセルの網かけを使用して、Word 文書を強化します。
weight: 10
url: /ja/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 表とセルを異なる境界線で書式設定する

## 導入

表やセルの境界線をカスタマイズして、Word 文書をよりプロフェッショナルに見せようとしたことがありますか? まだ試したことがなければ、ぜひお試しください。このチュートリアルでは、Aspose.Words for .NET を使用して、表やセルをさまざまな境界線で書式設定する手順を説明します。わずか数行のコードで表の外観を変更できると想像してみてください。興味が湧きましたか? 早速、これを簡単に実現する方法を詳しく見ていきましょう。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。
- C# プログラミングの基本的な理解。
- Visual Studio がコンピューターにインストールされています。
-  Aspose.Words for .NETライブラリ。まだインストールしていない場合はダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
- 有効なAsposeライセンス。無料トライアルまたは一時ライセンスは以下から入手できます。[ここ](https://purchase.aspose.com/temporary-license/).

## 名前空間のインポート

Aspose.Words for .NET を使用するには、必要な名前空間をプロジェクトにインポートする必要があります。コード ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## ステップ 1: Document と DocumentBuilder を初期化する

まず、新しいドキュメントを作成し、ドキュメント コンテンツの構築に役立つ DocumentBuilder を初期化する必要があります。 

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: テーブルの作成を開始する

次に、DocumentBuilder を使用してテーブルの作成を開始し、最初のセルを挿入します。

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## ステップ3: 表の境界線を設定する

表全体の境界線を設定します。この手順により、特に指定がない限り、表内のすべてのセルの境界線スタイルが一定になります。

```csharp
//表全体の境界線を設定します。
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## ステップ4: セルの網掛けを適用する

セルに網掛けを適用して、視覚的に区別できるようにします。この例では、最初のセルの背景色を赤に設定します。


```csharp
//このセルのセルの網掛けを設定します。
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## ステップ5: 異なる網掛けのセルを挿入する

番目のセルを挿入し、異なる網掛け色を適用します。これにより、表がよりカラフルになり、読みやすくなります。

```csharp
builder.InsertCell();
// 2 番目のセルに異なるセルの網かけを指定します。
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## ステップ6: セルの書式設定をクリアする

前の操作からセルの書式設定をクリアして、次のセルが同じスタイルを継承しないようにします。


```csharp
//以前の操作によるセルの書式設定をクリアします。
builder.CellFormat.ClearFormatting();
```

## ステップ7: 特定のセルの境界線をカスタマイズする

特定のセルの境界線をカスタマイズして目立たせます。ここでは、新しい行の最初のセルに大きな境界線を設定します。

```csharp
builder.InsertCell();
//この行の最初のセルに大きい境界線を作成します。これは異なります
//テーブルに設定された境界線と比較します。
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## ステップ8: 最終セルを挿入する

最後のセルを挿入し、その書式設定がクリアされて、テーブルの既定のスタイルが使用されることを確認します。

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## ステップ9: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、表とセルをさまざまな境界線で書式設定する方法を学びました。表の境界線とセルの網掛けをカスタマイズすることで、ドキュメントの見た目を大幅に向上させることができます。さあ、さまざまなスタイルを試して、ドキュメントを目立たせましょう。

## よくある質問

### セルごとに異なる境界線スタイルを使用できますか?
はい、セルごとに異なる境界線スタイルを設定できます。`CellFormat.Borders`財産。

### テーブルからすべての境界線を削除するにはどうすればよいですか?
境界線スタイルを次のように設定すると、すべての境界線を削除できます。`LineStyle.None`.

### セルごとに異なる境界線の色を設定することは可能ですか?
もちろんです！各セルの境界線の色は、`CellFormat.Borders.Color`財産。

### セルの背景として画像を使用できますか?
Aspose.Words はセルの背景として画像を直接サポートしていませんが、画像をセルに挿入し、セル領域をカバーするようにサイズを調整することができます。

### 表内のセルを結合するにはどうすればよいですか?
セルを結合するには、`CellFormat.HorizontalMerge`そして`CellFormat.VerticalMerge`プロパティ。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
