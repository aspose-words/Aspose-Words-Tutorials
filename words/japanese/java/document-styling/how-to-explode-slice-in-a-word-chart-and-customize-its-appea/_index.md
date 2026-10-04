---
category: general
date: 2026-10-04
description: ステップバイステップのJava例で、Word のチャートでスライスを分離する方法、円グラフのスライスを分離する方法、そしてドーナツチャートのサイズを変更する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: ja
lastmod: 2026-10-04
og_description: JavaでWordのチャートのスライスを分離し、円グラフやドーナツグラフをカスタマイズする方法。Wordのチャートを変更する完全な例をご覧ください。
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Word のチャートでスライスを分割表示する方法 – 完全な Java ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Word のチャートでスライスを分離し、外観をカスタマイズする方法
url: /ja/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordチャートでスライスを爆発させて外観をカスタマイズする方法

If you need to **how to explode slice** in a Word chart, this guide shows you exactly how. Whether you’re preparing a sales presentation or a financial report, exploding a pie‑chart slice or adjusting a doughnut hole can make the most important data stand out. In the following sections you’ll also learn how to **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, and **customize pie chart word** documents using Aspose.Words for Java.

> **翻訳:** Wordチャートで**スライスを爆発させる方法**が必要な場合、このガイドが正確に手順を示します。販売プレゼンテーションや財務レポートを作成する際、円グラフのスライスを爆発させたりドーナツの穴を調整したりすることで、最も重要なデータを際立たせることができます。以下のセクションでは、**Wordでチャートを変更する**、**円グラフのスライスを爆発させる**、**ドーナツチャートのサイズを変更する**、そしてAspose.Words for Javaを使用して**円グラフのWord文書をカスタマイズする**方法も学びます。

You’ll finish this tutorial with a complete, ready‑to‑run Java program that loads a `.docx` file, explodes the first slice of a pie chart, changes the doughnut hole size, and saves the result. No external scripts or manual editing are required.

> **翻訳:** このチュートリアルを終えると、`.docx` ファイルを読み込み、円グラフの最初のスライスを爆発させ、ドーナツの穴のサイズを変更し、結果を保存する完全な実行可能な Java プログラムが手に入ります。外部スクリプトや手動編集は不要です。

## 前提条件

- 開発マシンにインストールされた Java 17 以降。  
- 依存関係管理のための Maven 3.6+（または Gradle）。  
- Aspose.Words for Java ライブラリ（無料トライアルは開発に使用可能）。  
- 少なくとも 1 つのチャート（円グラフまたはドーナツ）を含む Word 文書（`input.docx`）。

## Step 1: プロジェクトに Aspose.Words を追加する

If you use Maven, add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

For Gradle, place this in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** ライブラリのバージョンは常に最新に保ちましょう。新しいリリースでは追加のチャートタイプがサポートされ、パフォーマンスが向上します。

## Step 2: チャートを含む Word 文書を読み込む

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** ドキュメントを読み込むことで、Aspose.Words が走査できるメモリ内表現が作成されます。このオブジェクトがなければ、チャートノードにアクセスできません。

