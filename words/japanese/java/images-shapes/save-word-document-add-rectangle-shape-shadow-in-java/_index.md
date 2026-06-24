---
category: general
date: 2026-06-20
description: JavaでAspose.Wordsを使用し、矩形の図形を追加して影を付けたWord文書を保存します。図形の挿入方法をステップバイステップで学びましょう。
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: ja
og_description: Aspose.Words JavaでWord文書を保存します。このガイドでは、長方形のシェイプを追加し、影を適用して段落に挿入する方法を示します。
og_title: Word文書を保存 – Javaで矩形シェイプと影を追加
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Word文書を保存 – Javaで長方形の図形と影を追加
url: /ja/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordドキュメントを保存 – Javaで矩形シェイプと影を追加

レイアウトをカスタマイズした後に **Wordドキュメントを保存** する方法を考えたことはありませんか？ あなたは一人ではありません。多くの開発者がプログラムで DOCX ファイルを拡張しようとしたときにこの壁にぶつかります。良いニュースは、Aspose.Words for Java を使えば **Wordドキュメントを保存** でき、任意の位置に矩形シェイプを配置し、さらにそのシェイプにさりげない影を付けることができるということです。

このチュートリアルでは、既存ファイルの読み込み、**矩形シェイプの追加**、**影の設定**、シェイプを最初の段落に挿入、そして最終的に **Wordドキュメントを保存** するまでの全工程を解説します。最後には、手動で調整することなく完成された `shadow.docx` を生成する実行可能な Java プログラムが手に入ります。

> **必要なもの**  
> * Java 17（または最近の JDK）  
> * Aspose.Words for Java ライブラリ（Maven/Gradle または JAR）  
> * 既知のフォルダーにある入力 DOCX ファイル（`input.docx`）  

これらの基本が揃っていれば、さっそく始めましょう。

---

## Wordドキュメントを保存 – 完全な Java サンプル

以下はそのまま実行可能なソースコードです。IDE に貼り付け、パスを調整して **Run** をクリックしてください。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**期待される結果:** プログラム実行後に `shadow.docx` を開くと、元のコンテンツに加えて 100 × 50 pt の黒い矩形がソフトな影とともに最初の段落の先頭に表示されます。

---

## Wordドキュメントに矩形シェイプを追加する

矩形シェイプを使う理由は何でしょうか？ ビジュアルアンカーとして、コールアウト、プレースホルダー、シンプルなグラフィックに最適です。Aspose.Words の `Shape` クラスはすべての描画オブジェクトを抽象化し、`ShapeType.RECTANGLE` で余計な手間なくクリーンな箱を作成できます。

**矩形シェイプを追加する際の重要ポイント**

- **単位はポイント**（1 pt = 1/72 in）。レイアウトに合わせて `setWidth`/`setHeight` を調整してください。  
- シェイプはドキュメントのノードツリー内に存在するため、`Paragraph` や `Run` が許可されている場所ならどこにでも挿入できます。  
- 影を適用する前に、矩形の塗りつぶしや線の色などをスタイル設定できます。

> **プロのコツ:** 透明な塗りつぶしが必要な場合は `rectangle.getFill().setTransparent(true);` を呼び出します。

---

## シェイプに影を適用する

影は奥行きを生み出します。`Shape` に付随する `Shadow` オブジェクトは、Word の UI オプションに直接対応するプロパティを公開しています。

| Property | 機能 | 典型的な値 |
|----------|------|------------|
| `setVisible(true)` | 影を有効にする | `true` |
| `setColor(Color.BLACK)` | 影の色 | `Color.BLACK` |
| `setBlurRadius(5.0)` | エッジの柔らかさ | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | 水平/垂直方向のオフセット | 各 `4.0` |
| `setTransparency(0.3)` | 透明度（0 = 不透明、1 = 透明） | `0.3` |

**「シェイプに影を適用する方法」** を尋ねたときの答えは、これら 6 つのプロパティを調整するだけです。オフセットを大きくすれば「持ち上げられた」感じになり、ブラー半径を上げればより拡散した外観になります。

> **よくある落とし穴:** `setVisible(true)` を忘れると、他のプロパティを設定していても影が表示されません。

---

## シェイプを段落に挿入する方法

シェイプの挿入は魔法ではなく、単なるノード操作です。`appendChild` メソッドはシェイプを段落の子ノードの末尾に配置します。テキストの前にシェイプが必要な場合は `insertBefore` を使用してください。

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

この小さな変更で **シェイプの挿入方法** に対する答えが得られます。既存の Run の前、見出しの後、あるいはテーブルセル内（適切な `Cell` ノードを取得すれば）にシェイプを配置できます。

---

## コードの実行と出力の確認

1. **コンパイル** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **実行** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **`shadow.docx` を** Microsoft Word または LibreOffice で開く。最初の段落の先頭にソフトな黒影付き矩形が表示されているはずです。

シェイプが表示されない場合は、次を再確認してください。

- 入力ファイルのパスが正しいか。  
- 使用している Aspose.Words のバージョンが最新か（API は 20.12 以前と若干異なります）。  
- ドキュメントに少なくとも 1 つの段落が存在するか（存在しないと `getParagraphs().get(0)` が IndexOutOfBoundsException を投げます）。

---

## よくある質問 (FAQ)

**Q: 特定のページにシェイプを追加できますか？**  
A: はい。対象の `Section` または `PageSetup` を取得し、そのページ上の段落にシェイプを挿入します。

**Q: .doc ファイルでも動作しますか？**  
A: 完全に対応しています。Aspose.Words はフォーマットを抽象化するため、同じコードで `.doc` でも `.docx` でも **Wordドキュメントを保存** できます。

**Q: 楕円など別の形状が必要な場合は？**  
A: `ShapeType.RECTANGLE` を `ShapeType.ELLIPSE` に置き換えるだけです。影のプロパティはそのまま使用できます。

---

## 結論

これで **Wordドキュメントを保存** しながら **矩形シェイプを追加**、**影を適用**、そして **シェイプを最初の段落に挿入** する方法がマスターできました。形状の種類を変えたり、影の設定を調整したり、テーブルやヘッダーに配置したりと、さまざまなシナリオに拡張可能です。ドキュメント自動化のニーズに応じて、無限の可能性が広がります。

次のチャレンジに進みませんか？ 複数のシェイプを重ねたり、矩形内にテキストを入れたり、チャートや透かし付きのレポートを生成したりしてみてください。ここで学んだ基礎がすべての応用タスクの土台となります。

Happy coding, and may your Word automation be shadow‑free of bugs!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to save word as pcl with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}