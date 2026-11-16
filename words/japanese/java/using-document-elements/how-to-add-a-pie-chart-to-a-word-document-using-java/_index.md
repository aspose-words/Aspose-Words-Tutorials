---
category: general
date: 2026-11-15
description: Aspose.Words for Java を使用して Word 文書に円グラフを追加する方法を学びましょう。ドーナツ変換、分割スライス、完全なコードサンプルが含まれています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: ja
lastmod: 2026-11-15
og_description: Aspose.Words for Java を使用して Word 文書に円グラフを追加します。このチュートリアルでは、スライスを分離（エクスプロード）する方法と、グラフをドーナツ形に変換する方法を示します。
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: JavaでWord文書に円グラフを追加する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Java を使用して Word 文書に円グラフを追加する方法
url: /ja/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word文書に円グラフを追加する – 完全なJavaガイド

プログラムで **Word文書に円グラフを追加** する必要がある場合、このチュートリアルでは Aspose.Words for Java を使用して具体的な手順を示します。DOCX の読み込み、円グラフの作成、最初のスライスの分離、そして穴のサイズを設定してドーナツグラフに変換するという全工程を確認できます。

このガイドでは、複数シリーズの追加、色のカスタマイズ、既にグラフが含まれている文書の処理など、一般的なバリエーションも取り上げています。自動レポート作成や動的プレゼンテーションなど、実務プロジェクトにコードを適用できるようになります。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17 以上（コードは JDK 11+ でもコンパイル可能です）
* Maven 3.6+ または Gradle（依存関係管理用）
* Aspose.Words for Java のライセンス（無料トライアルでテスト可能）
* Java の基本構文と Maven プロジェクト構造の理解

## 手順 1: Maven プロジェクトを設定し Aspose.Words をインポート

新しい Maven プロジェクトを作成（または既存プロジェクトに追加）し、Aspose.Words の依存関係を追加します。

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **プロのコツ:** Gradle を使用する場合、同等のエントリは `implementation 'com.aspose:aspose-words:24.9'` です。

この依存関係により、`Document`、`Chart`、`ChartType` クラスが利用可能になり、グラフの操作が行えます。

## 手順 2: 対象文書を読み込む

既存の `.docx` ファイルから開始するか、空の新規文書を作成できます。以下の例は、`src/main/resources` フォルダーにある `input.docx` というテンプレートを読み込みます。

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

ファイルが存在しない場合、`new Document()` をファイル名なしで呼び出すと Aspose.Words が自動的に空の文書を作成します。

## 手順 3: 円グラフを作成し文書に挿入

Aspose.Words ではグラフは段落が配置できる場所ならどこでも配置可能なシェイプとして扱われます。以下のコードは **円グラフ** を作成し、単一のデータシリーズを追加し、最初の段落の後にグラフを挿入します。

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**この手順が重要な理由:**  
* `ChartType.PIE` は Aspose.Words に従来の円グラフを描画させます。  
* カテゴリラベルと数値を両方持つシリーズを追加することで、スライスが自動的に生成されます。  
* `Paragraph` の子要素としてグラフを挿入することで、文書のフローが保たれます。

## 手順 4: 最初のスライスを分離して強調表示

*分離スライス* は特定のデータポイントに注目させるために使用します。API は `ChartSeries` オブジェクトの `setExplode(boolean)` を提供しています。最初のシリーズ（インデックス 0）に対して設定すると、最初のスライスが突出します。

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **よくある質問:** *複数のシリーズがある場合はどうすればよいですか？*  
> インデックスで特定のシリーズを指定できます。例: `pieChart.getSeries().get(1).setExplode(true)` は 2 番目のシリーズを分離します。

## 手順 5: 穴のサイズを設定して円グラフをドーナツに変換

ドーナツグラフは、中心が空洞になった円グラフです。Aspose.Words では、穴のサイズをグラフ半径のパーセンテージで指定できます。

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize` メソッドは **0**（通常の円）から **100**（完全に空）までの値を受け取ります。**30‑40** 前後の値が視覚的にバランスの取れたドーナツになります。

## 手順 6: 保存して結果を確認

すべての変更が完了したら文書を保存します。以下の行は `output` フォルダーにファイルを書き出します。

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### 期待される出力

Microsoft Word で `final-pie-doughnut.docx` を開くと:

* 最初の段落の位置にドーナツグラフが表示されます。  
* 「Apples」スライスが分離され（他のスライスから少し離れています）。  
* グラフには *Apples*、*Bananas*、*Cherries*、*Dates* の 4 つのスライスがラベル付きで、指定した割合が表示されます。

PDF 出力が必要な場合は、`SaveFormat` を `SaveFormat.PDF` に変更してください。

## エッジケースとバリエーションの処理

### 複数シリーズの追加

スタックドーナツなど、複数シリーズが必要な場合は順次追加します。

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### カスタムカラー

`ChartDataPoint.setFillFormat().setSolidFillColor()` を使用して、各スライスに色を割り当てられます。

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### 既存のグラフを操作する

文書にすでにグラフが含まれていてそれだけを変更したい場合は、グラフシェイプを検索します。

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### ライセンスの取り扱い

Aspose.Words は本番環境での使用にライセンスが必要です。`Aspose.Words.lic` ファイルをクラスパスに配置し、アプリケーション起動時にロードしてください。

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

ライセンスを設定しないと、生成された文書に透かしが付加されます。

## 完全な実行可能サンプル

以下は、ここまで説明したすべての手順を組み込んだ完全な Java クラスです。`src/main/java/com/example/AddPieChart.java` にコピーし、`mvn compile exec:java` で実行してください。

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

プログラムを実行すると、前述のドーナツグラフが生成されます。`categories`、`values`、`holeSize` をデータに合わせて調整してください。

## 結論

これで Java と Aspose.Words を使用して **Word文書に円グラフを追加** する方法が分かりました。チュートリアルでは、文書の読み込み、円グラフの作成、スライスの分離、ドーナツへの変換、そして複数シリーズやカスタムカラー、既存グラフの操作といった一般的なバリエーションの扱い方を網羅しました。この基礎を活かして、自動レポートツールの構築や動的プレゼンテーションの生成、Word ファイルへのリッチな可視化埋め込みが可能になります。

### 次に探求すべきこと

* **add bar chart to Word document** – 同様の手順で `ChartType.BAR` を使用  
* **customize chart legends and titles** – `pieChart.getTitle().setText("...")` と `pieChart.getLegend().setPosition(LegendPosition.RIGHT)` を活用  
* **export the Word document as PDF** – 配布用ファイルとして `SaveFormat` を `PDF` に変更  
* **populate chart data from a database** – 静的配列の代わりに JDBC クエリ結果を使用  

さまざまなグラフタイプ、データソース、スタイリングオプションを試してみてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの説明と完全なコード例が含まれており、API の追加機能を習得したり、代替実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}