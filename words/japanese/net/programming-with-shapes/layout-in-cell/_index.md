---
title: セル内のレイアウト
linktitle: セル内のレイアウト
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なガイドでは、Aspose.Words for .NET を使用してセルのレイアウトを設定する方法を学習します。Word ドキュメントをカスタマイズしたい開発者に最適です。
weight: 10
url: /ja/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# セル内のレイアウト

## 導入

Word 文書の表のセルのレイアウトをプログラムで微調整したいと思ったことがあるなら、ここが最適な場所です。今日は、Aspose.Words for .NET を使用してセルのレイアウトを設定する方法について詳しく説明します。実用的な例を段階的に説明していくので、簡単に理解できます。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。まだインストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
2. 開発環境: .NET でセットアップされた開発環境が必要です。推奨事項を探している場合は、Visual Studio が最適です。
3. C# の基礎知識: 各ステップについて説明しますが、C# の基礎を理解しておくと、より簡単に理解できるようになります。
4. ドキュメントディレクトリ: ドキュメントを保存するディレクトリパスを用意します。これを`YOUR DOCUMENT DIRECTORY`.

## 名前空間のインポート

開始するには、プロジェクトに必要な名前空間をインポートしていることを確認してください。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

プロセスを管理しやすいステップに分解してみましょう。

## ステップ1: 新しいドキュメントを作成する

まず、新しいWord文書を作成し、`DocumentBuilder`コンテンツの構築に役立つオブジェクト。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: テーブルを開始して行の書式を設定する

テーブルの構築を開始し、行の高さと高さルールを指定します。

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## ステップ3: セルを挿入してコンテンツを入力する

次に、ループしてテーブルにセルを挿入します。7 つのセルごとに行を終了して新しい行を作成します。

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## ステップ4: 透かし図形を追加する

さて、文書に透かしを追加してみましょう。`Shape`オブジェクトを作成し、そのプロパティを設定します。

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, //図形をセル内に配置した場合は、表のセルの外側に図形を表示します。
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## ステップ5: 透かしの外観をカスタマイズする

色とテキストのプロパティを設定して、透かしの外観をさらにカスタマイズします。

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## ステップ6: 文書に透かしを挿入する

ドキュメント内の最後の実行を見つけて、その位置に透かしを挿入します。

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## ステップ 7: Word 2010 用に文書を最適化する

互換性を確保するために、ドキュメントを Word 2010 用に最適化します。

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## ステップ8: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、カスタマイズされたテーブル レイアウトの Word 文書を作成し、透かしを追加しました。このチュートリアルの目的は、プロセスの各部分を理解できるように、わかりやすいステップ バイ ステップ ガイドを提供することです。これらのスキルがあれば、より洗練されたカスタマイズされた Word 文書をプログラムで作成できます。

## よくある質問

### 透かしテキストに別のフォントを使用できますか?
はい、設定することでフォントを変更できます。`watermark.TextPath.FontFamily`プロパティを希望のフォントに設定します。

### 透かしの位置を調整するにはどうすればよいですか?
変更することができます`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` 、 そして`VerticalAlignment`透かしの位置を調整するためのプロパティ。

### 透かしにテキストの代わりに画像を使用することは可能ですか?
もちろんです！`Shape`タイプ`ShapeType.Image`そしてそのイメージを`ImageData.SetImage`方法。

### 行の高さが異なる表を作成できますか?
はい、各行に異なる高さを設定するには、`RowFormat.Height`その行にセルを挿入する前に、プロパティを設定します。

### 文書から透かしを削除するにはどうすればよいですか?
透かしを削除するには、ドキュメントの図形コレクションで透かしを見つけて、`Remove`方法。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
