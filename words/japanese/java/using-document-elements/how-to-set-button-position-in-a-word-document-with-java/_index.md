---
category: general
date: 2026-09-24
description: Java と Aspose.Words を使用して Word 文書内のボタン位置を設定します。ボタンの挿入方法、ActiveX コントロールの追加方法、Java
  スタイルの Word 文書の作成方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: ja
lastmod: 2026-09-24
og_description: Java を使用して Word 文書内のボタン位置を設定する。このガイドでは、ボタンの挿入方法、ActiveX コントロールの追加方法、そして
  Aspose.Words を使用した Java の Word 文書作成方法を示します。
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: JavaでWord文書のボタン位置を設定する – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: JavaでWord文書のボタン位置を設定する方法
url: /ja/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでWord文書のボタン位置を設定する方法

Word ファイル内に **ボタン位置を設定** したい場合、このガイドでは完全に実行可能なソリューションを示します。ユーザー操作が必要なテンプレートを作成する場合でも、フォームを自動化する場合でも、**ボタンの挿入方法** を Aspose.Words for Java を使って学び、その配置を制御する方法が分かります。

このチュートリアルでは、Word 文書に **ActiveX コントロールを追加** する手順をすべて網羅し、**Word にボタンを追加** する方法を解説し、**Java で Word 文書を作成** するフロー全体を実演します。外部参照は不要です—コピーして実行し、結果を確認するだけです。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17（または Java 8 以上のランタイム）
* 依存関係管理に Maven または Gradle
* Aspose.Words for Java のライセンス（評価用の無料トライアルでも可）
* Java の基本的な構文理解

> **プロのコツ:** Aspose.Words の JAR を `libs/` フォルダーに入れ、プロジェクトのクラスパスに追加してバージョン競合を回避しましょう。

## 手順 1: Maven プロジェクトのセットアップ

シンプルな Maven プロジェクト（または Gradle）を作成し、Aspose.Words の依存関係を追加します。

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean compile` を実行するとライブラリがダウンロードされ、ビルドパスが設定されます。

## 手順 2: 新しい Word 文書を作成

最初の操作は **Java で Word 文書を作成** することです。`Document` オブジェクトと、ファイル編集を可能にする `DocumentBuilder` をインスタンス化します。

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` クラスは .docx 全体を表し、`DocumentBuilder` はコンテンツ挿入用の流暢な API を提供します。

## 手順 3: ボタンの挿入 – ActiveX コントロールの追加

Aspose.Words は `Forms2OleControl` クラスを通じて、CommandButton などのレガシー ActiveX コントロールを挿入できます。この手順では、**ボタンの挿入方法** を正確に示します。

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

`insertForms2OleControl` メソッドは `Forms2OleControl` インスタンスを返し、これを設定します。これが **ActiveX コントロールを追加** するプロセスの核心です。

## 手順 4: ボタン位置の設定

ここで実際に **ボタン位置を設定** します。コントロールの `setLeft` と `setTop` メソッドはポイント単位で値を受け取ります（1 pt = 1/72 in）。画面座標に合わせるため、ピクセルをポイントに変換します（1 px ≈ 0.75 pt）。例では左端から 100 px、上端から 150 px の位置にボタンを配置します。

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

**ボタン位置の設定** ロジックがここにカプセル化されているため、コントロールの移動が必要なときはこのコードを再利用できます。数値はレイアウト要件に合わせて調整してください。

## 手順 5: サイズとキャプションの定義

ラベルのないボタンは分かりにくいです。`setWidth`、`setHeight`、`setCaption` を使って見た目を整えましょう。

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

サイズもポイントで表すため、一貫性を保つためにピクセルから変換しています。

## 手順 6: 文書の保存 – **Java で Word 文書を作成** フローの完了

最後にファイルをディスクに永続化します。パスは絶対でもプロジェクトルートからの相対でも構いません。

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

プログラムを実行すると `output` フォルダー内に `CommandButtonDemo.docx` が生成されます。Microsoft Word で開くと、設定した位置にクリック可能なボタンが正確に表示されます。

### 期待される出力

* **CommandButtonDemo.docx** という名前の `.docx` ファイル
* 文書内に「Click Me」とラベル付けされた **CommandButton** が左余白から 100 px、上余白から 150 px の位置に表示される
* Word で文書を開くとボタンがクリックに応答し、カスタム VBA コードを付加しない限りデフォルトの ActiveX メッセージが表示される

## 手順 7: よくあるバリエーションとエッジケース

### 複数ボタンの追加

**Word にボタンを追加** する必要が複数回ある場合は、手順 3‑5 を新しい `Forms2OleControl` インスタンスで繰り返します。`setTop` の値を調整してボタンが重ならないようにしてください。

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### ライセンスなしでの動作

ライセンス未取得で使用すると Aspose.Words は透かしを付加します。本番コードではライセンスを購入し、`main` の冒頭で適用してください。

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### 古い Office バージョンとの互換性

ActiveX コントロールは `.doc`（Word 97‑2003）形式でもサポートされています。レガシーファイルを作成するには、保存形式を変更します。

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## 完全なソースコード（実行可能）

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

ファイルを `src/main/java/CommandButtonDemo.java` として保存し、`mvn exec:java -Dexec.mainClass=CommandButtonDemo` を実行、生成された文書を開いて結果を確認してください。

## よくある質問

**Q: OpenJDK でも動作しますか？**  
A: はい。Aspose.Words は純粋な Java ライブラリで、OpenJDK を含む JDK 8 以上の実装で動作します。

**Q: ボタンのフォントや色を変更できますか？**  
A: ActiveX ボタンの外観はホストアプリケーション（Word）で制御されます。実行時にプロパティを変更する VBA コードを添付できますが、静的な外観はデフォルトスタイルに限られます。

**Q: ボタンを表セル内に配置したい場合は？**  
A: `DocumentBuilder` のカーソルをセル内に移動してから `insertForms2OleControl` を呼び出します。コントロールはセルのレイアウトを継承し、`setLeft`/`setTop` で微調整できます。

## 結論

これで Java を使って Word 文書内の **ボタン位置を設定** する方法、**ボタンの挿入方法**、**ActiveX コントロールの追加**、そして **Word にボタンを追加** する手順をマスターしました。**Java で Word 文書を作成** プロジェクトのベストプラクティスに沿った完全なサンプルが、プロジェクト設定から機能する `.docx` ファイルの生成までの全工程を示しています。

### 次のステップ

* `Forms2OleControl.ControlType` の他の値（例: `CHECKBOX`、`TEXTBOX`）を試して、よりリッチなフォームを構築する  
* ボタンに VBA マクロを組み合わせてカスタムクリック処理を実装する  
* Aspose.Words のメールマージ機能を活用し、インタラクティブコントロールを含むパーソナライズ文書を自動生成する

Happy coding, and enjoy automating Word documents with Java!

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、完全に動作するコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}