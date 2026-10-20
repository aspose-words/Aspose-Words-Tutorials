---
category: general
date: 2026-08-01
description: Aspose.Words を使用して Java で Word の図形をグループ化します。図形のグループ化方法と、矩形の図形をすばやく挿入する方法を、完全なコード例とともに学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: ja
lastmod: 2026-08-01
og_description: Java を使用して Word で図形をグループ化する。このガイドでは、図形のグループ化、長方形の挿入、そして Aspose.Words
  を使用した DOCX の保存方法を示します。
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: JavaでWordの図形をグループ化 – 完全プログラミング解説
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: JavaでWordの図形をグループ化する – 完全ステップバイステップガイド
url: /ja/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWordの図形をグループ化 – 完全ステップバイステップガイド

Javaを使用して**Wordで図形をグループ化**する必要がある場合、このガイドが役立ちます。レポートジェネレータや動的テンプレートエンジンを構築している場合でも、図形をグループ化することで文書が洗練され、関連するグラフィックが一緒に保たれます。

この数分で、**図形のグループ化方法**と**矩形形状の挿入**をAspose.Wordsで正確に行う方法、さらに一般的な落とし穴を回避する実用的なヒントをいくつか紹介します。ばらばらの矩形や楕円を整然としたグループに変換する準備はできましたか？さっそく始めましょう。

## 本チュートリアルでカバーする内容

* 最小限の前提条件（Java 17+、Aspose.Words 24.10 以降）。  
* Word 文書を作成し、矩形と楕円を挿入、グループ化し、必要に応じて非表示にして保存する、完全で実行可能な Java プログラム。  
* 各 API 呼び出しが重要な理由、単なる機能説明だけでなく。  
* 古い Aspose.Words バージョンや 2 つ以上の図形をグループ化する際のエッジケース処理。  
* 期待される出力と結果をすばやく検証する方法。

最後まで読めば、このスニペットを任意の Java プロジェクトに貼り付けるだけで、散在するドキュメントを探さずに Word で図形をグループ化できるようになります。

---

## 前提条件

| 要件 | なぜ重要か |
|-------------|----------------|
| **Java 17+** | 最新の言語機能とパフォーマンス向上のため。 |
| **Aspose.Words for Java 24.10+** | 後述の `setHidden` メソッドはこのバージョン以降でのみ利用可能です。 |
| **Maven または Gradle ビルド** | 依存関係管理が楽になります。 |
| **IDE (IntelliJ, Eclipse, VS Code)** | 素早いテストに便利ですが、テキストエディタでも可。 |

`pom.xml` に Aspose.Words の Maven 依存関係を追加します:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Gradle を使う場合は以下が同等です:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Step 1: 新しい Document と Builder の作成

まず空の `Document` と `DocumentBuilder` を作成します。Builder は図形やテキストなどを挿入できる作業の中心です。

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*このステップの理由*  
`Document` は DOCX ファイル全体を表し、`DocumentBuilder` はカーソルベースの便利な API を提供します。Builder がなければ、低レベルのノードコレクションを手動で操作しなければならず、ミスしやすくなります。

---

## Step 2: 矩形形状（と楕円）の挿入

次に、グループ化したい 2 つの基本図形を追加します。**insert rectangle shape** 呼び出しに注目してください—これが求めている二次キーワードです。

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

覚えておくべきポイント:

* 幅 (`100`) と高さ (`50`) はポイント単位です (1 pt ≈ 1/72 in)。レイアウトに合わせて調整してください。  
* 矩形が先に描画されるため、デフォルトでは楕円の背後に配置されます。逆の順序が必要な場合は、先に楕円を挿入してください。  
* 両方の図形は Builder の現在の書式設定（色、線のスタイル）を継承します。グループ化前にカスタマイズすることも可能です。

---

## Step 3: Aspose.Words で図形をグループ化する方法

ここがチュートリアルの核心—**図形のグループ化方法**です。`insertGroupShape` API は既存の図形配列を受け取り、グループを表す新しい `Shape` を返します。

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

なぜグループを使うのか？

* グループは単一ユニットとして移動し、相対位置を保持します。  
* 回転やスケーリングなどの変換を 1 回の呼び出しで全体に適用できます。  
* 後で個別要素を調整したい場合は、アン・グループすれば簡単です。

---

## Step 4 (オプション): 文書ビューからグループを非表示にする

ユーザーが Word で文書を開いたときにグループを表示したくない場合、非表示にできます。このステップはオプションですが、背景グラフィックや透かしに便利です。

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**古い Aspose.Words バージョンを使用している場合は？**  
`setHidden` メソッドはコンパイルできません。その場合は、図形の `WrapType` を `NONE` に設定し、テキストレイヤーの背後に移動させることで同様の効果を得られます:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

少し冗長ですが、読者の視界からグループを除外することはできます。

---

## Step 5: 文書の保存

最後に、文書をディスクに書き出します。ファイルの保存先パスは好きな場所に変更してください。

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

`GroupShapeResult.docx` を Microsoft Word で開くと、矩形と楕円がきれいにまとめられているのが確認できます。`setHidden(true)` を設定している場合、エディタ上ではグループは見えませんが、ファイル内には残っているため、後続のプログラム処理に利用できます。

---

## 完全動作サンプル

すべてをまとめた、コピー＆ペースト可能な完全な Java クラスは以下です:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**期待される出力:** `GroupShapeResult.docx` という名前のファイルが生成され、青色塗りつぶしの矩形と赤枠の楕円（デフォルト色）を保持する単一のグループが含まれます。文書を開き、グループを選択して右クリック → **Group → Ungroup** を実行すると、元の 2 つの図形が再び表示されます。

---

## よくある質問とエッジケース

### 1. 2 つ以上の図形をグループ化できますか？

もちろんです。`insertGroupShape` により大きな配列を渡すだけです:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

API は線形にスケールします。唯一の制限は極端に大きなグループに対するメモリです。

### 2. 作成後にグループの位置を変更したい場合は？

他の図形と同様に、グループの `setLeft` と `setTop` メソッドを使用します:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

グループは単一の図形として振る舞うため、子図形はすべて一緒に移動します。

### 3. グループ全体に枠線や塗りを適用するには？

グループ自体にも書式設定は可能ですが、子図形には直接影響しません。共通の枠線が必要な場合は、まず矩形で図形を囲んでからすべてをグループ化します。あるいは、各子図形を走査して同じ `fillColor` や `strokeWeight` を設定します。

### 4. `setHidden(true)` は印刷に影響しますか？

非表示の図形は Word のデフォルト設定では **印刷されません**。透かしやテンプレートマーカーに便利です。画面上は見えなくても印刷したい場合は、別の手法（例: 不透明度を 0% に設定）を使用する必要があります。

---

## 現場からのプロ・ティップ

* **図形に名前を付ける** – `groupShape.setName("HeaderGraphics");` とすれば、後で名前で図形を取得する際のデバッグが楽になります。  
* **Builder を再利用する** – グループを挿入した後も Builder のカーソルはグループの位置に留まるため、位置リセットなしでその直後に段落を追加できます。  
* **バージョンガード** – ライブラリが古い Aspose.Words バージョンでも動作する可能性がある場合、`setHidden` 呼び出しを `NoSuchMethodError` の try‑catch で囲み、前述の `WrapType.NONE` 手法にフォールバックします。  
* **パフォーマンス・ティップ** – 数千件の文書を生成する際…

---

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした密接に関連するトピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for Java でのドキュメント図形の使用](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Java で Word 文書を作成 – 影効果付き矩形形状の追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java での図形のレンダリング](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}