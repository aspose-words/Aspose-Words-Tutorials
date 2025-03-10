---
title: 図形を使用してグラフを作成およびカスタマイズする
linktitle: 図形を使用してグラフを作成およびカスタマイズする
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書でグラフを作成およびカスタマイズする方法を学習します。データの視覚化に最適です。
weight: 10
url: /ja/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 図形を使用してグラフを作成およびカスタマイズする

## 導入

ドキュメント内でグラフを作成およびカスタマイズすることは、今日のデータ駆動型の世界では重要なスキルです。グラフはデータを視覚化し、複雑な情報をより理解しやすくするのに役立ちます。Aspose.Words for .NET は、Word ドキュメントをプログラムで作成および操作できる強力なライブラリです。このチュートリアルでは、Aspose.Words for .NET を使用して折れ線グラフを作成およびカスタマイズするプロセスについて説明します。このガイドを読み終える頃には、プロ並みのグラフを簡単に作成できるようになります。

## 前提条件

コードに進む前に、次のものを用意してください。

-  Aspose.Words for .NETライブラリ: ダウンロードできます[ここ](https://releases.aspose.com/words/net/).
- Visual Studio: .NET をサポートする任意のバージョン。
- C# の基礎知識: C# の基礎を理解しておくと、チュートリアルを理解しやすくなります。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。この手順は、Aspose.Words for .NET によって提供されるクラスとメソッドを使用できるようにするため、不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## ステップ1: 新しいドキュメントを作成する

まず、新しい Word 文書を作成する必要があります。この文書は、グラフのキャンバスとして機能します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: グラフを挿入する

次に、ドキュメントに折れ線グラフを挿入します。`DocumentBuilder.InsertChart`この目的にはこの方法が使用されます。

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## ステップ3: グラフのタイトルをカスタマイズする

グラフのタイトルをカスタマイズすると、表示されるデータのコンテキストを提供するのに役立ちます。次のコードを使用して、タイトルを表示し、そのテキストを設定できます。

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
//タイトル テキストとして null または空の値が指定されている場合は、自動生成されたタイトルが表示されることに注意してください。
```

## ステップ4: 凡例の位置を調整する

凡例は、グラフ内のさまざまなデータ系列を識別するのに役立ちます。次のように凡例の位置とオーバーレイ設定をカスタマイズできます。

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを保存する必要があります。この手順により、すべての変更がファイルに書き込まれます。

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## 結論

このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書に折れ線グラフを作成し、カスタマイズする方法について説明しました。ステップ バイ ステップ ガイドに従うことで、データを効果的に伝える視覚的に魅力的なグラフを作成できます。Aspose.Words for .NET には幅広いカスタマイズ オプションが用意されており、特定のニーズに合わせてグラフをカスタマイズできます。

## よくある質問

### Aspose.Words for .NET を使用して他の種類のグラフを作成できますか?

はい、Aspose.Words for .NETは棒グラフ、円グラフなど、さまざまなグラフタイプをサポートしています。ドキュメントをご覧ください。[ここ](https://reference.aspose.com/words/net/)詳細についてはこちらをご覧ください。

### 購入前に Aspose.Words for .NET を試すにはどうすればいいですか?

無料試用版は以下からダウンロードできます。[ここ](https://releases.aspose.com/)これにより、購入前にライブラリとその機能をテストできます。

### 問題が発生した場合にサポートを受ける方法はありますか?

もちろんです。Asposeコミュニティフォーラムを通じてサポートを受けることができます。[ここ](https://forum.aspose.com/c/words/8)コミュニティと Aspose スタッフは非常に反応が良いです。

### Aspose.Words for .NET のライセンスを購入するにはどうすればよいですか?

ライセンスはAsposeのWebサイトから直接購入できます。[ここ](https://purchase.aspose.com/buy)さまざまなニーズに合わせて、さまざまなライセンス オプションがあります。

### 短期プロジェクトのために一時的なライセンスが必要な場合はどうすればよいですか?

 Asposeは一時的なライセンスを提供しており、リクエストすることができます。[ここ](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
