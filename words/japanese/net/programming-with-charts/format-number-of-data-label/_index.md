---
"description": "このステップバイステップガイドでは、Aspose.Words for .NET を使用してグラフのデータラベルを書式設定する方法を学習します。Word文書を簡単に強化できます。"
"linktitle": "グラフのデータラベルの数値の書式設定"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "グラフのデータラベルの数値の書式設定"
"url": "/ja/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# グラフのデータラベルの数値の書式設定

## 導入

魅力的で情報豊富なドキュメントを作成するには、多くの場合、適切にフォーマットされたデータラベル付きのグラフを含める必要があります。.NET開発者で、Word文書に洗練されたグラフを追加したいとお考えなら、Aspose.Words for .NETはまさにうってつけのライブラリです。このチュートリアルでは、Aspose.Words for .NETを使用してグラフ内の数値ラベルの書式を設定する手順を、ステップごとに解説します。

## 前提条件

コードに進む前に、いくつかの前提条件を満たす必要があります。

- Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。まだインストールしていない場合は、 [ここからダウンロード](https://releases。aspose.com/words/net/).
- 開発環境：.NET開発環境をセットアップする必要があります。Visual Studioを強く推奨します。
- C# の基礎知識: このチュートリアルでは C# コードの記述と理解を行うため、C# プログラミングの知識が必須です。
- 一時ライセンス: Aspose.Wordsを制限なく使用するには、 [一時ライセンス](https://purchase。aspose.com/temporary-license/).

それでは、グラフ内の数値ラベルをフォーマットする手順を詳しく説明します。

## 名前空間のインポート

まず最初に、Aspose.Words for .NET を使用するために必要な名前空間をインポートする必要があります。C# ファイルの先頭に次の行を追加してください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## ステップ1: ドキュメントディレクトリを設定する

Word文書の操作を始める前に、文書を保存するディレクトリを指定する必要があります。これは、後の保存操作に不可欠です。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ドキュメント ディレクトリへの実際のパスを入力します。

## ステップ2: DocumentとDocumentBuilderを初期化する

次のステップは、新しい `Document` そして `DocumentBuilder`。その `DocumentBuilder` ドキュメントのコンテンツを構築できるようにするヘルパー クラスです。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ3: ドキュメントにグラフを挿入する

それでは、 `DocumentBuilder`このチュートリアルでは、折れ線グラフを例として使用します。

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

ここでは、特定の幅と高さを持つ折れ線グラフを挿入し、グラフのタイトルを設定します。

## ステップ4: デフォルトのシリーズをクリアして新しいシリーズを追加する

デフォルトでは、チャートにはいくつかの事前生成された系列が含まれています。これらをクリアし、特定のデータポイントを含む独自の系列を追加する必要があります。

```csharp
// デフォルトで生成されたシリーズを削除します。
chart.Series.Clear();

// カスタム データ ポイントを使用して新しいシリーズを追加します。
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## ステップ5: データラベルを有効にする

グラフにデータ ラベルを表示するには、シリーズに対してデータ ラベルを有効にする必要があります。

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## ステップ6: データラベルの書式設定

このチュートリアルの核となるのは、データラベルの書式設定です。各データラベルに個別に異なる数値書式を適用できます。

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // 通貨形式
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // 日付形式
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // パーセンテージ形式
```

さらに、データラベルの書式を元のセルにリンクすることもできます。リンクすると、 `NumberFormat` 一般にリセットされ、ソース セルから継承されます。

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## ステップ7: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

これにより、ドキュメントが指定された名前で保存され、フォーマットされたデータ ラベルを含むグラフが保持されます。

## 結論

Aspose.Words for .NET を使用してグラフのデータラベルを書式設定すると、Word 文書の読みやすさとプロフェッショナリズムが大幅に向上します。このステップバイステップガイドに従うことで、グラフを作成し、データ系列を追加し、ニーズに合わせてデータラベルを書式設定できるようになります。Aspose.Words for .NET は、Word 文書の広範なカスタマイズと自動化を可能にする強力なツールであり、.NET 開発者にとって非常に貴重な資産となります。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、C# を使用してプログラム的に Word 文書を作成、操作、変換するための強力なライブラリです。

### Aspose.Words for .NET を使用して他の種類のグラフをフォーマットできますか?
はい、Aspose.Words for .NET は、棒グラフ、縦棒グラフ、円グラフなど、さまざまな種類のグラフをサポートしています。

### Aspose.Words for .NET の一時ライセンスを取得するにはどうすればよいですか?
臨時免許証を取得できます [ここ](https://purchase。aspose.com/temporary-license/).

### Excel でデータ ラベルをソース セルにリンクすることは可能ですか?
はい、データ ラベルをソース セルにリンクして、数値形式をソース セルから継承することができます。

### Aspose.Words for .NET の詳細なドキュメントはどこで入手できますか?
包括的なドキュメントが見つかります [ここ](https://reference。aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}