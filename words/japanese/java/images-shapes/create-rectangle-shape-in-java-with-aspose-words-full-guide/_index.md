---
category: general
date: 2026-07-06
description: Aspose.Words を使用して Java で矩形シェイプを作成する – シェイプに影を付け、透明度を設定し、ドキュメントを PDF
  として保存する方法を学びます。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: ja
og_description: Aspose.Words を使用して Java で矩形シェイプを作成します。このガイドでは、シェイプに影を追加し、シェイプの透明度を設定し、ドキュメントを
  PDF として保存する方法を示します。
og_title: Javaで長方形シェイプを作成 – Aspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: JavaでAspose.Wordsを使用して矩形シェイプを作成する – 完全ガイド
url: /ja/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java と Aspose.Words で矩形シェイプを作成 – 完全ガイド

低レベルの描画 API と格闘せずに Java で **矩形シェイプを作成** できるか、考えたことはありませんか？ あなたは一人ではありません。多くの開発者は、Word 文書に矩形を手軽に挿入し、さりげない影を付け、透明度を調整し、最終的に PDF として出力したいと考えています。

このチュートリアルでは、まさにそれをステップバイステップで、完全に実行可能なコードとともに解説します。最後まで読むと、Aspose.Words for Java を使って **シェイプに影を追加** する方法、**シェイプの透明度を設定** する方法、そして **ドキュメントを PDF として保存** する方法が分かります。余計な説明は省き、すぐにプロジェクトにコピペできる実践的なガイダンスだけを提供します。

## 学べること

- Java プロジェクトで Aspose.Words を使用するために必要な最小限のセットアップ。  
- プログラムから **矩形シェイプを作成** する方法。  
- **シェイプに影を追加** し、ぼかし、オフセット、透明度を調整するために必要な正確な呼び出し。  
- 矩形が周囲のコンテンツと自然に馴染むように **シェイプの透明度を設定** する方法。  
- 余分な変換ステップなしで **ドキュメントを PDF として保存** する最もシンプルな手法。  

基本的な Java が扱えて、Maven または Gradle ビルド環境があればすぐに始められます。

## 前提条件

- Java 8 以降。  
- Aspose.Words for Java 23.x（または執筆時点での最新バージョン）。  
- IDE またはコマンドラインビルドツール（IntelliJ、Eclipse、Maven、Gradle のいずれか）。  

> **プロのコツ:** Aspose は評価用の無料一時ライセンスを提供しています。アカウントポータルから取得し、`license.xml` ファイルをクラスパスに配置してください。そうしないと PDF に透かしが表示されます。

---

## ステップ 1: Aspose.Words で **矩形シェイプを作成**

最初に必要なのは空の `Document` と `DocumentBuilder` です。ビルダーはシェイプを文書のフローに直接挿入できる作業馬です。

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Why this matters:** `ShapeType.RECTANGLE` は Aspose に対して完全な矩形が欲しいことを示します。幅と高さはポイント単位で表され（1 pt ≈ 1/72 in）、最終サイズを細かく制御できます。

---

## ステップ 2: **シェイプに影を追加**

矩形ができたので、さりげないドロップシャドウを付けましょう。`ShadowFormat` オブジェクトは、ぼかし半径、X/Y オフセット、透明度まで、必要なすべてを公開しています。

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Why this matters:** ぼかしのない影はハードな線に見えてしまい、デザイナーが求めるものではほとんどありません。`setBlur` 呼び出しでエッジを滑らかにし、`setTransparency` で影を背景に溶け込ませます。これらの値は UI ガイドラインに合わせて調整してください。

---

## ステップ 3: **シェイプの透明度を設定**

場合によっては矩形自体を半透明にしたいことがあります（ロゴや透かしを重ねる場合など）。Aspose ならワンライナーで実現できます。

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Why this matters:** 透明度はシェイプを重ねる際の命綱です。影の透明度は独立しているため、薄いシェイプに濃い影を付けるといったデザインも可能です。

---

