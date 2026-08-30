---
category: general
date: 2026-07-20
description: Aspose.Words を使用して Word 文書にボタンを追加する方法。DocumentBuilder で Forms2OleControl
  ボタンを数分で挿入する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: ja
lastmod: 2026-07-20
og_description: Aspose.WordsでWord文書にボタンを追加する方法。Javaを使用してForms2OleControl CommandButtonを埋め込む実践ガイドをご覧ください。
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Word文書にボタンを追加する方法 – 完全なAspose.Wordsチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Word文書にボタンを追加する方法 – ステップバイステップガイド
url: /ja/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメントにボタンを追加する方法 – 完全な Aspose.Words チュートリアル

UI を開いてクリックすることなく、**Word ドキュメントにボタンを追加する方法**を考えたことがありますか？ あなただけではありません。多くの開発者がプログラムでインタラクティブなコントロールを埋め込む必要があります—たとえば、後でエンドユーザーが入力するテンプレート内の「Submit」ボタンを想像してください。良いニュースは、Aspose.Words for Java を使えば、数行のコードで実現できることです。

このチュートリアルでは、`DocumentBuilder` を使用して **CommandButton** タイプの `Forms2OleControl` を挿入する正確な手順を解説します。最後には、クリック可能な「Click Me」ラベルの付いた `.docx` ファイルがすぐに使える状態になります。謎はなく、明快なコードと各行の背後にある理由だけです。

## 学べること

- ゼロから新しい Word ドキュメントを作成する方法
- **DocumentBuilder** を使って **Forms2OleControl** を配置する方法
- ボタンのキャプションを設定し、サイズを調整する理由
- ドキュメントを保存して結果を確認する方法
- よくある落とし穴（例：ライブラリが見つからない、サポートされていないコントロールタイプ）と回避策

**前提条件** – Java 8 以上（またはそれ以降）と Aspose.Words for Java ライブラリ（バージョン 23.12 以降）が必要です。IntelliJ IDEA や Eclipse といった IDE があると作業が楽になりますが、テキストエディタでも構いません。

---

## 手順 1: プロジェクトをセットアップし依存関係をインポート

コードを実行する前に、Maven（または Gradle）に Aspose.Words の取得先を知らせる必要があります。`pom.xml` に以下のスニペットを追加してください。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle を使用する場合は、同等の記述は次のとおりです。

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **プロのコツ:** 常に最新リリースを使用してください。古いバージョンには `Forms2OleControl` API が含まれていないことがあります。

依存関係が解決したら、Java コードを書き始める準備が整います。

---

## 手順 2: 新しい Document を作成し DocumentBuilder を取得

`Document` クラスは `.docx` パッケージ全体を表し、`DocumentBuilder` はその上にコンテンツを描画するための筆です。`DocumentBuilder` は次に配置すべき要素の位置を把握している「カーソル」のようなものです。

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**この処理が重要な理由:** 新しい `Document` を初期化すると、クリーンなキャンバスが得られます。ビルダーは自動的に最初の段落を指すので、セクションやページを手動で管理する必要がありません。

---

## 手順 3: CommandButton タイプの Forms2OleControl を挿入

ここが本題です: `insertForms2OleControl` メソッドは、Word がフォーム要素として扱う OLE（Object Linking and Embedding）コントロールを作成します。3 つの引数を渡します。

1. `Forms2OleControlType.COMMANDBUTTON` – ボタンであることを Word に指示します。
2. `100` – 幅（ポイント、約 1.39 インチ）。
3. `30` – 高さ（ポイント、約 0.42 インチ）。

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**動作概要:** Aspose.Words は内部で `word/document.xml` 部分に適切な XML を生成し、OLE オブジェクトを参照します。指定した寸法は Word のレイアウトエンジンに尊重されるため、ビルダーのカーソル位置にボタンが正確に表示されます。

---

## 手順 4: ボタンのキャプション（テキスト）を設定

