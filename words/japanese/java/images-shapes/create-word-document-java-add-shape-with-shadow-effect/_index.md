---
category: general
date: 2026-06-30
description: Word文書に図形を追加し、図形の塗りつぶし色を設定し、影効果を適用するJavaのサンプルを数行で作成する。
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: ja
og_description: Word文書に図形を追加し、図形の塗りつぶし色を設定し、影効果を適用する方法を示すJavaチュートリアルを作成する。
og_title: JavaでWord文書を作成 – 影効果付きシェイプを追加
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: JavaでWord文書を作成 – 影効果付きシェイプを追加
url: /ja/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメントを Java で作成 – 影効果付きシェイプの追加

四角形を描画し、さりげない影を付ける **create word document java** コードが必要になったことはありませんか？ あなただけではありません。レポートや請求書、シンプルなチラシを生成する場合でも、プログラムで **add shape to word document** ができると手作業の調整にかかる時間を大幅に削減できます。  

このガイドでは、完全に実行可能なサンプルを順に解説します。このサンプルは新しい Word ファイルを作成するだけでなく、Aspose.Words for Java を使用して **set shape fill color**、**how to add shadow to shape**、そして最終的に **apply shadow effect shape** を行います。余計な説明は省き、IDE にコピー＆ペーストできる正確な手順だけを示します。

> **Pro tip:** Aspose.Words が初めての方は、クラスパスに最新の JAR があることを確認してください。使用している API はバージョン 23.10 以降で動作します。

## 作成するもの

このチュートリアルの最後には、次の内容を含む `.docx` ファイルが作成されます：

* 最初から作成した空白の Word ドキュメント。
* 1 ページ目に挿入された黄色の矩形（150 × 80 pts）。
* 数ポイントだけオフセットされた柔らかいグレーの影で、シェイプが浮き上がって見える。
* 上記すべてが、ほんの数行の Java 文で実現できる。

外部テンプレートや煩雑な XML は不要です。誰でも実行できる純粋な Java コードです。

## Word ドキュメントを Java で作成 – シェイプの挿入

最初に必要なのは新しい `Document` オブジェクトと `DocumentBuilder` です。ビルダーはドキュメント内に描画できるペンのようなものと考えてください。

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* `Document` はファイル全体を表し、`DocumentBuilder` は `insertShape` などの便利なメソッドを提供します。ビルダーがなければ低レベルのノードを直接操作する必要があり、はるかに手間がかかります。

## Word ドキュメントにシェイプを追加 – 矩形の挿入

ここで実際に **add shape to word document** を行います。今回は矩形ですが、Aspose がサポートする任意の `ShapeType`（楕円、矢印など）を選択できます。

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

この1行で次の3つのことが行われます：

1. シェイプオブジェクトを作成する。
2. 現在のカーソル位置（デフォルトではページ左上）に配置する。
3. ドキュメント内部のノードコレクションに追加する。

この後に *how to add shadow to shape* が気になる場合は、次のセクションまで読み進めてください。

## シェイプの塗りつぶし色を設定 – 外観のカスタマイズ

白い矩形だけでは面白くないので、**set shape fill color** を明るい色に設定しましょう。Aspose が直接受け取れる Java の `java.awt.Color` クラスを使用します。

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

`YELLOW` を `RED`、`GREEN`、あるいは任意のカスタム RGB 値（`new Color(123, 45, 67)`）に置き換えても構いません。塗りつぶし色は影が適用される前に最初に目にする表面です。

## シェイプに影を追加 – 影の設定

ここが魔法の部分です。Aspose.Words は `ShadowEffect` オブジェクトを提供し、影の外観を細かく調整できます。

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**各プロパティの重要性:**

| Property | What it does | Typical values |
|----------|--------------|----------------|
| `setColor` | 影の色相を決定します。多くの場合はグレーで十分ですが、`Color.BLUE` のように大胆な色も指定可能です。 | Any `java.awt.Color` |
| `setBlurRadius` | エッジの柔らかさを制御します。数値が大きいほどぼやけた外観になります。 | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | 影を左右・上下に移動させます。正の値は右下方向に影を移動させます。 | -10 – 10 |
| `setTransparency` | 不透明度を設定します。0 が不透明、1 が完全に透明です。 | 0.0 – 1.0 |

