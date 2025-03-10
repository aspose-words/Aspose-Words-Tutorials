---
title: グラフの軸の数値形式
linktitle: グラフの軸の数値形式
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用してグラフの軸の数字をフォーマットする方法を学習します。ドキュメントの読みやすさとプロフェッショナリズムを簡単に向上できます。
weight: 10
url: /ja/net/programming-with-charts/number-format-for-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# グラフの軸の数値形式

## 導入

こんにちは! ドキュメント内のグラフを操作していて、軸の数字をフォーマットしてよりプロフェッショナルな見た目にしたいと思ったことはありませんか? 幸運にも、このチュートリアルでは、Aspose.Words for .NET を使用してそれを実現する方法について詳しく説明します。この強力なライブラリを使用すると、Word ドキュメントを非常に簡単に処理できます。今日は、カスタム数値フォーマットを使用してグラフの軸を一新することに焦点を当てます。

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

-  Aspose.Words for .NET: インストールされていることを確認してください。インストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- .NET Framework: 互換性のある .NET Framework がインストールされていることを確認します。
- 開発環境: Visual Studio などの IDE は完璧に動作します。
- C# の基礎知識: コーディング例を理解するのに役立ちます。

## 名前空間のインポート

まず最初に、プロジェクトに必要な名前空間をインポートする必要があります。これは、家を建てる前に基礎を築くようなものです。コード ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

それでは、プロセスをシンプルでわかりやすいステップに分解してみましょう。

## ステップ1: ドキュメントの設定

見出し: ドキュメントを初期化する

まず、新しいドキュメントとドキュメント ビルダーを作成する必要があります。このステップは、傑作の制作を始める前にキャンバスとブラシを準備するステップと考えてください。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここ、`dataDir`最終ファイルを保存するドキュメント ディレクトリへのパスです。`Document`そして`DocumentBuilder` Word 文書の作成と操作に役立つ Aspose.Words のクラスです。

## ステップ2: グラフの挿入

見出し: ドキュメントにグラフを追加する

次に、ドキュメントにグラフを追加しましょう。ここから魔法が始まります。空白のキャンバスとして機能する縦棒グラフを挿入します。

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

の`InsertChart`メソッドは、指定されたタイプ (この場合は列) とディメンションのグラフをドキュメントに挿入します。

## ステップ3: チャートシリーズのカスタマイズ

見出し: チャートにデータを入力する

ここで、チャートにデータを追加する必要があります。このステップは、チャートに意味のある情報を入力することに似ています。

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

ここでは、5つのデータポイントを持つ「Aspose Series 1」という新しいシリーズを追加します。`Series.Clear`このメソッドにより、新しいシリーズを追加する前に既存のデータがすべて削除されます。

## ステップ4: 軸の数字の書式設定

見出し: 軸の数字を美しくする

最後に、Y 軸の数字を読みやすくするために書式設定しましょう。これは、アートワークに最後の仕上げを施すようなものです。

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

の`FormatCode`プロパティを使用すると、軸上の数字のカスタムフォーマットを設定できます。この例では、`#,##0`大きな数字が 1000 単位ごとにコンマで表示されるようになります。

## ステップ5: ドキュメントを保存する

見出し: 傑作を保存する

すべての設定が完了したら、ドキュメントを保存します。このステップで、作業の成果が明らかになります。

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

ここでは、`Save`メソッドは、指定されたパスにファイル名でドキュメントを保存します。`WorkingWithCharts.NumberFormatForAxis.docx`.

## 結論

これで完了です。Aspose.Words for .NET を使用して、グラフの Y 軸の数字を正常にフォーマットできました。これにより、グラフの見た目がよりプロフェッショナルになるだけでなく、読みやすさも向上します。Aspose.Words には、プログラムで魅力的な Word 文書を作成するのに役立つさまざまな機能が用意されています。さらに詳しく調べて、他に何ができるか確認してみませんか。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムで Word 文書を作成、操作、変換できるようにする強力なライブラリです。

### 軸の数字以外のグラフの要素をフォーマットできますか?
もちろんです! Aspose.Words for .NET を使用すると、タイトルやラベルを書式設定したり、グラフの外観をカスタマイズしたりすることもできます。

### Aspose.Words for .NET の無料試用版はありますか?
はい、[無料トライアルはこちら](https://releases.aspose.com/).

### Aspose.Words for .NET を C# 以外の他の .NET 言語で使用できますか?
はい、Aspose.Words for .NET は、VB.NET や F# を含むあらゆる .NET 言語と互換性があります。

### より詳細なドキュメントはどこで見つかりますか?
詳細なドキュメントは、[Aspose.Words for .NET ドキュメント ページ](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