## ステップ 4: **ドキュメントを PDF として保存**

すべてのビジュアル作業が完了したら、最後にドキュメントを永続化します。Aspose.Words は直接 PDF に書き出せるため、別途変換ライブラリは不要です。

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Why this matters:** `SaveFormat.PDF` を指定すると、ライブラリがフォント埋め込み、画像圧縮、PDF/A 準拠などを内部で処理します。生成されたファイルは配布、印刷、アーカイブにすぐ使えます。

---

## 完全動作サンプル

すべてを組み合わせた、実行可能なクラス全体です。コピー＆ペーストし、出力フォルダーを調整すれば、リアルな影を落とした矩形が入った PDF が作成できます。

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Expected output:** `RectangleWithShadow.pdf` を開くと、1 ページ目の中央に薄いグレーの矩形が配置され、ソフトで半透明の影がページから少し持ち上がっているのが確認できます。シェイプ自体は 20 % 透明で、下にあるテキスト（追加していれば）が透けて見えます。

---

## よくある質問とエッジケース

### 1️⃣ より大きな矩形が必要な場合は？

`insertShape` の幅と高さのパラメーターを変更するだけです。72 pt = 1 in であることを覚えておいてください。たとえば `400.0, 200.0` と指定すれば、5.5 × 2.8 インチの矩形になります。

### 2️⃣ 影の色を別のものに変えられますか？

もちろんです。`ShadowFormat` クラスは `setColor(java.awt.Color)` も提供しています。さりげないグレーの影にしたい場合は `shadow.setColor(java.awt.Color.DARK_GRAY);` を試してください。

### 3️⃣ `save document as pdf` はすべてのプラットフォームで動作しますか？

はい。Aspose.Words for Java はプラットフォームに依存せず、互換性のある JRE があれば Windows、macOS、Linux のいずれでも同じコードが実行できます。

### 4️⃣ 後から影を削除するには？

`rect.getShadowFormat().clear();` と呼び出すか、`Visible` プロパティを `false` に設定します（`shadow.setVisible(false);`）。

### 5️⃣ DPI と画像品質はどうなりますか？

PDF に保存する際、Aspose はベクターグラフィック（シェイプなど）に対して自動的に 300 DPI を使用するため、ズームレベルに関係なく鮮明な結果が得られます。

---

## プロのコツとベストプラクティス

- **Batch processing:** 数十件の PDF を生成する必要がある場合は、`Document` インスタンスを 1 つだけ再利用し、イテレーション間でセクションだけをクリアして GC の負荷を減らします。  
- **Licensing:** `License license = new License(); license.setLicense("license.xml");` を `main` の冒頭に配置して、評価用透かしを回避します。  
- **Performance:** シンプルなシェイプの影描画はコストが低いですが、複雑なパスになると PDF 生成が遅くなることがあります。大量バッチ処理時はプロファイルを取ってください。  
- **Testing:** まず `Document.save(..., SaveFormat.DOCX)` で Word に保存し、シェイプが正しく表示されることを確認してから PDF に変換すると安全です。

---

## 結論

これで、Aspose.Words を使って Java で **矩形シェイプを作成**し、**シェイプに影を追加**し、**シェイプの透明度を設定**し、最終的に **ドキュメントを PDF として保存** する方法が分かりました。コードは自己完結型で、最新の Aspose ライブラリで動作し、ほとんどのドキュメント自動化シナリオで必要となる主要 API 呼び出しを示しています。

次のチャレンジに挑みますか？ 矩形を楕円に置き換えてみたり、グラデーション塗りを試したり、テキストフレームに **影を追加** してみたりしてください。同じ原則が適用でき、Aspose API があれば簡単に実装できます。

Happy coding, and feel free to drop a comment if you hit any snags!

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説付きの完全なコード例が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Word ドキュメント作成 Java – 矩形シェイプに影効果を追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java でドキュメントを PDF として保存する方法](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java の DocumentBuilder を使用してフォームフィールドを作成し、コンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}