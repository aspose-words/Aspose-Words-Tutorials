---
category: general
date: 2026-11-22
description: Java を使用して Word 文書にマクロボタンを作成する。コマンドボタンの挿入、ボタンテキストの設定、マクロをボタンにリンクさせる方法を学び、インタラクティブな文書を実現する。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: ja
lastmod: 2026-11-22
og_description: Java を使用して Word 文書にマクロ ボタンを作成します。このチュートリアルでは、コマンド ボタンの挿入方法、ボタン テキストの設定方法、そしてマクロをボタンにリンクさせて完全なインタラクティブ性を実現する方法を示します。
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: JavaでWord文書にマクロボタンを作成する – ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Aspose.Words for Java を使用して Word 文書にマクロボタンを作成する方法
url: /ja/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して Word 文書にマクロボタンを作成する方法

Word ファイルに **マクロボタンを作成** する必要がある場合、このガイドでは必要な手順を正確に説明します。**コマンドボタンの挿入**、**ボタンテキストの設定**、**マクロのボタンへのリンク** の方法を学び、文書を完全にインタラクティブにします。

開発者はしばしば OLE コントロールを埋め込み、文書内から VBA マクロをトリガーします。このチュートリアルでは、プロジェクトのセットアップから、.docx ファイルに **インタラクティブなボタン** を追加する実行可能な Java サンプルまで、全工程をカバーします。外部スクリプトは不要で、すべて Java プロセス内で実行されます。

## 前提条件

開始する前に、以下がインストールされていることを確認してください。

* JDK 17 以上
* Maven 3.8+（または Gradle） – 依存関係管理用
* Aspose.Words for Java 23.9 以上 – `DocumentBuilder` と OLE コントロール API を提供
* Java と VBA マクロの基本的な知識

これらの項目のいずれかが不足している場合は、先にインストールしてください。以降のチュートリアルはそれらが利用可能であることを前提としています。

## Aspose.Words for Java でマクロボタンを作成する方法

ソリューションのコアは次の 4 つのアクションで構成されます。

1. **コマンドボタン OLE コントロールを文書に挿入**  
2. **ボタンテキスト（キャプション）を設定**  
3. **マクロをボタンにリンク**  
4. **マクロを埋め込んだ状態で文書を保存**

各アクションは以下のセクションで詳しく説明します。

### 手順 1: 文書にコマンドボタンを挿入

`DocumentBuilder.insertForms2OleControl` は指定されたタイプの OLE コントロールを作成します。`Forms2OleControlType.COMMAND_BUTTON` 定数により、Aspose.Words はマクロをホストできるコマンドボタンを生成します。

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**この重要性:** OLE コントロールはマクロのコンテナとして機能します。これを挿入しなければ、ユーザーがクリックできる視覚要素が存在しません。

### 手順 2: ボタンテキスト（キャプション）を設定

キャプションはボタン上に表示されるラベルです。`setCaption` を使用して、ユーザーに見せるテキストを定義します。

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**この重要性:** 明確なボタンテキストはユーザビリティを向上させます。`setCaption` メソッドは OLE コントロールの `Caption` プロパティを更新し、Word がボタンラベルとして描画します。

### 手順 3: マクロをボタンにリンク

マクロは名前で識別されます（例: `MyMacro`）。`setOnClick` メソッドはこの名前をボタンの `OnClick` イベントハンドラに格納します。

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**この重要性:** マクロをリンクすることでインタラクティブな動作が実現します。ユーザーが Word でボタンをクリックすると、関連付けられた VBA ルーチンが実行されます。

### 手順 4: Word 文書にインタラクティブなボタンを追加

OLE コントロールの設定が完了したら、位置を調整したりサイズを変更したり、周囲にテキストを追加したりできます。`DocumentBuilder` は文書上で引き続き操作できるため、ボタンの前後に段落を挿入することが可能です。

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**この重要性:** `.docm` として保存するとマクロコードが保持されます。`.docx` で保存するとマクロ参照は失われます。

