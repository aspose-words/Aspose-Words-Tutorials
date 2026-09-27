---
category: general
date: 2026-09-27
description: Aspose.Words を使用して Java で ActiveX を含む docx を作成します。ActiveX コマンドボタンの挿入方法をステップバイステップで学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: ja
lastmod: 2026-09-27
og_description: Aspose.Words を使用して Java で ActiveX を含む docx を作成します。このガイドに従って ActiveX
  コマンドボタンを挿入し、ドキュメントを保存してください。
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: JavaでActiveXを含むdocxを作成する完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Java と Aspose.Words を使用して ActiveX を含む docx を作成する方法
url: /ja/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java と Aspose.Words を使用して ActiveX を含む docx を作成する方法

ActiveX を含む docx を作成する必要がある場合、このガイドでは完全なソリューションを示します。Aspose.Words for Java を使用して Word ファイルに **insert ActiveX command button** を挿入する方法を学び、結果を Microsoft Word で開くことができる .docx として保存します。

プログラムで Word ドキュメントを生成することで、手動編集の手間を省き、レポート、契約書、フォームテンプレート間での一貫性を保証できます。以下の手順では、プロジェクトのセットアップから一般的な落とし穴の対処まで網羅しているので、任意の Java アプリケーションにこの手法を組み込むことができます。

## 前提条件

* Java Development Kit (JDK) 8 以上がインストールされていること。
* Maven 3.6+（またはお好みのビルドツール）。
* Aspose.Words for Java のライセンス ファイル（無料評価版はテストに使用可能）。
* ActiveX コントロールを視覚的に確認したい場合は、対象マシンに Microsoft Word がインストールされていること。

これらは必須項目です。Aspose.Words がドキュメント作成用の API を提供し、Word が ActiveX コントロールの表示に必要となります。

## 手順 1: Maven プロジェクトのセットアップ

新しい Maven プロジェクトを作成するか、既存の `pom.xml` に Aspose.Words の依存関係を追加します：

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Aspose.Words のバージョンを公式リリースノートと同期させて、バグ修正や新しい ActiveX 機能の恩恵を受けましょう。

## 手順 2: ドキュメントを作成する Java コードを書く

`ActiveXDocxCreator` という名前のクラスを作成します。以下のコードには必要なインポート、`main` メソッド、各操作を説明する詳細なコメントが含まれています。

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### 各行が重要な理由

* `Document` はすべての Word コンテンツのコンテナです。新しいインスタンスを作成するとクリーンなキャンバスが得られます。
* `DocumentBuilder` は要素を挿入するためのフルエント API を提供し、挿入位置を自動的に追跡します。
* `insertForms2OleControl()` は汎用的な OLE コントロールのプレースホルダーを作成します。Aspose.Words はこれを ActiveX コンテナとして扱います。
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` は、プレースホルダーを CommandButton としてレンダリングするよう Word に指示します。
* `setCaption("Click Me")` はボタンに表示されるテキストを定義します。
* `setLeft` と `setTop` はページ余白に対するボタンの位置を設定します。レイアウトに合わせてこれらの値を調整してください。
* `setWidth` と `setHeight` はオプションですが、デフォルトサイズが小さい場合などにボタンの外観を改善します。
* `doc.save` はメモリ上の構造を物理的な .docx ファイルに書き出し、Word で開くことができるようにします。

## 手順 3: 生成されたドキュメントを検証する

Microsoft Word で `output/ActiveXCommandButton.docx` を開きます：

1. ドキュメントは、**Click Me** とラベル付けされたボタンが左上付近に配置された単一ページを表示するはずです。
2. ボタンが表示されない場合は、Word の「信頼センター」(File → Options → Trust Center → Trust Center Settings → ActiveX Settings) で **ActiveX controls are enabled** が有効になっているか確認してください。
3. ボタンは ActiveX をサポートする Windows 版 Word でのみ機能します。macOS や Web ベースの Word では、コントロールは静的画像として表示されます。

## 手順 4: 一般的なエッジケースの対処

| 状況 | 理由 | 推奨アクション |
|-----------|--------|--------------------|
| ファイルを開いた後にボタンが表示されない | Word のセキュリティ設定が ActiveX をブロックしている | 信頼できる場所に対して “Run all controls without restrictions” を有効にする。 |
| 生成された .docx が開けない | Aspose.Words のバージョンが互換性がない | 最新の Aspose.Words リリースにアップグレードする。古いバージョンでは必要な OLE パーツが正しく埋め込まれない可能性がある。 |
| ボタンにマクロを実行させたい | ActiveX だけではマクロコードが含まれない | `Click` イベントを処理する VBA マクロと ActiveX コントロールを組み合わせる。`DocumentBuilder.insertOleObject` メソッドを使用してマクロ有効テンプレートを埋め込む。 |
| ページサイズが異なるとレイアウトが崩れる | 座標が絶対ポイントで指定されている | コントロールを配置する前に `builder.getPageSetup().setPageWidth` と `setPageHeight` を使用してページサイズを標準化する。 |

## 手順 5: ソリューションの拡張

`ControlType` 列挙体を変更することで、他の ActiveX コントロールを挿入できます：

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words は **ActiveX テキスト ボックス**、**リスト ボックス**、**コンボ ボックス** の挿入もサポートしています。同じ配置メソッド（`setLeft`、`setTop`、`setWidth`、`setHeight`）が適用されます。

複数のコントロールを配置する必要がある場合は、`builder.insertForms2OleControl()` を繰り返し呼び出し、各コントロールの座標を適宜調整してください。

## 完全なソースファイル

以下はコピー＆ペースト用に用意した `ActiveXDocxCreator.java` ファイル全体です。

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

このプログラムを実行すると、**docx containing ActiveX** が生成され、インタラクティブ フォームが必要なエンドユーザーに配布できます。

## 結論

これで、Java と Aspose.Words を使用して **create docx containing ActiveX** を行い、プログラムで **insert ActiveX command button** する方法が分かりました。このチュートリアルでは、プロジェクトのセットアップ、完全なソースコード、検証手順、一般的な問題への対処戦略を網羅しました。

ここからは以下を検討できます：

* ボタンのクリックに応答する VBA マクロの追加。
* チェックボックスやコンボボックスなど、他の ActiveX コントロールの埋め込み。
* 動的データを使用した複数ページのフォーム自動生成。

特定のドキュメントレイアウトに合わせて、座標、サイズ、コントロールタイプを色々試してみてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、独自プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java で OLE オブジェクトと ActiveX コントロールを使用する](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Aspose.Words for Java で DocumentBuilder を使用してフォーム フィールドを作成しコンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words で Word に矩形シェイプを作成する – ステップバイステップ ガイド](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}