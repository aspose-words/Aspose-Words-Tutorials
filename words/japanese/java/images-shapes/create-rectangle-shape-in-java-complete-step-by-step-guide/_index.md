---
category: general
date: 2026-07-03
description: Javaで長方形のシェイプを作成し、シェイプに影を追加する方法、影効果の適用、シェイプの透明度設定、そして空白のドキュメントをすばやく作成する方法を学びましょう。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: ja
og_description: Javaで影と透明度を持つ長方形を作成し、空白のドキュメントを使用します。このガイドに従って形状操作をマスターしましょう。
og_title: Javaで長方形を作成する – 完全プログラミングチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Javaで矩形を作成する – 完全ステップバイステップガイド
url: /ja/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaで長方形シェイプを作成 – 完全ステップバイステップガイド

JavaでWord文書に**長方形シェイプを作成**する方法を考えたことはありますか？ あなただけではありません—開発者はしばしば幾何学的なグラフィックを手早く追加し、微妙な影を付けてレイアウトをより洗練されたものにしたいと考えます。このチュートリアルでは、**空白文書の作成**から**シェイプへの影の追加**、**影効果の適用**、さらには**シェイプの透明度設定**まで、全工程を順に解説します。

次のコードスニペットは、プロジェクトにコピー＆ペーストできる完全に機能する例です。外部ドキュメントは不要です—手順に従い「なぜ」かを理解すれば、数秒で影付き長方形を生成できます。

## 学べること

- Aspose.Words for Java を使用してプログラムで**長方形シェイプを作成**する方法。
- **シェイプへの影の追加**に必要な正確な呼び出しと、視覚プロパティの設定方法。
- **影効果の適用**と、オフセット、ぼかし半径、色などのパラメータ調整方法。
- より微妙な外観のための**シェイプの透明度設定**テクニック。
- **空白文書の作成**、シェイプの挿入、結果の保存方法。

> **プロのコツ:** これらすべての操作は単一の `Document` インスタンス上で行われるため、途中のファイル I/O を気にせずに連続して実行できます。

## 前提条件

本格的に始める前に、以下が揃っていることを確認してください。

- Java 17（または最新の JDK）をインストール済み。
- Aspose.Words for Java ライブラリをプロジェクトに追加（Maven 座標: `com.aspose:aspose-words:23.12`）。
- Java IDE またはシンプルなテキストエディタ—特別なものは不要で、コンパイルと実行ができれば OK。

これらが不足している場合は、Oracle から JDK を取得し、Maven または Gradle で Aspose の依存関係を追加してください。設定が完了すれば、すぐに作業を開始できます。

## ステップ 1: **空白文書の作成** – すべての基盤となるキャンバス

最初に必要なのは空の `Document` オブジェクトです。新しい紙のようなものと考えてください。これがなければ、長方形を配置する場所がありません。

```java
// Step 1: Create a new blank document
Document document = new Document();
```

なぜ空白文書から始めるのでしょうか？ すべてのシェイプは `Section` 内に存在し、新しくインスタンス化された `Document` にはデフォルトのセクションが既に含まれ、ノードを受け取るボディが用意されています。このステップを省略すると、後で手動でセクションを作成しなければならず、不要な複雑さが増します。

## ステップ 2: **長方形シェイプの作成** とサイズの定義

キャンバスが用意できたので、**長方形シェイプを作成**しましょう。`Shape` クラスは文書参照と `ShapeType` を受け取ります。ここでは `RECTANGLE` を選び、幅と高さをポイント単位で設定します（1 pt ≈ 1/72 インチ）。

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

なぜ `WrapType.INLINE` を設定するのでしょうか？ インラインラップはシェイプを段落内の文字のように扱い、周囲のテキストと一緒に移動します。浮動的な動作が必要な場合は、`WrapType.SQUARE` や `WrapType.TOP_BOTTOM` に切り替えてください。

## ステップ 3: **影効果の適用** – 長方形に奥行きを付ける

平坦な長方形は… 文字通り平らに見えます。影を追加すると立体感が出ます。`ShadowEffect` インスタンスを作成し、視覚プロパティを調整して**影効果を適用**します。

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

これを少し分解すると:

- **Color** – `Color.getGray(0.5)` は 50 % のグレーを生成し、ニュートラルでほとんどの背景に適します。
- **OffsetX/Y** – 正の値は影を右下に、負の値は左上に移動させます。
- **BlurRadius** – 値が大きいほど、柔らかく拡散した影になります。
- **Transparency** – `0`（不透明）から `1`（完全に透明）までの範囲です。ここでは微妙な効果のために `0.3` を選びました。

