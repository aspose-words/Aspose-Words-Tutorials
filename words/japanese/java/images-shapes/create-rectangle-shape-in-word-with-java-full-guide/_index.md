---
category: general
date: 2026-02-10
description: Aspose.Words for Java を使用して Word 文書に矩形シェイプを作成します。影の色の設定方法、影の追加方法、そしてプログラムで
  Word 文書を作成する方法を学びます。
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: ja
og_description: Aspose.Words for Java を使用して Word 文書に長方形の図形を作成します。このステップバイステップのチュートリアルに従い、影の色を設定し、影を追加して、Word
  文書を作成してください。
og_title: JavaでWordに長方形の図形を作成する – 完全ガイド
tags:
- Aspose.Words
- Java
- Document Automation
title: JavaでWordに長方形の図形を作成する – 完全ガイド
url: /ja/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

codes exactly as original.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWordに矩形シェイプを作成 – 完全ガイド

Word文書で **矩形シェイプを作成** したいと思ったことはありませんか？最初はどこから始めればいいか分からないことが多いです。多くの開発者がプログラムでWordにグラフィックを描く際に壁にぶつかります。良いニュースは、Aspose.Words for Java を使えば、ページに矩形を配置し、きれいな影を付け、数秒でファイルを保存できることです。このチュートリアルでは、**影の追加方法**、**影の色の設定**、そして **Word文書の作成** をゼロから詳しく解説します。

必要なものすべてをカバーします：必須ライブラリ、各コード行、設定が重要な理由、公式ドキュメントに載っていないちょっとしたコツ。最後まで読めば、ソフトなグレーの影付き矩形シェイプを作成し、*Shadow.docx* として保存する実行可能なサンプルが手に入ります。

## 前提条件 – 開始前に必要なもの

| Requirement | Reason |
|-------------|--------|
| Java Development Kit (JDK) 8 or newer | Aspose.Words は最新の JDK で動作します。 |
| Maven or Gradle (optional) | Aspose.Words の依存関係追加が簡単になります。 |
| Aspose.Words for Java license (or a free trial) | ライブラリは商用ですが、トライアルでテスト可能です。 |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | サンプルをすぐに実行・デバッグできます。 |

既に Java プロジェクトがある場合は、次の Maven 座標を追加するだけです。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

それ以上の設定は不要です。`public static void main` メソッドだけあれば動作します。

