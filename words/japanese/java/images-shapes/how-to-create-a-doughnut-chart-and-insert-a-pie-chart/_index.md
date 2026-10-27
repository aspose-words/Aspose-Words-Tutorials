---
category: general
date: 2026-10-26
description: Javaでドーナツチャートを作成し、ステップバイステップのコードで円グラフを挿入します。柔軟なチャート可視化の全ワークフローを学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: ja
lastmod: 2026-10-26
og_description: このガイドを使ってJavaでドーナツチャートを作成し、柔軟な可視化のためにパイチャートの挿入方法も示します。
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: ドーナツチャートを作成し、円グラフを挿入する – Javaガイド
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: ドーナツグラフの作成方法と円グラフの挿入方法
url: /ja/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドーナツチャートの作成と円グラフの挿入方法

Javaで**ドーナツチャートを作成**する必要がある場合、このチュートリアルでは正確な手順を案内します。また、同じビルダー API を使用して**円グラフを挿入**する方法も示すので、視覚スタイルを簡単に切り替えることができます。ガイドの最後までに、両方のチャートタイプを生成し、一般的なカスタマイズを示す完全な実行可能プログラムが手に入ります。

このチュートリアルで扱う内容:

* 選択したライブラリが提供するチャートビルダーの初期化  
* ドーナツチャートの作成と穴のサイズ設定  
* 円グラフの挿入とスライスの強調（エクスプロード）  
* シリーズが欠落している場合やサポートされていないチャートタイプなど、エッジケースの対処法

必要なのは最近の JDK（8 以上）と、クラスパスに配置したチャートライブラリの JAR だけです。外部サービスは不要です。

---

## 前提条件

| アイテム | 理由 |
|------|--------|
| Java Development Kit (JDK) 8+ | サンプルのコンパイルと実行に必須です。 |
| チャートライブラリ（例: **Aspose.Cells for Java** または **JFreeChart**） | コードで使用する `ChartBuilder`、`ChartType`、シリーズ操作メソッドを提供します。 |
| IDE またはテキストエディタ | Java ソースファイルを書いて実行するために使用します。 |

ライブラリの JAR がプロジェクトのビルドパスに追加されていることを確認してください。Maven を使用する場合は適切な依存関係を追加し、そうでなければ `libs` フォルダーに JAR を置き、コンパイル時に参照します。

---

## 手順 1: チャートビルダーのセットアップ

最初のステップは、チャートオブジェクトを生成する `ChartBuilder`（または同等の）インスタンスを作成することです。このオブジェクトはファクトリとして機能し、チャートを配置するワークシートまたはキャンバスを保持します。

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**重要ポイント:**  
ビルダーはチャートを特定のワークシートに結び付け、以降のすべてのチャートオブジェクトが同じ描画領域を共有できるようにします。このステップを省略すると、ビジュアル要素の配置先がなくなります。

---

## 手順 2: **ドーナツチャートの作成**

次に、サイズが定義されたドーナツチャートを生成します。穴のサイズはチャートの中心がどれだけ空になるかを決め、通常の円グラフをドーナツに変換します。

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**解説:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` はチャートオブジェクトを作成し、ワークシート上に領域を確保します。  
* `setHoleSize(30)` は中心部を 30 % 空にしてドーナツに変換します。  
* `add("{10, 20, 30, 40}", true)` は 4 つのデータポイントを提供し、`true` フラグはライブラリにこれらの値を単一シリーズとして扱うよう指示します。

**エッジケース:** 選択したチャートタイプが穴をサポートしていない場合（例: 棒グラフ）、`getDoughnutChart()` を呼び出すと例外がスローされます。穴のサイズを調整する前に必ずチャートタイプを確認してください。

---

## 手順 3: **円グラフの挿入**

ドーナツが完成したら、同じビルダーを使って**円グラフを挿入**する方法を示します。このステップは 2 つのチャートタイプの類似点を強調し、スライスを強調する方法を示します。

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**解説:**  

* `ChartType.PIE` はビルダーに従来の円グラフを作成させます。  
* `setExplode(10)` は最初のスライスを半径の 10 % だけオフセットし、重要なデータポイントを目立たせる一般的な手法です。  

**ヒント:** `setExplode` メソッドは円グラフの最初のシリーズに対してのみ機能します。複数シリーズがある場合は、対象となるインデックスを指定してください。

---

## 手順 4: ワークブックの保存

最後に、ワークブックをファイルに書き出して、Excel や互換ビューアでチャートを確認できるようにします。

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**保存が必要な理由:** ワークブックを永続化することで、すべての描画操作が確定します。保存前にファイルを開こうとすると、空または不完全なドキュメントになる可能性があります。

**結果:** *DoughnutAndPieChart.xlsx* を開くと、左側に 30 % の穴を持つドーナツチャート、右側に最初のスライスがエクスプロードされた円グラフが表示されます。

---

## 手順 5: よくあるバリエーションとトラブルシューティング

| 状況 | 調整方法 |
|-----------|------------|
| **異なるチャートサイズ** | `insertChart` の幅と高さの引数を変更します。 |
| **複数データシリーズ** | `add` を複数回呼び出すか、2 次元配列文字列を渡します。 |
| **動的な穴サイズ** | データ範囲に基づいて穴サイズを計算し、`setHoleSize` を呼び出します。 |
| **複数スライスのエクスプロード** | `chart.getSeries().get(i).setExplode(percent)` をループして、オフセットしたい各スライスに適用します。 |
| **ライブラリがドーナツをサポートしていない** | 円グラフを使用し、白い円を手動でオーバーレイして擬似的にドーナツを作成しますが、精度は低くなります。 |

**プロのコツ:** 大規模なワークブックでチャートを挿入した後は、可能であれば `builder.flush()` を呼び出してください。内部バッファが解放され、メモリリークを防止できます。

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "create doughnut chart example in Java")

*画像は、両方のチャートが横並びに配置された最終的なワークブックレイアウトを示しています。*

---

## 結論

これで、Java のフルエントビルダー API を使って**ドーナツチャートを作成**し、**円グラフを挿入**する方法が分かりました。完全なサンプルは、初期化、サイズ設定、穴の調整、スライスのエクスプロード、ファイル出力を網羅しています。ここからは、色、凡例、データラベルなどの追加カスタマイズを検討し、レポート要件に合わせて調整してください。

**次のステップ**

* **chart customization Java** の機能（グラデーション塗りつぶしやデータラベルなど）を試す。  
* ワークブックをオンデマンドで返す Web サービスにチャート生成を組み込む。  
* ビルダーアプローチと他のライブラリ（例: JFreeChart）を比較し、プロジェクトに最適なものを選択する。

チャート作成を楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法に基づく関連トピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探求に役立ちます。

- [How to create doughnut chart in a Word document with Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Save Word document after editing doughnut chart in Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}