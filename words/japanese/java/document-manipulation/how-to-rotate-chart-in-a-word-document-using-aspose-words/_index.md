---
category: general
date: 2026-10-10
description: Word ファイル内のグラフを回転させる方法と、Word でドーナツ グラフのサイズを変更する方法を、完全な Java のサンプルで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: ja
lastmod: 2026-10-10
og_description: Aspose.Words for Java を使用して、Word ファイル内のチャートを回転させ、ドーナツチャートのサイズを変更する方法。
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Word文書内のチャートを回転させる方法 – ステップバイステップ Java ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words を使用して Word 文書内のチャートを回転させる方法
url: /ja/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して Word 文書内のチャートを回転させる方法

Microsoft Word ファイル内で **チャートを回転させる方法** が必要な場合、このガイドでは正確な手順を示します。また、Java コードから離れることなく **Word のチャートを変更してドーナツチャートのサイズを変更する方法** も学べます。

Word の自動化はしばしば切れ目のある API 呼び出しの連続に感じられますが、Aspose.Words を使えばチャートを他の文書ノードと同様に扱えます。このチュートリアルの最後までに、既存の `.docx` を読み込み、ドーナツチャートを 45° 回転させ、穴の半径を 50 % に縮小し、結果を新しいファイルとして保存する実行可能なプログラムが完成します。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17 以上がインストールされていること。
* 依存関係管理のための Maven（または Gradle）。
* すでにドーナツチャートが含まれている入力 Word 文書（`input.docx`）。
* 有効な Aspose.Words for Java ライセンス（または評価モード）。

## 手順 1: Maven プロジェクトのセットアップ

新しい Maven プロジェクトを作成するか、既存の `pom.xml` に以下の依存関係を追加してください。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

`mvn clean install` を実行するとライブラリがダウンロードされ、クラスがクラスパスに利用可能になります。

## 手順 2: チャートを含む Word 文書を読み込む

最初の操作は既存の文書を開くことです。`Document` クラスはファイル全体を表します。

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

ファイルの読み込みは **変更を加えません**。単にメモリ上に表現を作成し、クエリや編集が可能になります。

## 手順 3: ナビゲーション用に DocumentBuilder を作成

`DocumentBuilder` はカーソルのような API を提供し、文書ツリーを歩き回れます。ここでは最初のチャートシェイプを見つけるために使用します。

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ビルダーは文書の先頭から開始しますが、必要に応じて後で任意のノードへ移動できます。

## 手順 4: 最初のチャートシェイプを取得

チャートは `Shape` ノードとして格納されています。`NodeType.SHAPE` 型の子ノードをフィルタリングすることでチャートオブジェクトを抽出できます。

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

文書に複数のチャートがある場合は、`getChildNodes` を反復処理し、各 `Shape` の `hasChart()` を確認してからキャストしてください。

## 手順 5: チャートを回転させる（チャートを回転させる方法）

ドーナツチャートは中心に穴のある円グラフです。回転させることで最初のスライスの開始角度が変わります。

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle` メソッドは度数を表す `double` を受け取ります。正の値は時計回り、負の値は反時計回りに回転します。

## 手順 6: ドーナツの穴のサイズを変更（ドーナツチャートのサイズを変更）

穴のサイズはチャート半径に対する割合で表されます。`0.5` の値は穴が全半径の 50 % を占めることを意味します。

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**ヒント:** 有効範囲は `0.0`（穴なし、すなわち通常の円グラフ）から `0.9`（非常に細いリング）です。この範囲外の値を設定すると `IllegalArgumentException` がスローされます。

## 手順 7: 変更後の文書を保存

最後に、変更をディスクに書き戻します。

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

`DoughnutFormatted.docx` を Microsoft Word で開くと、ドーナツチャートが 45° 回転し、穴が元のサイズの半分に縮小されていることが確認できます。

## 完全な実行可能サンプル

すべての要素を組み合わせた完全なプログラムは以下の通りです。IDE にコピー＆ペーストして使用してください。

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### 期待される出力

プログラムを実行すると次のように出力されます。

```
Chart rotated and doughnut size changed successfully.
```

`DoughnutFormatted.docx` を開くと、最初のスライスが 45° の位置から始まり、内側の半径が外側半径の半分になっているドーナツチャートが表示されます。

## 一般的なバリエーションとエッジケース

| 状況 | 調整内容 | 重要な理由 |
|-----------|----------------|----------------|
| **複数のチャート** | `getChildNodes(NodeType.SHAPE, true)` をループし、各 `shape.hasChart()` を確認 | 最初のチャートではなく、目的のチャートを確実に変更できる |
| **棒グラフや折れ線グラフ** | `setStartAngle` は適用できません。代わりに `chart.getSeries().get(0).setFillFormat(...)` で視覚的調整 | すべてのチャートタイプが回転をサポートしているわけではなく、ドーナツ/円グラフのみが開始角度を持つ |
| **穴のないチャート** | `setDoughnutHoleSize` をスキップするか、`chart.setChartType(ChartType.DONUT)` でドーナツに変換 | ドーナツでないチャートに対して穴サイズを変更しようとすると例外が発生する |
| **大規模文書** | `DocumentBuilder.moveToDocumentStart()` と `builder.moveToNode(chartShape)` を使用して対象ノードへ直接移動 | 関係のないノードの全走査を避け、パフォーマンスが向上する |

## 信頼性の高いチャート操作のプロティップ

* **チャート参照をキャッシュ** – 複数のプロパティを変更する場合、`chartShape.getChart()` を繰り返し呼び出すのではなく、ローカルの `Chart` 変数に保持してください。
* **入力値の検証** – `setStartAngle` や `setDoughnutHoleSize` を呼び出す前に範囲を確認し、実行時エラーを防止します。
* **ライセンスを使用** – 評価モードでは最初のページに透かしが挿入されます。ライセンスを適用（`License license = new License(); license.setLicense("Aspose.Words.lic");`）すると透かしが除去されます。

## 次のステップ

**チャートを回転させる方法** と **ドーナツチャートのサイズを変更する方法** を習得したので、他の **Word のチャートを変更する** シナリオにも挑戦できます。

* `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())` でスライスの色を変更
* `chart.getSeries().get(0).setHasDataLabel(true)` でデータラベルを追加
* `chart.toImage(300, 300, ImageType.PNG)` でチャートを画像としてエクスポート

これらの拡張も同じパターンに従います：`Chart` オブジェクトを取得し、適切なセッターを呼び出し、文書を保存するだけです。

---

**これで Java を使って Word のドーナツチャートを回転・サイズ変更する方法をマスターしました。** コードを他のチャートタイプに適用したり、より大規模な文書生成パイプラインに統合したり、PowerPoint 自動化のために Aspose.Slides と組み合わせたりして自由に活用してください。コーディングを楽しんでください！


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}