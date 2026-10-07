---
category: general
date: 2026-10-07
description: JavaでActiveXコマンドボタンを作成し、プログラムでWord文書にコマンドボタンを追加します。ボタンの左上位置の設定方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: ja
lastmod: 2026-10-07
og_description: JavaでActiveXコマンドボタンを作成し、Word文書にインタラクティブなコントロールを埋め込みましょう。プログラムでコマンドボタンを追加し、位置を設定し、外観をカスタマイズする方法を学べます。
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: JavaでActiveXコマンドボタンを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: JavaでActiveXコマンドボタンを作成する方法
url: /ja/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでActiveX command buttonを作成する方法

Javaを使用してWord文書に**ActiveX command button**を作成する必要がある場合、本ガイドでその手順を詳しく解説します。**プログラムでコマンドボタンを追加**し、`setLeft` と `setTop` で位置を設定し、結果を `.docx` ファイルとして保存する完全な実行可能サンプルをご覧いただけます。

インタラクティブなボタンを埋め込むことで、フォームの作成、ワークフローの自動化、またはWordファイル内で直接ユーザー入力を収集できます。以下の手順はプロジェクトのセットアップから最終確認まで網羅しているので、コードを自分のプロジェクトにそのままコピーしても細部が抜け落ちることはありません。

## 前提条件

- JDK 17 以上がインストールされていること  
- Maven 3.8 以上（またはお好みのビルドツール）  
- Aspose.Words for Java 23.9 以降 – `DocumentBuilder` と OLE コントロールのサポートを提供するライブラリ  
- Java の構文とオブジェクト指向の概念に関する基本的な知識  

Maven を使用している場合は、`pom.xml` に以下の依存関係を追加してください：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **プロのコツ:** バグ修正や新しい OLE 機能を利用できるよう、最新の Aspose.Words バージョンを使用してください。

## 手順 1: 新しい空のドキュメントと DocumentBuilder を作成する

**ActiveX command button** を作成する最初のステップは、空の `Document` と `DocumentBuilder` をインスタンス化することです。Builder は OLE コントロールを含むコンテンツ挿入のための流暢な API を提供します。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` はメモリ上の Word ファイルを表し、`DocumentBuilder` は要素を必要な位置に正確に配置できるカーソルとして機能します。

## 手順 2: OLE コマンドボタン コントロールを挿入する

ActiveX コントロールは OLE オブジェクトとして挿入されます。この目的のために Aspose.Words は `Forms2OleControl` クラスを提供しています。

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

`insertForms2OleControl()` を呼び出すと、Aspose は自動的に ActiveX ボタンをホストするプレースホルダーシェイプを作成します。

## 手順 3: ボタンのプロパティを設定する

ここで **プログラムでコマンドボタン** の詳細（ProgID、キャプション、サイズなど）を追加します。コマンドボタンで最も一般的な ProgID は `"Forms.CommandButton.1"` です。

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### ボタンの左上位置を設定する方法

ボタンの位置設定は、二次キーワード **how to set button left top** が関係する部分です。`setLeft` と `setTop` メソッドはポイント単位（1 ポイント = 1/72 インチ）で値を受け取ります。

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

レイアウトに合わせてこれらの数値を調整してください。例えば、ボタンを表のセルに合わせる場合は、セルの座標を計算し、`setLeft`/`setTop` に渡します。

## 手順 4: ドキュメントを保存する

最後に、ドキュメントをディスクに書き出します。このファイルには、Microsoft Word で開いたときに操作可能な ActiveX ボタンが含まれます。

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`main` メソッドを実行すると `CommandButton.docx` が生成されます。Word でファイルを開き、プロンプトが表示されたらコンテンツを有効にし、指定した座標に配置された **Click Me** というラベルのクリック可能なボタンが表示されます。

![JavaでActiveXコマンドボタンを作成](/images/activex-button-screenshot.png){.center width=600 alt="JavaでActiveXコマンドボタンを作成したスクリーンショット（Word文書内のボタンを示す）"}

## よくあるバリエーションとエッジケース

### 複数のボタンを追加する

複数のボタンが必要な場合は、各コントロールに対して **Step 2** と **Step 3** を繰り返します。ボタンが重ならないように `setLeft` と `setTop` を調整することを忘れないでください。

### ボタンの動作を変更する

ActiveX ボタンはクリック時に VBA マクロを実行できます。マクロを割り当てるには、`setOnAction` プロパティにマクロ名を設定します：

```java
commandButton.setOnAction("MyMacro");
```

対象のドキュメントに対応する VBA モジュールが含まれていることを確認してください。そうでない場合、Word はエラーを表示します。

### 互換性に関する注意点

- このボタンは ActiveX をサポートするデスクトップ版 Word（例: Windows 用 Word）でのみ動作します。Mac 用 Word やオンラインエディタでは静的画像として表示されます。  
- 混在環境を対象とする場合は、ActiveX コントロールの代わりに **content control**（`RichTextContentControl`）の使用を検討してください。

## 参考用の完全なソースコード

以下は、すぐに新しい Maven プロジェクトにコピーして実行できる、完全で自己完結型のサンプルです。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**期待される出力:** 実行後、プロジェクトの作業ディレクトリに `CommandButton.docx` が作成されます。Microsoft Word でファイルを開くと、指定した位置に「Click Me」というキャプションのボタンが表示されます。

## 結論

これで、Java で **ActiveX command button** を **プログラムでコマンドボタンを追加** し、**how to set button left top** メソッドを使用してレイアウトを正確に制御する方法が分かりました。この手法により、マクロをトリガーしたり外部アプリケーションを起動したり、文書内で直接ユーザー入力を収集できるリッチでインタラクティブな Word フォームを作成できるようになります。

### 次のステップ

- `Forms.TextBox.1` や `Forms.CheckBox.1` など、他の ActiveX コントロールを調査する。  
- 複数のコントロールを VBA モジュールと組み合わせて、フル機能のフォームを実装する。  
- クロスプラットフォームの互換性が必要な場合は、ActiveX の代わりに content control を使用する。  

サイズ、キャプション、位置を自由に試して UI デザインに合わせてください。問題が発生した場合は、使用している Aspose.Words のバージョンが OLE コントロールをサポートしているか、Word のセキュリティ設定で ActiveX の実行が許可されているかを再確認してください。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word 文書への OLE オブジェクトと ActiveX コントロールの埋め込み](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Aspose.Words for Java で DocumentBuilder を使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Java で Word に矩形シェイプを作成する – 完全ガイド](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}