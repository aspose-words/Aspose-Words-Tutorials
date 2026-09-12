---
category: general
date: 2026-09-11
description: JavaでWord文書のグラフを編集する方法 – グラフ設定の更新、グリッドラインの有効化、グラフオプションの変更、そして更新された文書の保存を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: ja
lastmod: 2026-09-11
og_description: JavaでWord文書のグラフを編集する方法。このガイドに従ってグラフ設定を更新し、グリッドラインを有効にし、グラフオプションを変更し、更新された文書を保存してください。
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: JavaでWord文書のグラフを編集する方法 – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: JavaでWord文書のチャートを編集する方法
url: /ja/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java を使用して Word ドキュメントのチャートを編集する方法

Word ファイルで **チャートの編集方法** が必要な場合、このガイドでは正確な手順を示します。チャート設定の更新、チャートのグリッドラインの有効化、チャートオプションの変更、そして最終的に **更新されたドキュメントを保存** して書式を失わない方法を学びます。

プログラムでチャートを操作することは、特に目盛りやグリッドラインといったビジュアルの細部を調整したいときに、ブラックボックス的に感じられることがあります。このチュートリアルでは、ドキュメントの読み込みから変更の永続化まで、必要なすべてを網羅します。外部ツールは不要で、Aspose.Words for Java ライブラリ（バージョン 24.9 以降）だけで完結します。

この記事を読み終えると、以下ができるようになります。

* チャートを含む `.docx` ファイルを読み込む。
* チャートのシェイプを特定し、プロパティを変更する。
* チャートのグリッドライン（目盛り）を有効にし、その他のオプションを調整する。
* **更新されたドキュメント** を新しいファイルとして保存する。

## 前提条件

* Java 17 以上がインストールされていること。  
* 依存関係管理に Maven または Gradle を使用できること。  
* Aspose.Words for Java 24.9 以上（`setShowGraduations` が導入されたバージョン）。  
* 少なくとも 1 つのチャートが含まれる Word ドキュメント（`input.docx`）。

Aspose.Words は、プログラムから Word ドキュメントを読み取り、変更し、書き出すことができるフル機能の API と考えてください。Web ブラウザで DOM を操作する感覚に近いです。

## 手順 1: プロジェクトをセットアップし、ライブラリをインポートする

新規 Maven プロジェクトを作成するか、既存プロジェクトに依存関係を追加します。

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **プロのコツ:** `setShowGraduations` メソッドが利用できるよう、最新の安定版リリースを使用してください。古いバージョンではコンパイルエラーになります。

## 手順 2: チャートを含む Word ドキュメントを読み込む

**チャートの編集方法** ワークフローの最初のアクションは、ソースファイルをロードすることです。Aspose.Words では、ドキュメント全体を `Document` クラスで表現します。

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

`Document` オブジェクトを通じて、シェイプ、テーブル、段落など、ファイル内のすべてのノードにアクセスできます。  

## 手順 3: ドキュメント内の最初のチャートシェイプを特定する

チャートは `Shape` ノードとして格納され、そのレンダラが `Chart` です。チャートを編集するには、まずそのノードを取得する必要があります。

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

ドキュメントに複数のチャートがある場合は、`shapes` を走査し、`chartShape.getChart() != null` を確認してからキャストしてください。これにより `ClassCastException` を防ぎ、**チャートオプションの変更** を有効なチャートオブジェクトに対してのみ行えます。

## 手順 4: チャートのグリッドライン（目盛り）を有効にする – バージョン 24.9 の新プロパティ

`setShowGraduations` プロパティは、値軸の小さなグリッドラインの表示/非表示を切り替えます。これを有効にすると、データが密集している場合でも可読性が向上します。

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **なぜ重要か:** グリッドラインは各データポイントの視覚的基準を提供し、トレンドを把握しやすくします。デフォルトは `false` なので、必要に応じて明示的に有効化する必要があります。

他にも、主要グリッドライン、軸タイトル、凡例の配置などをカスタマイズできます。以下はチャートタイトルと凡例位置を変更する例です（**チャートオプションの変更** の一環）。

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## 手順 5: 更新されたチャート設定でドキュメントを保存する

チャートの変更が完了したら、変更を永続化します。このステップで **更新されたドキュメント** の保存が完了します。

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

プログラムを実行すると `output.docx` が生成され、チャートにグリッドラインが表示され、タイトルと凡例が新しい位置に変更されます。Microsoft Word で開いてビジュアルの変化を確認してください。

## 完全なソースコード（実行可能）

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### 期待される結果

`output.docx` を開くと:

* 値軸に小さなグリッドラインが表示されます。  
* タイトルが **“Sales Overview 2026”** に変更されています。  
* 凡例がチャートの下部に配置されています。

元のチャートにすでにグリッドラインがあった場合でも、見た目は変わらず、コードが **冪等 (idempotent)** であることが確認できます。

## よくある質問とエッジケースの対処

### ドキュメントにチャートがない場合は？

チャートでないシェイプをキャストしようとすると `ClassCastException` が発生します。以下のようにシェイプタイプをチェックしてガードしてください。

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### 最初のチャートではなく、特定のチャートを編集したい場合は？

`shapes` を走査し、既知のタイトルや別の識別子と照合します。

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### 後でグリッドラインを無効にできるか？

はい、プロパティを `false` に設定すれば無効化できます。

```java
chart.setShowGraduations(false);
```

### `.doc`（バイナリ）ファイルでも動作しますか？

Aspose.Words はファイル形式を抽象化しているため、`.doc` と `.docx` の両方で同じコードが動作します。ただし、目盛りなどの新しいチャート機能は OOXML 形式にのみ格納されるため、効果を確認できるのは `.docx` として保存したときだけです。

## 本番環境向けコードのヒント

* **入力パスの検証** – `Files.exists(Paths.get(inputPath))` を使用してロード前に存在を確認。  
* **API 呼び出しは try‑catch でラップ** し、特に破損したドキュメントを扱う際に `Exception` の詳細を取得。  
* **リソースの解放** – Aspose.Words はメモリ管理を行いますが、`doc.close()`（または try‑with‑resources が利用可能ならそれ）を呼び出すことでネイティブハンドルを早期に解放できます。  
* **バージョンチェック** – `setShowGraduations` を呼び出す前に、ランタイムライブラリのバージョンが ≥ 24.9 であることを確認。`License.getVersion()` でプログラム的にガードできます。

## 結論

これで **チャートの編集方法** を Java で Word ドキュメントに対して実装できました。プロセスは「ドキュメントをロード → チャートを特定 → グリッドラインを有効化 → チャートオプションを変更 → **更新されたドキュメントを保存**」という流れで、プログラムによるチャート操作の最も一般的なシナリオをカバーしています。

ここからは、データ系列の色変更、チャートスタイルの適用、チャートを画像としてエクスポートするなど、さらなるカスタマイズに挑戦できます。いずれの作業も同じパターンです：`Chart` インスタンスを取得し、プロパティを調整し、**更新されたドキュメントを保存** します。

コーディングを楽しんで、レポート作成に最適なチャート設定を自由に試してみてください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能を習得したり、別の実装アプローチを探求したりするのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}