---
category: general
date: 2026-09-11
description: Aspose.Words for Java を使用してドーナツ グラフを編集した後、Word 文書を保存します。ドーナツの穴のサイズを変更する方法、ドーナツ
  グラフを回転させる方法、ドーナツ グラフのプロパティを編集する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: ja
lastmod: 2026-09-11
og_description: Aspose.Words for Java を使用してドーナツ グラフを編集した後に Word 文書を保存します。このチュートリアルでは、ドーナツの穴のサイズを変更し、ドーナツ
  グラフを回転させ、グラフの外観をカスタマイズする方法を示します。
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: ドーナツチャートを編集した後に Word 文書を保存する – Java ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Javaでドーナツチャートを編集した後にWord文書を保存する
url: /ja/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでドーナツチャートを編集した後にWord文書を保存する

カスタマイズされたドーナツチャートを含む **Word文書を保存** する必要がある場合、このガイドで具体的な手順を示します。数行のJavaコードでドーナツの穴を変更し、ドーナツチャートを回転させ、結果をディスクに書き戻すことができます。

Aspose.Words for Java を使用した完全な実行可能サンプルと、複数のチャートの処理、ノードタイプの検証、一般的な落とし穴の回避に関するヒントが示されています。外部参照は不要で、必要なものはすべて含まれています。

## 前提条件

- Java 17 以上がインストールされていること
- 依存関係管理に Maven または Gradle を使用すること
- Aspose.Words for Java（バージョン 23.9 以降）をプロジェクトに追加すること  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- 単一のドーナツチャートを含む Word ファイル（`input.docx`）

## 手順 1: Word 文書をロードする

最初のステップはソースファイルを開くことです。このステップは重要で、以降のすべての操作がメモリ上の `Document` オブジェクトで行われるためです。

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **なぜ？** 文書をロードすると DOM 表現が作成され、シェイプ、テーブル、チャートを走査できるようになります。ファイルを開けない場合、Aspose.Words は例外をスローするため、パスが間違っていることがすぐに分かります。

## 手順 2: ドーナツチャートのシェイプを特定する

チャートは `Shape` ノード内に格納されています。チャートを保持する最初のシェイプを取得し、そのレンダラを `Chart` にキャストします。

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **なぜ？** `isChart()` をチェックすることで、チャートの前に画像や他のシェイプがある文書で `ClassCastException` が発生するのを防ぎます。これにより、混在したコンテンツを含む文書でもコードが堅牢になります。

## 手順 3: ドーナツの穴のサイズを変更する  

ここでドーナツの穴を編集します。`setHoleSize` メソッドはチャート半径のパーセンテージ（10 〜 90）を受け取ります。

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **なぜ？** ドーナツの穴（`change doughnut hole` / `change chart hole size`）を変更すると、中心領域を強調または弱調できます。10‑90 % の範囲外の値は API によって無視されます。

## 手順 4: ドーナツチャートを回転する  

最初のスライスの開始位置を制御するには、first‑slice の角度を設定します。これにより実質的に **ドーナツチャートを回転** させます。

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **なぜ？** 特定のスライスを上部に表示したい場合やデザイン仕様に合わせたい場合、チャートを回転させることが有用です。

## 手順 5: 更新された文書を保存する  

最後に、変更を新しいファイルに書き戻します。ここが編集したチャートとともに **Word文書を保存** する瞬間です。

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **期待結果:** `output.docx` は元のコンテンツを保持しますが、ドーナツチャートの穴が 30 % になり、最初のスライスが 45 ° から始まります。Microsoft Word でファイルを開くと、変換されたチャートが表示されます。

## 完全な動作例

以下は IDE にコピー＆ペーストできる完全なプログラムです。**ドーナツチャートを編集** し、**Word文書を安全に保存** するために必要なインポートとエラーハンドリングがすべて含まれています。

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 期待される出力

`output.docx` を開くと:

- ドーナツチャートの中心の穴はチャート半径の約 1/3 を占めます。  
- 最初のスライスは 45 度の位置から始まり、チャート全体が時計回りにシフトします。  

これらの視覚的変更は Word ですぐに反映されます。

## 一般的なバリエーションとエッジケース

| Situation | How to handle |
|-----------|----------------|
| **複数のチャート** | `doc.getChildNodes(NodeType.SHAPE, true)` をイテレートし、`shape.isChart()` でフィルタリングします。各 `Chart` に対して `setHoleSize` / `setFirstSliceAngle` を適用します。 |
| **チャートがドーナツでない場合** | `chart.getType()` を確認し、`chart.getType() == ChartType.DOUGHNUT` の場合にのみ `setHoleSize` を呼び出します。 |
| **穴のサイズを動的に変更する必要がある場合** | データ値に基づいて目的のパーセンテージを計算し、`setHoleSize(computedValue)` を呼びます。 |
| **ストリームに保存する場合** | 使用する |

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用した列チャートの作成方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java を使用して文書を PDF として保存する方法](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java を使用したパスワード付き Word の保存](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}