## ステップ 4: **シェイプへの影の追加** – 効果をバインドする

効果を作成しただけでは不十分です。`ShadowEffect` オブジェクトを長方形に割り当てて**シェイプへの影の追加**を行う必要があります。

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

内部では、この呼び出しが Word が影を描画するために使用する基礎的な OpenXML マークアップ（`<w:shdw>`）を更新します。保存された `.docx` を確認すれば、設定したパラメータが入った `<w:effect>` 要素が見られます。

## ステップ 5: **シェイプの透明度設定** – 任意ですがしばしば有用

場合によっては、長方形自体を半透明にして背景のテキストを透過させたいことがあります。`Shape` クラスは `setFillColor` と `setFillTransparency` を提供しています。以下は長方形を 40 % 透明にする簡単な例です。

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

なぜこのようにするのでしょうか？ 背景のコンテンツを読みやすく保ちつつ、透かしやハイライトされた呼び出しを想像してください。デザインに合わせて透明度の値を調整しましょう。

## ステップ 6: シェイプを文書に挿入する

長方形を作成し、影を追加し、（任意で）透明度も設定しました。最後のステップは**シェイプを文書の最初のセクションに追加**することです。

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

シェイプをボディに追加すると、最初の段落の末尾に配置されます。特定の挿入位置が必要な場合は、対象の `Paragraph` を取得し、`insertBefore` または `insertAfter` を使用してください。

## ステップ 7: 文書を保存 – 結果を確認

これまでの作業は、1 回の `save` 呼び出しで完了します。環境に合わせたパスを選択してください。

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

生成された `ShadowShape.docx` を Microsoft Word または LibreOffice で開くと、柔らかなグレーの影が付いた鮮明な長方形が表示されます。オプションのステップを実行した場合は、若干透明になっています。ビジュアルはプログラムで定義したパラメータと一致しています。

---

![Word文書で影付き長方形シェイプを作成](https://example.com/images/rectangle-shadow.png "影付き長方形シェイプの作成")

*画像代替テキスト:* **影付き長方形シェイプの作成** – 最終出力のビジュアル表現。

## よくある質問とエッジケース

### 別の影の色にしたい場合は？

`setColor` 呼び出しを変更するだけです。

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

鮮やかすぎる影はプロフェッショナルでない印象になることがあるので、控えめな色調が通常は最適です。

### 同じ影を複数のシェイプに適用できますか？

はい。`ShadowEffect` インスタンスを1つ作成し、設定した後で再利用できます。

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

他のシェイプに付与した後で `ShadowEffect` を変更しないようにしてください。すべてのシェイプを同時に更新したい場合を除きます。

### 影のぼかしを動的に変更するには？

`setBlurRadius` に対応する UI スライダーを用意します。`2`〜`12` の値が一般的で、数値が大きくなるほどクリアな影ではなく「グロー」効果になります。

### シェイプをインラインではなく浮動させたい場合は？

ラップタイプを変更してください。

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

## 完全な動作例

以下は、説明したすべてのステップを組み込んだ、コピー＆ペースト可能な完全なプログラムです。通常の Java アプリケーションとして実行してください。

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**期待される出力:** `ShadowShape.docx` を開くと、幅 200 × 100 pt の白い長方形が最初の段落の中央に配置され、5 pt のオフセットと半径 8 のぼかしを持つ中程度のグレーの影が付いています。透明度は 30 % です。長方形自体は 40 % 透明で、下のテキストが透けて見えるようになっています。

## まとめ

ここまでで、**長方形シェイプの作成**、**シェイプへの影の追加**、**影効果の適用**、さらには**シェイプの透明度設定**までを、**空白文書の作成**を基盤として実現しました。この手法はシンプルで、Aspose.Words の流暢な API を活用しており、円形や星形、カスタムポリゴンへも拡張可能です。

次にやるべきことは何ですか？ `ShapeType.RECTANGLE` を `ShapeType.OVAL` に置き換えて影付き円を生成したり、グラデーション塗りを試してみたりしてください。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を応用した、密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [JavaでWord文書を作成 – 影付き長方形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [影付き長方形シェイプで空白Word文書を作成 – ステップバイステップガイド](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words シェイプ影チュートリアル – C#でWordシェイプに影を追加](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}