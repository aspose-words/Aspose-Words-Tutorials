---
title: Aspose.Words Java を使用した HTML ドキュメントの保存オプションの強化
linktitle: HTML文書を保存する
second_title: Aspose.Words Java ドキュメント処理 API
description: このチュートリアルでは、Aspose.Words for Javaのさまざまな高度なHTMLドキュメント保存オプションについて説明しました。これらのオプションにより、高品質のHTMLを作成できます。
weight: 16
url: /ja/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java を使用した HTML ドキュメントの保存オプションの強化


このチュートリアルでは、Aspose.Words for Java が提供する高度な HTML ドキュメント保存オプションについて説明します。Aspose.Words は、Word ドキュメントを操作するための強力な Java API であり、ドキュメントの操作と変換のための幅広い機能を提供します。

## 1. はじめに
Aspose.Words for Java を使用すると、Word 文書をプログラムで操作できます。このチュートリアルでは、Word 文書を HTML に変換する方法を制御できる、高度な HTML 文書保存オプションに焦点を当てます。

## 2. 輸出ラウンドトリップ情報
の`exportRoundtripInformation`この方法を使用すると、ラウンドトリップ情報を保持しながら Word 文書を HTML にエクスポートできます。この情報は、文書固有の詳細を失うことなく HTML を Word 形式に戻す場合に役立ちます。

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. フォントをBase64としてエクスポートする
と`exportFontsAsBase64`この方法を使用すると、文書で使用されているフォントを HTML 内の Base64 エンコード データとしてエクスポートできます。これにより、HTML 表現で元の Word 文書と同じフォント スタイルが保持されます。

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. リソースのエクスポート
の`exportResources`メソッドを使用すると、CSS スタイルシートの種類を指定し、フォント リソースをエクスポートできます。また、HTML 内のリソース フォルダーとリソースのエイリアスを設定することもできます。

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

## 5. メタファイルをEMFまたはWMFに変換する
の`convertMetafilesToEmfOrWmf`この方法を使用すると、ドキュメント内のメタファイルを EMF または WMF 形式に変換して、HTML での互換性とスムーズなレンダリングを確保できます。

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAABJRU5ErkJggg==\" alt=\"赤い点\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. メタファイルをSVGに変換する
使用`convertMetafilesToSvg`メタファイルを SVG 形式に変換する方法。この形式は、HTML ドキュメントでベクター グラフィックを表示するのに最適です。

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

## 7. CSSクラス名プレフィックスを追加する
と`addCssClassNamePrefix`メソッドを使用すると、エクスポートされた HTML 内の CSS クラス名にプレフィックスを追加できます。これにより、既存のスタイルとの競合を防ぐことができます。

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. MHTMLリソースのCID URLをエクスポートする
の`exportCidUrlsForMhtmlResources`このメソッドは、ドキュメントを MHTML 形式で保存するときに使用されます。これにより、リソースの Content-ID URL をエクスポートできます。

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

## 9. フォント名を解決する
の`resolveFontNames`このメソッドは、ドキュメントを HTML 形式で保存するときにフォント名を解決するのに役立ち、異なるプラットフォーム間で一貫したレンダリングを保証します。

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

## 10. テキスト入力フォームフィールドをテキストとしてエクスポートする
の`exportTextInputFormFieldAsText`このメソッドは、フォーム フィールドを HTML 内のプレーン テキストとしてエクスポートし、簡単に読み取りおよび編集できるようにします。

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	//指定されたフォルダーは存在している必要があり、空である必要があります。
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	//フォーム フィールドを HTML 入力要素ではなくプレーン テキストとしてエクスポートするオプションを設定します。
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## 結論
このチュートリアルでは、Aspose.Words for Java が提供する高度な HTML ドキュメント保存オプションについて説明しました。これらのオプションを使用すると、変換プロセスを細かく制御できるため、元の Word ドキュメントによく似た HTML ドキュメントを作成できます。

## よくある質問
Aspose.Words for Java および HTML ドキュメント保存オプションの使用に関するよくある質問を次に示します。

### Q1: Aspose.Words for Java を使用して HTML を Word 形式に戻すにはどうすればよいですか?
 HTMLをWord形式に戻すには、Aspose.Words APIの`load`HTML ドキュメントを読み込み、Word 形式で保存する方法。

### Q2: HTML にエクスポートするときに CSS スタイルをカスタマイズできますか?
はい、HTMLで使用されているスタイルシートを変更するか、`addCssClassNamePrefix` CSS クラス名にプレフィックスを追加するメソッド。

### Q3: HTML 出力を Web 表示用に最適化する方法はありますか?
はい、フォントを Base64 としてエクスポートしたり、メタファイルを SVG に変換したりするなどのオプションを構成することで、HTML 出力を Web 表示用に最適化できます。

### Q4: 複雑な Word 文書を HTML に変換する場合、何か制限はありますか?
Aspose.Words for Java は強力な変換機能を提供しますが、複雑なレイアウトを持つ複雑な Word 文書では、目的の HTML 出力を実現するために追加の後処理が必要になる場合があります。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
