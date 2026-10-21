---
category: general
date: 2026-08-23
description: Aspose.Words for Java を使用して空白の Word 文書を作成し、図形のグループ化や長方形の色付け方法を学び、数分で
  docx として保存します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: ja
lastmod: 2026-08-23
og_description: Aspose.Words for Javaを使用して空白のWord文書を作成し、図形のグループ化、長方形図形への色付け、そして効率的にdocxとして保存する方法をご覧ください。
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Javaで空白のWord文書を作成し、図形をグループ化する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Javaで空白のWord文書を作成し、図形をグループ化する
url: /ja/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空のWord文書を作成し、Javaでシェイプをグループ化する

プログラムで **空のWord文書** を作成したい場合、Aspose.Words for Java を使用すれば簡単です。このチュートリアルでは、**空のWord文書** の作成方法、**Wordでシェイプをグループ化** する方法、**カラー長方形シェイプ** の適用、そして最終的に **docx として文書を保存** する手順を詳しく解説します。最後まで読むと、任意の Java プロジェクトにすぐ貼り付けられる再利用可能なコードスニペットが手に入ります。

学べること:

* Aspose.Words の Maven/Gradle 依存関係
* 空の Document と `DocumentBuilder` のインスタンス化方法
* `GroupShape` 内で **シェイプをグループ化** する正確な手順
* 長方形シェイプの塗りつぶし色の設定方法
* **docx として文書を保存** するベストプラクティスと出力ファイルの場所

Aspose.Words の事前知識は不要ですが、基本的な Java 開発に慣れており、JDK 8 以上がインストールされていることが前提です。

---

## 前提条件

| 要件 | バージョン / 詳細 |
|-------------|-------------------|
| Java Development Kit | 8 以上 |
| ビルドツール | Maven 3+ または Gradle 6+ |
| Aspose.Words for Java | 23.12 以上（執筆時点での最新バージョン） |
| IDE（任意） | IntelliJ IDEA、Eclipse、VS Code、または任意の Java 対応エディタ |

---

## ステップ 1: プロジェクトに Aspose.Words を追加する

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **プロのコツ:** 社内プロキシを使用している場合は、公式ドキュメントに従って Maven/Gradle が Aspose リポジトリからパッケージを取得できるよう設定してください。

---

## ステップ 2: ビルダーで **空のWord文書** を作成する

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` コンストラクタはメモリ上に空の `.docx` コンテナを作成します。`DocumentBuilder` はコンテンツ（シェイプを含む）を追加するための流暢な API を提供します。

---

## ステップ 3: **Word のグループシェイプ** コンテナを挿入する

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` はミニキャンバスのように機能します。そこに追加したすべてのシェイプは一緒に移動し、**シェイプをグループ化** してレイアウトの一貫性を保つことができます。

---

## ステップ 4: 最初の **カラー長方形シェイプ**（赤）を追加する

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE` 定数でシンプルな長方形を作成します。`getFill().setForeColor(...)` を呼び出すことで **カラー長方形シェイプ** の色を制御できます。`java.awt.Color.RED` は任意の `java.awt.Color` 定数やカスタム RGB 値に置き換え可能です。

---

## ステップ 5: 2 番目の **カラー長方形シェイプ**（緑）を追加し位置を設定する

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

`setLeft`（または `setTop`）でシェイプを **Word のグループシェイプ** コンテナの左上隅からの相対位置に移動させます。これにより、**シェイプをグループ化** した状態で正確な配置が実現します。

---

## ステップ 6: **docx として文書を保存** し結果を確認する

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` メソッドはファイル拡張子が `.docx` であることを検出し、自動的に `.docx` ファイルを書き出します。別の形式（例: PDF）が必要な場合は、対応する `SaveFormat` 列挙体を渡してください。

> **ヒント:** ターゲットディレクトリ（この例では `output/`）が存在しない場合は、`new File("output").mkdirs();` でプログラム的に作成してください。

---

## クイックコピー用のフルソースコード

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**期待される出力:** Microsoft Word で `GroupShapeDemo.docx` を開くと、1 ページに 2 つのカラー長方形（左が赤、右が緑）が表示され、グループとして選択したときに一緒に移動します。

---

## よくある質問とエッジケースの対処法

| 質問 | 回答 |
|----------|--------|
| *同じグループに 2 つ以上のシェイプを追加できますか？* | はい。追加したいシェイプごとに `groupShape.appendChild(yourShape)` を呼び出します。グループは自動的に最も外側のシェイプに合わせてサイズ調整されますが、幅・高さを手動で設定することも可能です。 |
| *別のシェイプタイプ（例: 楕円）が必要な場合は？* | `ShapeType.RECTANGLE` を `ShapeType.ELLIPSE` に置き換えてください。塗りつぶし色のロジックは同じです。 |
| *`Document` オブジェクトを明示的に破棄する必要がありますか？* | Aspose.Words は内部でネイティブリソースを管理します。JVM が終了すればリソースは解放されます。長時間稼働するアプリケーションの場合、**Aspose.Words for Java (Native)** バージョンを使用しているなら `doc.dispose();` を呼び出すことを検討してください。 |
| *Z 順序を変更して片方の長方形を前面に出すには？* | `groupShape.insertAfter(shape, referenceShape);` または `groupShape.insertBefore(shape, referenceShape);` を使用して、グループ内の子要素の順序を入れ替えます。 |
| *異なるセクションにまたがってシェイプをグループ化できますか？* | できません。`GroupShape` は単一の段落またはシェイプコンテナ内に存在する必要があります。セクションを跨いでグループ化したい場合は、各セクションに別々のグループを作成してください。 |

---

## 結論

これで **Aspose.Words for Java** を使って **空のWord文書** を作成し、**Word でシェイプをグループ化** し、**カラー長方形シェイプ** のスタイリングを行い、**docx として文書を保存** する方法が分かりました。このパターンは、シェイプを追加したりオフセットを調整したり、テキスト・画像・ハイパーリンクをグループ内に配置したりすることで、より複雑なレイアウトにも拡張できます。

**次のステップ** として検討できること:

* **Word のグループシェイプ** を使ってフローチャートや UI モックアップを作成する
* **docx として文書を保存** した後に PDF 変換 (`doc.save("out.pdf")`) を試す
* **カラー長方形シェイプ** にグラデーションやパターンを適用してビジュアルを豊かにする
* テーブルやチャートと組み合わせて高度なレポート文書を作成する

寸法、色、シェイプタイプはプロジェクトのブランディングに合わせて自由に変更してください。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを試したりするのに役立ちます。

- [JavaでWord文書を作成 – 影効果付き長方形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Javaで文書をPDFとして保存する方法](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Javaでドキュメントシェイプを使用する](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}