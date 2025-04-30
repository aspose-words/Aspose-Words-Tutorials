---
"description": "Aspose.Words for .NET を使用して、グラフのデータラベルのデフォルトオプションを設定する方法を学びましょう。ステップバイステップのガイドに従って、簡単にグラフを作成およびカスタマイズできます。"
"linktitle": "グラフのデータラベルのデフォルトオプションを設定する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "グラフのデータラベルのデフォルトオプションを設定する"
"url": "/ja/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# グラフのデータラベルのデフォルトオプションを設定する

## 導入

こんにちは！ドキュメント自動化の世界に飛び込んでみませんか？今日は、Aspose.Words for .NET を使って、プログラムで魅力的なドキュメントを作成する方法をご紹介します。Aspose.Words は、Word 文書を簡単に操作できる強力なライブラリです。このチュートリアルでは、グラフのデータラベルのデフォルト設定に焦点を当てます。経験豊富な開発者の方でも、初心者の方でも、このガイドを読めば、すぐに使い始められるよう、ステップごとに丁寧に解説します。

## 前提条件

始める前に、このチュートリアルを進めるために必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

- Visual Studio またはその他の .NET 互換 IDE: ここでコードを記述して実行します。
- Aspose.Words for .NET: 次のようなことが可能です [最新バージョンをダウンロード](https://releases.aspose.com/words/net/) プロジェクトにインストールします。
- C# プログラミングの基礎知識: このガイドは初心者向けですが、C# について少し知っておくと役立ちます。
- .NET Framework がインストールされている: マシンに .NET Framework が設定されていることを確認します。
- Aspose.Wordsの一時ライセンス: 1つ入手 [ここ](https://purchase.aspose.com/temporary-license/) 全機能のロックを解除します。

これらの前提条件が満たされたら、準備は完了です。

## 名前空間のインポート

まずはプロジェクトをセットアップし、必要な名前空間をインポートしましょう。これらの名前空間は、Aspose.Words の機能にアクセスするために不可欠です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## ステップ1：新しいドキュメントを作成する


この旅は、新しいドキュメントを作成し、 `DocumentBuilder`。その `DocumentBuilder` クラスは、ドキュメントのコンテンツを簡単に操作するための一連のメソッドを提供します。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 新しいドキュメントを作成する
Document doc = new Document();

// DocumentBuilderを初期化する
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 説明

このステップでは、コンテンツを挿入してフォーマットするために使用するドキュメントとビルダーを設定しました。 `dataDir` 変数は、最終的なドキュメントを保存するパスを保持します。

## ステップ2: グラフを挿入する

次に、ドキュメントに円グラフを追加します。 `InsertChart` の方法 `DocumentBuilder` クラスを使用すると、これが非常に簡単になります。

```csharp
// 円グラフを挿入する
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// チャートオブジェクトにアクセスする
Chart chart = shape.Chart;
```

### 説明

ここでは、文書に円グラフを挿入しています。 `InsertChart` メソッドは、チャートの種類、幅、高さをパラメータとして指定します。チャートを挿入した後、チャートオブジェクトにアクセスしてさらに操作を行います。

## ステップ3: グラフシリーズをカスタマイズする

次に、チャート内の既存の系列をすべてクリアし、カスタム系列を追加します。この系列がデータポイントを表します。

```csharp
// 既存のチャートシリーズをクリア
chart.Series.Clear();

// チャートに新しいシリーズを追加する
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### 説明

このステップでは、既存の系列をすべてクリアして、チャートが空であることを確認します。次に、カスタムカテゴリと値を持つ新しい系列を追加し、円グラフに表示します。

## ステップ4: データラベルのデフォルトオプションを設定する

データラベルは、チャートに情報を伝える上で非常に重要です。パーセンテージや値を表示したり、区切り線をカスタマイズしたりするオプションを設定します。

```csharp
// データラベルコレクションにアクセスする
ChartDataLabelCollection labels = series.DataLabels;

// データラベルオプションを設定する
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### 説明

ここでは、 `DataLabels` 系列のプロパティを使用して、各データラベルに表示される外観と情報をカスタマイズします。ここでは、パーセンテージと値の両方を表示し、引き出し線を非表示にし、カスタムセパレーターを設定することを選択しました。

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを指定のディレクトリに保存します。この手順により、すべての変更がファイルに書き込まれます。

```csharp
// ドキュメントを保存する
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### 説明

この最後のステップでは、 `Save` メソッドで指定されたディレクトリに保存されます。 `dataDir`「WorkingWithCharts.DefaultOptionsForDataLabels.docx」という名前です。

## 結論

これで完了です！Aspose.Words for .NET を使って、カスタマイズされた円グラフ付きのWord文書を作成できました。この強力なライブラリを使えば、文書の作成と操作を簡単に自動化でき、時間と労力を節約できます。レポート、請求書、その他あらゆる種類の文書を作成する場合でも、Aspose.Words がきっと役に立ちます。

ぜひ、 [Aspose.Words ドキュメント](https://reference.aspose.com/words/net/) より多くの機能と例についてはこちらをご覧ください。楽しいコーディングを！

## よくある質問

### Aspose.Words を無料で使用できますか?
Aspose.Wordsは無料でご利用いただけます。 [一時ライセンス](https://purchase.aspose.com/temporary-license/) または、 [無料トライアル](https://releases。aspose.com/).

### Aspose.Words のサポートを受けるにはどうすればよいですか?
サポートを受けるには [Aspose.Words サポートフォーラム](https://forum。aspose.com/c/words/8).

### 他の種類のグラフを追加できますか?
はい、Aspose.Wordsは棒グラフ、折れ線グラフ、縦棒グラフなど、さまざまなグラフの種類をサポートしています。 [ドキュメント](https://reference.aspose.com/words/net/) 詳細についてはこちらをご覧ください。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Wordsは.NET Coreと互換性があります。詳しくは [ドキュメント](https://reference。aspose.com/words/net/).

### Aspose.Words のライセンスを購入するにはどうすればよいですか?
ライセンスは以下から購入できます。 [Asposeストア](https://purchase。aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}