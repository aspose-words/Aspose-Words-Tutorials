---
date: 2025-12-19
description: Aspose.Words Java を使用して HTML にエクスポートする方法を学び、Word を HTML として保存する高度なオプションや、Word
  を効率的に HTML に変換する方法を網羅しています。
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Aspose.Words JavaでHTMLをエクスポートする方法: 高度なオプション'
url: /ja/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words JavaでHTMLをエクスポートする方法: 高度なオプション

このチュートリアルでは、Aspose.Words for Java を使用して Word 文書から **HTML をエクスポートする方法** を学びます。Web 公開のために **Word を HTML として保存** したり、下流処理のために **Word を HTML に変換** したりする必要がある場合、詳細な保存オプションを使うことで出力を細かく制御できます。各オプションをステップバイステップで解説し、使用シーンと実際の効果を示します。

## Quick Answers
- **HTMLエクスポートの主要クラスは何ですか？** `HtmlSaveOptions`  
- **フォントをHTMLに直接埋め込むことはできますか？** はい、`exportFontsAsBase64` を `true` に設定します。  
- **Word固有のラウンドトリップデータを保持するには？** `exportRoundtripInformation` を有効にします。  
- **ベクターグラフィックに最適な形式はどれですか？** SVG 出力には `convertMetafilesToSvg` を使用します。  
- **CSSクラス名の衝突を回避できますか？** はい、`addCssClassNamePrefix` を使用します。

## 1. Introduction
Aspose.Words for Java は、開発者がプログラムから Word 文書を操作できる強力な API です。本ガイドでは、特定の Web 要件や統合シナリオに合わせて変換プロセスをカスタマイズできる高度な HTML 保存オプションに焦点を当てます。

## 2. Export Roundtrip Information
ラウンドトリップ情報を保持すると、HTML を Word 文書に戻す際にレイアウトや書式設定の詳細が失われません。

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### When to use
- HTML → Word → HTML のように、変換を往復させる必要がある場合。  
- 元の Word 構造を保持したまま共同編集を行うシナリオに最適です。

## 3. Export Fonts as Base64
フォントを HTML に直接埋め込むことで、外部フォントへの依存を排除し、ブラウザ間での視覚的一貫性を確保できます。

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Pro tip
ターゲット環境が外部リソースへのアクセスが制限されている場合（例: メールニュースレター）にこのオプションを使用してください。

## 4. Export Resources
CSS やフォントリソースの出力方法を制御し、これらのアセット用にカスタムフォルダーまたは URL エイリアスを指定できます。

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Why it matters
CSS を外部ファイルに分離すると HTML のサイズが削減され、キャッシュが有効になるためページ読み込みが高速化します。

## 5. Convert Metafiles to EMF or WMF
メタファイル（例: EMF/WMF）を、ブラウザが確実に描画できる形式に変換します。

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Use case
対象ブラウザがこれらのベクターフォーマットをサポートし、かつロスレスなスケーリングが必要な場合に EMF/WMF を選択してください。

## 6. Convert Metafiles to SVG
SVG は最高のスケーラビリティを提供し、モダンブラウザで広くサポートされています。

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### Benefit
SVG ファイルは軽量で解像度に依存せず、レスポンシブ Web デザインに最適です。

## 7. Add CSS Class Name Prefix
生成されるすべての CSS クラス名にプレフィックスを付けることで、スタイルの衝突を防止します。

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Practical tip
HTML を既存ページに埋め込む際は、プロジェクト名などのユニークなプレフィックスを使用して CSS の競合を回避してください。

## 8. Export CID URLs for MHTML Resources
MHTML 形式で保存する場合、リソースを Content‑ID URL でエクスポートでき、メールでの互換性が向上します。

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### When to use
メールに添付できる単一の自己完結型 HTML ファイルを生成したい場合に最適です。

## 9. Resolve Font Names
HTML が正しいフォントファミリーを参照するようにし、クロスプラットフォームでの一貫性を向上させます。

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### Why it helps
元の文書で使用されているフォントがクライアントマシンにインストールされていない場合、Web セーフな代替フォントに置き換えることができます。

## 10. Export Text Input Form Field as Text
フォームフィールドをインタラクティブな HTML 入力要素ではなく、プレーンテキストとしてレンダリングします。

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Use case
アーカイブや印刷目的で、フォームの読み取り専用表現が必要な場合に使用します。

## Common Pitfalls & Troubleshooting
| 問題 | 典型的な原因 | 対策 |
|------|--------------|------|
| 出力にフォントが欠如している | `exportFontsAsBase64` が有効になっていない | `setExportFontsAsBase64(true)` を設定する |
| 埋め込み後にCSSが壊れる | CSSファイルを提供せずに `EXTERNAL` を使用 | 指定された `resourceFolderAlias` にCSSファイルが配置されていることを確認する |
| HTMLサイズが大きくなる | 多数の画像をBase64で埋め込んでいる | `setExportFontResources(true)` を使用して外部画像リソースに切り替え、`resourceFolder` を設定する |
| 古いブラウザでSVGが表示されない | ブラウザがSVGをサポートしていない | EMF/WMFとしてもエクスポートし、代替PNGを提供する |

## Frequently Asked Questions

**Q: フォントをBase64で埋め込みつつ、外部CSSも保持できますか？**  
A: はい。`exportFontsAsBase64(true)` を設定し、`CssStyleSheetType.EXTERNAL` を保持することで、フォントデータとスタイルルールを分離できます。

**Q: 既存の HTML を Word 文書に変換するにはどうすればよいですか？**  
A: `Document doc = new Document("input.html");` で HTML を読み込み、`doc.save("output.docx");` と保存します。初回エクスポート時に `exportRoundtripInformation` を使用してラウンドトリップデータを保持してください。

**Q: SVG 変換を使用するとパフォーマンスに影響がありますか？**  
A: 大きなメタファイルを SVG に変換すると処理時間が増加する可能性がありますが、生成される HTML は通常は小さくなり、ブラウザでの描画が速くなります。

**Q: これらのオプションは Aspose.Words for .NET でも使用できますか？**  
A: 同様の概念は .NET API にも存在しますが、メソッド名が若干異なる場合があります（例: `HtmlSaveOptions` はプラットフォーム間で共有されています）。

**Q: メールフレンドリーな HTML にはどのオプションを選べばよいですか？**  
A: `SaveFormat.MHTML` と `exportCidUrlsForMhtmlResources` を使用して、すべてのリソースをメール本文に直接埋め込みます。

**最終更新日:** 2025-12-19  
**テスト環境:** Aspose.Words for Java 24.12  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}