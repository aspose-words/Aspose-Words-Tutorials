---
category: general
date: 2026-08-07
description: Aspose.Words を使用して Java でグループ化された図形を含む空白の Word 文書を作成します。図形のグループ化方法、図形サイズの設定方法、Word
  への図形の追加方法を学びます。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: ja
lastmod: 2026-08-07
og_description: Javaでグループ化された図形を含む空白のWord文書を作成します。このガイドに従って図形のサイズを設定し、Wordに図形を追加し、図形のグループ化方法をマスターしてください。
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: グループ化された図形で空白のWord文書を作成 – Javaチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Javaでグループ化された図形を含む空白のWord文書を作成する
url: /ja/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Javaでグループ化されたシェイプを含む空のWord文書を作成する

空の **Word 文書** に複数のシェイプを 1 つのユニットとして配置したい場合、このチュートリアルで手順をすべて解説します。シェイプ オブジェクトの **グループ化** 方法、サイズの調整、そして Aspose.Words for Java を使用した **Word へのシェイプ追加** を実演する、完全に実行可能なサンプルが掲載されています。

プロジェクトのセットアップから最終的な .docx ファイルの保存まで、すべての手順を順に説明しますので、コードをそのまま自分のアプリケーションにコピーして使用できます。外部参照は不要で、Aspose.Words 23.9 以降で動作します。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17（またはサポート対象の JDK）
* Maven または Gradle（依存関係管理用）
* Aspose.Words for Java のライセンス（または一時評価キー）
* 既知のディレクトリに配置したサンプル画像ファイル（例：`sample.jpg`）

これらのいずれかが不足している場合は先にインストールしてください。以降のチュートリアルは環境が整っていることを前提に進めます。

## 手順 1: Aspose.Words をプロジェクトに追加する

`pom.xml`（Maven）または `build.gradle`（Gradle）に Aspose.Words の依存関係を追加します。このライブラリが `Document`、`DocumentBuilder`、`GroupShape`、`Shape` クラスを提供し、後述のコードで使用します。

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**重要ポイント:** ライブラリが無いと Word 処理 API が利用できず、プログラムで **空の Word 文書** を **作成** できません。

## 手順 2: 空の Word 文書を作成する

最初の具体的な操作は、メモリ上の **空の Word 文書** を表す `Document` オブジェクトをインスタンス化することです。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* はデフォルト設定（A4 用紙、標準余白）で **空の Word 文書** を生成します。併せて使用する `DocumentBuilder` により、現在のカーソル位置にコンテンツを挿入できます。

## 手順 3: グループ シェイプを挿入する（シェイプのグループ化方法）

*グループ シェイプ* は他のシェイプを格納するコンテナとして機能します。このステップでは **シェイプのグループ化** 方法を学び、複数の描画をまとめて移動できるようにします。

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

`insertGroupShape` メソッドはビルダーのカーソル位置にコンテナを配置します。複数の描画を 1 つのエンティティとして扱いたい場合にグループ化は必須で、これが **group shapes word** 機能の核心です。

## 手順 4: 四角形を作成しサイズを設定する

次に、グループ内に四角形を追加します。ここでは **シェイプのサイズ設定** を実演し、正確なレイアウトを実現します。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*サイズを設定する理由*：`setWidth` と `setHeight` を明示的に呼び出すことで、ドキュメントの既定シェイプスタイルに左右されず、四角形が意図した通りの大きさで表示されます。

## 手順 5: 画像を挿入しグループに追加する

画像の追加は **add shapes to word** の典型的なユースケースです。画像も同じグループの一部となり、四角形と一緒に移動します。

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

画像ファイルが見つからないと Aspose.Words は例外をスローします。実務的なヒントとして、事前にパスを確認しておくと安全です。

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## 手順 6: グループ化されたシェイプを含む文書を保存する

最後に、**空の Word 文書**（現在はグループ シェイプで構成）をディスクに永続化します。

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

`GroupShapeDemo.docx` を Microsoft Word で開くと、四角形と画像を含む単一のグループ オブジェクトが表示されます。グループの任意の部分を選択すると、全体が一緒に移動し、シェイプが正しく **グループ化** されていることが確認できます。

### 期待される出力

* 指定ディレクトリに `GroupShapeDemo.docx` という名前のファイルが作成されます。
* ファイルを開くと、300 × 200 ポイントのコンテナ内に以下が配置されます：
  * (20, 20) に位置する 100 × 50 ポイントの四角形
  * 同コンテナ内の (150, 30) に位置する画像

## エッジケースとバリエーション

| 状況 | 対処方法 |
|-----------|-----------------|
| **ページサイズが異なる** | グループ挿入前に `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` を呼び出す |
| **複数のグループ** | 新しい `GroupShape` インスタンスで手順 3‑5 を繰り返す。各グループは独立して配置可能 |
| **シェイプの回転** | `shape.setRotationAngle(45.0);` で四角形や画像を回転させ、グループに追加する |
| **画像以外のシェイプ** | `ShapeType.ELLIPSE`、`ShapeType.LINE` などの `Shape` オブジェクトを作成し、四角形と同様に追加 |
| **大きな画像** | `picture.setWidth(80.0); picture.setHeight(60.0);` でスケールダウンし、元のグループ境界内に収める |

これらのバリエーションにより、コアパターンをさまざまな文書生成シナリオに適用できます。

## 実務的なヒント

* **プロのコツ:** グループの `RelativeHorizontalPosition` と `RelativeVerticalPosition` をそれぞれ `RelativeHorizontalPosition.PAGE`、`RelativeVerticalPosition.PAGE` に設定すると、カーソルではなくページに固定されます。
* **注意点:** グループのサイズを超えるシェイプを追加すると、Word で切り取られて表示されます。`group.setWidth()` と `group.setHeight()` で適切にサイズ調整してください。
* **パフォーマンス:** ループで多数の文書を生成する場合、`DocumentBuilder` インスタンスを再利用し、`doc.clone()` を呼び出すことでオブジェクト生成コストを削減できます。

## 結論

これで、Aspose.Words for Java を使用して **空の Word 文書** にシェイプのグループ コレクションを作成する方法が習得できました。チュートリアルでは、ライブラリの設定、文書作成、グループ挿入、**シェイプのサイズ設定**、**Word へのシェイプ追加**、そして保存までの全工程を網羅しました。

ここからは、チャートのグループ化や個別シェイプへのスタイル適用、PDF へのエクスポートなど、より高度な機能に挑戦してみてください。これらすべては本ガイドで示した原則に基づいています。

---


## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示したテクニックを応用した関連トピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、API の追加機能習得や代替実装アプローチの検討に役立ちます。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}