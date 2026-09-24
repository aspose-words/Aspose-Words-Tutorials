---
category: general
date: 2026-09-24
description: Aspose.Words for Java を使用して DOCX に円グラフを挿入します。穴のサイズ設定、円グラフのスライスを分離、スライスをハイライトし、簡単に
  DOCX チャートを作成する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: ja
lastmod: 2026-09-24
og_description: Aspose.Words for Java を使用して DOCX に円グラフを挿入します。穴のサイズ設定、円グラフのスライスの分離、スライスのハイライトをマスターし、数分で
  DOCX のチャートを作成できます。
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Javaで円グラフの文字を挿入する – ステップバイステップチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Javaで円グラフを挿入する – 完全ガイド
url: /ja/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでpie chart wordを挿入する完全ガイド

DOCXファイルに**insert pie chart word**を挿入する必要がある場合、このチュートリアルではAspose.Words for Javaを使用してその手順を正確に示します。ドキュメントの作成から、スライスを爆発させ、ホールサイズを0に設定し、スライスをハイライトするまでの全作業フローを確認できます。

Word文書でのチャート操作は通常のテキスト処理とは別の課題のように感じられますが、Aspose.Wordsは両方を統合します。以下の手順では、**create docx chart** ファイルを作成し、Microsoft Word、Google Docs、またはその他のDOCX対応ビューアで開ける方法も学べます。

## 達成できること

* **Insert pie chart word** を空白のドキュメントに挿入
* **Set hole size** を設定してチャートをフルパイ（ドーナツなし）にする
* **Explode pie slice** で特定のセグメントに注目させる
* **Highlight pie chart slice** をカスタム書式でハイライト
* **Create docx chart** を作成し、共有またはさらに編集できる

### 前提条件

* Java 17以降（コードはJava 8でもコンパイル可能）
* Aspose.Words for Java ライブラリ（バージョン 23.9以降）
* Aspose.Words の依存関係を解決できるIDEまたはビルドツール（Maven/Gradle）

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Aspose.Wordsを使用してDOCXにpie chart wordを挿入する方法

最初のステップは新しい空白のドキュメントを作成し、`DocumentBuilder` を取得することです。ビルダーはドキュメントのコンテンツストリームへの直接アクセスを提供し、**insert pie chart word** を簡単に行えます。

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### なぜ重要か
`Document` はWordファイル全体を表し、`DocumentBuilder` は段落、テーブル、チャートを低レベルのXMLを扱わずに挿入できる高レベルAPIです。クリーンなドキュメントから開始することで、追加したチャートが唯一のコンテンツとなり、学習やテンプレートベースのレポート生成に最適です。

## フルパイを作成するためにホールサイズを設定

デフォルトでは、pie chartを要求するとAspose.Wordsはドーナツチャートを作成します。チャートを真の円にするには、**set hole size** を `0` に設定する必要があります。これにより内部の穴が除去され、従来のパイチャートが得られます。

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### 実用的なヒント
後でドーナツチャートに切り替える場合は、`holeSize` の値をパーセンテージ（例：`30`）に変更するだけです。同じAPIが両方のチャートタイプで機能します。

## セグメントをハイライトするためにpie sliceを爆発させる

スライスを爆発させると視覚的に目立ちます。**explode pie slice** 操作は、選択したスライスをチャート半径のパーセンテージ分外側へ移動させます。

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### なぜexplodeするのか
爆発したスライスは読者の目を最も重要なデータポイントに引き付けます—ダッシュボードやエグゼクティブサマリーに最適です。値 `20` は半径の20 %を意味し、`0`（爆発なし）から`100`（完全に分離）まで調整可能です。

## カスタム書式でpie chart sliceをハイライト

爆発に加えて、塗りつぶし色や枠線を変更して**highlight pie chart slice**したい場合があります。デモコードは爆発に焦点を当てていますが、以下のように拡張できます：

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### エキスパートノート
特定のスライスの塗りつぶし色を変更するには `DataPoint` オブジェクトにアクセスする必要があります。複数のシリーズがある場合は、`series.getDataPoints()` を反復し、条件に応じてスタイルを適用してください。

## 作成したdocx chartを保存して検証

最後に、`Document` を保存して **create docx chart** を行います。生成されたファイルはMicrosoft Wordで開き、書式設定された円グラフを確認できます。

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### 期待される出力
`PieChartFormatted.docx` を開くと単一の円グラフが表示されます：

* チャートは 400 × 300 pt の領域を占めます。  
* ホールサイズは `0` で、チャートはフルパイです。  
* 最初のスライスは 20 % 爆発し、赤色に設定されています（オプションの書式設定を追加した場合）。  

これで、配布やメールへの埋め込み、プログラムによるさらなる編集が可能な **create docx chart** が完成しました。

---

## 一般的なバリエーションとエッジケース

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | `pieChart.getChart().getSeries()` をループし、シリーズごとに `Explosion` または `FillColor` を設定します。 |
| **Dynamic data** | `setExplosion` を呼び出す前に、データベースやCSVから取得した値でシリーズを埋めます。 |
| **Different chart size** | `insertChart(ChartType.PIE, width, height)` の幅/高さ引数を変更します。 |
| **Export to PDF** | DOCXを保存した後、`doc.save("output.pdf")` を呼び出して同じチャートのPDF版を生成します。 |
| **Localization** | ラベルにロケール固有の数値形式を使用して `DocumentBuilder.insertChart` を利用します。 |

### プロのコツ
`insertChart` の **後** に必ず `setHoleSize(0)` を呼び出してください。挿入前に設定すると、チャート作成時にAspose.Wordsがデフォルトのドーナツサイズに戻ります。

---

## まとめ

これで、Javaを使用してWord文書に **insert pie chart word** を挿入する方法、フルパイ表示のために **set hole size** を設定する方法、注目させるために **explode pie slice** を行う方法、カスタムカラーで **highlight pie chart slice** する方法が分かりました。完全なサンプルは、配布可能な **create docx chart** ファイルの作成方法も示しています。

---

## 次のステップ

* `ChartType` を使用して他のチャートタイプ（`BAR`、`LINE`、`SCATTER`）を調査する。  
* チャート生成とメールマージを組み合わせて、パーソナライズされたレポートを作成する。  
* 生成したDOCXをオンデマンドでファイルを返すWebサービスに統合する。  

問題が発生した場合は、使用しているAspose.Wordsのバージョンが互換性があるか、出力ディレクトリが存在し書き込み可能かを確認してください。

コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加のAPI機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Java 用 Aspose.Words でカラムチャートを作成する方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Word Chart API の使用](/words/english/net/programming-with-charts/)
- [Aspose.Words for .NET を使用して Word にバブルチャートを挿入する](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}