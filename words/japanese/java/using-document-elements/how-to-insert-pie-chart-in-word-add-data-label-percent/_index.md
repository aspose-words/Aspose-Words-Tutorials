---
category: general
date: 2026-07-20
description: Aspose.Words を使用して Word に円グラフを挿入する方法。データラベルのパーセンテージを追加し、プロフェッショナルな文書用にチャートにパーセンテージを表示する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: ja
lastmod: 2026-07-20
og_description: Aspose.Words を使用して Word に円グラフを挿入する方法。このガイドでは、データ ラベルのパーセンテージを追加し、数行でチャートにパーセンテージを表示する方法を示します。
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: Wordで円グラフを挿入する方法 – クイックガイド
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Wordで円グラフを挿入する方法 – データラベルにパーセンテージを追加
url: /ja/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word に円グラフを挿入する方法 – データラベルのパーセンテージを追加

Ever wondered **how to insert pie chart** into a Word document without wrestling with the UI? You’re not alone. In many reporting scenarios you need to *add pie chart to Word* and, more importantly, **show percent on pie chart** so readers instantly grasp the data distribution.

Word 文書に **円グラフを挿入する方法** を UI と格闘せずに知りたくなったことはありませんか？ あなただけではありません。多くのレポートシナリオでは *Word に円グラフを追加* する必要があり、さらに重要なのは **円グラフにパーセンテージを表示** して、読者がデータ分布を瞬時に把握できるようにすることです。

In this tutorial we’ll walk through the complete process using Aspose.Words for Java. By the end you’ll know exactly how to **add data label percent**, **display percentages on chart**, and get a polished pie chart that looks right the first time. No extra plugins, no manual tweaks—just clean code you can drop into any project.

このチュートリアルでは Aspose.Words for Java を使用して、全工程を順に解説します。最後まで読むと、**データラベルのパーセンテージを追加**する方法、**チャートにパーセンテージを表示**する方法、そして最初から見栄えの良い円グラフを作成する方法が正確に分かります。余計なプラグインや手動の調整は不要で、どのプロジェクトにも組み込めるクリーンなコードだけです。

---

## 前提条件

- Java 17（またはそれ以降）– Aspose.Words がサポートする現在の LTS バージョン。
- Aspose.Words for Java 24.x（執筆時点（2026年7月）での最新バージョン）。
- ライブラリを取得するための基本的な Maven または Gradle の設定。
- お好みの IDE（IntelliJ IDEA、Eclipse、VS Code など）。

If you already have these, great—let’s dive in.

これらがすでに揃っているなら、素晴らしいです—さっそく始めましょう。

## 手順 1: プロジェクトを設定し、ライブラリをインポートする

First, add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). This gives you access to the `Document`, `DocumentBuilder`, and chart classes.

まず、`pom.xml`（Maven）または `build.gradle`（Gradle）に Aspose.Words の依存関係を追加します。これにより、`Document`、`DocumentBuilder`、およびチャート関連クラスが使用可能になります。

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **プロのコツ:** バージョン番号は常に最新に保ちましょう。新しいリリースでは、チャート関連の修正が追加されることが多く、**チャートにパーセンテージを表示**の信頼性が向上します。

## 手順 2: 新しい Word 文書とビルダーを作成する

The builder is your Swiss‑army knife for inserting content. Here we create a fresh document and attach a `DocumentBuilder` to it.

ビルダーはコンテンツ挿入のための万能ツールです。ここでは新しい文書を作成し、`DocumentBuilder` をそれに結び付けます。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Why do we need a builder? It abstracts the low‑level OpenXML structures, letting us focus on *what* we want—like **add pie chart to word**—instead of *how* the XML looks.

なぜビルダーが必要なのでしょうか？ 低レベルの OpenXML 構造を抽象化し、*何を*したいか（例: **Word に円グラフを追加**）に集中でき、*XML がどのように見えるか*は気にしなくて済みます。

## 手順 3: 円グラフを挿入する

Now comes the core of **how to insert pie chart**. We ask the builder to place a pie chart of a specific size. The dimensions are in points (1 pt ≈ 1/72 in).

ここで **円グラフを挿入する方法** の核心に入ります。ビルダーに特定のサイズの円グラフを配置させます。サイズはポイント単位です（1 pt ≈ 1/72 in）。

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

At this point the chart is empty, but the placeholder is already in the document. You’ve just **add pie chart to word** programmatically.

この時点でチャートは空ですが、プレースホルダーは文書内に配置されています。プログラムで **Word に円グラフを追加** したことになります。

## 手順 4: データでチャートに値を設定する

A pie chart needs at least one series of values. Let’s feed it some sample data that represents market share.

円グラフには少なくとも 1 つのデータ系列が必要です。市場シェアを表すサンプルデータを入力してみましょう。

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

If you ever need multiple series (stacked pies, doughnuts, etc.) you can call `pieChart.getSeries().add()` and repeat the steps. The same logic applies when you want to **display percentages on chart** for each slice.

複数の系列（積み上げ円グラフ、ドーナツなど）が必要な場合は `pieChart.getSeries().add()` を呼び出し、手順を繰り返すことができます。同様のロジックで各スライスに **チャートにパーセンテージを表示** することも可能です。

## 手順 5: **データラベルのパーセンテージを追加** – スライスにパーセンテージを表示する

This is the part most developers forget: configuring the data labels to show percentages. Without it, the chart only shows raw numbers, which can be ambiguous.

多くの開発者が忘れがちな部分です: データラベルをパーセンテージ表示に設定します。これがないと、チャートは生の数値だけを表示し、曖昧になることがあります。

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

