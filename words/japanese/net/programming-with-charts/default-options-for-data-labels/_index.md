---
title: グラフのデータラベルのデフォルトオプションを設定する
linktitle: グラフのデータラベルのデフォルトオプションを設定する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、グラフのデータ ラベルの既定のオプションを設定する方法を学びます。ステップ バイ ステップ ガイドに従って、グラフを簡単に作成およびカスタマイズします。
weight: 10
url: /ja/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# グラフのデータラベルのデフォルトオプションを設定する

## 導入

こんにちは！ドキュメント自動化の世界に飛び込むことにワクワクしていますか？今日は、Aspose.Words for .NET を使用して、プログラムで魅力的なドキュメントを作成する方法を説明します。Aspose.Words は、Word ドキュメントを簡単に操作できる強力なライブラリです。このチュートリアルでは、グラフのデータ ラベルの既定のオプションの設定に焦点を当てます。熟練した開発者でも初心者でも、このガイドでは各ステップを順を追って説明し、すぐに使い始めることができます。

## 前提条件

始める前に、このチュートリアルを進めるために必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

- Visual Studio またはその他の .NET 互換 IDE: ここでコードを記述して実行します。
-  Aspose.Words for .NET: 次のようなことができます[最新バージョンをダウンロード](https://releases.aspose.com/words/net/)プロジェクトにインストールします。
- C# プログラミングの基礎知識: このガイドは初心者向けですが、C# について少し知っておくと役立ちます。
- .NET Framework がインストールされている: マシンに .NET Framework が設定されていることを確認します。
-  Aspose.Wordsの一時ライセンス: 1つ入手[ここ](https://purchase.aspose.com/temporary-license/)全機能のロックを解除します。

これらの前提条件を整理したら、準備は完了です。

## 名前空間のインポート

まず最初に、プロジェクトをセットアップして必要な名前空間をインポートしましょう。これらの名前空間は、Aspose.Words 機能にアクセスするために不可欠です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## ステップ1: 新しいドキュメントを作成する


この旅は、新しいドキュメントを作成し、`DocumentBuilder` 。`DocumentBuilder`クラスは、ドキュメントのコンテンツを簡単に操作するための一連のメソッドを提供します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

//新しいドキュメントを作成する
Document doc = new Document();

// DocumentBuilder を初期化する
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 説明

このステップでは、コンテンツを挿入してフォーマットするために使用するドキュメントとビルダーを設定しました。`dataDir`変数には、最終的なドキュメントを保存するパスが保持されます。

## ステップ2: グラフを挿入する

次に、ドキュメントに円グラフを追加します。`InsertChart`方法の`DocumentBuilder`クラスを使用すると、これが非常に簡単になります。

```csharp
//円グラフを挿入する
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

//チャートオブジェクトにアクセスする
Chart chart = shape.Chart;
```

### 説明

ここでは、文書に円グラフを挿入しています。`InsertChart`メソッドには、チャートの種類、幅、高さをパラメータとして指定する必要があります。チャートを挿入した後、チャート オブジェクトにアクセスしてさらに操作します。

## ステップ3: チャートシリーズをカスタマイズする

ここで、グラフ内の既存のシリーズをクリアし、カスタム シリーズを追加します。このシリーズはデータ ポイントを表します。

```csharp
//既存のチャートシリーズをクリア
chart.Series.Clear();

//チャートに新しいシリーズを追加する
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### 説明

このステップでは、既存のシリーズをすべてクリアして、チャートが空であることを確認します。次に、カスタム カテゴリと値を持つ新しいシリーズを追加します。これは円グラフに表示されます。

## ステップ4: データラベルのデフォルトオプションを設定する

データ ラベルは、グラフに情報を伝えるために重要です。パーセンテージや値を表示したり、区切り線をカスタマイズしたりするためのオプションを設定します。

```csharp
//データラベルコレクションにアクセスする
ChartDataLabelCollection labels = series.DataLabels;

//データラベルオプションを設定する
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### 説明

ここでは、`DataLabels`シリーズのプロパティを使用して、各データ ラベルに表示される外観と情報をカスタマイズします。パーセンテージと値の両方を表示し、リーダー ラインを非表示にして、カスタム セパレーターを設定することを選択しました。

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。この手順により、すべての変更がファイルに書き込まれるようになります。

```csharp
//文書を保存する
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### 説明

この最後のステップでは、`Save`メソッドで指定されたディレクトリに文書が保存されます。`dataDir`「WorkingWithCharts.DefaultOptionsForDataLabels.docx」という名前です。

## 結論

これで完了です。Aspose.Words for .NET を使用して、カスタマイズされた円グラフを含む Word 文書を作成できました。この強力なライブラリを使用すると、文書の作成と操作を簡単に自動化できるため、時間と労力を節約できます。レポート、請求書、またはその他の種類の文書を生成する場合でも、Aspose.Words が役立ちます。

ぜひご自由に探索してください[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/)より多くの機能と例については、こちらをご覧ください。コーディングを楽しんでください!

## よくある質問

### Aspose.Words を無料で使用できますか?
Aspose.Wordsは無料でご利用いただけます。[一時ライセンス](https://purchase.aspose.com/temporary-license/)または、[無料トライアル](https://releases.aspose.com/).

### Aspose.Words のサポートを受けるにはどうすればよいですか?
サポートを受けるには[Aspose.Words サポート フォーラム](https://forum.aspose.com/c/words/8).

### 他の種類のグラフを追加できますか?
はい、Aspose.Wordsは棒グラフ、折れ線グラフ、縦棒グラフなど、さまざまなグラフタイプをサポートしています。[ドキュメント](https://reference.aspose.com/words/net/)詳細についてはこちらをご覧ください。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Wordsは.NET Coreと互換性があります。詳細については、[ドキュメント](https://reference.aspose.com/words/net/).

### Aspose.Words のライセンスを購入するにはどうすればよいですか?
ライセンスは以下から購入できます。[Aspose ストア](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
