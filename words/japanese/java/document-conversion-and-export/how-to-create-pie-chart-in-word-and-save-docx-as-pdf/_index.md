---
category: general
date: 2026-11-15
description: Java を使用して Word 文書に円グラフを作成し、docx を PDF に保存する方法を学びます。このガイドでは、Word を PDF
  に変換する方法や、グラフの追加方法も取り上げています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: ja
lastmod: 2026-11-15
og_description: JavaでWordファイルに円グラフを作成し、docxをPDFとして保存します。WordをPDFに変換し、グラフを追加する手順をステップバイステップでご紹介します。
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Wordで円グラフを作成し、docxをPDFとして保存する – Javaガイド
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Wordで円グラフを作成し、docxをPDFとして保存する方法
url: /ja/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordで円グラフを作成し、docxをPDFとして保存する方法

If you need to **create pie chart** inside a Word document and then **save docx as PDF**, this tutorial shows you exactly how. You’ll see a complete, runnable example that converts a .docx file to a PDF while embedding a pie chart, so you can answer “how to add chart” without hunting for scattered snippets.

Word文書内に **create pie chart** を作成し、さらに **save docx as PDF** したい場合、このチュートリアルで具体的な手順を示します。.docx ファイルを PDF に変換しながら円グラフを埋め込む完全な実行可能サンプルが見られるので、散在するコードを探すことなく “how to add chart” に答えることができます。

In this guide you’ll learn to:

* Load an existing *.docx* (or start from scratch)  
* Use Aspose.Words for Java to **create pie chart** and populate data  
* **Save docx as PDF** with the chart rendered correctly  
* Understand the nuances of **convert word to pdf** when charts are involved  

このガイドで学べること:

* 既存の *.docx* を読み込む（または最初から作成する）  
* Aspose.Words for Java を使用して **create pie chart** を作成し、データを入力する  
* **Save docx as PDF** を使用して、チャートが正しくレンダリングされた状態で保存する  
* チャートが含まれる場合の **convert word to pdf** の微妙な点を理解する  

The steps work with Aspose.Words 2024‑x.x and Java 17, but the concepts apply to any library that supports Word chart manipulation.

手順は Aspose.Words 2024‑x.x と Java 17 で動作しますが、概念は Word のチャート操作をサポートする任意のライブラリにも適用できます。

## 前提条件

| 要件 | 重要な理由 |
|------|------------|
| Java 17 (or later) | 最新の Aspose.Words JAR が必要です |
| Maven or Gradle build tool | 依存関係の管理を簡素化します |
| Aspose.Words for Java (latest version) | `Document`、`Chart`、`ChartType` クラスを提供します |
| An input **.docx** file (or a blank document) | チャートはこのファイルに挿入されます |

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

Maven の `pom.xml` または Gradle の `build.gradle` に Aspose.Words の依存関係を追加します。Maven の例:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 手順 1: Word 文書を読み込む（または新規作成）

The first action is to obtain a `Document` instance. If you already have a template, pass its path; otherwise create an empty document.

最初の操作は `Document` インスタンスを取得することです。テンプレートがある場合はそのパスを渡し、ない場合は空のドキュメントを作成します。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* The `Document` object is the container for all Word content, including charts. Loading an existing file lets you preserve surrounding text and styles while adding a new visual element.

*Why this step?* `Document` オブジェクトはチャートを含むすべての Word コンテンツのコンテナです。既存ファイルを読み込むことで、周囲のテキストやスタイルを保持しつつ新しいビジュアル要素を追加できます。

## 手順 2: **Create pie chart** – “how to create chart” の核心

Now we instantiate a `Chart` object with `ChartType.PIE`. This automatically creates a pie chart placeholder that you can later fill with data.

