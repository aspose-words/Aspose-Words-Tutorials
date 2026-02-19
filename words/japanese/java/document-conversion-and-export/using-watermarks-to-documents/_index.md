---
date: 2026-02-19
description: Aspose.Words for Java を使用して透かし付きのドキュメントを作成し、画像透かしを追加してプロフェッショナルな文書を作る方法を学びましょう。
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用して透かし付きドキュメントを作成する
url: /ja/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して透かし付きドキュメントを作成する

このチュートリアルでは **透かし付きドキュメントを作成** する方法を Aspose.Words for Java API を使って解説します。テキストでも画像でも透かしは、ファイルを機密、ドラフト、承認済みなどとラベル付けするのに役立ち、任意の Word 文書にプログラムから適用できます。ライブラリのセットアップ、テキストと画像の透かしの追加、外観のカスタマイズ、不要になったときの削除までを順に見ていきましょう。

## クイック回答
- **透かしは何をするものですか？** 各ページにテキストまたは画像を重ねて、ステータスやブランディングを示します。  
- **Java で透かしを追加できるライブラリはどれですか？** Aspose.Words for Java が組み込みの透かし機能を提供します。  
- **画像透かしを追加できますか？** はい — `Shape` クラスと `add image watermark java` の手法を使用します。  
- **透かしは半透明にできますか？** テキスト透かしの場合は `setSemitransparent` で不透明度を制御できます。  
- **ライセンスは必要ですか？** 無料トライアルでテストは可能ですが、商用利用にはライセンスが必要です。

## 透かしとは何か、なぜ使用するのか

透かしは文書の各ページに追加される薄いオーバーレイ（テキストまたは画像）です。**機密性**、**ドラフト状態**、**ブランディング** などを示すために使用され、元のコンテンツを変更せずに情報を伝えられます。プログラムで透かしを追加すれば、大量のファイルに対して一貫した処理が可能になり、手動編集に比べて時間を大幅に節約できます。

## Aspose.Words for Java のセットアップ

透かしを追加する前に、プロジェクトでライブラリが使用できる状態にしてください。

1. Aspose.Words for Java を [こちら](https://releases.aspose.com/words/java/) からダウンロードします。  
2. ダウンロードした JAR（または Maven/Gradle の依存関係）をプロジェクトのクラスパスに追加します。  
3. Java ソースファイルで必要なクラスをインポートします:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

ライブラリの準備ができたので、実際の透かしコードに進みましょう。

## テキスト透かしの追加方法

テキスト透かしは文書を「CONFIDENTIAL」や「DRAFT」などとラベル付けするのに最適です。以下のコードスニペットは `TextWatermarkOptions` を使用して **透かし付きドキュメントを作成** するシンプルな方法を示しています。

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### テキスト透かしのカスタマイズ
- **フォントファミリーとサイズ** – `setFontFamily` と `setFontSize` を変更します。  
- **カラー** – 任意の `java.awt.Color` を使用します。  
- **レイアウト** – `HORIZONTAL`、`DIAGONAL` などを選択します。  
- **透過性** – より薄く表示するには `setSemitransparent(true)` を切り替えます。

## 画像透かしの追加方法（add image watermark java）

画像透かしはロゴやカスタムグラフィックに最適です。以下は各ページの中央に PNG を挿入する **add image watermark java** の例です。

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### 画像透かしのヒント
- **リサイズ** – ページに合わせて `setWidth` / `setHeight` を使用します。  
- **位置** – `RelativeHorizontalPosition` / `RelativeVerticalPosition` を使用して中央または任意の余白に配置できます。  
- **透過性** – 読み込む前に画像のアルファチャンネルを調整することで適用できます。

## 透かしの削除方法

文書から透かしが不要になった場合は、プログラムで削除できます。以下のコードはすべてのシェイプを走査し、名前に “Watermark” を含むものを削除します。

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## よくある落とし穴とトラブルシューティング

- **保存後に透かしが欠落する** – 透かしを設定した後に `doc.save()` を呼び出すことを確認してください。  
- **画像が表示されない** – 画像パスが正しいか、サポートされている形式（PNG、JPEG、BMP）か確認してください。  
- **透過が適用されない** – `setSemitransparent(true)` はテキスト透かしにのみ有効です。画像の場合は PNG のアルファチャンネルを編集してください。  
- **複数セクション** – ドキュメントに複数のセクションがある場合、各セクションの本文に透かしを追加するか、全体に適用される `doc.getWatermark().setText(...)` を使用してください。

## よくある質問

**Q: テキスト透かしのフォントを変更するにはどうすればよいですか？**  
A: `TextWatermarkOptions` の `setFontFamily` プロパティを変更します。例: `options.setFontFamily("Times New Roman");`。

**Q: 1 つの文書に複数の透かしを追加できますか？**  
A: はい。画像の場合は複数の `Shape` オブジェクトを作成するか、テキスト透かしの場合は `doc.getWatermark().setText(...)` を異なるオプションで呼び出します。

**Q: 透かしを回転させることは可能ですか？**  
A: 画像透かしの場合は `Shape` オブジェクトの `watermark.setRotation(angle)` で回転させます。テキスト透かしは `setLayout` プロパティ（例: `WatermarkLayout.DIAGONAL`）で実現します。

**Q: 透かしを半透明にするにはどうすればよいですか？**  
A: `TextWatermarkOptions` で `options.setSemitransparent(true)` を設定します。画像の場合は読み込む前に画像の不透明度を調整してください。

**Q: 文書の特定のセクションだけに透かしを追加できますか？**  
A: はい。`doc.getSections()` を走査し、目的のセクションだけに透かしを追加します。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**最終更新日:** 2026-02-19  
**テスト環境:** Aspose.Words for Java 24.12 (latest)  
**作者:** Aspose