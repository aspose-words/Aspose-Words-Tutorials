---
category: general
date: 2026-10-16
description: Javaで空白のWord文書を作成し、Aspose.Wordsを使用してActiveXボタンを追加し、キャプションを設定し、サイズを調整する方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: ja
lastmod: 2026-10-16
og_description: Javaで空白のWord文書を作成し、ActiveXボタンを追加してキャプションを設定し、Aspose.Wordsでサイズを定義します。
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: 空白のWord文書を作成し、ActiveXボタンを埋め込む – Javaガイド
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: 空白のWord文書を作成し、ActiveXボタンを追加する（Java）
url: /ja/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白のWord文書を作成し、ActiveXボタンを追加する (Java)

プログラムで **空白のWord文書を作成** する必要がある場合、このガイドではJavaとAspose.Wordsを使用してその方法を示します。また、**ActiveXボタンを追加**、**ボタンのキャプションを設定**、**ボタンのサイズを設定** する方法も学び、コントロールが期待通りに表示されるようにします。

このチュートリアルでは以下を取り上げます:

* Aspose.Words for Java を使用した空のWordファイルの初期化。  
* `CommandButton` のActiveXコントロールの挿入。  
* ボタンのキャプションとサイズの設定。  
* 最終的な `.docx` ファイルの保存。  

基本的なJavaの知識と、Aspose.Words for Java ライブラリの最新バージョン（コードは 23.9 以降で動作します）を用意してください。追加の依存関係は必要ありません。

![ActiveXボタン付きの空白のWord文書を作成](/images/activex-button-example.png){: .align-center alt="ActiveXボタン付きの空白のWord文書を作成"}

## Aspose.Words を使用して空白のWord文書を作成する

最初のステップは空の `Document` オブジェクトをインスタンス化することです。このオブジェクトはメモリ上の Word ファイル全体を表し、編集用に `DocumentBuilder` クラスを提供します。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**重要性:**  
空白の文書を作成することで、クリーンなキャンバスが得られ、後のレイアウト計算に干渉する可能性のある隠れたスタイルやセクションを回避できます。

## 文書にActiveXボタンを追加する

Aspose.Words は `Forms2OleControl` クラスを介してレガシーなActiveXコントロールを埋め込むことができます。以下のコードは現在のカーソル位置に `CommandButton` コントロールを挿入します。

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**ヒント:** `setOleClassName` の値 `"Forms.CommandButton.1"` は標準の Microsoft Forms ボタンの ProgID です。別の ProgID（例: `"Forms.CheckBox.1"`）を使用すると、異なる種類のコントロールが挿入されます。

## ボタンのキャプションを設定する

キャプションはボタン面に表示されるテキストです。文書を保存する前であればいつでも変更できます。

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**必要性:** ユーザーはコントロールの目的が明確であるときにのみ理解できます。意味のあるキャプションを設定することで、特にWindows上のWordで文書を開く際の使いやすさが向上します。

## ボタンのサイズを設定する

位置とサイズはポイント単位で指定します（1ポイント = 1/72インチ）。レイアウトに合わせて値を調整してください。

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**一般的なバリエーション:**

| シナリオ | 調整 |
|----------|------------|
| タッチスクリーン用の大きなボタン | `setWidth` と `setHeight` を比例的に増加させる |
| ページ上で中央に配置するボタン | `left = (pageWidth - width) / 2` を計算する |
| 列に複数のボタンを配置する | 新しいボタンごとに `setTop` を増加させる |

## ActiveXボタンを含む文書を保存する

最後に、文書をディスクに書き込みます。`.docx` 形式は Windows 用 Microsoft Word の ActiveX コントロールを保持します。

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**期待結果:** `ActiveXCommandButton.docx` を Word（Windows）で開くと、左余白から 100 pt、上余白から 200 pt の位置に **Click Me** とラベル付けされたクリック可能なボタンが表示された空白ページが表示されます。

## 完全な実行可能サンプル

以下のクラス全体を IDE にコピーし、プロジェクトのクラスパスに Aspose.Words for Java の JAR を追加して実行してください。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

プログラムを実行すると作業ディレクトリに `ActiveXCommandButton.docx` が生成されます。Microsoft Word（Windows）で開き、ボタンが設定どおりに表示されていることを確認してください。

## このアプローチが推奨される理由

* **シンプルさ:** コアの Aspose.Words API だけを使用し、COM 相互運用や追加ライブラリは不要です。  
* **ポータビリティ:** Java をサポートする任意のプラットフォームでコードは動作しますが、ActiveX コントロール自体は Windows 用 Word でのみ機能します。  
* **保守性:** すべてのプロパティ（キャプション、サイズ、位置）は明確で自己文書化されたメソッドで設定されるため、将来的な調整が容易です。

## よくある落とし穴と回避策

| 落とし穴 | 対策 |
|---------|------------|
| macOS や Linux の Word でボタンが表示されない | ActiveX コントロールは Windows 専用です。クロスプラットフォーム文書には別のコントロール（例: コンテンツコントロール）を使用してください。 |
| キャプションが切り取られる | テキストが収まるようにボタン幅を十分に確保してください。`setWidth` を増やすか、短いキャプションを使用します。 |
| ボタンが他のコンテンツと重なる | `setTop` と `setLeft` の値を調整するか、コントロールの前に新しい段落を挿入してスペースを確保してください。 |

## 次のステップ

これで **空白のWord文書を作成**、**ActiveXボタンを追加**、**ボタンのキャプションを設定**、**ボタンのサイズを設定** ができるようになったので、以下を検討してみてください:

* VBA マクロによるイベントハンドリングコードの追加（マクロモジュールの埋め込みが必要）。  
* フォームのような文書のために、テーブルレイアウトで複数のコントロールを挿入する。  
* クロスプラットフォームのフォームソリューションのために、Aspose.Words の **FormField** API を使用する。

さまざまなサイズ、位置、キャプションを試して、特定の文書デザインに合わせてください。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Word文書作成 Java – 影付き矩形シェイプの追加](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java の DocumentBuilder を使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java を使用して文書に透かしを追加する](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}