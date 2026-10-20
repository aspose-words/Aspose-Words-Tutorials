---
category: general
date: 2026-10-20
description: Aspose.Words for Javaでシェイプをグループ化する方法 – 四角形シェイプの挿入、グループ化、ドキュメントの保存をひとつのガイドで学ぶ。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: ja
lastmod: 2026-10-20
og_description: Aspose.Words for Javaでシェイプをグループ化する方法。このチュートリアルでは、長方形シェイプの挿入、グループ化、そして結果のエクスポート方法を示します。
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Aspose.Words for Javaで図形をグループ化する方法 – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Aspose.Words for Javaで図形をグループ化する方法
url: /ja/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でシェイプをグループ化する方法

Aspose.Words for Java を使用して Word ドキュメントで **シェイプをグループ化する方法** が必要な場合、本ガイドでは完全なワークフローを示します。**矩形シェイプの挿入** 方法を学び、2 つ目の矩形を追加し、2 つのシェイプをグループ化し、最後にファイルを保存するまでを、明確で実行可能なコードとともに解説します。

シェイプをグループ化すると、複数の描画を単一のユニットとして移動、回転、またはスタイル設定できるため便利です。レポートテンプレート、図、カスタムフライヤーの作成など、シェイプのグループ化を習得すれば、作業時間の短縮とレイアウトの一貫性が保てます。

このチュートリアルで行うこと:

* `Document` と `DocumentBuilder` を新規作成します。
* 正確なサイズで **矩形シェイプを挿入する方法** を学びます。
* 矩形を `GroupShape` にグループ化します。
* ドキュメントを保存し、結果を確認します。

> **Prerequisite** – プロジェクトに Aspose.Words for Java（v23.12 以降）を追加している必要があります。Maven ユーザーは以下の依存関係を含めることができます。

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## 必要なもの

| Item | Reason |
|------|--------|
| Java 17+ | 最新の言語機能とパフォーマンス向上 |
| Aspose.Words for Java | `DocumentBuilder`、`Shape`、`GroupShape` API を提供 |
| IDE (IntelliJ IDEA、Eclipse、VS Code など) | サンプルをコンパイル・実行するため |
| フォルダーへの書き込み権限 | ドキュメントをディスクに保存するため |

---

## 矩形シェイプの挿入方法

最初のステップは `Document` と `DocumentBuilder` を作成することです。`DocumentBuilder` には `insertShape` など、描画オブジェクトを配置するためのメソッドが用意されています。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – `insertShape` を使用することは、Aspose.Words で **矩形オブジェクトを挿入する標準的な方法** です。シェイプは自動的に現在の段落に追加されるため、低レベルの OpenXML を直接扱う必要がありません。

## 矩形の位置調整（オプション）

2 番目の矩形を 1 番目に対してカスタム位置にしたい場合は、`left` と `top` プロパティを変更できます。この手順はオプションですが、正確な図のレイアウトにはしばしば必要です。

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** すべての測定単位はポイントです（1 pt ≈ 1/72 in）。UI 計算でピクセル値が必要な場合は `convertPointsToPixels` を使用してください。

## シェイプをグループ化する方法

矩形が作成されたら、`GroupShape` の中に配置できます。グループ化すると、2 つの矩形が単一のオブジェクトとして扱われ、グループ全体の移動、回転、書式設定が両方のシェイプに適用されます。

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` は `Shape` を継承しているため、他の描画オブジェクトと同様に扱えます。`appendChild` を呼び出すと、シェイプは元の位置から削除され、グループの子オブジェクトになります。

## グループ化されたシェイプを含むドキュメントの保存

最後に、ドキュメントをディスクに書き込みます。ファイルには 2 つの矩形が含まれた単一の `GroupShape` が格納されます。

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 期待される結果

Microsoft Word で `GroupShape.docx` を開くと:

* 青と緑の 2 つの矩形が横に並んで表示されます。
* どちらかの矩形を選択するとグループ全体が選択され、ドラッグすると両方が一緒に移動します。
* グループには細い赤い枠線があり、`GroupShape` のプロパティが適用されていることが確認できます。

グループを右クリックして **Group → Ungroup** を選択すると、矩形は個別のシェイプに戻り、グループ化操作が可逆であることが示されます。

## 一般的なバリエーションとエッジケース

| Situation | How to handle it |
|-----------|------------------|
| **2 つ以上のシェイプ** | 各シェイプを挿入し、すべてを同じ `GroupShape` に追加します。 |
| **異なるシェイプタイプ**（例：楕円、画像） | 追加前に `builder.insertShape(ShapeType.ELLIPSE, …)` または `builder.insertImage(...)` を使用します。 |
| **グループのスケーリング** | `group.setWidth(newWidth)` または `group.setHeight(newHeight)` を呼び出すと、子シェイプが比例して拡大縮小します。 |
| **グループの回転** | `group.setRotationAngle(45);` で中心を基準に全体が回転します。 |
| **元の位置の保持** | グループ化前に各シェイプの `left`/`top` を保存し、必要に応じてアンングループ後に復元します。 |

## 完全な実行可能サンプル

以下は IDE にコピー＆ペーストできる完全な Java クラスです。すべてのインポート、エラーハンドリング、コメントが含まれており、分かりやすくなっています。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

プログラムを実行し、生成された `GroupShape.docx` を開くと、説明通りにグループ化された矩形が表示されます。

## 結論

これで、Aspose.Words for Java で **シェイプをグループ化する方法** が分かりました。ドキュメントの作成、矩形シェイプの挿入、位置調整、そして最終的に `GroupShape` でのグループ化までの手順を習得しました。この手法により、複数の描画を単一のエンティティとして扱えるようになり、レイアウト調整やビジュアルの一貫性が容易になります。

**次のステップ**

* **異なる塗りパターンや枠線を持つ矩形シェイプの挿入方法** を探求してください。
* **矩形シェイプの挿入** とテキストボックスを組み合わせて、ラベル付き図を作成します。
* グループの回転やスケーリングを試して、より複雑なグラフィックを作成してみてください。

他のシェイプタイプや大規模なグループ、動的なドキュメント生成シナリオに合わせてコードを自由にカスタマイズしてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Java で矩形シェイプを挿入 – シェイプのグループ化と位置設定](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Java でグループシェイプを挿入する方法 – 完全ガイド](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Aspose.Words でシェイプに影を設定する方法 – 完全ガイド](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}