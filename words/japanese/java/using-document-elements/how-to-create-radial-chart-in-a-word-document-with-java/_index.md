---
category: general
date: 2026-09-18
description: Java を使用して Word 文書に放射状チャートを作成し、チャートのデータラベルを追加し、シリーズ データを挿入する方法を、完全なコード例とともに学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: ja
lastmod: 2026-09-18
og_description: Java を使って Word 文書に放射状チャートを作成し、チャートのデータラベルを追加し、シリーズ データを挿入する単一のチュートリアル。
og_image_alt: Radial chart displayed inside a generated Word document
og_title: JavaでWordに放射状チャートを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: JavaでWord文書にレーダーチャートを作成する方法
url: /ja/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWord文書に放射状チャートを作成する方法

Word文書に放射状チャートを作成する必要がある場合、このガイドでは正確な手順を示します。また、チャートのデータラベルの追加方法やシリーズデータの挿入方法も学び、プレゼンテーション用にチャートを準備できるようになります。

プログラムでチャートを生成すると、手動での書式設定作業が不要になり、レポート全体での一貫性が保証されます。このチュートリアルは、基本的なJavaの知識と、最新バージョンの Aspose.Words for Java ライブラリがインストールされていることを前提としています。

## 必要なもの

* Java 17 以上  
* Aspose.Words for Java（バージョン 23.12 以降）  
* Maven/Gradle の依存関係を解決できる IDE またはビルドツール  

これらの前提条件がインストールされていれば、追加の設定なしでサンプルを実行できます。

## Word文書に放射状チャートを作成する方法

最初のステップは、チャートを配置するための空白のWordファイルを作成することです。空白の文書はクリーンなキャンバスを提供し、意図しないスタイルの適用を防ぎます。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` は .docx ファイル全体を表し、`DocumentBuilder` は段落、表、チャートなどの要素を挿入するためのメソッドを提供します。

## チャートの挿入方法

次に、実際のチャートを挿入します。`insertChart` メソッドはチャートオブジェクトを作成し、ビルダーの現在のカーソル位置に配置します。

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

ポーラーチャートはデータポイントを中心軸の周りに描画し、循環情報の表示に最適です。サイズはポイント単位で表されます（1 pt ≈ 1/72 インチ）。

## チャートにシリーズデータを追加する

シリーズデータのないチャートは空です。シリーズを手動で追加するか、データソースにバインドできます。以下の例では、3 つのデータポイントを持つ単一のシリーズを追加しています。

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` はシリーズ名、カテゴリラベルのリスト、対応する数値のリストを受け取ります。このブロックを繰り返すことで、追加のシリーズ（`addSeriesData`）を追加できます。

## 最初のシリーズにチャートデータラベルを追加する

データラベルを付けることで、ポイントにマウスオーバーしなくてもチャートが読みやすくなります。次の行は最初のシリーズの値ラベルを有効にします。

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

`showValue` を `true` に設定すると、各ポイントの値がチャート上に直接表示されます。同じ `DataLabelFormat` オブジェクトを使用して、カテゴリ名、パーセンテージ、リーダーラインなども有効にできます。

## Wordファイルの保存

チャートの設定が完了したら、ドキュメントをディスクに書き込みます。アプリケーションがアクセスできる場所を選択してください。

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

ファイル `RadialChart.docx` には、データラベル付きの完全に機能する放射状チャートが含まれています。

## 完全な動作例

以下は、コピーしてコンパイルし、実行できる自己完結型のプログラムです。空白のWord文書の作成から、データラベル付き放射状チャートの保存までの完全なワークフローを示しています。

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**期待結果**

Microsoft Word で `output/RadialChart.docx` を開くと、*Quarterly Sales* というタイトルの放射状チャートが表示されます。各ポイントはマーカーの横に数値（例: “15000”）を表示します。

## 一般的なバリエーションとエッジケース

| 状況 | 推奨される変更 |
|-----------|--------------------|
| 別のチャートタイプが必要な場合 | `ChartType.POLAR` を他の任意の `ChartType` 列挙値（例: `ChartType.COLUMN`）に置き換えます。 |
| チャートが外部の Excel 範囲を使用する必要がある場合 | チャート作成後、ワークブックをロードした後に `chart.setDataRange("Sheet1!A1:B5")` を使用します。 |
| 凡例を非表示にしたい場合 | `chart.getLegend().setVisible(false);` |
| 文書を PDF として保存する必要がある場合 | `doc.save("RadialChart.pdf");` を呼び出します – Aspose.Words が自動的にチャートを変換します。 |

これらの調整により、コアロジックはそのままに、出力を特定の要件に合わせて調整できます。

## プロのコツ

* **Reuse the builder** – 同じ文書に複数のチャートを挿入する場合、`builder.insertChart` を繰り返し呼び出すことでビルダーを再利用できます。
* **Performance** – 多数のチャートを生成する際は、`DocumentBuilder` のインスタンスを1つ作成し、再利用することでオブジェクト割り当てのオーバーヘッドを削減できます。
* **Styling** – チャートの外観（色、線の太さ）は `Chart` オブジェクトの `getSeries().get(i).getFormat()` メソッドで制御します。企業のブランディングに合わせるため、これらの設定を試してみてください。

## 結論

これで、Java を使用して Word 文書に放射状チャートを作成し、シリーズデータとチャートデータラベルを追加してファイルを保存する方法が分かりました。完全なサンプルは、追加のシリーズやカスタムスタイル、別の出力形式に対応するよう拡張できます。

外部データソースからの **チャートの挿入方法**、事前定義されたテンプレートを使用した **空白の Word 文書の作成**、データベースから動的に **シリーズデータを追加** するなどの関連トピックを探求してください。さまざまなチャートタイプを試して、データを最も効果的に伝えるビジュアルを見つけましょう。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用した列チャートの作成方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Java で Word 文書を作成 – 影効果付き長方形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [チャートのデータラベルのデフォルトオプションを設定する](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}