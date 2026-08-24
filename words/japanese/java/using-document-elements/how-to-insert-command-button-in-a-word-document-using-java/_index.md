---
category: general
date: 2026-08-23
description: Java と Aspose.Words を使用して Word 文書にコマンド ボタンを挿入する方法を学びましょう。このガイドでは、フォーム
  コントロールの追加、ボタン名の設定、ActiveX ボタンの埋め込み方法を示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: ja
lastmod: 2026-08-23
og_description: Java を使用して Word 文書にコマンド ボタンを挿入します。このガイドに従ってフォーム コントロールを追加し、ボタン名を設定し、Aspose.Words
  で ActiveX ボタンを埋め込みます。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: JavaでWordにコマンドボタンを挿入する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java を使用して Word 文書にコマンドボタンを挿入する方法
url: /ja/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java を使用して Word 文書にコマンドボタンを挿入する方法

Word ファイルに **コマンドボタン** を挿入する必要がある場合、このチュートリアルでは Aspose.Words for Java を使用した完全なソリューションを示します。フォームコントロールの追加方法、キャプションの設定方法、ボタン名の設定方法を IDE から離れることなく確認できます。

このガイドでは、Microsoft Word で使用できる ActiveX ボタンを含む `.docx` を作成するために必要なすべてをカバーしています。追加のツールは不要で、例は Java 8+ で動作します。

## 学べること

* **CommandButton** タイプのフォームコントロールを Word 文書に追加する方法。  
* **ボタン名を設定**し、**ActiveX ボタン** のプロパティを追加する正確な手順。  
* ボタンが Word で正しく表示されるように文書を保存する方法。  

基本的な Java 開発環境と、Aspose.Words ライブラリをインポートできる Maven または Gradle プロジェクトがあれば始められます。

## 前提条件

| 要件 | 理由 |
|------|------|
| Java 8 以上 | Aspose.Words for Java は Java 8+ で動作します。 |
| Maven または Gradle ビルドツール | Aspose.Words の依存関係追加が簡単になります。 |
| Aspose.Words for Java ライセンス（または無料トライアル） | フル機能を使用するにはライセンスが必要です。API は評価モードでも動作します。 |
| IntelliJ IDEA や Eclipse などの IDE | サンプルの編集と実行が容易になります。 |

## 手順 1: Aspose.Words をプロジェクトに追加

Maven を使用している場合、`pom.xml` に以下の依存関係を追加します。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Gradle を使用している場合は、`build.gradle` に次の行を記述します。

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

依存関係が解決したら、Java ソースファイルでライブラリクラスをインポートできます。

## 手順 2: コマンドボタンを挿入 – コアコード

`InsertCommandButtonDemo` という名前の新しい Java クラスを作成します。以下のコードは **コマンドボタンを挿入** するために必要な 4 つの操作をすべて実行します。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### 各行の重要ポイント

* **Document & DocumentBuilder** – Word ファイルのメモリ上表現と、内容を変更するための API を提供します。  
* **insertForms2OleControl** – このメソッドは `COMMAND_BUTTON` タイプの **フォームコントロールを追加** します。返される `Forms2OleControl` オブジェクトが ActiveX コントロールを表します。  
* **setName** – プログラム上の識別子（例: `btnSubmit`）を設定します。Word のマクロや VBA はこの名前を後で参照できます。  
* **setCaption** – ユーザーがボタン上で見るテキストを定義し、**ボタンの追加方法** に対する回答となります。  
* **save** – `.docx` をディスクに書き出し、埋め込まれた ActiveX ボタンを保持します。

プログラムを実行すると、作業ディレクトリに `CommandButtonDemo.docx` が作成されます。Microsoft Word で開くと **Submit** と表示されたボタンが表示され、評価モードではデフォルトの ActiveX ダイアログが表示されます。

## 手順 3: Word で挿入されたボタンを確認

1. Microsoft Word（2016 以降）で `CommandButtonDemo.docx` を開きます。  
2. 挿入時にカーソルがあった位置に **Submit** ボタンが表示されます。  
3. ボタンを右クリックし **Properties** を選択すると、**Name** フィールドに `btnSubmit` が入っていることが確認できます。  

ボタンが表示されない場合は、Word の Trust Center 設定で **ActiveX コントロール** が有効になっているか確認してください。

## 手順 4: ボタンのカスタマイズ（任意）

サイズや位置を変更したり、VBA マクロを追加したりしてボタンをさらにカスタマイズできます。`Forms2OleControl` クラスは `setWidth`、`setHeight`、`setLeft` などの追加プロパティを公開しています。以下はボタンを大きくする例です。

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

これらの行は `setCaption` 呼び出しの後に配置できます。基本的な挿入を超えた **ActiveX ボタンのカスタマイズ** を示しています。

## よくある落とし穴と回避策

| 症状 | 原因 | 対策 |
|------|------|------|
| Word でボタンが表示されない | コントロールを追加する前に文書を保存している | `insertForms2OleControl` を `doc.save` の前に呼び出すことを確認してください。 |
| ボタンのキャプションが空 | `setCaption` を呼び出していない、または空文字列を渡している | `"Submit"` のように空でない文字列を指定してください。 |
| VBA がボタンを見つけられない | VBA コードと `setName` の値が一致していない | 名前を統一し、`setName("btnSubmit")` とし、VBA でも `btnSubmit` を参照してください。 |
| ファイルを開くとセキュリティ警告が出る | Word のマクロセキュリティが ActiveX コントロールをブロックしている | Trust Center > Macro Settings を調整するか、信頼できる証明書で文書に署名してください。 |

## 完全な実行可能サンプル

以下は IDE にコピペできる完全なソースファイルです。インポート文、例外処理、各主要ステップを説明するコメントブロックが含まれています。

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**期待される結果:** プログラム実行後、`CommandButtonDemo.docx` に **Submit** ボタンが 1 つだけ含まれます。Word で開くと、`DocumentBuilder` のカーソル位置にボタンが正確に配置されていることが確認できます。

## 次のステップ

* **さらにフォームコントロールを追加** – `Forms2OleControlType.CHECK_BOX`、`RADIO_BUTTON`、`TEXT_BOX` を使用して完全な Word フォームを構築します。  
* **メールマージと組み合わせ** – メールマージされた文書にボタンを挿入し、パーソナライズされたインタラクティブフォームを作成します。  
* **VBA マクロを添付** – ボタンの `Click` イベントに反応する VBA をプログラムで埋め込み、高度な自動化を実現します。  

これらのトピックは、ここで習得した **フォームコントロールの追加** 手法を自然に拡張します。

---

### まとめ

Java を使用して Word 文書に **コマンドボタンを挿入** する方法、**フォームコントロールの追加**、**ボタン名の設定**、そして **ActiveX ボタンのカスタマイズ** 方法を習得しました。完全なサンプルはすぐに実行でき、任意の文書生成ワークフローに合わせて調整可能です。コーディングを楽しんでください！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示した手法を基にした関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全なコード例が含まれており、API の追加機能をマスターしたり、代替実装アプローチを自分のプロジェクトで試したりするのに役立ちます。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Combo Box Form Field in Word Document](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}