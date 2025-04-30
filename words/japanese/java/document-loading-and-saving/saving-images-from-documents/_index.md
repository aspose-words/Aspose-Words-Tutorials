---
"description": "Aspose.Words for Java を使用してドキュメントから画像を保存する方法を、包括的なステップバイステップガイドで学びましょう。フォーマットや圧縮などをカスタマイズできます。"
"linktitle": "ドキュメントから画像を保存する"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントから画像を保存する"
"url": "/ja/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントから画像を保存する


## Aspose.Words for Java でドキュメントから画像を保存する方法の紹介

このチュートリアルでは、Aspose.Words for Java を使用してドキュメントから画像を保存する方法を説明します。画像保存の様々なシナリオとカスタマイズオプションについて説明します。このガイドでは、ソースコードの例とともに、ステップバイステップの手順を説明します。

## 前提条件

始める前に、Aspose.Words for Javaライブラリがプロジェクトに統合されていることを確認してください。ダウンロードはこちらから可能です。 [ここ](https://releases。aspose.com/words/java/).

## ステップ1: しきい値制御を使用して画像をTIFFとして保存する

しきい値制御を使用して画像を TIFF 形式で保存するには、次の手順に従います。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## ステップ2: 特定のページをマルチページTIFFとして保存する

特定のページを複数ページの TIFF として保存するには、次のコードを使用します。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## ステップ3: 画像を1BPPインデックスPNGとして保存する

画像を 1 BPP インデックス付き PNG として保存するには、次の手順に従います。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## ステップ4: カスタマイズしたページをJPEGとして保存する

特定のページをカスタマイズ オプション付きで JPEG として保存するには、次のコードを使用します。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## ステップ5: ページ保存コールバックの使用

コールバックを使ってページの保存をカスタマイズできます。例を以下に示します。

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

## Aspose.Words for Java でドキュメントから画像を保存するための完全なソースコード

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
	// ドキュメントの最初のページのみを変換するには、「PageSet」を「0」に設定します。
	options.setPageSet(new PageSet(0));
	// 画像の明るさとコントラストを変更します。
	// どちらも 0 ～ 1 のスケールで、デフォルトでは 0.5 になっています。
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// 水平解像度を変更します。
	// これらのプロパティのデフォルト値は 96.0 (解像度 96dpi) です。
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

## 結論

Aspose.Words for Java を使用してドキュメントから画像を保存する方法を学習しました。これらの例では、画像保存の形式、圧縮、コールバックの使用など、さまざまなカスタマイズオプションを示しています。Aspose.Words for Java の強力な機能で、さらなる可能性を探ってみましょう。

## よくある質問

### Aspose.Words for Java で保存するときに画像形式を変更するにはどうすればよいですか?

希望のフォーマットを指定することで画像フォーマットを変更できます。 `ImageSaveOptions`たとえばPNGとして保存するには、 `SaveFormat.PNG` コードに示されているように:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### TIFF 画像の圧縮設定をカスタマイズできますか?

はい、TIFF画像の圧縮設定をカスタマイズできます。例えば、圧縮方式をCCITT_3に設定するには、次のコードを使用します。

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### ドキュメントの特定のページを別の画像として保存するにはどうすればよいですか?

特定のページを画像として保存するには、 `setPageSet` 方法 `ImageSaveOptions`たとえば、最初のページだけを保存するには、 `PageSet` に `new PageSet(0)`。

```java
saveOptions.setPageSet(new PageSet(0)); // 最初のページを画像として保存する
```

### 保存時に JPEG 画像にカスタム設定を適用するにはどうすればよいですか?

JPEG画像にカスタム設定を適用するには、 `ImageSaveOptions`明るさ、コントラスト、解像度などのプロパティを調整します。例えば、明るさを0.3、コントラストを0.7に変更するには、次のコードを使用します。

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### 画像の保存をカスタマイズするためにコールバックを使用するにはどうすればよいですか?

画像保存をカスタマイズするためのコールバックを使用するには、 `PageSavでgCallback` in `ImageSaveOptions`を実装するクラスを作成します。 `IPageSavingCallback` インターフェースをオーバーライドし、 `pageSaving` 方法。

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

次に、 `IPageSavingCallback` インターフェースでファイル名と場所をカスタマイズし、 `pageSaving` 方法。

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}