**how to add shadow to shape** がレイアウトを崩さずに行えるか気になる場合、オフセットは控えめに保つことがポイントです。大きすぎると影が次のページにまではみ出す可能性があります。

## 影効果シェイプの適用 – ドキュメントの保存

シェイプのスタイルと影の設定が完了したら、あとはファイルを保存するだけです。

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`YOUR_DIRECTORY` を、マシン上に存在する絶対パスまたは相対パスに置き換えてください。プログラムを実行した後、Microsoft Word または LibreOffice で `ShadowShape.docx` を開くと、適用したグレーの影によりページ上に浮かんでいる黄色の矩形が表示されます。

## 結果の確認 – 確認ポイント

生成されたファイルを開くと：

* 矩形はカーソルが開始した位置（デフォルトではページ左上）に配置されているはずです。
* 塗りつぶしは明るい黄色です。
* さりげないグレーのぼかしが右下に 4 pts オフセットされ、透明度は約 30 % です。

影が強すぎる場合は `BlurRadius` を下げるか `Transparency` を上げてください。シェイプ自体が見えない場合は `setFillColor` の呼び出しを再確認しましょう—選択した色がページの背景と同化している可能性があります。

## よくある落とし穴とエッジケース

| Issue | Cause | Fix |
|-------|-------|-----|
| **Shadow disappears** | `Transparency` が `1.0`（完全に透明）に設定されている。 | より低い値（例: `0.3`）に設定する。 |
| **Shape not visible** | 塗りつぶし色がページ背景（多くは白）と同じ。 | `setFillColor` で対照的な色を選択する。 |
| **Shadow clips on page margin** | オフセットにより影が印刷可能領域の外に出ている。 | `OffsetX`/`OffsetY` を減らすか、`PageSetup` で余白を拡大する。 |
| **Compilation error: `cannot find symbol ShadowEffect`** | 影機能を含まない古い Aspose.Words バージョンを使用している。 | Aspose.Words 23.10 以上にアップグレードする（`ShadowEffect` は 22.12 で導入）。 |

## 次のステップ – 基本を超えて

これで **create word document java**、**add shape to word document**、**set shape fill color**、**how to add shadow to shape**、**apply shadow effect shape** のやり方が分かったので、次に何ができるか気になるでしょう。以下にいくつかのアイデアを示します：

* **Dynamic colors** – データベースから RGB 値を取得し、ステータスに応じてシェイプに色を付ける。
* **Multiple shadows** – シェイプをクローンし、各コピーに異なる `ShadowEffect` を設定して二重の影を重ねる。
* **Text inside shapes** – `Shape.getTextFrame()` を使用してキャプションやラベルを埋め込む。
* **Export to PDF** – `document.save("output.pdf", SaveFormat.PDF)` を呼び出して、同等のビジュアル品質を持つ印刷用 PDF を生成する。

これらはすべて、今回示した「ドキュメント作成 → シェイプ挿入 → スタイル設定 → 保存」という基本パターンに基づいています。

## 完全な動作例（コピー＆ペースト用）

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

クラスを実行すると、カレントディレクトリに `ShadowShape.docx` が生成されます。開くと、前述の通りの結果が確認できます。

## 結論

私たちは、**create word document java**、**add shape to word document**、**set shape fill color**、**how to add shadow to shape**、そして最終的に **apply shadow effect shape** を最初から行う方法を示しました—コンパクトで分かりやすいコードサンプルです。  

この手法は意図的にシンプルに設計されているため、複数のシェイプや異なる色、アニメーション風の影など、より複雑なシナリオにも応用できます。API のバージョン互換性に注意し、デザインに合わせて影のパラメータを遠慮なく調整してください。  

試したアレンジはありますか？矩形の背後に画像を重ねたり、シェイプ内に表を追加したりしたかもしれません。ぜひコメントで教えてください。開発者の皆さんがこの例をどのように拡張したか聞くのが楽しみです。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれ、追加の API 機能を習得し、独自プロジェクトで代替実装方法を探求するのに役立ちます。

- [Word ドキュメントを Java で作成 – 影効果付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java で PDF ドキュメントを作成する方法 | Document Processing API](/words/english/java/)
- [Aspose.Words Java: Word ドキュメント処理の包括的ガイド](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}