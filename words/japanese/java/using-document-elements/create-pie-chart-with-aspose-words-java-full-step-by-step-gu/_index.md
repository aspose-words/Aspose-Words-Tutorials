---
category: general
date: 2026-07-16
description: Aspose.Words を使用して Java で円グラフを作成します。リーダーラインの追加、凡例の表示、スライスの分離（エクスプロード）方法を1つのチュートリアルで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: ja
lastmod: 2026-07-16
og_description: Aspose.Words を使用して Java で円グラフを作成します。このガイドでは、リーダーラインの追加、チャート凡例の表示、スライスの分離方法を示し、数分で洗練されたビジュアルを実現します。
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Aspose.Words Javaで円グラフを作成 – 完全な書式設定チュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Aspose.Words Javaで円グラフを作成する – 完全ステップバイステップガイド
url: /ja/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Javaで円グラフを作成 – 完全ステップバイステップガイド

Javaで低レベルの描画 API と格闘せずにプログラムで **円グラフを作成** したいと思ったことはありませんか？ あなただけではありません。多くの開発者がレポートやダッシュボード、あるいは自動生成ドキュメントのためにすぐに使えるビジュアルを必要としており、重い作業を Aspose.Words に任せています。

このチュートリアルでは、**円グラフを作成** するだけでなく、**リーダーラインを追加**、**チャート凡例を表示**、さらには **スライスを強調表示（エクスプロード）** する方法も示す、完全に実行可能なサンプルを順を追って解説します。最後には、クライアントを感心させるほど洗練された `.docx` ファイルが手に入ります。

> **クイックウィン:** 以下のコードスニペットは Aspose.Words for Java 23.9（またはそれ以降のバージョン）ですぐに動作します。追加の依存関係は不要で、JAR だけです。

## 学べること

- `DocumentBuilder` を使って空の Word 文書を作成する方法
- カスタムサイズの **円グラフ** を挿入する方法
- データポイントを強調するための **スライスのエクスプロード** 機能の使用方法
- エクスプロードしたスライスをラベルに接続する **リーダーライン** の有効化方法
- 読者が各スライスをすぐに識別できるように **チャート凡例** を表示する方法
- 作成した文書を `.docx` ファイルとして保存し、Microsoft Word や LibreOffice で開く方法

**前提条件** – 必要なもの:

1. Java 17（またはそれ以降）がインストールされていること。
2. クラスパスに Aspose.Words for Java の JAR があること。
3. 基本的な IDE またはテキストエディタ – IntelliJ IDEA、Eclipse、VS Code など、好みのもの。

それでは、始めましょう。

## 手順 1: Document と Builder の初期化 – **円グラフを作成** の準備

まず、クリーンな文書キャンバスが必要です。`Document` は Word ファイル全体を表し、`DocumentBuilder` はコンテンツを追加するヘルパーです。

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **重要ポイント:** 新しい `Document` から始めることで、チャート描画に干渉する可能性のある隠れたスタイルや残存オブジェクトがないことが保証されます。

## 手順 2: **円グラフ** を挿入 – サイズが重要

Aspose.Words ではチャート挿入がワンライナーで行えます。ここでは幅 400 × 高さ 300 ポイント（典型的な画面で約 5.5 × 4.2 インチ）の円グラフを要求します。

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **プロのコツ:** 別のサイズが必要な場合は、数値引数を変更するだけです。API はポイント単位で動作し、72 ポイント = 1 インチです。

## 手順 3: **スライスをエクスプロード** する方法 – 重要データポイントの強調

スライスをエクスプロードすると、他の部分から切り離され、読者の目を引きます。`setExplosion` メソッドは、ポイント単位の距離を表す整数を受け取ります。

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **複数シリーズがある場合は?** 任意のシリーズインデックス（`get(1)`, `get(2)` …）に対して `setExplosion` を呼び出すことで、異なるスライスをエクスプロードできます。

## 手順 4: **リーダーライン** と **チャート凡例** を **追加** – 点と点をつなぐ