ここで `ChartType.PIE` を指定して `Chart` オブジェクトをインスタンス化します。これにより、後でデータを入れられる円グラフのプレースホルダーが自動的に作成されます。

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` tells Aspose.Words to use a pie‑chart template. The chart is added to the document’s body, so it appears where you need it. This satisfies the “how to add chart” requirement in a single call.

*Explanation*: `ChartType.PIE` は Aspose.Words に円グラフのテンプレートを使用させます。チャートは文書の本文に追加されるため、必要な場所に表示されます。これにより「how to add chart」の要件が一度の呼び出しで満たされます。

## 手順 3: チャートにデータを設定 – “how to add chart” にデータで回答

A pie chart is meaningless without series data. Use the `Series` collection to add categories and values.

円グラフはシリーズデータがなければ意味がありません。`Series` コレクションを使用してカテゴリと値を追加します。

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: Each call to `add` creates a slice of the pie. The first argument is the label, the second is the numeric value. You can replace these with dynamic data from a database or CSV file.

*Why this matters*: `add` の呼び出しごとに円のスライスが作成されます。第1引数がラベル、第2引数が数値です。これらはデータベースや CSV ファイルから取得した動的データに置き換えられます。

### オプション: 外観のカスタマイズ（必須ではないが便利）

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

These tweaks illustrate how you can **how to create chart** with a professional look, without leaving the Java code.

これらの調整により、Java コードから離れることなく **how to create chart** をプロフェッショナルな外観で実現できることが示されています。

## 手順 4: **Save docx as PDF** – “convert word to pdf” の最終ステップ

Once the chart is embedded, export the document to PDF. Aspose.Words renders the chart as a vector graphic, preserving quality.

チャートが埋め込まれたら、文書を PDF にエクスポートします。Aspose.Words はチャートをベクターグラフィックとして描画し、品質を保持します。

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: The `save` method automatically converts the Word file to PDF, handling chart rasterization, font embedding, and page layout. This fulfills the **save docx as pdf** goal and demonstrates a reliable way to **convert word to pdf** when charts are present.

*Key point*: `save` メソッドは Word ファイルを自動的に PDF に変換し、チャートのラスタライズ、フォント埋め込み、ページレイアウトを処理します。これにより **save docx as pdf** の目的が達成され、チャートが含まれる場合の **convert word to pdf** の信頼できる方法が示されます。

### 期待される出力

Running the program produces `output.pdf` that contains:

プログラムを実行すると `output.pdf` が生成され、以下が含まれます:

* The original content of `input.docx` (if any)  
* A fully rendered pie chart titled *Sales Distribution Q1*  
* Accurate slice percentages matching the data (40 %, 30 %, 30 %)

* `input.docx` の元のコンテンツ（存在する場合）  
* *Sales Distribution Q1* というタイトルの完全にレンダリングされた円グラフ  
* データに一致した正確なスライス割合（40 %、30 %、30 %）

## よくある落とし穴と回避策

| 問題点 | 原因 | 対策 |
|--------|------|------|
| PDF でチャートが空白になる | フォントまたはチャート描画設定が不足している | 最新の Aspose.Words バージョンを使用してください。必要な描画ライブラリが同梱されています。 |
| データ値が不正確に丸められる | 大きな整数値を使用している | `double` 値を使用するか、シリーズに追加する前に数値をスケーリングしてください。 |
| 出力 PDF が巨大になる | 画像が高 DPI で埋め込まれている | 画像も埋め込む場合は `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` を設定してください。 |
| “convert word to pdf” が `UnsupportedOperationException` をスロー | Java バージョンが古い（< 11） | Java 17 以降にアップグレードしてください。Aspose.Words 24.x はそれを必要とします。 |

## プロのコツ: チャート作成ロジックの再利用

If you need to add multiple charts to the same document, extract the chart‑building code into a helper method:

同じ文書に複数のチャートを追加する必要がある場合は、チャート作成コードをヘルパーメソッドに抽出します:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Now you can call `doc.getFirstSection().getBody().appendChild(createPieChart(...));` for each dataset, keeping your code DRY (Don’t Repeat Yourself).

これで各データセットに対して `doc.getFirstSection().getBody().appendChild(createPieChart(...));` を呼び出せるようになり、コードを DRY（Don't Repeat Yourself）に保てます。

## 結論

You now know how to **create pie chart** inside a Word document, populate it with data, and **save docx as PDF** using Java. This end‑to‑end example covers the entire **convert word to pdf** workflow, answers **how to add chart**, and demonstrates **how to create chart** programmatically.

これで、Java を使って Word 文書内に **create pie chart** を作成し、データを入力し、**save docx as PDF** する方法が分かりました。このエンドツーエンドの例は、**convert word to pdf** の全工程を網羅し、**how to add chart** に答え、**how to create chart** をプログラムで実装する方法を示しています。

From here you might explore:

ここからは以下を検討できます:

* Adding bar or line charts (`ChartType.BAR`, `ChartType.LINE`) – another **how to create chart** scenario.  
* Exporting to other formats such as PNG or HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamically generating the input document with tables or placeholders before inserting charts.

* バーやラインチャートの追加（`ChartType.BAR`、`ChartType.LINE`） – 別の **how to create chart** シナリオ  
* PNG や HTML など他の形式へのエクスポート（`SaveFormat.PNG`、`SaveFormat.HTML`）  
* チャートを挿入する前に、テーブルやプレースホルダーで入力ドキュメントを動的に生成する

Feel free to experiment with different data sets, styling options, or even embedding multiple charts per page. Happy coding!

さまざまなデータセットやスタイリングオプション、ページごとの複数チャート埋め込みなどを自由に試してみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説付きの完全なコード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Java を使用して Word 文書に円グラフを挿入する方法](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Java で Word を PDF に保存し、アクセシブル PDF を作成する方法](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Java と Aspose.Words を使用して Word にチャートを作成する方法](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}