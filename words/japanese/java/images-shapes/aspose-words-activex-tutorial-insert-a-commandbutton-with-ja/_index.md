---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX チュートリアルでは、Java を使用して Word 文書に CommandButton コントロールを追加する方法を示します。完全なコード、設定、保存手順を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: ja
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX チュートリアルでは、Java を使用して Word 文書に CommandButton ActiveX
  コントロールを埋め込む方法を解説します。完全なサンプルに従って、文書の作成、設定、保存を行ってください。
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX チュートリアル – Java ステップバイステップガイド
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX チュートリアル – Javaで CommandButton を挿入する
url: /ja/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX チュートリアル – Javaで CommandButton を挿入する

Word ファイルに ActiveX コントロールを埋め込む必要がある場合、この **Aspose.Words ActiveX チュートリアル** が全工程を案内します。ブランクドキュメントの作成、CommandButton の挿入、プロパティの設定、結果の保存を、純粋な Java コードだけで行う方法が分かります。

この例は Aspose.Words for Java API を使用しており、ビルドサーバーに Microsoft Office が不要です。このガイドの最後までに、Windows 環境で使用できる完全に機能する CommandButton コントロールを含む .docx ファイルを生成できるようになります。

## 前提条件

- Java Development Kit (JDK) 8 以上がインストールされていること。
- Maven などのビルドツールで依存関係を管理できること。
- Aspose.Words for Java のライセンス（または一時評価キー）を取得し、評価透かしを回避すること。
- Java の構文とオブジェクト指向プログラミングの基本的な知識があること。

> **Pro tip:** Aspose.Words の Maven 依存関係を `pom.xml` に追加すると、IDE がクラスを自動的に解決します：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Step 1: 新しい空白ドキュメントと `DocumentBuilder` を作成する

`Document` クラスはメモリ上の Word ファイルを表し、`DocumentBuilder` はドキュメント編集用のフルエント API を提供します。両方のオブジェクトを初期化することで、以降の変更に備えたドキュメントが準備されます。

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**この点が重要な理由:**  
`DocumentBuilder` は現在のカーソル位置を追跡するため、コントロールの挿入などの後続操作が意図した正確な位置に表示されます。

## Step 2: CommandButton ActiveX コントロールを挿入する

Aspose.Words は ActiveX オブジェクト用に `Forms2OleControl` を公開しています。`insertForms2OleControl` メソッドはコントロールタイプを要求し、`Forms2OleControlType` 列挙体で指定します。

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**説明:**  
挿入されたコントロールは COM ベースのオブジェクトで、Windows 環境でドキュメントを開くとクリック可能なボタンとして Word に表示されます。

## Step 3: ボタンのプロパティを設定する

挿入後、ボタンの名前、キャプション、サイズ、位置を調整できます。これらのプロパティは Word 内でのコントロールの見た目と動作に影響します。

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**これらの設定が重要な理由:**  

- **Name** – VBA マクロがコントロールを参照できるようにします (`ActiveDocument.Forms("cmdSubmit")`)。
- **Caption** – ユーザーがクリックする表示ラベルを決定します。
- **Left / Top** – ページ余白に対する配置を制御します。
- **Width / Height** – 異なる画面解像度でも一貫した見た目のサイズを保証します。

## Step 4: ドキュメントを保存する

`save` を呼び出すと、メモリ上の表現が物理ファイルに書き出されます。任意のサポート形式（`.docx`、`.doc`、`.pdf` など）を選択できますが、このチュートリアルではネイティブの Word 形式を使用します。

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**結果:**  
`ActiveXDemo.docx` を Microsoft Word で開くと、指定した座標に **Submit** とラベル付けされた CommandButton が表示されます。クリックするとデフォルトの動作が実行されます（デフォルトでは VBA コードは付随しません）。

## 完全なソースコード

部品を組み合わせた、実行可能な完全プログラムは次のとおりです：

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### 期待される出力

- `output` フォルダーに **ActiveXDemo.docx** という名前のファイルが作成されます。
- Microsoft Word (Windows) で開くと、定義された位置にクリック可能な **Submit** ボタンが表示されます。
- ボタンは選択、移動、または Word UI（Developer → Properties）から VBA コードにリンクできます。

## 一般的なバリエーションの取り扱い

| シナリオ | 調整 |
|----------|------------|
| **.doc 形式で保存**（レガシーフォーマット） | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **イベントハンドラを追加** | Word は Aspose.Words 経由で ActiveX イベントを公開していません。ドキュメント生成後に手動で VBA コードを追加する必要があります。 |
| **複数のコントロール** | `setName` と `setCaption` の値を変えて、挿入/設定ブロックを繰り返します。 |
| **異なるコントロールタイプ（例: CheckBox）** | `insertForms2OleControl` 呼び出しで `Forms2OleControlType.CHECKBOX` を使用します。 |
| **非 Windows プラットフォーム** | ActiveX コントロールは Windows の Word でのみ表示されます。クロスプラットフォームの解決策として、コンテンツコントロール（`StructuredDocumentTag`）を検討してください。 |

## ベストプラクティスと落とし穴

- **ライセンスは早めに取得** – `Document` を作成する前に Aspose.Words のライセンスを登録し、評価プロンプトを回避します。
- **座標系** – 位置はポイントで測定されます (1 pt = 1/72 in)。UI デザインでピクセルやセンチメートルを使用している場合は変換してください。
- **ファイルパス** – 出力ディレクトリが存在しない場合の `FileNotFoundException` を防ぐため、絶対パスまたは Java の `Paths` API を使用します。
- **スレッド安全性** – `Document` と `DocumentBuilder` はスレッドセーフではありません。並列でドキュメントを生成する場合は、スレッドごとに別々のインスタンスを作成してください。
- **テスト** – 生成されたドキュメントを対象の Word バージョン（例: Word 2016、Word 365）で確認してください。古いバージョンでは ActiveX コントロールの表示が異なる場合があります。

## 結論

この **Aspose.Words ActiveX チュートリアル** は、Java を使用して Word ドキュメントに CommandButton コントロールをプログラムで追加する方法を示しています。学んだことは次のとおりです。

1. `Document` と `DocumentBuilder` を初期化する。
2. `Forms2OleControl` の `COMMAND_BUTTON` タイプを挿入する。
3. ボタンの名前、キャプション、サイズ、位置を設定する。
4. ActiveX コントロールを含む .docx ファイルとして保存する。

ここからは、他のコントロールタイプを試したり、VBA マクロの自動挿入を行ったり、ActiveX コントロールと Aspose.Words の他機能（メールマージやコンテンツコントロールなど）を組み合わせたりできます。さまざまなレイアウトで実験し、生成されたドキュメントを Java ベースのレポートパイプラインに統合してください。

---


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした関連トピックを扱っています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得したり、プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Aspose.Words for Java における OLE オブジェクトと ActiveX コントロールの使用](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Aspose.Words for Java で DocumentBuilder を使用してフォームフィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java チュートリアル：Word を RTF に変換する](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}