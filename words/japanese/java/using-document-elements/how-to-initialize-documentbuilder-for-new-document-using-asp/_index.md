---
category: general
date: 2026-10-04
description: Aspose.Words for Java を使用して、新しいドキュメントの DocumentBuilder を初期化し、ActiveX
  ボタンを追加する方法を学びます。ステップバイステップのガイドと完全なコード付き。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: ja
lastmod: 2026-10-04
og_description: Aspose.Words Java API を使用して新しいドキュメントの DocumentBuilder を初期化し、ActiveX
  コマンドボタンを埋め込みます。この簡潔なチュートリアルをご覧ください。
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: 新しいドキュメント用 DocumentBuilder の初期化 – 完全な Aspose.Words ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Aspose.Words を使用して新しいドキュメントの DocumentBuilder を初期化する方法
url: /ja/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words を使用して新しいドキュメント用 DocumentBuilder を初期化する方法

Java プロジェクトで **新しいドキュメント用 DocumentBuilder を初期化** する必要がある場合、このチュートリアルで正確な手順を示します。空白の Word ファイルを作成し、ActiveX コマンドボタンを添付し、結果を保存するまでを、単一の自己完結型コードサンプルで確認できます。

プログラムから Word ドキュメントを操作することは、フォームコントロールなどの低レベルな詳細を扱うことを意味します。本ガイドの最後までに、IDE を離れることなく ActiveX ボタンを埋め込めるようになり、テンプレート生成や自動レポート、インタラクティブフォームの作成に役立ちます。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17 以降がインストール済み  
* Maven 3.8+（または好みで Gradle）  
* Aspose.Words for Java のライセンス（無料トライアルでもテスト可）  
* Java 文法の基本的な知識  

Aspose.Words は、Word ドキュメントの作成・編集・保存のための高レベル API を提供します。`DocumentBuilder` クラスがドキュメントコンテンツ構築の主要エントリーポイントです。

## 手順 1: Maven プロジェクトの設定

新規 Maven プロジェクトを作成するか、既存プロジェクトに追加し、Aspose.Words の依存関係を記述します。

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **プロのコツ:** ライブラリのバージョンは常に最新に保ちましょう。新しいリリースでは追加のフォームコントロールがサポートされ、パフォーマンスも向上します。

## 手順 2: 新しいドキュメント用 `DocumentBuilder` を初期化

チュートリアルの核心は **新しいドキュメント用 DocumentBuilder を初期化** する操作です。まず空の `Document` インスタンスを作成し、これを `DocumentBuilder` コンストラクタに渡します。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*重要性のポイント:* `DocumentBuilder` を初期化すると、ビルダーが特定の `Document` オブジェクトに結び付けられ、段落・テーブル・フォームコントロールを直接そのドキュメントに追加できるようになります。この手順がないと、ビルダーは対象がなく操作できません。

## 手順 3: ActiveX コマンドボタンコントロールを挿入

Aspose.Words はレガシーな ActiveX コントロールを埋め込むために `Forms2OleControl` クラスを提供します。以下のコードは、現在のカーソル位置に **Forms2OleControl コマンドボタン** を追加します。

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### ActiveX コマンドボタンとは？

ActiveX コマンドボタンは、Word 文書内でユーザーがクリックしたときにマクロを実行したりイベントをトリガーしたりできるレガシー UI 要素です。最新の Office バージョンではコンテンツコントロールが推奨されていますが、互換性のために多くのエンタープライズテンプレートが依然として ActiveX を使用しています。

## 手順 4: ドキュメントを保存

コントロールを挿入したら、単に `save` を呼び出すだけです。ファイルには ActiveX ボタンが含まれ、Microsoft Word で開くことができます。

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`ActiveXButton.docx` を Word で開くと、**Click Me** とラベル付けされたボタンが表示されます。マクロを添付しない限りクリックしても何も起こりませんが、コントロール自体は完全に機能します。

## 完全な実行可能サンプル

以下は `src/main/java/com/example/ActiveXButtonDemo.java` にコピペできる完全プログラムです。インポート文とエラーハンドリングをすべて含んでいるので、すぐにテストできます。

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**期待される出力**

```
Document saved to output/ActiveXButton.docx
```

Microsoft Word 2016 以降で生成されたファイルを開くと、1 ページ目の上部に *Click Me* と表示されたボタンが見えるはずです。

## 一般的なバリエーションとエッジケース

| シナリオ | 調整方法 |
|----------|------------|
| **特定の段落にボタンを追加** | `builder.moveToParagraph(index, NodeType.PARAGRAPH);` でビルダーのカーソルを移動してから `insertForms2OleControl` を呼び出す。 |
| **ボタンサイズを設定** | `commandButton.setWidth(100);` と `commandButton.setHeight(30);` でポイント単位のサイズを指定。 |
| **ボタンにマクロを追加** | ドキュメント保存後、Word で開き、開発タブを有効にして手動で VBA マクロをボタンに割り当てる（ActiveX コントロールは Aspose.Words から直接スクリプト化できません）。 |
| **.doc（バイナリ）形式を対象** | `doc.save(outputPath, SaveFormat.DOC);` に変更して Word 97‑2003 形式のレガシーファイルを生成。 |
| **Android で実行** | Android 用 Aspose.Words の Java API を使用すれば、同じコードが APK にライブラリを含めるだけで動作します。 |

## トラブルシューティングのヒント

* **`java.lang.NoClassDefFoundError`** – Aspose.Words の JAR がクラスパスに含まれているか確認してください。Maven なら自動で追加されます。手動ビルドの場合は JAR を `libs/` に置き、IDE のライブラリに追加します。  
* **Word にボタンが表示されない** – Word の「信頼センター」設定で *レガシーフォームの表示* が有効になっているか確認します（`ファイル → オプション → 信頼センター → 信頼センターの設定 → マクロの設定`）。  
* **ライセンス例外** – 有効なライセンスなしで実行すると、Aspose.Words は透かしを挿入します。無料トライアルを登録するか、ライセンスを購入して透かしを除去してください。

## 結論

これで **新しいドキュメント用 DocumentBuilder を初期化** し、ActiveX コマンドボタンを挿入し、Aspose.Words for Java で結果を保存する方法が分かりました。このパターンを使えば、プログラムからインタラクティブな Word テンプレートを生成でき、レポート自動化やフォーム駆動ワークフローに非常に便利です。

ここからは、さらに `Forms2OleControlType.CHECKBOX`、`COMBOBOX` などの追加フォームコントロールを試したり、ボタンにカスタム VBA マクロを組み合わせたり、テーブル・画像・スタイリングを含むフル機能ドキュメントを同じ `DocumentBuilder` ワークフローで生成したりできます。

---

*もっと高度な Word 自動化に挑戦したいですか？ **DocumentBuilder でテーブルを挿入**、**プログラムでスタイルを適用**、**Aspose.Words で PDF にエクスポート** に関するガイドもぜひご覧ください。*


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作サンプルコードが含まれているので、API の追加機能を習得したり、プロジェクトで代替実装アプローチを検討したりする際に役立ちます。

- [Aspose.Words for Java で DocumentBuilder を使用してフォームフィールドを作成し、コンテンツを追加する方法](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java でドキュメントを PDF として保存する方法](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java を使用してドキュメントに透かしを追加する方法](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}