---
category: general
date: 2026-10-13
description: Aspose.Words for Java を使用して Word にフォームフィールド ボタンを作成します。コマンド ボタンのワード フォーム
  フィールドの挿入方法と、コマンド ボタンのキャプションの設定方法を、簡単な手順で学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: ja
lastmod: 2026-10-13
og_description: Aspose.Words for Java を使用して Word にフォームフィールド ボタンを作成します。このチュートリアルでは、コマンド
  ボタンのワード フィールドを挿入し、コマンド ボタンのキャプションをすばやく設定する方法を示します。
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Wordでフォームフィールドボタンを作成 – Aspose.Words Java ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words JavaでWordにフォームフィールドボタンを作成する
url: /ja/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して Word にフォーム フィールド ボタンを作成する

Word 文書に **form field button** を作成する必要がある場合、このガイドでは Aspose.Words for Java を使用した完全な手順をご案内します。入力フォームのテンプレートを作成する場合でも、レポートにインタラクティブなコントロールを追加する場合でも、最小限のコードで **insert command button word** フィールドの挿入と **set command button caption** の設定方法を学べます。

このチュートリアルは Maven のセットアップから完全に実行可能なサンプルまで網羅しているため、コードをコピー＆ペーストして実行し、クリック可能なボタンを含む `.docx` ファイルを確認できます。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

- Java 17（またはそれ以降）がインストールされ、環境設定されていること。
- 依存関係管理のための Maven 3.6+。
- お好みの IDE またはテキストエディタ（例：IntelliJ IDEA、VS Code）。
- 有効な Aspose.Words for Java ライセンス（評価用の無料トライアルでも可）。

## 手順 1: Aspose.Words を Maven プロジェクトに追加する

`pom.xml` を作成（または既存のものを編集）し、Aspose.Words の依存関係を追加します。

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **プロのコツ:** バージョン番号は常に最新に保ちましょう。新しいリリースは最新の Word 機能への対応やパフォーマンス向上が含まれます。

## 手順 2: 空のドキュメントと `DocumentBuilder` を初期化する

`DocumentBuilder` クラスは Word 文書を編集するためのフルエント API を提供します。この手順では空の `Document` を作成し、ビルダーを紐付けます。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

ドキュメントの作成は、後続で **form field button** オブジェクトを作成するための基盤となります。

## 手順 3: コマンド ボタン フォーム フィールドを挿入する

Aspose.Words は OLE フォーム コントロール用に `Forms2OleControl` クラスを公開しています。**insert command button word** フィールドを挿入するには、`COMMANDBUTTON` 列挙値を指定して `insertForms2OleControl` を呼び出します。

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

このメソッドは `Forms2OleControl` インスタンスを返し、保存前に設定を行うことができます。

## 手順 4: ボタンのサイズと位置を定義する

コマンド ボタンには明示的な寸法とページ上の配置が必要です。幅・高さ・座標をレイアウトに合わせて調整してください。

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

これらの値を微調整することで、最終文書内でボタンが正確に配置されます。

## 手順 5: **コマンド ボタンのキャプションを設定する**

ボタンに表示されるテキストは `setCaption` メソッドで制御します。ここで **set command button caption** を使用してユーザーへの指示を設定します。

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

`"Click Me"` を、フォームの目的に合わせた任意のラベル（例：`"Submit"` や `"Approve"`）に置き換えることができます。

## 手順 6: ドキュメントを保存する

最後にドキュメントをディスクに書き出します。生成されたファイルにはインタラクティブなボタンが含まれ、Microsoft Word や LibreOffice で開くことができます。

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

プログラムを実行すると `CommandButtonDemo.docx` が生成されます。Word で開くと、左端から 50 pt、上端から 100 pt の位置に **Click Me** と表示されたボタンが配置されています。

### 期待される出力

- `CommandButtonDemo.docx` という名前の `.docx` ファイル。
- ドキュメントは単一ページで、コマンド ボタン フォーム フィールドが含まれています。
- ボタンは設定したキャプション（例：**Click Me**）を表示します。

## 一般的なバリエーションとエッジケース

| 状況 | 対応方法 |
|-----------|--------------|
| **複数のボタン** | `insertForms2OleControl` を繰り返し呼び出し、各ボタンの `setLeft`/`setTop` を調整します。 |
| **ボタンごとに異なるキャプション** | 挿入後に `setCaption` をユニークな文字列で呼び出します。 |
| **テーブルセル内のボタン** | `builder.moveTo(cell.getFirstParagraph())` で目的のセルにカーソルを移動してからコントロールを挿入します。 |
| **レガシー Word 形式（.doc）** | `doc.save("Demo.doc", SaveFormat.DOC);` で保存します。コマンド ボタンは保持されます。 |
| **読み取り専用フォーム** | 挿入後に `commandButton.setEnabled(false);` を設定し、ユーザー操作を無効化します。 |

## 安定した実装のためのヒント

- **寸法の検証**: 幅が極端に大きいとページ余白をはみ出す可能性があります。
- **ライセンスの適用**: 有効なライセンスがない場合、Aspose.Words は生成ドキュメントに透かしを追加します。`License license = new License(); license.setLicense("Aspose.Words.lic");` のように早めにライセンスを適用してください。
- **テスト**: 生成ファイルを Word で開き、**Design Mode**（開発タブ → Design Mode）を切り替えてボタンのプロパティを確認します。

## 完全なソースコードまとめ

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

コードを `InsertCommandButtonDemo.java` という名前のファイルにコピーし、Maven でコンパイル（`mvn compile`）し、実行（`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`）してください。生成されたドキュメントはプロジェクトのルートフォルダに出力されます。

## 結論

これで Aspose.Words for Java を使用して Word に **form field button** を作成し、**insert command button word** フィールドを挿入し、**set command button caption** をプログラムで設定する方法が分かりました。このエンドツーエンドの例は、単一の送信ボタンからフルセットのフォーム コントロールまで、リッチでインタラクティブな Word 文書を構築するための堅実な基盤を提供します。

### 次にやることは？

- チェック ボックス (`Forms2OleControlType.CHECKBOX`) やテキスト ボックス (`Forms2OleControlType.TEXTBOX`) など、他のフォーム コントロールを探求する。
- メールマージと組み合わせて、個別化されたアンケートを自動生成する。
- Aspose.Words の `FormField` API を使用して、文書が記入された後のユーザー入力データを取得する。

さまざまなサイズ、キャプション、配置で実験してみてください。コマンド ボタンの操作に慣れたら、Word 自動化パイプラインにフル機能のフォームを追加する作業はシンプルになります。コーディングを楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした、密接に関連するトピックをカバーしています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for Java の DocumentBuilder を使用してフォーム フィールドを作成し、コンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for .NET で Word 文書にコンボ ボックス フォーム フィールドを追加する](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words for .NET で Word 文書にチェック ボックス フォーム フィールドを追加する](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}