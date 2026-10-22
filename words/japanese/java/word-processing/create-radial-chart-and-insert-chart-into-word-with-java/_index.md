---
category: general
date: 2026-09-27
description: Javaで放射状チャートを作成し、Wordに挿入します。チャートのサイズ設定、データ系列の追加、空白のWord文書の生成方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: ja
lastmod: 2026-09-27
og_description: Javaで放射状チャートを作成し、Wordに挿入します。このガイドでは、チャートのサイズ設定、データ系列の追加、空白のWord文書の作成方法を示します。
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Javaでラジアルチャートを作成し、Wordに挿入する
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Javaで放射状チャートを作成し、Wordに挿入する
url: /ja/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでラジアルチャートを作成し、Wordに挿入する

Word ファイル内に **ラジアルチャートを作成** したい場合、このチュートリアルで手順をすべて解説します。**チャートを Word に挿入** する方法、チャートのサイズ設定、**空の Word ドキュメント** を最初から作成する方法が分かります。

ドキュメントの初期化からデータ系列の追加、最終的な `.docx` の保存まで、必要なステップをすべて順に説明します。最後まで実行すれば、ラジアルチャートが埋め込まれた完全に機能する Word ファイルが手に入り、**チャートサイズの設定方法** と **データ系列チャートの追加方法** が理解でき、将来的なカスタマイズにも応用できます。

## 前提条件

* Java 17 以降（任意の最新 JDK でコンパイル可能）
* Aspose.Words for Java 24.9 以上 – `setShowGraduations` メソッドはこのバージョンから利用可能
* Aspose.Words JAR を組み込める IDE またはビルドツール（Maven/Gradle）
* Java の基本構文と Maven/Gradle の依存管理に慣れていること

> **プロのコツ:** Maven を使用している場合、`pom.xml` に以下を追加してください。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## 手順 1: 空の Word ドキュメントを作成する

空のドキュメントは、チャートを配置するキャンバスとなります。`Document` クラスが `.docx` 全体を表します。

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

空のドキュメントを作成することで、既存のコンテンツがチャートのレイアウトに干渉することを防げます。

## 手順 2: DocumentBuilder を初期化する

`DocumentBuilder` は、オブジェクトやテキスト、その他要素をドキュメントに挿入する便利なメソッドを提供します。

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

このビルダーは後で **チャートを Word に挿入** する際に使用します。

## 手順 3: ラジアルチャートを構築する

Aspose.Words は多数のチャートタイプをサポートしています。`ChartType.RADIAL` がラジアル（ポーラ）チャートを生成します。

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

この時点でチャートは生成されていますが、データやサイズ、ビジュアルオプションは未設定です。

## 手順 4: データ系列をチャートに追加する

データ系列が無いチャートは空です。`add` メソッドは系列名と値の配列を受け取ります。

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

`add` を繰り返し呼び出すことで複数系列を追加できます。これで **データ系列チャートの追加** 要件が満たされます。

## 手順 5: グラデーション（目盛り）を有効にする（任意）

目盛りはラジアルグリッド線で、可読性を向上させます。バージョン 24.9 以降でのみ利用可能です。

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

古い Aspose.Words バージョンを使用している場合、この行は例外をスローしますので、まずライブラリのバージョンを確認してください。

## 手順 6: チャートのサイズを設定する

チャートサイズを制御することで、ページ余白内にきれいに収められます。これが **チャートサイズの設定方法** に該当します。

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

レイアウトに合わせて幅と高さの値を調整してください。1 ポイントは約 1/72 インチです。

## 手順 7: チャートを Word 文書に挿入する

いよいよチャートを配置します。`DocumentBuilder` の `insertChart` メソッドが挿入処理を行います。

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

これが **Word にチャートを挿入** する核心部分です。

## 手順 8: ドキュメントを保存する

最後にドキュメントをディスクに書き出します。ファイルには先ほど作成したラジアルチャートが含まれます。

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

プログラムを実行すると、プロジェクトの作業ディレクトリに `RadialChart.docx` が生成されます。Microsoft Word で開くと、3 つのデータポイントと目盛りが表示されたラジアルチャートが確認できます。

### 期待される出力

* `RadialChart.docx` という名前の Word ファイル
* ファイル内部は、サイズ 400 × 300 ポイントのラジアルチャートが 1 ページに配置されている
* チャートは **Series 1** という系列名で、値は **10, 20, 30** と表示される
* ラジアルグリッド線（目盛り）がチャート周囲に表示されている

## よくあるバリエーションとエッジケース

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Multiple series** | `chart.getSeries().add(...)` を系列ごとに呼び出す | 比較データの可視化が可能になる |
| **Different chart type** | `ChartType.RADIAL` を `ChartType.COLUMN`（または他のタイプ）に置き換える | データに最適なチャートタイプを選択できる |
| **Custom colors** | `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` を使用 | ビジュアルブランディングが向上する |
| **Older Aspose.Words version** | `setShowGraduations` 行を削除するかライブラリをアップグレードする | `NoSuchMethodError` を防止できる |
| **Saving to a different format** | `doc.save("RadialChart.pdf", SaveFormat.PDF)` を使用 | DOCX の代わりに PDF を生成できる |

## 完全な実行可能サンプル

以下は単体で動作する Java プログラムです。`RadialChartExample.java` という名前で保存し、Aspose.Words の依存関係を追加して実行してください。

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## まとめ

これで **ラジアルチャートをプログラムで作成** し、**データ系列チャートを追加**、**チャートサイズの設定方法** を制御し、**空の Word ドキュメントからチャートを Word に挿入** する手順が分かりました。例は Aspose.Words for Java 24.9 を使用していますが、同様の API を提供する他のチャートライブラリでも同様の概念が適用できます。

### 次のステップ

* 他のチャートタイプ（`ChartType.PIE`, `ChartType.LINE` など）を試す – これも二次キーワード **insert chart into word** に関連します
* 軸ラベル、凡例、カラーをカスタマイズしてブランドガイドラインに合わせる
* データベースクエリや CSV ファイルから動的にチャートを生成する
* 生成した `.docx` を PDF に変換して配布する（`doc.save("output.pdf", SaveFormat.PDF)`）

サイズ、系列データ、スタイリングオプションを自由に試して、必要なビジュアルを作り上げてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、別の実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [Aspose.Words for Java を使用してコラムチャートを作成する方法](/words/english/java/document-conversion-and-export/using-charts/)
- [Word Document Java – 影付き長方形シェイプを追加する](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Word ドキュメントにエリアチャートを挿入する](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}