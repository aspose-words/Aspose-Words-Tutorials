---
category: general
date: 2026-11-25
description: Javaで円グラフを作成し、Word文書に挿入し、円のスライスを分離してチャートの向きを変更する方法を、分かりやすいコード例とともに学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: ja
lastmod: 2026-11-25
og_description: Javaで円グラフを作成し、文書に円グラフを挿入し、円のスライスを分離し、ステップバイステップのコードでチャートの向きを変更する。
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Javaで円グラフを作成 – 挿入、スライスの分離、回転
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Javaで円グラフを作成し、挿入し、向きをカスタマイズする方法
url: /ja/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで円グラフを作成し、挿入し、向きをカスタマイズする方法

Word 文書内に **円グラフを作成** したい場合、このガイドで手順をすべて解説します。**円グラフの挿入**、強調表示のためのスライスの爆発、そしてシンプルな回転で **チャートの向き変更** を行う方法が分かります。

このチュートリアルでは、Aspose.Words for Java ライブラリのセットアップから、回転・爆発した円グラフを表示する最終的な `.docx` ファイルの生成まで、必要なすべてを網羅しています。外部ドキュメントは不要です。手順に従ってコードを実行するだけです。

## 前提条件

開始する前に、以下を確認してください。

* Java 17 以上がインストールされていること。
* 依存関係管理に Maven または Gradle が使用できること。
* 有効な Aspose.Words for Java ライセンス（または無料評価モード）を用意すること。

`pom.xml`（Maven）または `build.gradle`（Gradle）に Aspose.Words の依存関係を追加します。Maven の例:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** ライブラリのバージョンは常に最新に保ちましょう。執筆時点の最新リリース (24.10) にはチャート描画に関するバグ修正が含まれています。

## 手順 1: 円グラフを作成し、文書に挿入する

最初のステップは **円グラフを作成** し、Word ファイルに埋め込むことです。以下のコードはシンプルな文書を作成し、チャートプレースホルダーを追加して、サイズ 400 × 300 ピクセルの円グラフを挿入します。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**ポイント:** `builder.insertChart` はチャートプレースホルダーを作成し、文書保存時に Aspose.Words が自動的に OOXML チャートに変換します。`ChartType.PIE` 引数により、**円グラフの挿入** 要件を満たす円グラフが描画されます。

## 手順 2: スライスを爆発させてセグメントを強調する

スライスを爆発させると、特定のデータポイントに注目が集まります。次の行は、最初のスライス（インデックス 0）を 10 ポイント分爆発させます。

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

インデックスを変更すれば別のスライスを対象にできますし、爆発距離を調整すれば効果を控えめにできます。スライスの爆発は Aspose.Words で **円グラフのスライスを爆発させる** 標準的な方法です。

## 手順 3: 回転させてチャートの向きを変更する

チャートを回転させると新しい視覚的視点が得られます。`setRotationAngle` を使用して、時計回りに全体を回転させます（角度は度数で指定）。

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

上記の呼び出しは **円グラフの回転** と **チャートの向き変更** の要件を満たします。0 から 360 度までの任意の角度が使用可能です。

## 完全に実行可能なサンプル

すべてをまとめた、円グラフを作成し、スライスを爆発させ、チャートを回転させる自己完結型プログラムです。IDE から、あるいはコマンドラインで `java -cp <classpath> PieChartDemo` と実行してください。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### 期待される出力

* 作業ディレクトリに **CreatePieChartDemo.docx** という名前のファイルが生成されます。
* Microsoft Word でファイルを開くと、400 × 300 ピクセルの円グラフが表示されます。
* 最初のスライス（Q1）が 10 ポイント外側にオフセットされ、**円グラフのスライスを爆発させる** 効果が確認できます。
* チャート全体が 45 度傾いており、**チャートの向き変更** と **円グラフの回転** が実演されています。

## よくあるバリエーションとエッジケース

| 状況 | コードの適応方法 |
|-----------|-----------------------|
| **異なるチャートサイズ** | `insertChart` の `400, 300` 引数を変更します。 |
| **複数シリーズ** | `chart.getSeries()` にさらに `ChartSeries` オブジェクトを追加します。 |
| **別のスライスを爆発させる** | 希望する `sliceIndex` を指定して `setExplode(sliceIndex, distance)` を使用します。 |
| **回転が不要** | `setRotationAngle` の呼び出しを省くか、角度を `0` に設定します。 |
| **DOCX ではなく PDF にエクスポート** | 文書作成後、`doc.save("output.pdf")` を PDF 形式で呼び出します。 |

> **Watch out for:** 負の爆発距離を指定すると `IllegalArgumentException` がスローされます。常に非負の値を提供してください。

## パフォーマンスのヒント

ループ内で多数のチャートを生成する場合、`DocumentBuilder` を 1 つだけ再利用し、各イテレーションで `insertChart` を呼び出すだけにすると、メモリ使用量が削減され処理速度が向上します。

## 結論

これで Aspose.Words for Java を使用して **円グラフを作成**、**円グラフを挿入**、**円グラフのスライスを爆発させる**、そして **円グラフを回転させる** 方法が分かりました。完全なサンプルは、文書の初期化から回転・爆発した円グラフを可視化したファイルの保存まで、フルワークフローを示しています。

次のステップとして、3‑D 効果を適用して **チャートの向き変更** をさらに深めたり、**棒グラフ** や **折れ線グラフ** など他のチャートタイプを試したりすると良いでしょう。同じ API パターンが使えるので、このチュートリアルの拡張は簡単です。

データ、スライスインデックス、回転角度を自由に変更して、独自のレポート要件に合わせ、コミュニティと結果を共有してください！


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}