![矩形シェイプ例](https://example.com/rectangle-shadow.png "Wordで影付き矩形シェイプの作成")

*画像の代替テキスト: シアンの矩形にグレーの影が付いた矩形シェイプ例を示しています。*

## 手順 1 – 新しい Word 文書を作成

最初に空の文書を作成します。これは、後で描画するための新しい Word ファイルを開くイメージです。

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

なぜ空の `Document` から始めるのか？ Aspose.Words では `Document` クラスがすべての操作のキャンバスとして扱われます。段落や表、シェイプの追加はすべてこのオブジェクト上で行われます。このステップを省くと、何かを挿入しようとした瞬間に `NullPointerException` が発生します。

## 手順 2 – DocumentBuilder の設定

`DocumentBuilder` は `Document` に書き込むためのペンのようなものです。カーソル位置を自動で管理してくれるので、コンテンツ追加に最適です。

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

「直接 Document を操作しないのはなぜ？」と思うかもしれません。答えは、Builder がセクション処理などの低レベルな詳細を抽象化してくれるため、コードがすっきりし、エラーが減ります。

## 手順 3 – 矩形シェイプを挿入

さあ楽しいパートです—**シェイプの作成方法**。幅 100 × 高さ 50 ポイントの矩形を挿入し、シアンの塗りつぶしを設定して見えるようにします。

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

ポイント:

* `ShapeType.RECTANGLE` は矩形を指定します。`OVAL`、`LINE` などに置き換えることも可能です。
* サイズはポイント単位です (1 pt ≈ 1/72 in)。レイアウトに合わせて調整してください。
* 塗りつぶし色が無いと白紙上で形が見えなくなるため、シアンで目立たせています。

## 手順 4 – 影を追加し **影の色を設定**

ここで **影の追加方法** に答えます。`ShadowFormat` オブジェクトが影の色からぼかし半径まで全てを制御します。

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

なぜこの値なのか？

* **Visibility** – `setVisible(true)` が無いと他の設定は無視されます。
* **Color** – グレーは明暗どちらの背景でも自然に見える中立的な色です。`java.awt.Color.GRAY` を好きな `java.awt.Color` に置き換えて構いません。
* **Blur radius** – `5.0` は柔らかな羽根効果です。数値を大きくすると影が拡散します。
* **OffsetX/Y** – 右下にずらすことで、左上から光が当たっているように見せます。
* **Transparency** – 半透明にすると印刷時にもページに馴染みやすくなります。

よりシャープにしたい場合はぼかし半径を `0` にし、オフセットを大きくしてみてください。影は視覚的要素なので、ドキュメントのデザインに合わせて試行錯誤することをおすすめします。

## 手順 5 – 文書を保存

最後にすべてを `.docx` ファイルに保存します。好きなパスを指定してください。ただしディレクトリが存在することを確認してください。

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Microsoft Word で *Shadow.docx* を開くと、シアンの矩形に右下へ 4 pt ずれた微かなグレーの影が表示されます。これが **Word文書の作成** フロー全体です。

### 期待結果

| Element | Appearance |
|---------|------------|
| Rectangle | シアン塗り、100 × 50 pt のサイズ |
| Shadow | グレー、30 % 透明、5 pt ぼかし、オフセット (4, 4) |
| File | 指定したパスに `Shadow.docx` が保存されます |

シェイプが表示されない場合は、塗りつぶし色がページ背景と同じになっていないか、影が `visible` に設定されているかを再確認してください。

## プロのコツとよくある落とし穴

* **Pro tip:** `rectangle.setStrokeColor(java.awt.Color.BLACK);` を使うとシェイプに枠線が付き、印刷時に矩形がより目立ちます。
* **Watch out for:** 読み取り専用フォルダーに保存しようとすると `IOException` が発生します。書き込み可能な場所を選ぶか、権限を調整してください。
* **Edge case:** 透明な塗りつぶしが必要な場合は `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);` とします。形自体は見えませんが、影は残るため透かし風グラフィックに利用できます。
* **Performance note:** ループで数百個のシェイプを追加するとメモリ使用量が増加します。すべてのシェイプを追加し終えた後に一度だけ `document.save` を呼び出すようにしましょう。

## 完全動作例

以下は `ShadowDemo` という名前の Java クラスにそのまま貼り付けて使用できる完全なプログラムです。Aspose.Words の JAR がクラスパスにあることを前提にコンパイル・実行できます。

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

プログラムを実行し、生成された *Shadow.docx* を開くと、説明通りの矩形と影が確認できます。

## もっと多くのシェイプが必要な場合は？

「**矩形シェイプを** 複数回作成したり、他のシェイプを使えるか？」と疑問に思うかもしれません。もちろん可能です。挿入コードをループで回し、`builder.moveTo` や `builder.insertParagraph` で座標を調整すれば OKです。同じ影設定を再利用したい場合はヘルパーメソッドに切り出すと便利です。

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

各シェイプ挿入後に `applyStandardShadow(rectangle);` を呼び出すことで、コードの重複（DRY）を防げます。

## 次のステップ – 基礎を超えて

影の追加方法が分かったので、次の関連トピックもぜひ探求してください：

* **テキストランの影の色を設定** – タイトルに微妙な立体感を付与します。
* **表や画像を含む Word 文書の作成** – シェイプと他コンテンツを組み合わせます。
* **Word の組み込み機能を使ったシェイプ アニメーションの作成**  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}