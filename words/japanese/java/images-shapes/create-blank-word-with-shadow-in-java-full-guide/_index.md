---
category: general
date: 2026-05-04
description: Javaで空白のWord文書を作成し、図形の影の色、ぼかし、オフセットの設定方法を学ぶ – 簡単チュートリアル。
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: ja
og_description: Javaで空白のWord文書を作成し、図形の影の色、ぼかし、オフセットの設定方法を学びましょう。ステップバイステップのチュートリアルをご覧ください。
og_title: Javaで影付きの空白文字を作成する – 完全ガイド
tags:
- Aspose.Words
- Java
- Document Automation
title: Javaで影付きの空白文字を作成する – 完全ガイド
url: /ja/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java で空白の Word に影を付ける – 完全ガイド

コードから **空白の Word** ファイルを作成し、少しだけリッチにしたいことはありませんか？レポートやテンプレート生成プロジェクトでは、最初に空の Word ドキュメントを作成し、そこに影付きのシェイプを配置して仕上げ感を出すことがよくあります。

このチュートリアルでは、Aspose.Words for Java を使って **空白の Word** を作成し、**影を追加** する方法、**影の色を設定**、**ぼかしを設定**、**オフセットを設定** する手順を詳しく解説します。最後には、赤い半透明の影がきれいにぼかされた矩形が表示された `.docx` ファイルが手に入ります。

## 必要なもの

- **Aspose.Words for Java**（最新バージョン; コードは 23.9 以降で動作）
- JDK 8 以上
- IDE またはシンプルなテキストエディタとターミナル
- 基本的な Java の知識 – `main` メソッドを実行できれば OK

デモ用に特別な Maven や Gradle の設定は不要です。Aspose の JAR をクラスパスに置くだけで動作します。

---

![create blank word document with shadow example](image-placeholder.png){: .center alt="create blank word document with shadow example"}

## 空白の Word を作成 – Document の初期化

最初のステップは、全く新しい空の Word ファイルを作成することです。これは、後からシェイプやテーブル、テキストを描くためのキャンバスになります。

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **ポイント:** `Document` は `.docx` パッケージ全体を表します。デフォルトコンストラクタで作成すると実質的に **空白の Word を作成** したことになり、コンテンツやセクションはなく、ファイル構造だけが用意された状態です。

## シェイプに影を追加する方法

クリーンなドキュメントができたので、影を付ける矩形を挿入します。ここからビジュアルマジックが始まります。

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **プロのコツ:** `insertShape` 呼び出しは自動的に現在の段落にシェイプを追加します。絶対位置指定が必要でない限り、手動で位置を管理する必要はありません。

## 影の色を設定 – 目立たせる

色のない影は単なるグレーのぼかしで、平坦に見えてしまいます。影の色を設定すれば、ブランドカラーに合わせたり、目立たせたりできます。

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **解説:** `ShadowFormat` は影のすべてのビジュアル属性を制御します。`setVisible(true)` で効果を有効にし、`setColor` で任意の `java.awt.Color` を指定できます。例では **影の色を設定** するために赤色を選びました。

## ぼかしを設定 – 柔らかい効果

硬いエッジの影はきつく見えることがあります。ぼかしを加えるとエッジが柔らかくなり、自然な見た目になります。

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **ぼかしが重要な理由:** `setBlur` の値はポイント単位です。`5.0` はやさしい拡散を作り、数値を上げるとよりぼんやりした影に、下げるとシャープな輪郭になります。

## オフセットを設定 – 影の位置調整

オフセットはシェイプに対する影の位置を決めます。X 軸と Y 軸のシフトと考えてください。

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **オフセットの説明:** 正の X は影を右に、正の Y は下に移動させます。負の数を使えば逆側に影を表示できます。

## 透明度の微調整

影を目立たせすぎたくない場合は透明度を調整します。このステップは必須キーワードではありませんが、ビジュアルコントロールを完成させます。

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## ドキュメントの保存 – 結果を確認

最後にドキュメントをディスクに書き出します。これで Word、LibreOffice、または対応ビューアで開ける `.docx` が完成します。

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **期待される結果:** `ShadowShape.docx` を開くと、150 × 80 pt の矩形に赤くややぼかされた影が右下に 8 pt 移動して付いているのが見えます。影は 30 % の透明度なので、矩形ははっきりと見えます。

---

## よくある質問とエッジケース

### 別のシェイプが必要な場合は？

`ShapeType.RECTANGLE` を `ELLIPSE`、`CLOUD`、`CALLOUT` など他の列挙値に置き換えるだけです。影の設定はシェイプに関係なく同様に機能します。

### 複数のシェイプに同じ影を適用したい場合は？

もちろん可能です。ヘルパーメソッドを作成しましょう。

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

その後、`applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` を任意のシェイプに対して呼び出します。

### 古い Aspose バージョンでも動作しますか？

`ShadowFormat` API はバージョン 19.8 以降で安定していますので、ほとんどの最新リリースで問題なく動作します。非常に古いビルドを使用している場合は、`ShadowFormat` の Javadoc でメソッド名を確認してください。

### 影を保持したまま PDF にエクスポートするには？

シェイプ作成後に `document.save("output.pdf");` を呼び出すだけです。Aspose.Words は PDF でも影を正しくレンダリングし、ぼかしや透明度を保持します。

---

## まとめ – カスタム影付きの空白 Word を作成

`new Document()` で **空白の Word を作成** し、矩形を挿入、**影の色を設定**、**影を追加**、**ぼかしを設定**、最後に **オフセットを設定** して位置調整を行いました。完全な実行可能コードは上記スニペットにあり、生成されたファイルで効果を確認できます。

---

## 次のステップは？

- `ShadowFormat.setStyle(ShadowStyle.OUTER)` など、他の影プロパティを試してみる
- 複数シェイプに個別の影を付けて複雑な図を作成する
- シェイプ挿入前に `builder.insertHtml("<b>Hello</b>")` でテキストを入れ、同じ影ロジックを適用する
- 線のスタイル、塗りつぶし色、グラデーションなど、他の書式設定オプションも探索する – Aspose.Words は豊富な API を提供しています

ぼかし半径、オフセット、色を自由に調整して、ドキュメントのデザイン言語に最適な影を作りましょう。コーディングを楽しんで、生成した Word ファイルがいつも少しだけ洗練されたものになるように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}