ラベルのないボタンは分かりにくいです—無音のエレベーターボタンを想像してください。`setCaption` メソッドで表示テキストを設定します。

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

キャプションは自由に変更可能です: 「Submit」や「Approve」、あるいはローカライズされた文字列でも構いません。キャプションは OLE オブジェクトのプロパティに保存され、Word がネイティブに描画します。

---

## 手順 5: ドキュメントを保存し結果を確認

最後に、ファイルをディスクに書き出します。書き込み権限のあるフォルダーを選んでください。権限がないと `IOException` が発生します。

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`button-demo.docx` を Microsoft Word で開くと、ドキュメント上部に **Click Me** とラベル付けされたボタンが表示されます。Word でクリックすると、デフォルトの OLE 動作（通常はプレースホルダー メッセージ）がトリガーされます（マクロをバインドしない限り）。

---

## よくあるエッジケースと対処法

| 状況 | 発生理由 | 対策 |
|-----------|----------------|-----|
| **Missing `Forms2OleControl` type** | 古い Aspose.Words バージョンではこの enum が公開されていません。 | 23.12 以降にアップグレードしてください。 |
| **Button appears as a picture** | Word のセキュリティ設定が OLE コントロールをブロックしています。 | Trust Center で「VBA プロジェクト オブジェクト モデルへのアクセスを信頼する」を有効にするか、マクロ有効 `.docm` を使用してください。 |
| **Incorrect size** | ポイントとピクセルの混同。 | 1 ポイント = 1/72 インチであることを忘れず、数値を調整してください。 |
| **Saving throws `FileNotFoundException`** | パスが存在しません。 | `output/` ディレクトリが存在することを確認してください。`new File("output").mkdirs();` を使用すると便利です。 |

---

## 例の拡張: 複数ボタンや他のコントロールを追加

ボタンを複数配置したい場合は、`builder.moveTo` や `builder.writeln()` でカーソルを移動させてから、再度 `insertForms2OleControl` を呼び出すだけです。

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

`Forms2OleControlType.COMMANDBUTTON` を適切な enum 値（`CHECKBOX`, `COMBOBOX` など）に置き換えることで、**CheckBox**、**ComboBox**、**ListBox** も挿入できます。幅・高さパラメータは同様に適用されます。

---

## 大規模な Word 自動化ワークフローへの位置付け

- **テンプレート生成:** 下流の承認用に「Approve」ボタンを含む契約テンプレートを作成。
- **レポーティング:** マクロをトリガーする「Refresh Data」ボタンを備えた日次レポートを生成。
- **フォーム配布:** 事前にインタラクティブコントロールが埋め込まれたアンケートを配布。

これらすべてのシナリオで、今回示した **Word 自動化** アプローチが有効です。プログラムでコントロールを埋め込むことで、手作業の編集を排除しヒューマンエラーを削減できます。

---

## 完全なソースコード（コピー＆ペースト用）

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**期待される出力:** `output/button-demo.docx` を Microsoft Word で開くと、ファイル上部に縦に並んだ 2 つのボタン—「Click Me」と「Submit」—が表示されます。

---

## 結論

Aspose.Words for Java を使用して **Word ドキュメントにボタンを追加する方法** をステップバイステップで解説しました。空の `Document` から開始し、**DocumentBuilder** で **CommandButton** タイプの `Forms2OleControl` を挿入し、キャプションを設定して保存するという流れです。この手法は複数コントロールへの拡張や、より大規模な **Word 自動化** パイプラインへの統合にも適しています。

次の課題に挑戦してみませんか？ボタンを **CheckBox** に置き換える、あるいは `.docm` ファイルでマクロをバインドしてクリック時に動作させるなど、同じパターンで実装できます。

問題が発生したら、ライブラリのバージョンと出力フォルダーの権限を再確認してください。質問や独自のユースケースがあれば、下のコメント欄でぜひ共有してください。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには、完全に動作するコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}