The `setShowPercent(true)` call tells Aspose.Words to render the label as “30 %”, “45 %”, etc. That’s exactly how you **show percent on pie chart** without any extra formatting work.

`setShowPercent(true)` の呼び出しにより、Aspose.Words はラベルを “30 %”、 “45 %” のように描画します。これが余計な書式設定なしで **円グラフにパーセンテージを表示**する正確な方法です。

## 手順 6: 文書を保存する

Finally, write the document to disk. You can choose `.docx`, `.pdf`, or even `.html`. For this guide we’ll stick with the modern `.docx` format.

最後に、文書をディスクに書き出します。`.docx`、`.pdf`、あるいは `.html` も選択可能です。このガイドでは最新の `.docx` 形式を使用します。

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Run the program, open `PieChartDemo.docx`, and you’ll see a neatly rendered pie chart with percentage labels on each slice.

プログラムを実行し、`PieChartDemo.docx` を開くと、各スライスにパーセンテージラベルが付いたきれいに描画された円グラフが表示されます。

## 期待される出力

Below is a screenshot of the generated Word file. Notice how each slice displays its share as a percentage—exactly what we wanted when we set **add data label percent**.

以下は生成された Word ファイルのスクリーンショットです。各スライスがパーセンテージでシェアを表示していることに注目してください—**データラベルのパーセンテージを追加** を設定したときに求めていた通りです。

![円グラフにパーセンテージラベルが付いた Word 文書のスクリーンショット](/images/pie-chart-percent.png){.center width=600px alt="Word に円グラフを挿入し、パーセンテージラベルを表示する方法のスクリーンショット"}

*Alt テキストには主要キーワードが含まれており、SEO とアクセシビリティの両方を満たしています。*

## よくある質問とエッジケースの対処

| Question | Answer |
|----------|--------|
| **パーセンテージラベルのフォントを変更できますか？** | はい。`setShowPercent(true)` を有効にした後、`DataLabel` オブジェクトを取得し、その `Font` プロパティを調整します（例: `dataLabel.getFont().setSize(10);`）。 |
| **円グラフではなくドーナツチャートが必要な場合はどうすればよいですか？** | `insertChart` 呼び出しで `ChartType.PIE` を `ChartType.DOUGHNUT` に置き換えます。同じ **データラベルのパーセンテージを追加** ロジックが機能します。 |
| **古い Word バージョン（2007‑2010）でもパーセンテージは正しく表示されますか？** | Aspose.Words は基盤となる XML をバージョンに依存しない形で書き込むため、チャートに対応した Word（2007 以降）であれば、どのバージョンでもパーセンテージが表示されます。 |
| **チャートにタイトルを追加するには？** | 保存する前に `pieChart.getTitle().setText("Market Share");` を使用します。 |
| **特定の段落やテーブルセルにチャートを挿入できますか？** | もちろん可能です。`insertChart` を呼び出す前に `DocumentBuilder` を目的の位置に移動させます（例: `builder.moveToParagraph(index, true);` または `builder.moveToCell(table, row, column, true);`）。 |

## 現場からのヒントとコツ

- **プロのコツ:** ループで多数のチャートを生成する場合、単一の `DocumentBuilder` インスタンスを再利用すると、メモリの消費が抑えられます。
- **注意点:** 非常に小さなスライス（< 2 %）です。Aspose.Words はラベルが混雑しないように省略することがありますが、`dataLabel.setShowLabel(true);` で強制的に表示できます。
- **パフォーマンスに関する注意:** チャートの描画は CPU 集中型です。大量レポート生成の場合はマルチスレッド化を検討してください。ただし、各スレッドが独自の `Document` インスタンスで作業するようにしてください。
- **バージョン確認:** `setShowPercent` メソッドは Aspose.Words 22.8 で導入されました。古いバージョンを使用している場合はアップグレードするか、手動でパーセンテージを計算しカスタムラベルとして設定してください。

## まとめ

We’ve covered **how to insert pie chart** into a Word document using Aspose.Words, shown you how to **add data label percent**, and demonstrated the easiest way to **display percentages on chart**. With just a few lines of Java you can **add pie chart to word** and **show percent on pie chart**, turning raw numbers into instantly readable visuals.

このセクションでは Aspose.Words を使用して Word 文書に **円グラフを挿入する方法** を解説し、**データラベルのパーセンテージを追加**する手順と、**チャートにパーセンテージを表示**する最も簡単な方法を示しました。数行の Java コードだけで **Word に円グラフを追加**し、**円グラフにパーセンテージを表示**でき、 生の数値をすぐに読めるビジュアルに変換できます。

## 次にやることは？

- 他のチャートタイプ（`BAR`、`LINE`、`AREA`）を試し、同じ **データラベルのパーセンテージを追加** ロジックがどのように適用されるか確認しましょう。
- チャートとテーブルを組み合わせて、よりリッチなレポートを作成できます—Aspose.Words ならチャートをデータテーブルの横に配置するのも簡単です。
- 同じ文書を PDF や HTML にエクスポートし、フォーマット間でパーセンテージがどのように表示されるか確認してみましょう。

Feel free to tweak the dimensions, colors, or data source (e.g., a database query) and watch your Word reports come alive. If you hit a snag, drop a comment below—happy charting!

次元や色、データソース（例: データベースクエリ）を自由に調整して、Word レポートを活き活きとさせてみてください。問題が発生したら下にコメントを残してください—楽しいチャート作成を！

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Word に列グラフを挿入する（Aspose.Words for .NET）](/words/english/net/working-with-charts/insert-column-chart/)
- [Word 文書にエリアチャートを挿入する | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Word にバブルチャートを挿入する（Aspose.Words for .NET）](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}