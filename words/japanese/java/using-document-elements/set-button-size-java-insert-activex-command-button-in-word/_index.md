---
category: general
date: 2026-07-29
description: ボタンサイズ設定 Java チュートリアル：Java と Aspose.Words を使用して Word 文書に ActiveX コマンドボタンを挿入する方法、サイズ設定および空白文書の作成について学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: ja
lastmod: 2026-07-29
og_description: set button size java guide は、Java を使用して Word ファイルに ActiveX コマンドボタンを挿入し、そのサイズを調整し、プログラムでドキュメントを保存する方法を示します。
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: ボタンサイズを設定 Java – JavaでWordにActiveXコマンドボタンを追加
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: ボタンサイズを設定する Java – Word に ActiveX コマンドボタンを挿入
url: /ja/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Word に ActiveX コマンドボタンを挿入

Word 文書を自動化するときに **how to set button size java** が気になったことはありませんか？たとえば、.docx ファイル内にクリック可能な「Submit」ボタンを配置するレポートツールを作成したいとします。このチュートリアルでは、空の Word 文書を作成し、ActiveX コマンドボタンを挿入し、幅と高さを明示的に設定するまでの一連の手順を Java と Aspose.Words で解説します。

また、多くの開発者が抱える「how to insert activex」についての疑問にも答えます。最後まで読めば、完璧なサイズのコマンドボタンを含む Word ファイルを生成できる実行可能なプログラムが手に入ります。

---

## 必要なもの

作業を始める前に、以下を用意してください。

- **Java Development Kit (JDK) 8 以上** – 任意の最新 JDK でコンパイル可能です。
- **Aspose.Words for Java**（2026年7月時点の最新バージョン）。JAR は [Aspose のウェブサイト](https://products.aspose.com/words/java) から取得するか、Maven で取得してください：
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- IntelliJ IDEA、Eclipse、VS Code などの IDE またはシンプルなテキストエディタ。
- 生成した **CommandButton.docx** を保存したいフォルダー。

以上です。余計な Office Interop ライブラリや COM トリックは不要で、純粋な Java だけで完結します。

---

## 手順別実装

解決策を 5 つの論理的ステップに分けて解説します。各ステップは H2 見出しで区切られており、1 つは SEO 用の **primary keyword** を含んでいます。

### 1. プロジェクトのセットアップと Aspose.Words のインポート

まず Maven（または Gradle）プロジェクトを作成し、上記の Aspose.Words 依存関係を追加します。その後、Java ソースファイルで必要なクラスをインポートします。

```java
import com.aspose.words.*;
```

> **Pro tip:** IDE を使用している場合は自動インポート機能を活用しましょう。入力量が減り、タイプミスも防げます。

### 2. java create blank word Document

次に実際に **java create blank word** 文書を作成します。これが後で **insert command button word** を行う土台となります。

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

`Document` オブジェクトはメモリ上の Word ファイル全体を表します。この時点ではページもテキストもなく、真っ白な状態です。

### 3. DocumentBuilder の初期化と ActiveX コントロールの挿入

`DocumentBuilder` はコンテンツ、段落、テーブル、そしてもちろん ActiveX コントロールを追加できるヘルパークラスです。ここで **how to insert activex** に答えます。

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` は Aspose が提供する OLE オブジェクトのラッパーです。`COMMANDBUTTON` を指定することで、Word に従来の ActiveX コマンドボタンを埋め込むよう指示します。

### 4. How to Set Button Size Java – 幅と高さの調整

本チュートリアルの核心部分です：**how to set button size java**。コントロールは `Left`、`Top`、`Width`、`Height` といったレイアウトプロパティを公開しています。これらを直接設定することで、ボタンの見た目をページ上で制御できます。

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

なぜこの数値なのか？ Word では 1 ポイントは 1/72 インチに相当します。したがって幅 `120` ポイントは約 1.67 インチとなり、ラベルとして読みやすいサイズですが大きすぎません。レイアウトに合わせて数値を調整してください。同じプロパティは **how to set button** に関する質問にも答えます。

> **Note:** 別のボタン種別（例：チェックボックス）が必要な場合は、`Forms2OleControlType.COMMANDBUTTON` を該当する enum 値に置き換えてください。

### 5. ドキュメントの保存

最後にドキュメントをディスクに永続化します。

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

`YOUR_DIRECTORY` をマシン上の絶対パスまたは相対パスに置き換えてください。プログラムを実行した後、Microsoft Word で生成されたファイルを開くと、左から 100 pts、上から 200 pts の位置に「Click Me」ラベルのボタンが表示され、設定したサイズ通りになっているはずです。

---

## 完全動作サンプル

以下はそのまま実行可能な Java クラスです。`CommandButtonActiveX.java` に貼り付け、出力パスを調整して **Run** をクリックしてください。

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**期待される出力:** Word で `CommandButton.docx` を開くと、1 ページにクリック可能な「Click Me」ボタンがほぼページ中央に配置されます。ボタンの寸法は設定した値と一致し、**set button size java** が正しく機能したことが確認できます。

---

## よくある質問とエッジケース

### ボタンが Word に表示されない場合は？

- **Word のバージョンを確認**してください。ActiveX コントロールはデスクトップ版 Word が必要で、Word Online では除去されます。
- **Aspose.Words のライセンスが適用されているか**確認してください（有料エディション使用時）。評価版は透かしが入りますが、コントロール自体は表示されます。

### ボタンのフォントや色を変更できる？

はい。コントロールを挿入した後、内部の OLE オブジェクトにアクセスして VBA プロパティを操作できます。高度な例として `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` を使用すれば、キャプションを赤色に変更できます。

### ボタンのクリックイベントはどう扱う？

ActiveX コマンドボタンは VBA の `Click` イベントを発火します。ボタンを機能させるには、同じ文書にマクロを埋め込む必要があります。Aspose.Words は `Document.getMacros()` API を通じてマクロモジュールを追加できますが、マクロ本体は VBA で記述する必要があります。

### 他のボタン種別は？

Aspose.Words は多数の `Forms2OleControlType` をサポートしています：`CHECKBOX`、`OPTIONBUTTON`、`LISTBOX` など。`insertForms2OleControl` 呼び出しの enum 定数を変更すれば、好きな種別のコントロールを試せます。

---

## 本番向けコードのプロチップ

1. **レイアウト値は定数化**しておくと、後からの調整が楽です。  
2. **保存パスは `Path` オブジェクトでラップ**し、プラットフォーム依存の区切り文字を回避しましょう。  
3. 複数ファイルをループ処理する場合は、`Document` を `try‑with‑resources` で **Dispose** してください。  
4. `save` 前に出力フォルダーの存在を **検証**し、`FileNotFoundException` を防ぎます。

---

## まとめ

このチュートリアルでは、空の Word ファイルを作成し、ActiveX コマンドボタンを挿入し、サイズを正確に設定する方法を **set button size java** で学びました。これにより **how to insert activex**、**how to set button**、**java create blank word**、**insert command button word** のすべてを単一の実例で網羅しました。

次のステップとして、ボタンのキャプションをカスタマイズしたり、クリック時に実行されるマクロを追加したり、同一ページに複数コントロールを配置してみてください。また、生成した .docx を Aspose.Words で PDF に変換すれば、ボタンは静的画像として保持されます。

実験を楽しみながら、問題があればコメントで質問してください。Happy coding!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を応用した関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能習得や代替実装アプローチの探求に役立ちます。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}