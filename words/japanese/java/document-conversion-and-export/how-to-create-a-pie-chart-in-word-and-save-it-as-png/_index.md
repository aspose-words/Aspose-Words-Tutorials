---
category: general
date: 2026-10-07
description: Java を使用して Word で円グラフを作成し、データ系列を追加し、チャートを PNG として保存する方法を学びましょう。手順に沿ったガイドで迅速に結果を得られます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: ja
lastmod: 2026-10-07
og_description: 'Wordで円グラフをすばやく作成: このチュートリアルでは、データ系列の追加、チャートの生成、そして Word のチャートを画像（PNG）として保存する方法を示します。完全なコード例に従ってください。'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Wordで円グラフを作成しPNGとしてエクスポートする – ガイド
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Wordで円グラフを作成し、PNGとして保存する方法
url: /ja/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordで円グラフを作成し、PNGとして保存する方法

Microsoft Word ファイル内に **円グラフ** オブジェクトを作成する必要がある場合、このガイドでは Java を使用して正確に行う方法を示します。また、**データ系列を追加** する方法と **円グラフを PNG として保存** する方法も学び、ビジュアルを Word の外部で再利用できるようにします。

ドキュメント内で直接チャートを生成することで、データを別のグラフィックツールにエクスポートする手間が省けます。このチュートリアルの最後までに、円グラフとそれに対応する PNG 画像がディスク上に保存された、完全に機能する Word ファイルが手に入ります。

## 前提条件

* Java 17 以降がインストールされていること。
* **GroupDocs.Viewer for Java**（または `Document`、`Chart`、`ChartType`、`ImageSaveOptions` クラスを提供する互換ライブラリ）。
* ライブラリ依存関係を追加できる Maven または Gradle プロジェクト。
* コードから参照できるフォルダーに配置された入力 Word ドキュメント（`input.docx`）。

Maven を使用している場合、依存関係を追加してください（`VERSION` は最新リリースに置き換えてください）：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Word で円グラフを作成する方法

このソリューションの核心は次の 3 つの操作に集約されます：

1. ソースの `.docx` ファイルを読み込む。
2. `PIE` タイプの新しい `Chart` オブジェクトに **データ系列を追加** する。
3. **円グラフを PNG として保存** し、Word ドキュメントの隣に画像ファイルを取得する。

以下に各ステップを詳細に説明し、必要な正確な Java コードを示します。

### 手順 1: ソースドキュメントを読み込む

チャートを配置する Word ファイルを開く必要があります。`Document` クラスは `.docx` の内容をメモリに読み込みます。

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters*（なぜ重要か）: ドキュメントを読み込むことで可変モデルが作成されます。その後のすべてのチャート操作はこのメモリ上の表現を変更し、後でディスクに永続化します。

### 手順 2: チャートにデータ系列を追加する

**円グラフ** を作成するには `Chart` インスタンスから始めます。コンストラクタは親 `Document` とチャートタイプ（`ChartType.PIE`）を受け取ります。チャートオブジェクトが作成されたら、数値とオプションのラベルでデータを設定します。

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Why this matters*（なぜ重要か）: `add` メソッドはチャートに **データ系列を追加** します。`values` の各エントリが円のスライスとなり、`categories` が凡例ラベルを提供します。ポイント数に制限はなく、ライブラリが自動的にスライス角度を計算します。

### 手順 3: 円グラフを PNG として保存する

チャートがドキュメントに組み込まれたら、ビジュアル表現をエクスポートできます。基礎となるチャートオブジェクトの `save` メソッドが PNG ファイルをファイルシステムに書き込みます。

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Why this matters*（なぜ重要か）: 円グラフを PNG として保存すると、元の Word ファイルが不要な状態でウェブページ、メール、レポートに埋め込めるラスタ画像が得られます。`ImageSaveOptions` オブジェクトで形式、解像度、その他のエクスポート設定を制御できます。

## Word で円グラフを生成 – 外観のカスタマイズ

基本的な手順に加えて、色、タイトル、データラベルなどをカスタマイズしたくなることがあります。多くのライブラリは `ChartOptions` などのオブジェクトを提供しています。以下はタイトルを追加し、スライスの色を変更する簡単な例です：

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

これらのカスタマイズは任意ですが、ブランドに合わせた **Word で円グラフを生成** できることを示しています。

## Word のチャートを画像として保存 – 代替アプローチ

画像だけが必要で、ドキュメント内にチャートを挿入しない場合は、Word ファイルへのチャートシェイプの挿入を省略し、チャート作成後に直接 `save` メソッドを呼び出すことができます。コードは同じで、チャートを本文に追加するステップを省くだけです。

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

この手法は、バッチ処理で多数のチャートを生成し、PNG 出力だけが必要な場合に便利です。

## 完全に実行可能なサンプル

以下のクラスをプロジェクトにコピーし、ファイルパスを調整して実行してください。プログラムは次のことを行います：

1. `input.docx` を読み込む。
2. **円グラフを作成**し、**データ系列を追加**して、ドキュメントに埋め込む。
3. **円グラフを PNG として保存**（`radial.png`）。
4. 変更された Word ファイルを `output.docx` として永続化する。



## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Java 用 Aspose.Words で縦棒グラフを作成する方法](/words/english/java/document-conversion-and-export/using-charts/)
- [.NET 用 Aspose.Words で Word 散布図チャートを作成する](/words/english/net/working-with-charts/insert-scatter-chart/)
- [.NET 用 Aspose.Words で Word 縦棒グラフを挿入する](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}