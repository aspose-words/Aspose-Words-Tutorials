---
category: general
date: 2026-08-14
description: Aspose.Words を使用して Java で docx の ActiveX ボタンを作成します。Word にプログラムでフォーム ボタンを追加し、ドキュメントを保存する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: ja
lastmod: 2026-08-14
og_description: Aspose.Words を使用して Java で docx の ActiveX ボタンを作成します。このガイドでは、Word にフォーム
  ボタンを追加し、設定し、ファイルを保存する方法を示します。
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: JavaでdocxのActiveXボタンを作成する – ステップバイステップチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: JavaでdocxのActiveXボタンを作成する – 完全プログラミングガイド
url: /ja/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでdocx ActiveXボタンを作成する – 完全プログラミングガイド

Javaで **docx ActiveX ボタン** を作成する必要がある場合、このガイドが全工程を案内します。Word にフォームボタンを追加し、プロパティを設定し、すぐに使用できる .docx ファイルを生成する方法が分かります。

レガシーな Word フォームを自動化する際、ActiveX コントロールの操作は一般的な要件です。このチュートリアルでは、Aspose.Words for Java ライブラリを使用して **Word 文書にフォームボタンを追加** する方法を学び、手動編集なしでインタラクティブなコントロールを埋め込めるようになります。

## 必要なもの

* Java 17 以降（コードは以前のバージョンでもコンパイルできますが、Java 17 が推奨されます）。
* Aspose.Words for Java 23.10 以上 – Aspose のウェブサイトから JAR をダウンロードするか、Maven 依存関係を追加してください。
* IDE（IntelliJ IDEA、Eclipse、または VS Code）またはシンプルなテキストエディタとコマンドラインビルドツール。
* Java の構文とオブジェクト指向プログラミングの基本知識。

## Aspose.Words を使用して docx ActiveX ボタンを作成する方法

以下の手順は、**docx ActiveX ボタン** オブジェクトを作成し、Word 文書に埋め込むために必要な正確なシーケンスを示しています。

### 手順 1: プロジェクトをセットアップし、Aspose.Words をインポートする

Maven を使用している場合、`pom.xml` に Aspose.Words の依存関係を追加します:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Gradle を使用したい場合は次のようにします:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

依存関係が解決したら、Java ソースファイルで必要なクラスをインポートします:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

これらのインポートにより、ActiveX コントロールの挿入に使用する `Document`、`DocumentBuilder`、`Forms2OleControl` API にアクセスできます。

### 手順 2: 新しい空白ドキュメントを作成する

`Document` オブジェクトをインスタンス化します。これは、コンテンツを受け取る準備ができた空の Word ファイルを表します。

```java
// Step 2: Create a new blank document
Document document = new Document();
```

最初にドキュメントを作成することで、以降のビルダーがクリーンなキャンバス上で動作することが保証されます。

### 手順 3: DocumentBuilder を初期化する

`DocumentBuilder` はテキスト、画像、コントロールの挿入のための流暢なインターフェイスを提供します。先ほど作成したドキュメントに紐付けます。

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

ビルダーはドキュメント内の現在のカーソル位置を追跡するため、次の挿入が必要な場所に正確に行われます。

### 手順 4: ActiveX CommandButton コントロールを挿入する

`insertForms2OleControl` メソッドを使用して ActiveX の `CommandButton` を埋め込みます。このメソッドは、さらに設定可能な `Forms2OleControl` インスタンスを返します。

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

この時点で .docx ファイルにはボタンのプレースホルダーが含まれますが、まだ視覚的なキャプションやサイズは設定されていません。

### 手順 5: ボタンのプロパティを設定する

コントロールの名前、キャプション、レイアウト属性を設定します。これらの値は、ボタンが Word 上でどのように表示されるか、また後で VBA や自動化スクリプトからどのように参照できるかを決定します。

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **プロのコツ:** Word では位置をポイントで測定します (1 pt ≈ 1/72 in)。`setTop` と `setLeft` を調整して、ボタンを周囲のコンテンツに合わせて配置してください。

### 手順 6: ドキュメントを保存する

最後に、ドキュメントをディスクに書き出します。`.docx` 拡張子を使用して、最新の Office Open XML 形式でファイルを保持します。

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

生成されたファイルを Microsoft Word で開くと、指定した座標に配置された **Submit** ボタンが表示されます。Word でボタンをクリックしても、VBA コードを添付しない限り何も起こりませんが、フォームベースのワークフローではコントロールは完全に機能します。

## よくある質問とエッジケース

| 質問 | 回答 |
|----------|--------|
| **特別な Word バージョンが必要ですか？** | ActiveX コントロールは Windows のデスクトップ版 Microsoft Word でサポートされています。Mac 用 Word や Word Online では利用できません。 |
| **`.doc` ファイルでも使用できますか？** | はい。`.doc` 拡張子でドキュメントを保存します（`document.save("ActiveXButton.doc")`）。同じ API が旧バイナリ形式でも機能します。 |
| **ボタンが表示されない場合はどうすればよいですか？** | **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** で ActiveX コントロールが許可されていることを確認してください。また、ドキュメントが「保護ビュー」で開かれていないことも確認してください。 |
| **他の ActiveX コントロールを追加できますか？** | もちろんです。`Forms2OleControlType.COMMAND_BUTTON` を `Forms2OleControlType.CHECK_BOX`、`RADIO_BUTTON` などに置き換えてください。 |
| **サイズに制限はありますか？** | コントロールのサイズはページレイアウトによってのみ制限されます。非常に大きな寸法はレイアウトのオーバーフローを引き起こす可能性があります。 |

## 完全な実行可能サンプル

以下は、コピーしてコンパイル・実行できる完全な Java クラスです。すべてのインポート、main メソッド、そして分かりやすいインラインコメントが含まれています。

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**期待結果:** プログラムを実行すると、作業ディレクトリに `ActiveXButton.docx` が生成されます。Microsoft Word で開くと、1 ページ目の左上付近に配置されたクリック可能な **Submit** ボタンが表示されます。

## 結論

これで、Aspose.Words を使用して Java で **docx ActiveX ボタン** オブジェクトを作成する方法、そしてプログラムで **Word 文書にフォームボタンを追加** する方法が分かりました。プロジェクトのセットアップ、ドキュメント作成、コントロール挿入、プロパティ設定、保存という手順は、最初から最後までの全ワークフローを網羅しています。

次に、以下を検討できます:

* ボタンのクリックに応答する VBA マクロの追加。
* チェックボックスやリストボックスなど、他の ActiveX コントロールの埋め込み。
* 複数ページにわたるフォームを自動生成し、複数のインタラクティブ要素を配置する。

サイズ、位置、キャプションを自由に試して、特定のフォーム設計要件に合わせてください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java で DocumentBuilder を使用してフォームフィールドを作成し、コンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java を使用して HTML をロードし DOCX として保存する方法](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Aspose.Words for Java で PDF ドキュメントを作成する方法 | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}