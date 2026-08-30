---
category: general
date: 2026-07-29
description: Aspose.Words を使用して Java で Word 文書を作成します。矩形シェイプの挿入、Word でのシェイプのグループ化を学び、ドキュメントをすばやく
  docx として保存します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: ja
lastmod: 2026-07-29
og_description: Aspose.Words を使用して Java で Word 文書を作成し、矩形シェイプを挿入、シェイプをグループ化し、数分で docx
  として保存します。
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: シェイプ付きWord文書の作成 – Java Aspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Javaで図形付きWord文書を作成する – 完全なAspose.Wordsガイド
url: /ja/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java でシェイプ付き Word 文書を作成 – 完全 Aspose.Words ガイド

プログラムで **Word 文書を作成**し、カスタムグラフィックで彩りたいと思ったことはありませんか？ あなただけではありません。ハイライトされたセクションを含むレポートを生成したり、即席でチラシをデザインしたりする必要がある場合、Word のシェイプ操作をマスターすれば手作業の時間を大幅に削減できます。

このチュートリアルでは、Aspose.Words for Java を使用して **Word 文書を作成**し、**長方形シェイプを挿入**し、**Word でシェイプをグループ化**し、最後に **docx として文書を保存**する手順を詳しく解説します。最後まで読めば、任意のプロジェクトにすぐ組み込める完全に実行可能なサンプルが手に入ります。

## 本チュートリアルで得られるもの

- Java コードだけで生成された新規 Word ファイル。  
- ページに追加された 2 つの異なるシェイプ（長方形と楕円）。  
- **group shapes in word** API を使ってこれらのシェイプを 1 つのオブジェクトとして扱えるようにグループ化。  
- 標準的な `.docx` としてディスクに保存され、Microsoft Word で問題なく開けるファイル。  

外部ツール不要、XML をいじる必要もなし—クリーンな型付け Java と Aspose.Words だけです。

---

## 前提条件

始める前に以下を用意してください。

1. **Java Development Kit (JDK) 8 以上** – 本コードは Java 8+ を対象としています。  
2. **Aspose.Words for Java** の JAR（最新バージョンは Maven Central リポジトリから取得可能）。  
3. 手軽な IDE（IntelliJ IDEA、Eclipse、またはシンプルなテキストエディタ）。  

これらが揃っていれば、さっそく始めましょう。

---

## 手順別実装

以下ではプロセスを小さなステップに分割しています。各ステップにコードスニペット、簡単な説明、公式ドキュメントには載っていないかもしれないヒントを添えています。

### ## Aspose.Words を使ってシェイプ付き Word 文書を作成

まずは空の Word ファイルを用意します。Aspose.Words なら 1 行で完了です。

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**ポイント:**  
`Document` はテキスト、テーブル、画像、シェイプなどすべてを格納するコンテナです。`DocumentBuilder` は低レベルオブジェクトと格闘せずにコンテンツを追加できる便利なヘルパーです。ページ上に直接書き込むペンのようなものと考えてください。

> **プロのコツ:** テンプレート（例: 会社のレターヘッド）から開始したい場合は、`new Document()` を `new Document("template.docx")` に置き換えてください。

### ## 長方形シェイプとその他のシェイプを挿入

次に青い長方形と緑の楕円を追加します。長方形は **insert rectangle shape** キーワードの例示で、楕円はシェイプタイプを自由に組み合わせられることを示します。

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**内部で何が起きているか:**  
`insertShape` の呼び出しごとに `Shape` オブジェクトが生成され、現在の段落に自動的に追加されます。`setLeft`/`setTop` メソッドはページ余白を基準にした位置をポイント単位で指定します（1 pt = 1/72 in）。数値を調整すればシェイプを好きな場所に配置できます。

> **よくある質問:** *塗りつぶしを単色ではなく画像にしたいですか？*  
> もちろん可能です。`shape.getFill().setImage("path/to/image.png")` のように画像を指定してください。

### ## Word でシェイプをグループ化して操作を簡略化

別々のオブジェクトでも構いませんが、まとめて移動したいことが多いでしょう。そこで **group shapes in word** が活躍します。

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**なぜグループ化するのか:**  
シェイプをグループ化すると、移動・回転・サイズ変更といった変換が全体に適用されます。これは Word の UI で複数シェイプを選択して *Group* をクリックしたときと同じ挙動です。また、後続のコードでも多数のオブジェクトを個別に操作する必要がなくなるため、コードがシンプルになります。

> **エッジケース:** 後でグループを解除したい場合は `group.getParentNode().removeChild(group)` を呼び出し、子要素を個別に再挿入してください。

### ## DOCX として文書を保存し、出力を確認

最後にファイルを永続化します。このステップで **save document as docx** の要件を満たします。

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**期待される結果:**  
生成された `GroupShapeExample.docx` を Microsoft Word で開くと、青い長方形と緑の楕円がグループ化された状態で表示されます。グループ全体をドラッグすれば、両シェイプが同時に移動します。UI で期待できる動作と同様です。

> **ヒント:** PDF が必要な場合は `SaveFormat.PDF` を使用すれば、コードを変更せずに PDF バージョンを出力できます。

### ## 完全動作サンプルとよくある落とし穴

以下はそのままコピペして実行できる Java クラスです。出力フォルダを調整し、*Run* をクリックしてください。

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### よくある落とし穴と回避策

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | `Document` 作成後に `DocumentBuilder` をインスタンス化し忘れる。 | `new DocumentBuilder(doc)` をシェイプ挿入前に必ず実行する。 |
| **Shapes appear off‑page** | ピクセル単位を使用したり、余白を考慮しなかったりするため。 | Aspose.Words はポイント単位を期待します。72 pt = 1 in。`setLeft`/`setTop` を適切に調整してください。 |
| **Group disappears after save** | グループ化を保存後に行っている。 | `doc.save()` を呼ぶ前に必ずシェイプをグループ化する。 |
| **File not found on save** | 出力ディレクトリが存在しない。 | `new File("output").mkdirs();` でディレクトリを作成するか、既存のパスを使用してください。 |

---

## 結論

ここまでで、**create word document** をゼロから作成し、**add shapes to word**、**insert rectangle shape**、**group shapes in word**、そして **save document as docx** までを数行の Java で実現しました。Aspose.Words の強みはシンプルなオブジェクトモデルにあり、Word ファイルをキャンバスのように扱い、シェイプで描画し、必要な形式でエクスポートできます。

さらに挑戦したいですか？ 長方形を星形に変えてみたり、`Shape.getTextBox()` でシェイプ内部にテキストを入れたり、`shape.setRotationAngle(45)` で回転させてみたり。API は豊富で、可能性はほぼ無限です。

ブックマークへのシェイプリンクや埋め込みフォント付き PDF 出力など、より高度なシナリオについて質問があればコメントを残してください。一緒に掘り下げていきましょう。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、別の実装アプローチを探求したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}