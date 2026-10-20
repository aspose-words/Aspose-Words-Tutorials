---
category: general
date: 2026-08-14
description: Aspose.Words を使用して Java で Word に円グラフを作成します。数行でチャートに系列データを追加し、円グラフのスライスを回転させる方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: ja
lastmod: 2026-08-14
og_description: Aspose.Words を使用して Java で Word に円グラフを作成します。このチュートリアルでは、チャートに系列データを追加し、円グラフのスライスをすばやく回転させる方法を示します。
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: JavaでWordに円グラフを作成する – 完全コーディングガイド
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: JavaでWordに円グラフを作成する – ステップバイステップガイド
url: /ja/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWordに円グラフを作成する – ステップバイステップガイド

Wordで円グラフをプログラムで作成する必要がある場合、このガイドではJavaとAspose.Wordsを使用して具体的な手順を示します。チャートの挿入からデータポイントの追加、最初のスライスの回転まで、完全なワークフローを学べます。

.docx ファイルに直接チャートを生成することで、手動のコピー＆ペースト作業が不要になり、レポート、請求書、ダッシュボードなどを自動化できます。また、**チャートへのシリーズデータの追加方法** と **円グラフのスライスの回転方法** についても解説します。

## Wordで円グラフを作成 – 概要

Aspose.Words for Java は、Word ドキュメントにチャートオブジェクトを挿入できる流暢な `DocumentBuilder` API を提供します。選択したチャートタイプに応じてデフォルトのレイアウトが決まり、シリーズ、色、角度をカスタマイズしたり、ワンメソッドでドーナツ形状に切り替えることもできます。

### Aspose.Words を使用する理由

* **Microsoft Office 不要** – このライブラリは任意のサーバーや CI 環境で動作します。  
* **完全な .docx 再現性** – 生成されたチャートは、Word で手動で作成したものと同一に見えます。  
* **単一ファイル依存** – JAR を追加するだけで使用可能です。  

## チャートへのシリーズデータの追加方法

データのないチャートは単なるプレースホルダーです。`Chart` オブジェクトは `Series` コレクションを公開しており、各シリーズはスライス（円グラフの場合）やポイント（折れ線グラフの場合）に対応する数値リストを保持します。データの追加は簡単です：

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**コードの動作:**  
* `chart.getSeries()` は `List<ChartSeries>` を返します。  
* `get(0)` は最初のシリーズを選択します。円グラフは定義上 1 つのシリーズしか持たないためです。  
* `add(double)` はデータポイントを追加します。値は自動的にパーセンテージに変換され、チャート描画時に合計が 100 % になるよう調整されます。

> **プロのコツ:** データソースに 3 つ以上のカテゴリがある場合は、同様に値を追加し続けてください。Aspose.Words が自動的に追加のスライスを作成します。

## 円グラフのスライスを回転する

特定のスライスを特定の角度から開始させ、最も重要なセグメントを視聴者に向けたいことがあります。`setFirstSliceAngle(double)` メソッドはチャート全体を回転させ、実質的に最初のスライスの開始位置を変更します：

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

角度は垂直軸から時計回りに度数で測定されます。`0`（デフォルト）に設定すると、最初のスライスが上部に配置されます。スライスを強調したりデザインガイドラインに合わせるために値を調整してください。

> **よくある質問:** *回転はデータの順序に影響しますか？*  
> いいえ。データの順序は変わらず、視覚的な開始位置だけが変わります。

## 完全な Java 例

以下は、円グラフ付きの Word ドキュメントを作成し、シリーズデータを追加し、スライスを回転させ、ファイルを保存する完全な実行可能プログラムです。必要なインポートがすべて記載されているので、任意の IDE にコードをコピーして使用できます。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 期待される出力

* `output` フォルダーに **PieChart.docx** という名前のファイルが作成されます。  
* Microsoft Word でファイルを開くと、3 つのスライス（40 %、30 %、30 %）を持つカラフルな円グラフが表示されます。  
* チャートは時計回りに 45° 回転しているため、最初のスライスは垂直軸のやや右側から開始します。

## よくある落とし穴とベストプラクティス

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **チャートが空白になる** | チャートが完全に描画される前にドキュメントが保存されました。 | `doc.save()` をすべてのチャート変更 **後** に呼び出してください。 |
| **スライスの値が 100 % に合計されない** | パーセンテージを表さない生の数値を追加すると、予期しないスケーリングが発生する可能性があります。 | 全体の一部を表す論理的な値を提供するか、Aspose.Words に自動でパーセンテージを計算させてください。 |
| **回転が効果を示さない** | `holeSize` を設定せずに `ChartType.DOUGHNUT` を使用すると、回転効果が見えなくなることがあります。 | チャートを `PIE` のままにするか、角度設定後に `holeSize` を調整してください。 |
| **ファイルパスエラー** | 相対パスは Windows と Linux で解決方法が異なる場合があります。 | 本番コードでは `Paths.get("output", "PieChart.docx").toString()` または絶対パスを使用してください。 |

### 本番環境での使用に関するヒント

* **`DocumentBuilder` の再利用** – `insertChart` を繰り返し呼び出すことで、同一ドキュメントに複数のチャートを挿入できます。  
* **スタイリング** – `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` を使用して、チャート上に直接パーセンテージを表示できます。  
* **パフォーマンス** – チャートを一度生成し、複数箇所で同一のチャートが必要な場合は `chart.deepClone()` でクローンしてください。

## 円グラフのスライスを回転 – 高度なシナリオ

* **動的な角度** – データに基づいて角度を計算します（例: 最大のスライスを上部から開始させる）。  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **複数シリーズ** – 通常円グラフは 1 系列ですが、Aspose.Words ではスタック円グラフ用に複数のシリーズを追加できます。回転は最初のシリーズのみに適用されます。

## 結論

Java を使用して **Word に円グラフを作成** する方法、**チャートへのシリーズデータの追加** 方法、そして視覚的に強調するための **円グラフのスライスの回転** 方法が分かりました。完全な例は、ドキュメントの初期化から最終的な `.docx` ファイルの保存までの全ワークフローを示しているので、チャート生成を任意の自動レポートパイプラインに組み込むことができます。

### 次にやることは？

* 他のチャートタイプ（`ChartType.BAR`、`ChartType.LINE`）を調査して、オートメーションツールキットを拡充しましょう。  
* チャート生成と **メールマージ** を組み合わせて、受取人ごとにパーソナライズされたレポートを作成します。  
* **Styling API**（`ChartFormat`、`DataLabel`、`ChartTitle`）を深く掘り下げて、企業のブランディングに合わせましょう。

さまざまなデータセット、角度、チャートスタイルで自由に試してみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用した縦棒グラフの作成方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java の DocumentBuilder を使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java を使用して Word を PDF に変換する方法](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}