## Step 3: ドキュメント内の最初のチャートを取得する

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` はチャートを含むすべての描画オブジェクトを対象とします。`true` 引数は Aspose に再帰的に検索させ、テーブル内にネストされていても最初のチャートが見つかるようにします。

## Step 4: 円グラフの最初のスライスを爆発させる

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** `setExplosion` メソッドは、スライスが中心からどれだけ離れるかを決定する数値を受け取ります。`20` の値は、チャートのレイアウトを崩さずに視覚的に目立ちます。

## Step 5: ドーナツチャートのドーナツ穴サイズを調整する

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** データポイントが多数ある場合、ドーナツ穴を大きくすると可読性が向上します。`setDoughnutHoleSize` メソッドはパーセンテージ（0‑100）を受け取ります。

## Step 6: 変更されたドキュメントを保存する

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### 期待される出力

- 最初の円グラフの最初のスライスが外側にオフセットされ、目立つようになります。
- チャートがドーナツの場合、中心の穴がチャート半径の 40 % に拡大されます。
- 生成されたファイル `PieChart.docx` は Microsoft Word、LibreOffice、または任意の互換ビューアで開くことができ、プログラムで適用した視覚的変更が表示されます。

## 完全な実行可能サンプル

Below is the entire program in one block. Copy it into `ChartExploder.java`, adjust the file paths, and run it with `mvn compile exec:java` (or your IDE’s run configuration).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Running this code will **modify chart in Word**, **explode pie chart slice**, and **change doughnut chart size** automatically.

> **翻訳:** このコードを実行すると、**Wordでチャートを変更する**、**円グラフのスライスを爆発させる**、そして**ドーナツチャートのサイズを変更する** が自動的に行われます。

## よくある質問とエッジケース

| Question | Answer |
|----------|--------|
| *What if the document contains multiple charts?* | The sample targets the **first** chart (`NodeType.SHAPE, 0`). To work with other charts, change the index or iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter by `shape.getChart() != null`. |
| *Can I explode a slice other than the first one?* | Yes. Access the desired series via `chart.getSeries().get(seriesIndex)` and call `setExplosion(value)`. Indexes are zero‑based. |
| *Does this work with Word 2007‑2021 files?* | Aspose.Words supports `.doc`, `.docx`, `.dot`, and `.dotx`. The same code works across versions because the library abstracts the file format. |
| *What if the chart is a bar or line chart?* | `setExplosion` and `setDoughnutHoleSize` are only applicable to pie‑type charts. The code safely skips those operations when the chart type differs. |
| *Do I need a license for Aspose.Words?* | A free evaluation license removes the 30‑day limit but adds a watermark. For production, purchase a license to remove the watermark and unlock full functionality. |

> **翻訳:**  
| 質問 | 回答 |
|----------|--------|
| *ドキュメントに複数のチャートが含まれている場合はどうなりますか？* | サンプルは **最初の** チャート (`NodeType.SHAPE, 0`) を対象としています。他のチャートを操作するには、インデックスを変更するか、`doc.getChildNodes(NodeType.SHAPE, true)` を反復処理し、`shape.getChart() != null` でフィルタリングしてください。 |
| *最初のスライス以外を爆発させることはできますか？* | はい。`chart.getSeries().get(seriesIndex)` で目的のシリーズにアクセスし、`setExplosion(value)` を呼び出します。インデックスはゼロベースです。 |
| *この方法は Word 2007‑2021 のファイルでも動作しますか？* | Aspose.Words は `.doc`, `.docx`, `.dot`, `.dotx` をサポートしています。ライブラリがファイル形式を抽象化するため、同じコードがバージョン間で動作します。 |
| *チャートが棒グラフや折れ線グラフの場合はどうなりますか？* | `setExplosion` と `setDoughnutHoleSize` は円グラフ系のチャートにのみ適用可能です。チャートタイプが異なる場合、コードはこれらの操作を安全にスキップします。 |
| *Aspose.Words のライセンスは必要ですか？* | 無料評価ライセンスは 30 日の制限を解除しますが、透かしが追加されます。本番環境では、透かしを除去しフル機能を利用するためにライセンスを購入してください。 |

## 結論

You now know **how to explode slice** in a Word chart, how to **modify chart in Word**, and how to **change doughnut chart size** using Aspose.Words for Java. The complete example demonstrates the full workflow—from loading a document, locating the chart, applying visual tweaks, to saving the result—so you can integrate these steps into any reporting or document‑generation pipeline.

> **翻訳:** これで、Aspose.Words for Java を使用して Word チャートで **スライスを爆発させる方法**、**チャートを変更する方法**、そして **ドーナツチャートのサイズを変更する方法** が分かりました。完全なサンプルは、ドキュメントの読み込み、チャートの検索、視覚的調整の適用、結果の保存というフルワークフローを示しており、任意のレポート作成や文書生成パイプラインにこれらの手順を組み込むことができます。

**Next steps**

- 色の変更、データラベルの追加、またはチャートタイプの切り替え（`chart.setChartType(ChartType.BAR_CLUSTERED)`）など、他のチャートカスタマイズを探求してください。  
- このロジックを Aspose.PDF と組み合わせて、同じレポートの PDF バージョンを生成します。  
- ディレクトリ内のファイルをループ処理して、複数のドキュメントに対してプロセスを自動化します。

Feel free to experiment with different explosion values or doughnut hole percentages to match your design guidelines. Happy coding!

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words for Java を使用した縦棒チャートの作成方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Word 文書でチャート軸を非表示にする方法](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Word 文書にバブルチャートを挿入する方法](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}