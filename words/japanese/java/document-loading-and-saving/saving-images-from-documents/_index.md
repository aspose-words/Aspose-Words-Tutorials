---
date: 2025-12-27
description: Aspose.Words for Java を使用して、ページを JPEG として保存し、Word 文書から画像を抽出する方法を学びます。画像の明るさや解像度の設定、マルチページ
  TIFF の作成に関するヒントも含まれています。
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用してページを JPEG として保存し、ドキュメントから画像を抽出する方法
url: /ja/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# WordでページをJPEGとして保存し、ドキュメントから画像を抽出する（Aspose.Words for Java）

このチュートリアルでは、Word ドキュメントから **ページを JPEG として保存** する方法と、**Word ファイルから画像を抽出** する方法を紹介します。画像の明るさ調整や Java での解像度設定、マルチページ TIFF の作成といった実践的シナリオを順に解説します。各手順にはすぐに実行できるコードスニペットが含まれているので、コピーして貼り付けるだけで結果を確認できます。

## Quick Answers
- **単一ページを JPEG として保存できますか？** はい – `ImageSaveOptions` に `setPageSet(new PageSet(pageIndex))` を指定します。  
- **画像の明るさはどう変更しますか？** `options.setImageBrightness(floatValue)`（範囲 0‑1）を呼び出します。  
- **マルチページ TIFF が必要な場合は？** 対象ページを含む `PageSet` を設定し、TIFF 圧縮方式を選択します。  
- **画像解像度はどう制御しますか？** `setResolution(floatDpi)` または `setHorizontalResolution(floatDpi)` を使用します。  
- **本番環境でライセンスは必要ですか？** トライアル以外で使用する場合は有効な Aspose.Words ライセンスが必須です。

## “save page as jpeg” とは？
ページを JPEG として保存するとは、Word 文書の 1 ページをラスタ画像（JPEG ファイル）に変換することです。プレビュー生成やサムネイル作成、PDF のレンダリングが難しい Web ページへの埋め込みなどに便利です。

## Word 文書から画像を抽出する理由
多くの業務フローでは、DOCX ファイルから元のグラフィック（ロゴ、図、写真）を取り出して再利用、アーカイブ、解析に利用します。Aspose.Words を使えば、品質を損なうことなく各画像を元の形式で簡単に抽出できます。

## 前提条件
- Java Development Kit（JDK 8 以上）がインストールされていること。  
- Aspose.Words for Java ライブラリがプロジェクトに追加されていること。ダウンロードは[こちら](https://releases.aspose.com/words/java/)。  
- サンプル Word 文書（例: `Rendering.docx`）が既知のディレクトリに配置されていること。

## Step 1: Save Images as TIFF with Threshold Control (Create Multipage TIFF)
高コントラストのグレースケール TIFF を生成する際に、二値化しきい値を制御できます。印刷用の白黒版が必要なときに便利です。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Step 2: Save a Specific Page as Multipage TIFF
特定のページ（例: 1‑2 ページ）だけを含む TIFF を作成したい場合は、`PageSet` を設定します。これにより **create multipage tiff** が実現できます。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Step 3: Save Images as 1 BPP Indexed PNG
超軽量な白黒 PNG（1 ビット/ピクセル）が必要な場合は、ピクセル形式を設定します。低帯域幅環境でシンプルなグラフィックを埋め込む際に有用です。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Step 4: Save a Page as JPEG with Customization (Set Image Brightness & Resolution)
ここでは **save page as jpeg** を行いながら、明るさ、コントラスト、解像度を調整します。サムネイルや Web 用プレビュー作成に最適です。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Step 5: Using a Page‑Saving Callback (Advanced Customization)
コールバックを使用すると、出力ファイル名を動的に変更できます。多数のページを一括エクスポートする際に便利です。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Complete Source Code for All Scenarios
以下は、上記すべてのシナリオを含む単一クラスです。各テストは個別に実行できます。

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## Common Issues and Solutions
- **「ドキュメントファイルが見つかりません」** – ファイルパスの区切り文字（`/` または `\\`）が OS に合っているか確認してください。  
- **画像が空白になる** – `ImageColorMode`（例: TIFF の場合は `GRAYSCALE`）を適切に設定してください。  
- **大容量ドキュメントでメモリ不足** – `PageSet` の範囲を分割してページごとに処理してください。  
- **JPEG の画質が低い** – `setHorizontalResolution` または `setResolution` で解像度を上げてください。

## Frequently Asked Questions

**Q: Aspose.Words for Java で保存時に画像形式を変更するには？**  
A: `ImageSaveOptions` で目的の形式を指定します。PNG にしたい場合は `ImageSaveOptions` を生成し、必要に応じて `SaveFormat.PNG` を設定してください。

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: TIFF 画像の圧縮設定をカスタマイズできますか？**  
A: はい。`setTiffCompression` を使用して `CCITT_3` などの圧縮アルゴリズムを選択できます。

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: ドキュメントの特定ページだけを別画像として保存するには？**  
A: `setPageSet` メソッドに単一ページインデックスを渡します。

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: JPEG 画像保存時にカスタム設定を適用するには？**  
A: 明るさ、コントラスト、解像度などのプロパティを `ImageSaveOptions` で調整します。

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: 画像保存をカスタマイズするコールバックはどう実装しますか？**  
A: `IPageSavingCallback` を実装し、`setPageSavingCallback` で登録します。

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Conclusion
これで **save page as jpeg**、画像抽出、明るさ調整、解像度設定、マルチページ TIFF 作成といった機能がすべて揃いました。プロジェクトの要件に合わせて `ImageSaveOptions` の各種設定を試し、Aspose.Words API の他のドキュメント操作機能もぜひ活用してください。

---

**最終更新日:** 2025-12-27  
**テスト環境:** Aspose.Words for Java 24.12（執筆時点の最新）  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}