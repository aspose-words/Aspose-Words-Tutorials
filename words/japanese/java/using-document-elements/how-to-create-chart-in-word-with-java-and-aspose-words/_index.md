---
category: general
date: 2026-09-24
description: Java を使用して Word でチャートを作成し、放射状チャートを挿入し、Aspose.Words でドキュメントを docx として保存する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: ja
lastmod: 2026-09-24
og_description: Java と Aspose.Words を使用して Word にチャートを作成します。このチュートリアルでは、放射状チャートを追加し、データをカスタマイズし、ドキュメントを
  docx として保存する方法を示します。
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: JavaでWordにチャートを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Java と Aspose.Words を使用して Word でチャートを作成する方法
url: /ja/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java と Aspose.Words を使用して Word にチャートを作成する方法

Java アプリケーションから **Word にチャートを作成** したい場合、このガイドはプロセス全体を順を追って説明します。ラジアルチャートの追加方法、オプションでシリーズにデータを設定する方法、そして Aspose.Words for Java ライブラリを使用して **docx として文書を保存** する手順を確認できます。

Word ファイル内に視覚的なデータを生成することは、レポート作成、請求書作成、または自動文書生成などで一般的な要件です。このチュートリアルを終える頃には、**Java で Word 文書を作成** し、**Word にチャートを追加** できるようになります。

## 前提条件

開始する前に、以下を用意してください。

* Java Development Kit (JDK) 8 以上
* 依存関係管理のための Maven または Gradle
* IntelliJ IDEA、Eclipse、または VS Code などの IDE
* 有効な Aspose.Words for Java ライセンス（開発用には無料トライアルで可）

これらのツールが、以降のコード例の基盤となります。

## 手順 1: Maven プロジェクトの設定

新規 Maven プロジェクトを作成（または既存プロジェクトを更新）し、`pom.xml` に Aspose.Words の依存関係を追加します。

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean install` を実行するとライブラリがダウンロードされ、`Document`、`DocumentBuilder`、`ChartType` などのクラスがクラスパスに利用可能になります。

> **プロのヒント:** ライブラリのバージョンは常に最新に保ちましょう。新しいリリースではチャートタイプが追加され、レンダリング性能が向上します。

## 手順 2: 新しい Word 文書を作成

**Word にチャートを作成** する最初のプログラム的ステップは、空の `Document` をインスタンス化することです。このオブジェクトは `.docx` パッケージ全体を表します。

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` はカーソルのように機能し、現在の挿入位置を把握しながらテキスト、テーブル、チャート用のメソッドを提供します。この時点で **Java で Word 文書を作成** した状態—コンテンツを追加できるクリーンなキャンバス—が得られます。

## 手順 3: ラジアルチャートを挿入

Aspose.Words は多数のチャートタイプをサポートしています。**ラジアルチャートを挿入** するには、`ChartType.RADIAL` を指定して `insertChart` を呼び出します。メソッドには幅と高さ（ポイント単位、1 ポイント ≈ 1/72 インチ）も必要です。

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

返される `Shape` オブジェクトは内部のチャートオブジェクトを保持しています。チャートは自動的に 24.9° のレイアウトで目盛りを描画し、これは Word のラジアルチャートのデフォルトです。

### なぜラジアルチャートを使うのか？

ラジアルチャートはデータを円周上に配置して可視化するため、周期的なパターン（例: 月次売上、時計フェイスの指標）を示すのに最適です。同じ API で棒グラフ、円グラフ、折れ線グラフも挿入できますが、ラジアルタイプは余分なスタイリングコードなしで独特の外観を提供します。

## 手順 4: (オプション) チャートのシリーズデータを設定

チャートに実際の数値を表示させるには、シリーズとデータポイントを追加する必要があります。以下のスニペットは 3 つのデータポイントを持つ単一シリーズを追加します。

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

必要に応じて `add` 呼び出しを繰り返し、任意の数のポイントを設定できます。Aspose.Words は自動的にビジュアルを更新するため、ラジアルスライスが新しい値に合わせて変化します。

> **よくある質問:** *データベースからバインドしたい場合はどうすればいいですか？*  
> 行を取得し、ループで `series.getDataPoints().add(value, label)` を呼び出します。API はスレッドセーフで、任意の `ResultSet` と組み合わせて使用できます。

## 手順 5: DOCX として文書を保存

チャートの準備ができたら、最後のステップは **docx として文書を保存** することです。`save` メソッドはファイル拡張子から出力形式を判断します。

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

生成されたファイルは完全に機能するラジアルチャートを含み、Microsoft Word、LibreOffice、または DOCX をサポートする任意のビューアで開くことができます。拡張子が `.docx` であるため、Word はファイルを Open XML 形式で保存し、これは Word 文書の最新標準です。

### 結果の確認

Word で `RadialChartDemo.docx` を開きます:

1. 中央にラジアルチャートが配置された単一ページが表示されます。  
2. シリーズデータを追加した場合、チャートは Q1‑Q4 とラベル付けされた 4 つのスライスを表示します。  
3. チャートを右クリック → **Edit Data** で基になるデータテーブルを確認できます。

チャートが空白の場合は、`chart.getChart()` を呼び出してからシリーズを追加したか、DocumentBuilder のカーソルがチャートを挿入したい位置にあるかを再確認してください。

## 手順 6: チャート操作の高度なヒント

| ヒント | 重要な理由 |
|-----|----------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | 各要素を手動で書式設定する手間を省き、視覚的一貫性を向上させます。 |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | ページレイアウトに合わせてチャートサイズを微調整できます。 |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | 文書本文がなくても読者にコンテキストを提供します。 |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | 配布用の編集不可バージョンが必要なときに便利です。 |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | 本番ビルドで評価版の透かしが表示されるのを防ぎます。 |

これらの拡張は任意ですが、**Word にチャートを追加** した後にさらにカスタマイズできることを示しています。

## 結論

これで、Java を使用して **Word にチャートを作成** し、**ラジアルチャートを挿入**、必要に応じてデータを設定し、**docx として文書を保存** する完全なサンプルが完成しました。同じパターンは他のチャートタイプでも機能するため、棒グラフ、折れ線グラフ、円グラフなどにも簡単に拡張できます。

次に検討できること:

* **Java で Word 文書を作成** し、テーブル、画像、複数のチャートを組み合わせるプロジェクト  
* **docx と pdf の両方で保存** してマルチフォーマットレポートを実現  
* REST API やデータベースから動的にデータを取得し、チャートに反映させる

スタイリングオプション、チャートサイズ、データソースを自由に試してみてください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、ステップバイステップの説明と完全なコード例が含まれており、API の追加機能を習得したり、代替実装アプローチを探求したりするのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}