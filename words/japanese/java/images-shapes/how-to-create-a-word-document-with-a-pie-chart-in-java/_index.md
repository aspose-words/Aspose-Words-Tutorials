---
category: general
date: 2026-09-18
description: Aspose.Words for Java を使用して Word 文書を作成し、円グラフを挿入する方法を学びます。円グラフの回転や Word
  ファイルの生成手順も含まれます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: ja
lastmod: 2026-09-18
og_description: Java を使用して Word 文書を作成し、円グラフを挿入します。このガイドに従って円グラフを回転させ、スライスを分離し、Word
  ファイルを生成してください。
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: パイチャート付きのWord文書を作成する – ステップバイステップJavaガイド
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Javaで円グラフ付きのWord文書を作成する方法
url: /ja/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで円グラフ付きWord文書を作成する方法

データを視覚化した **Word 文書** を作成する必要がある場合は、Aspose.Words for Java を使った手順をご紹介します。円グラフの挿入、スライスの爆発表示、チャートの回転、そして最終的に **Word ファイルを生成** して Microsoft Word で開く方法を学びます。

テキストとチャートを組み合わせたレポート作成に別途グラフィックツールは不要です。このチュートリアルの最後までに、完全に構成された円グラフを含む .docx ファイルを作成する実行可能なプログラムが完成します。

## 前提条件

- Java 17 以上（コードは Java 8+ でもコンパイル可能）
- 依存関係管理のための Maven または Gradle
- Aspose.Words for Java のライセンス（無料トライアルでも本例は動作します）
- Java の基本的な文法に関する知識

## 手順 1: Maven プロジェクトのセットアップ

新しい Maven プロジェクトを作成し、`pom.xml` に Aspose.Words の依存関係を追加します。

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **プロのコツ:** バージョン番号は常に最新に保ちましょう。新しいリリースではチャートタイプの改善やバグ修正が含まれます。

## 手順 2: 新しい Word 文書を作成する

プログラムで **Word 文書を作成** する最初の操作は、`Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の .docx ファイル全体を表します。

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document` クラスはすべての Word 処理機能へのエントリーポイントです。この時点ではディスクにファイルは書き込まれず、すべて RAM 上で行われます。`save` を呼び出すまでです。

## 手順 3: 円グラフを挿入する方法

`DocumentBuilder` を使って文書にコンテンツを追加します。`insertChart` を使用すると **円グラフ** オブジェクトを直接挿入できます。

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` を指定すると Aspose.Words が円グラフを作成します。サイズはポイント単位で指定します（1 pt ≈ 1/72 in）。この呼び出しの後、チャートは新しい段落に表示されます。

## 手順 4: チャートにデータを設定する

円グラフには値の系列が必要です。ここでは「Apples」「Bananas」「Cherries」の 3 つのカテゴリを追加します。

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add` メソッドは系列を構築し、同時に凡例エントリを自動生成します。このパターンは任意の数値データセットに対して再利用できます。

## 手順 5: 最初のスライスを強調表示する

スライスを爆発させることで特定の値に注目させます。最初のスライス（インデックス 0）は 20 ポイント分爆発させます。

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

系列全体に対して `explode` を設定すると、最初のデータポイントだけがオフセットされます。

## 手順 6: 円グラフを回転させる方法

チャートを回転させると視覚的なバランスが向上します。特に最大のスライスが上部にない場合に有効です。`setRotationAngle` メソッドは角度（度）を受け取ります。

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

45° の回転は開始角度を時計回りにずらし、多くのレイアウトでチャートが読みやすくなります。

## 手順 7: 文書を保存して Word ファイルを生成する

最後に文書をディスクに書き出します。このステップで **Word ファイルを生成** し、Microsoft Word、LibreOffice、または互換ビューアで開くことができます。

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` メソッドは自動的に .docx 拡張子を検出し、Word 互換のパッケージとして書き出します。`output` フォルダーが存在しない場合は、プログラムで作成するか事前に用意してください。

### 期待される出力

プログラム実行後、`output/PieChart.docx` を開くと以下が確認できます。

- 400 × 300 pt の円グラフが 1 ページに表示される
- 「Apples」スライスが 20 pt 外側に爆発表示されている
- チャート全体が時計回りに 45° 回転している
- 3 つのフルーツカテゴリに対応した凡例が表示されている

## よくあるバリエーションとエッジケース

### 複数のチャートを挿入する

複数のチャートが必要な場合は、カーソルを移動させた後に `builder.insertChart` を再度呼び出します。

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### チャートの色を変更する

系列の `getPoints()` コレクションを使ってスライスの色をカスタマイズできます。

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### 大規模データセットの取り扱い

スライスが 10 個以上になるデータセットでは、視認性を保つためにドーナツチャート（`ChartType.DOUGHNUT`）の使用を検討してください。

## 結論

これで **Word 文書の作成**、**円グラフの挿入**、**円グラフの回転**、そして Aspose.Words for Java を使った **Word ファイルの生成** 方法が分かりました。ドキュメントの初期化から最終的なファイル出力までのフルワークフローを示す完全なソリューションです。各ステップの「やり方」だけでなく「なぜそうするのか」も理解できたはずです。

次は、データベースから **円グラフ用データを作成** する方法、データラベルの追加、チャートを画像としてエクスポートする方法などを探求してください。棒グラフ、折れ線グラフ、ドーナツグラフなど、さまざまなチャートタイプを試して Word 自動化ツールキットを拡充しましょう。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、プロジェクトで代替実装を試したりするのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}