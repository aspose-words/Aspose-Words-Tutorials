---
"description": "Aspose.Words for Java를 사용하여 문서에서 이미지를 저장하는 방법을 단계별 가이드를 통해 자세히 알아보세요. 형식, 압축 등을 사용자 지정할 수 있습니다."
"linktitle": "문서에서 이미지 저장"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Aspose.Words for Java에서 문서의 이미지 저장하기"
"url": "/ko/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 문서의 이미지 저장하기


## Aspose.Words for Java에서 문서의 이미지 저장 소개

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 문서에서 이미지를 저장하는 방법을 살펴보겠습니다. 이미지 저장을 위한 다양한 시나리오와 사용자 정의 옵션을 다룹니다. 이 가이드는 소스 코드 예제와 함께 단계별 지침을 제공합니다.

## 필수 조건

시작하기 전에 Aspose.Words for Java 라이브러리가 프로젝트에 통합되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/).

## 1단계: 임계값 제어를 사용하여 TIFF로 이미지 저장

임계값 제어를 사용하여 이미지를 TIFF 형식으로 저장하려면 다음 단계를 따르세요.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 2단계: 특정 페이지를 다중 페이지 TIFF로 저장

특정 페이지를 다중 페이지 TIFF로 저장하려면 다음 코드를 사용하세요.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 3단계: 이미지를 1 BPP 인덱스 PNG로 저장

이미지를 1 BPP 인덱스 PNG로 저장하려면 다음 단계를 따르세요.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 4단계: 사용자 정의를 사용하여 페이지를 JPEG로 저장

사용자 정의 옵션을 사용하여 특정 페이지를 JPEG로 저장하려면 다음 코드를 사용하세요.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 5단계: 페이지 저장 콜백 사용

콜백을 사용하여 페이지 저장을 사용자 지정할 수 있습니다. 예를 들어 다음과 같습니다.

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

## Aspose.Words for Java에서 문서의 이미지를 저장하기 위한 완전한 소스 코드

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
	// 문서의 첫 페이지만 변환하려면 "PageSet"을 "0"으로 설정합니다.
	options.setPageSet(new PageSet(0));
	// 이미지의 밝기와 대비를 변경합니다.
	// 둘 다 0~1점 척도이며 기본값은 0.5입니다.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// 수평 해상도를 변경합니다.
	// 이러한 속성의 기본값은 96dpi의 해상도를 나타내는 96.0입니다.
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

## 결론

Aspose.Words for Java를 사용하여 문서에서 이미지를 저장하는 방법을 알아보았습니다. 이 예제에서는 형식, 압축, 콜백 사용 등 이미지 저장을 위한 다양한 사용자 지정 옵션을 보여줍니다. Aspose.Words for Java의 강력한 기능으로 더 많은 가능성을 탐색해 보세요.

## 자주 묻는 질문

### Aspose.Words for Java로 저장할 때 이미지 형식을 어떻게 변경합니까?

원하는 형식을 지정하여 이미지 형식을 변경할 수 있습니다. `ImageSaveOptions`예를 들어 PNG로 저장하려면 다음을 사용합니다. `SaveFormat.PNG` 코드에 표시된 대로:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### TIFF 이미지의 압축 설정을 사용자 정의할 수 있나요?

네, TIFF 이미지 압축 설정을 사용자 지정할 수 있습니다. 예를 들어, 압축 방식을 CCITT_3으로 설정하려면 다음 코드를 사용하세요.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### 문서의 특정 페이지를 별도 이미지로 저장하려면 어떻게 해야 하나요?

특정 페이지를 이미지로 저장하려면 다음을 사용하세요. `setPageSet` 방법 `ImageSaveOptions`예를 들어, 첫 번째 페이지만 저장하려면 다음을 설정합니다. `PageSet` 에게 `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // 첫 번째 페이지를 이미지로 저장
```

### JPEG 이미지를 저장할 때 사용자 지정 설정을 적용하려면 어떻게 해야 하나요?

JPEG 이미지에 사용자 정의 설정을 적용할 수 있습니다. `ImageSaveOptions`밝기, 대비, 해상도 등의 속성을 조정합니다. 예를 들어 밝기를 0.3으로, 대비를 0.7로 변경하려면 다음 코드를 사용하세요.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### 콜백을 사용하여 이미지 저장을 사용자 정의하려면 어떻게 해야 하나요?

이미지 저장을 사용자 정의하기 위해 콜백을 사용하려면 다음을 설정하세요. `PageSav~에gCallback` in `ImageSaveOptions`. 구현하는 클래스를 만듭니다. `IPageSavingCallback` 인터페이스 및 재정의 `pageSaving` 방법.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

그런 다음, 다음을 구현하는 클래스를 만듭니다. `IPageSavingCallback` 인터페이스 및 파일 이름과 위치를 사용자 정의합니다. `pageSaving` 방법.

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