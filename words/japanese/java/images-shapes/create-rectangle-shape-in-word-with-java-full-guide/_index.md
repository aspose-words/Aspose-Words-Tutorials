---
category: general
date: 2026-02-15
description: Java を使用して Word 文書に矩形の図形を作成します。図形の影の追加方法、Word 文書の保存方法、そして Aspose.Words
  を使用した矩形図形の追加方法を学びます。
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: ja
og_description: JavaでWordファイルに長方形の図形を作成します。このガイドでは、図形の影を追加する方法、Word文書を保存する方法、そして長方形の図形をステップバイステップで追加する方法を示します。
og_title: 矩形シェイプの作成 – Java Aspose.Words チュートリアル
tags:
- Aspose.Words
- Java
- Document Automation
title: JavaでWordに長方形の図形を作成する – 完全ガイド
url: /ja/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWordに長方形シェイプを作成 – 完全ガイド

Wordファイルに**長方形シェイプを作成**したいと思ったことはありませんか？始め方が分からないと感じているのはあなただけではありません—レポートや請求書の自動化で多くの開発者が同じ壁にぶつかります。良いニュースは、Aspose.Words for Java を使えば、数行のコードで長方形を作成し、きれいな影を付けて、Word文書を保存できることです。

このチュートリアルでは、必要な手順をすべて解説します：空のドキュメントの初期化から、影の設定、そして最終的なファイル保存まで。最後まで読むと、**シェイプに影を付ける方法**、**シェイプの影を追加**、そして**長方形シェイプを追加**する方法が分かります。外部ドキュメントは不要で、純粋な実行可能コードだけです。

## 前提条件

- Java 8 以上（APIはJava 11+でも動作します）。  
- Aspose.Words for Java ライブラリ（バージョン 23.9 以降）。  
- IntelliJ IDEA や Eclipse などの IDE—どれでも構いません。  
- Java構文の基本的な知識。

> **プロのコツ:** Maven を使用している場合は、`pom.xml` に Aspose.Words の依存関係を追加し、残りは IDE に任せましょう。

---

## 手順 1: 新しいドキュメントを初期化 – **長方形シェイプを作成**する方法  

まず最初に、クリーンなキャンバスが必要です。Aspose.Words ではそのキャンバスは `Document` オブジェクトです。

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document` クラスは .docx ファイル全体を表します。後で**長方形シェイプを追加**し、その影を付けるためのノートブックと考えてください。

## 手順 2: 長方形を作成 – **長方形シェイプを追加**  

ここで実際に長方形を構築します。サイズ、レイアウト、塗りつぶし色を設定します。

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

`INLINE` ラップを使用する理由は何ですか？シェイプを段落のように扱いたいからです—シンプルなレポートに最適です。後でテキストをシェイプの周りに回り込ませたい場合は、`TOPBOTTOM` に変更できます。

## 手順 3: 影を適用 – **シェイプに影を付ける方法**  

平坦な長方形はやや味気ないです。影を追加すると奥行きが出て、文書がより洗練された印象になります。ここで実際に“**シェイプに影を付ける方法**”を示します。

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

各プロパティは特定の役割を持ちます：

- `setVisible(true)` は影を有効にします。  
- `setColor` は微妙な効果のために濃い灰色を選択します。  
- `setBlurRadius` はエッジのぼかし具合を制御します。  
- `setOffsetX/Y` は影を右下に移動させ、光源を模倣します。  
- `setTransparency` は影をやや透過させ、シェイプが主役のままにします。

> **注:** カラフルな影が必要な場合は、`setColor` に別の `java.awt.Color` を渡すだけです。

---

## 手順 4: シェイプをドキュメントに挿入  

長方形とその影の準備ができたら、ドキュメントの最初のセクションに挿入します。

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

body に追加すると、シェイプは新しい段落が入る位置に配置されます。特定の位置に長方形を置きたい場合は、`insertBefore` を使用するか、`Paragraph` コレクションを操作できます。

## 手順 5: **Word文書を保存** – 作業を永続化  

最後のステップはファイルをディスクに書き込むことです。これが実際に**Word文書を保存**する瞬間です。

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`YOUR_DIRECTORY` をマシン上の絶対パスまたは相対パスに置き換えてください。プログラムを実行した後、Microsoft Word で `ShadowShape.docx` を開くと、淡いグレーの長方形に柔らかい暗い影が付いているのが確認できるはずです。

![Diagram showing a rectangle shape with shadow created using Aspose.Words](https://example.com/rectangle-shadow.png "create rectangle shape with shadow")

---

## よくある質問とエッジケース  

### 複数の長方形が必要な場合は？

**手順 2** と **手順 3** をループで繰り返し、各イテレーションで `setWidth`、`setHeight`、または `setFillColor` を調整してください。各シェイプにユニークな変数名を付けるか、リストに格納することを忘れずに。

### DOCX の代わりに PDF にエクスポートできますか？

もちろんです。シェイプを追加した後、`document.save("output.pdf")` を呼び出します。Aspose.Words が変換を処理し、影を保持します。

### 古い Word バージョンはどうですか？

`document.save("file.doc", SaveFormat.DOC)` のオーバーロードを使用してください。API は自動的に機能をダウングレードしますが、レガシーフォーマットでは影のスタイルが若干異なる場合があります。

### 影の方向を変更するには？

`setOffsetX` と `setOffsetY` を操作します。X が正の値だと影は右へ、負の値だと左へ移動します。Y が正の値だと下へ、負の値だと上へ移動します。これらの数値を調整して、任意の角度からの光源をシミュレートしてください。

---

## シェイプ操作のヒント  

- **シェイプのグループ化**: 長方形の横にラベルが必要な場合は、`GroupShape` を作成し、長方形と `TextBox` の両方を追加します。  
- **Z順序が重要**: `shape.moveToFront()` または `shape.moveToBack()` を使用して、どのシェイプが前面に表示されるか制御します。  
- **パフォーマンス**: 数百のシェイプを追加すると遅くなることがあります。単一のセクションにまとめてバッチ処理し、最後に `document.updatePageLayout()` を一度だけ呼び出してください。

---

## まとめ  

Java を使用して Word 文書に**長方形シェイプを作成**する方法、**シェイプに影を追加**する方法、そして結果を**Word文書として保存**する方法をカバーしました。完全な実行可能コードは上記のスニペットにあり、各プロパティの“なぜ”を理解したので、色やぼかし、オフセットを自由に調整して任意のデザインに合わせられます。

次のチャレンジに備えましたか？長方形とチャートを組み合わせたり、PDF としてエクスポートして影の描画を確認したりしてみてください。また、テーブル内に**長方形シェイプを追加**して、洗練されたレポートレイアウトを試すこともできます。

コーディングを楽しんで、あなたのドキュメントがコードと同じくらいシャープに見えることを願っています！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}