スライスがエクスプロードされると、ラベルが離れてしまうことがあります。リーダーラインはラベルを固定し、可読性を保ちます。同時に、凡例はすべてのスライスのキーをすぐに提供します。

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **リーダーラインを有効にする理由:** これがないと、ラベルが浮いて見え、どのスライスに属しているかが分かりにくくなります。  
> **凡例の位置をカスタマイズしたい場合:** `chart.getLegend().setPosition(LegendPosition.TOP)` など、任意の enum 値を使用してください。

## 手順 5: 文書を保存 – 最終的な **円グラフ作成** 手順

最後に、文書をディスクに永続化します。書き込み権限のあるフォルダーにパスを調整してください。

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

プログラムを実行し、生成された `PieChartDemo.docx` を開くと、最初のスライスがエクスプロードされ、リーダーラインと凡例が表示されたきれいに整形された円グラフが確認できます。

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Create pie chart example with exploded slice, leader lines, and legend"}

### 期待される出力

Word ファイルを開くと、チャートは概ね以下のようになります:

- 400 × 300 pt の円グラフ
- 最初のスライスが 10 pt オフセットされている
- 薄いリーダーラインがエクスプロードしたスライスとラベルを接続
- チャート下部に凡例が表示され、各シリーズ名が列挙されている

リーダーラインが表示されない場合は、`setLeaderLines(true)` が **エクスプロード設定の後** に呼び出されているか確認してください。順序が重要です。

## よくある落とし穴と回避策

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **凡例が表示されない** | `setShowLegend(true)` が省略されているか、間違ったチャートオブジェクトで呼び出されている。 | `Chart` を取得した後、**必ず** `chart.setShowLegend(true)` を呼び出してください。 |
| **リーダーラインが欠落** | スライスがエクスプロードされていない、またはチャートタイプがリーダーラインに対応していない。 | `ChartType.PIE`（または `PIE_3D`）のみがリーダーラインをサポートします。まず `setExplosion` を呼び、次に `setLeaderLines(true)` を実行してください。 |
| **スライスが動かない** | エクスプロード値が低すぎる（0‑2 pt）。 | 整数を大きくし、例として `setExplosion(10)` 以上に設定して効果を強調してください。 |
| **チャートが歪む** | 幅と高さが等しくないサイズ（幅 ≠ 高さ）を使用すると円が潰れます。 | 幅と高さを同じか近い値に保ちます。400 × 300 でも動作しますが、400 × 400 にすると完全な円になります。 |

## 上級調整（オプション）

基本を超えてさらにカスタマイズしたい場合は、以下を検討してください:

- **カスタムカラー**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **データラベル**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D 効果**: `ChartType.PIE` を `ChartType.PIE_3D` に置き換える。

これらのオプションを使えば、企業のブランディングガイドラインに合わせてビジュアルを細かく調整できます。

## まとめ – 達成したこと

空の Word 文書から始め、**円グラフを作成**、**最初のスライスをエクスプロード**、**リーダーラインを追加**、そして **チャート凡例を表示** しました。全体のフローは簡潔な `main` メソッドに収められており、より大規模なレポートパイプラインに組み込みやすくなっています。

## 次のステップ

- **シリーズを増やす**: データベースや CSV から実データを取得してチャートに反映させる。
- **PDF にエクスポート**: `doc.save("output.pdf", SaveFormat.PDF);` を使用して PDF バージョンを生成する。
- **他の図形と組み合わせる**: テーブル、画像、追加のチャートを挿入してフルレポートを作成する。

他のチャートタイプ（柱状、棒、折れ線）に興味がある場合は、`ChartType.PIE` を目的の enum に置き換えて同様の手順を実行してください。

---

*チャート作成を楽しんでください！* 期待通りに動作しなかった点や凡例位置のカスタマイズ方法など、コメントでお気軽にシェアしてください。皆さんのフィードバックが、より良い自動文書作成に役立ちます。

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、API の追加機能をマスターし、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}