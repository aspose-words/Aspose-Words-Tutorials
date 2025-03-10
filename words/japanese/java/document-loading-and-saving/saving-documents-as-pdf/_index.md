---
title: Aspose.Words for Java でドキュメントを PDF として保存する
linktitle: ドキュメントをPDFとして保存する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して Word 文書を PDF として保存する方法を学びます。フォント、プロパティ、画像の品質をカスタマイズします。PDF 変換の包括的なガイド。
weight: 22
url: /ja/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントを PDF として保存する


## Aspose.Words for Java でドキュメントを PDF として保存する方法の紹介

このステップバイステップ ガイドでは、Aspose.Words for Java を使用してドキュメントを PDF として保存する方法について説明します。PDF 変換のさまざまな側面を取り上げ、プロセスを簡単にするためのコード例を示します。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

- システムに Java 開発キット (JDK) がインストールされています。
-  Aspose.Words for Javaライブラリ。ここからダウンロードできます。[ここ](https://releases.aspose.com/words/java/).

## 文書をPDFに変換する

Word 文書を PDF に変換するには、次のコード スニペットを使用できます。

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

交換する`"input.docx"` Word文書へのパスと`"output.pdf"`希望する出力 PDF ファイル パスを指定します。

## PDF保存オプションの制御

さまざまなPDF保存オプションをコントロールするには、`PdfSaveOptions`クラス。たとえば、PDF ドキュメントの表示タイトルを次のように設定できます。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## PDF にフォントを埋め込む

生成された PDF にフォントを埋め込むには、次のコードを使用します。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## ドキュメントプロパティのカスタマイズ

生成された PDF のドキュメント プロパティをカスタマイズできます。例:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## ドキュメント構造のエクスポート

ドキュメント構造をエクスポートするには、`exportDocumentStructure`オプション`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## 画像圧縮

次のコードを使用して画像の圧縮を制御できます。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## 最後に印刷したプロパティの更新

PDF の「最終印刷」プロパティを更新するには、次を使用します。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## DML 3D 効果のレンダリング

DML 3D 効果の高度なレンダリングを行うには、レンダリング モードを設定します。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## 画像の補間

画像補間を有効にすると、画像の品質が向上します。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## 結論

Aspose.Words for Java は、柔軟性とカスタマイズ オプションを備えた Word 文書を PDF 形式に変換するための包括的な機能を提供します。フォント、文書のプロパティ、画像圧縮など、PDF 出力のさまざまな側面を制御できます。

## よくある質問

### Aspose.Words for Java を使用して Word 文書を PDF に変換するにはどうすればよいですか?

Word 文書を PDF に変換するには、次のコードを使用します。

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

交換する`"input.docx"` Word文書へのパスと`"output.pdf"`希望する出力 PDF ファイル パスを指定します。

### Aspose.Words for Java で生成された PDF にフォントを埋め込むことはできますか?

はい、PDFにフォントを埋め込むには、`setEmbedFullFonts`オプション`true`で`PdfSaveOptions`次に例を示します。

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### 生成された PDF 内のドキュメント プロパティをカスタマイズするにはどうすればよいですか?

 PDFのドキュメントプロパティをカスタマイズするには、`setCustomPropertiesExport`オプション`PdfSaveOptions`。 例えば：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Aspose.Words for Java での画像圧縮の目的は何ですか?

画像圧縮を使用すると、生成されたPDF内の画像の品質とサイズを制御できます。画像圧縮モードは、以下を使用して設定できます。`setImageCompression`で`PdfSaveOptions`.

### PDF の「最終印刷」プロパティを更新するにはどうすればよいですか?

 PDFの「最終印刷」プロパティを更新するには、次のように設定します。`setUpdateLastPrintedProperty`に`true`で`PdfSaveOptions`これにより、PDF メタデータに最終印刷日が反映されます。

### PDF に変換するときに画像の品質を向上させるにはどうすればよいですか?

画質を向上させるには、設定で画像補間を有効にします。`setInterpolateImages`に`true`で`PdfSaveOptions`これにより、PDF 内の画像がより滑らかで高品質になります。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
