---
category: general
date: 2026-10-04
description: Java を使用して Word で図形を非表示にする方法を学びましょう。このステップバイステップガイドでは、Word で図形を非表示にする方法、図形を見えなくする方法、そしてプログラムで
  Microsoft Word の図形を非表示にする方法を示します。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: ja
lastmod: 2026-10-04
og_description: JavaでWordの図形を非表示にする方法。このガイドに従って、Wordの図形を隠し、図形を見えなくし、数行のコードでMicrosoft
  Wordの図形を非表示にしましょう。
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Javaを使ってWord文書の図形を非表示にする方法 – 完全ガイド
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: JavaでWord文書の図形を非表示にする方法
url: /ja/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java で Word 文書の図形を非表示にする方法

Word ファイル内の図形を非表示にしたい場合、このガイドでは **図形を非表示にする方法** をプログラムで実装する手順を正確に示します。レポートの生成、テンプレートのクリーンアップ、コンプライアンス用の文書作成など、ファイル構造から削除せずに図形を見えなくすることができます。

以下のセクションでは、Word で図形を非表示にする方法、Word で図形を見えなくする方法、Aspose.Words for Java ライブラリを使用して Microsoft Word の図形を非表示にする方法を学びます。本チュートリアルは、基本的な Java の知識と動作する Java 開発環境があることを前提としています。

## 前提条件

開始する前に、以下を用意してください。

* Java Development Kit (JDK) 8 以上  
* 依存関係管理のための Maven または Gradle  
* Aspose.Words for Java（バージョン 23.9 以降） – Maven 座標 `com.aspose:aspose-words:23.9` を追加  
* 少なくとも 1 つの図形（画像、テキストボックス、SmartArt など）が含まれる Word 文書（`input.docx`）

## 手順 1: プロジェクトのセットアップと Aspose.Words のインポート

新しい Maven プロジェクトを作成するか、既存プロジェクトに Aspose.Words の依存関係を追加します。

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

このライブラリは、以下のクラスを提供します：`Document`、`NodeType`、`Shape`。これらを Java ソースファイルの先頭でインポートします。

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## 手順 2: Word 文書を読み込む

文書の読み込みは、すべての Word 処理ワークフローの最初のステップです。`Document` コンストラクタはファイルをメモリに読み込み、隠し図形を含むすべてのノードを保持します。

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*重要性*: ファイルを読み込むことで DOM（Document Object Model）が生成され、図形、段落、テーブルなど個々のノードをナビゲート、クエリ、変更できるようになります。

## 手順 3: 対象の図形を取得する

文書に複数の図形がある場合、インデックス、名前、その他の条件で特定の図形を検索できます。簡単なデモとして、例では文書階層内の最初の図形（テーブルやグループ内に入れ子になっている図形も含む）を取得します。

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*重要性*: `getChild` メソッドに `true` を渡す `isDeep` フラグにより、ノードツリー全体を走査し、文書本文の直接の子でない図形も取得できます。

## 手順 4: 図形を非表示にする

`Hidden` プロパティを `true` に設定すると、Microsoft Word はレイアウト描画からその図形を除外しますが、文書構造内には残ります。ファイルを Word で開いたときに図形は表示されませんが、後で処理することは可能です。

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*重要性*: 図形を非表示にすると、後から再度有効化できる（例: 条件付きコンテンツ、バージョン管理）ため、エンドユーザーに表示したくないが保持したい場合に便利です。

## 手順 5: 変更後の文書を保存する

図形の可視性を変更したら、文書をディスクに書き戻します。元のファイルを上書きするか、新しいファイルを作成できます。例では `HiddenShape.docx` に書き出します。

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

`HiddenShape.docx` を Microsoft Word で開くと、図形は見えなくなりますが、文書のレイアウトは非表示状態（余分な空白なし）を反映します。

## 完全に実行可能な例

すべての手順をまとめると、以下のような自己完結型プログラムになります。

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**期待される結果**  
プログラムを実行すると `HiddenShape.docx` が生成されます。そのファイルを Microsoft Word で開くと、元のコンテンツはそのままですが、`input.docx` に存在した図形は表示されなくなります。文書構造内には依然として図形ノードが残っており、`shape.setHidden(false)` と設定すれば後で再表示できます。

## なぜシェイプを削除せずに非表示にするのか？

* **メタデータを保持** – 図形には代替テキスト、ハイパーリンク、カスタムデータなど、後で必要になる情報が含まれていることがあります。  
* **条件付き表示** – メールマージやレポート生成シナリオで、特定の受取人にだけ図形を表示したい場合があります。  
* **バージョン管理** – 図形を非表示にしておくことで、単一のテンプレートを保ちつつ、プログラムで可視性を切り替えられます。

## 一般的なバリエーションとエッジケース

| 状況 | 推奨される調整 |
|-----------|------------------------|
| 複数の図形があり、特定のものが必要 | `doc.getChild(NodeType.SHAPE, index, true)` を適切なインデックスで使用するか、`doc.getChildNodes(NodeType.SHAPE, true)` をイテレートして `shape.getName()` または `shape.getAlternativeText()` と照合します。 |
| 図形が GroupShape 内にある | 深い検索 (`true`) はすでにグループ内部まで到達しますが、グループのメンバーだけを非表示にしたい場合は最初に `GroupShape` にキャストする必要があります。 |
| すべての図形を非表示にしたい | すべての図形ノードをループし、ループ内で `setHidden(true)` を呼び出します。 |
| 古い Word バージョンとの互換性 | `Hidden` フラグは Word 2000 以降でサポートされています。古い形式（`.doc`）でも機能しますが、レイアウトの予期しない変化がある場合は対象バージョンでテストしてください。 |

**プロのコツ**: 図形を非表示にした後、保存前にページレイアウトを再計算したい場合は `doc.updatePageLayout()` を呼び出すことができます。これは Word が開くと自動的に再フローするため通常は不要ですが、サーバー側でプレビューを生成する際には有用です。

## プログラムで結果をテストする

Word を開かずに図形が非表示かどうか確認したい場合、保存後にプロパティをクエリできます。

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## 次のステップ

Word で図形を非表示にする方法が分かったので、以下の関連トピックも検討してください。

* **カスタム条件に基づく Word の図形非表示** – `Hidden` フラグとメールマージフィールドを組み合わせて、受取人ごとに可視性を切り替えます。  
* **VBA で Word の図形を見えなくする** – デバイス上の自動化では、同じプロパティを VBA (`Shape.Visible = msoFalse`) で設定できます。  
* **大量の Word 文書で図形を非表示にする** – フォルダー内の文書をループ処理し、同じコードを各ファイルに適用します。  

これらの拡張を探求することで、Word 文書の自動化に対する制御が深まり、生成ファイルをクリーンでプロフェッショナルに保つことができます。

--- 

*このチュートリアルは Google Developer Documentation Style Guide に従い、能動態・二人称視点で記述し、検索エンジンと AI アシスタントの両方に対して完全で引用に値するソリューションを提供します。*

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを基にした、密接に関連するトピックを扱っています。各リソースには、ステップバイステップの説明と完全なコード例が含まれており、追加の API 機能を習得したり、独自プロジェクトで代替実装アプローチを探求したりするのに役立ちます。

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}