## 完全な実行可能サンプル

以下はインポート、例外処理、各ステップの説明コメントを含む完全な Java プログラムです。Aspose.Words の依存関係を持つ Maven プロジェクトにコードをコピーし、実行してください。

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### 期待される出力

プログラムを実行すると `MacroButtonDemo.docm` が生成されます。Microsoft Word でファイルを開くと次のように表示されます。

* 「**Press the button to execute the macro:**」という段落  
* 段落のすぐ下に **Run Report** とラベル付けされたボタン  
* ボタンをクリックすると、Word がマクロ `MyMacro` の実行を試みます（実際の VBA コードは手動で文書に追加するか、別の自動化手順で挿入してください）

マクロが存在しない場合、Word はセキュリティ警告を表示します。これはマクロ有効文書の標準的な動作です。

## よくあるバリエーションとエッジケース

| シナリオ | コードの適応方法 |
|----------|-------------------|
| **異なるボタンキャプション** | `setCaption` に渡す文字列を変更 |
| **複数ボタン** | `insertForms2OleControl` を繰り返し呼び出し、各々に `setCaption` と `setOnClick` を設定 |
| **カスタムマクロ名** | `"MyMacro"` を任意の有効な VBA 手続き名（例: `"ExportToExcel"`）に置き換え |
| **ボタンサイズの制約** | `setWidth` と `setHeight` の値を調整。Word は指定したポイント数を尊重 |
| **プログラムでマクロを埋め込む** | `Document.getBuiltInDocumentProperties().add("Macros", …)` もしくは別途 VBA 注入ステップを使用。Aspose.Words 自体は VBA コードを書き込めません |

**プロのコツ:** 開発中はマクロセキュリティを *すべてのマクロを有効にする* に設定したマシンで生成した `.docm` を必ずテストしてください。本番環境では、信頼できる証明書でマクロに署名し、セキュリティ警告を回避します。

## トラブルシューティングチェックリスト

* **ボタンが表示されない** – 文書が `.docm` で保存され、OLE コントロールをサポートする Word バージョンで開かれているか確認  
* **マクロが実行されない** – マクロ名が完全に一致しているか（大文字小文字含む）と、文書の VBA プロジェクトにマクロが存在するか確認  
* **ボタンキャプションが切れる** – `setWidth` でボタン幅を拡大し、長いテキストを収める  
* **予期しないレイアウトシフト** – `builder.moveTo` でカーソル位置を正確に指定してからコントロールを挿入  

## 結論

これで Java を使用して Word 文書に **マクロボタンを作成** し、**コマンドボタンの挿入**、**ボタンテキストの設定**、**マクロのボタンへのリンク** を行う方法が分かりました。完全なサンプルは必要な API 呼び出しをすべて示し、各ステップの重要性を解説し、一般的なバリエーションへの対応策も提供しています。

次に検討できること:

* 既存テンプレートに **インタラクティブなボタンを追加** する  
* Open XML SDK や別の自動化ツールを使って **プログラムで VBA コードを注入** する  
* 複数の OLE コントロール（チェックボックス、リストボックスなど）を組み合わせてリッチフォームを構築  

さまざまなキャプション、マクロ名、ボタンサイズを試して、特定のユースケースに合わせて調整してください。ハッピーコーディング！

## 次に学ぶべきこと

以下のチュートリアルは、本ガイドで示したテクニックを基にした関連トピックを扱っています。各リソースには完全なコード例とステップバイステップの解説が含まれており、API の追加機能を習得したり、代替実装アプローチを探求したりするのに役立ちます。

- [Java を使用して Word 文書にコマンドボタンを挿入する方法](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Java で Word 文書のボタン位置を設定する方法](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [ActiveX ボタンを Word に挿入 – ボタンキャプションを設定する方法](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}