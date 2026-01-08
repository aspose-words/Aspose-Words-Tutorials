---
date: 2025-12-27
description: Aspose.Words for Java를 사용하여 페이지를 JPEG로 저장하고 Word 문서에서 이미지를 추출하는 방법을 배우세요.
  이미지 밝기, 해상도 설정 및 다중 페이지 TIFF 생성에 대한 팁이 포함되어 있습니다.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 페이지를 JPEG로 저장하고 문서에서 이미지 추출하는 방법
url: /ko/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 페이지를 JPEG로 저장하고 문서에서 이미지 추출하기

이 튜토리얼에서는 Word 문서에서 **save page as jpeg** 를 수행하고 Aspose.Words for Java를 사용하여 **extract images from Word** 파일을 추출하는 방법을 알아봅니다. 이미지 밝기 설정, Java에서 이미지 해상도 조정, 멀티페이지 TIFF 생성과 같은 실제 시나리오를 단계별로 살펴봅니다. 각 단계에는 바로 실행할 수 있는 코드 스니펫이 포함되어 있어 복사·붙여넣기만으로 즉시 결과를 확인할 수 있습니다.

## 빠른 답변
- **단일 페이지를 JPEG로 저장할 수 있나요?** 예 – use `ImageSaveOptions` with `setPageSet(new PageSet(pageIndex))`.
- **이미지 밝기를 어떻게 변경하나요?** `options.setImageBrightness(floatValue)` 를 호출합니다 (0‑1 범위).
- **멀티페이지 TIFF가 필요하면 어떻게 하나요?** 원하는 페이지를 포함하는 `PageSet`을 설정하고 TIFF 압축 방식을 선택합니다.
- **이미지 해상도를 어떻게 제어하나요?** `setResolution(floatDpi)` 또는 `setHorizontalResolution(floatDpi)` 를 사용합니다.
- **프로덕션에서 라이선스가 필요합니까?** 비시험용으로는 유효한 Aspose.Words 라이선스가 필요합니다.

## “save page as jpeg”란 무엇인가요?
페이지를 JPEG로 저장한다는 것은 Word 문서의 단일 페이지를 래스터 이미지 파일(JPEG)로 변환하는 것을 의미합니다. 이는 미리보기 생성, 썸네일 제작, 또는 PDF 렌더링이 실용적이지 않은 웹 페이지에 문서 페이지를 삽입할 때 유용합니다.

## Word 문서에서 이미지를 추출해야 하는 이유는?
많은 비즈니스 워크플로에서는 DOCX 파일에서 원본 그래픽(로고, 다이어그램, 사진)을 재사용, 보관 또는 분석을 위해 추출해야 합니다. Aspose.Words를 사용하면 품질 손실 없이 각 이미지를 원본 형식으로 손쉽게 추출할 수 있습니다.

## 사전 요구 사항
- Java Development Kit (JDK 8 이상)이 설치되어 있어야 합니다.
- 프로젝트에 Aspose.Words for Java 라이브러리를 추가합니다. [here](https://releases.aspose.com/words/java/)에서 다운로드하세요.
- 알려진 디렉터리에 샘플 Word 문서(예: `Rendering.docx`)를 배치합니다.

## Step 1: 임계값 제어로 TIFF 저장 (멀티페이지 TIFF 생성)
고대비 흑백 TIFF를 생성하려면 이진화 임계값을 제어할 수 있습니다. 이는 문서의 인쇄용 흑백 버전이 필요할 때 유용합니다.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Step 2: 특정 페이지를 멀티페이지 TIFF로 저장
페이지 1‑2와 같이 일부 페이지만 포함하는 TIFF가 필요하면 `PageSet`을 구성합니다. 이는 **create multipage tiff** 를 보여줍니다.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Step 3: 1 BPP 인덱스 PNG로 이미지 저장
초경량 흑백 PNG(픽셀당 1비트)가 필요할 때는 픽셀 포맷을 해당 방식으로 설정합니다. 이는 저대역폭 환경에서 간단한 그래픽을 삽입할 때 유용합니다.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Step 4: 페이지를 JPEG로 저장 및 사용자 지정 (이미지 밝기 및 해상도 설정)
여기서는 **save page as jpeg** 를 수행하면서 밝기, 대비 및 해상도를 조정합니다—썸네일이나 웹용 미리보기를 만들기에 적합합니다.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Step 5: 페이지 저장 콜백 사용 (고급 사용자 지정)
콜백을 사용하면 각 출력 파일의 이름을 동적으로 지정할 수 있어 여러 페이지를 한 번에 내보낼 때 유용합니다.

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

## 모든 시나리오에 대한 전체 소스 코드
아래는 위에서 시연한 모든 메서드를 포함하는 단일 클래스입니다. 각 테스트를 개별적으로 실행할 수 있습니다.

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

## 일반적인 문제와 해결 방법
- **“Unable to locate the document file”** – OS에 맞는 올바른 구분자(`/` 또는 `\\`)를 사용했는지 파일 경로를 확인하세요.
- **Images appear blank** – 적절한 `ImageColorMode`(예: TIFF의 경우 `GRAYSCALE`)를 설정했는지 확인하세요.
- **Out‑of‑memory errors on large documents** – `PageSet` 범위를 조정하여 페이지를 배치 처리하세요.
- **JPEG quality looks poor** – `setHorizontalResolution` 또는 `setResolution` 로 해상도를 높이세요.

## 자주 묻는 질문

**Q: Aspose.Words for Java로 저장할 때 이미지 형식을 어떻게 변경하나요?**  
A: `ImageSaveOptions`에서 원하는 형식을 설정합니다. PNG의 경우 `ImageSaveOptions`를 인스턴스화하고 필요하면 `SaveFormat.PNG`를 지정하면 됩니다.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: TIFF 이미지의 압축 설정을 사용자 지정할 수 있나요?**  
A: 예. `setTiffCompression`을 사용하여 `CCITT_3`와 같은 압축 알고리즘을 선택합니다.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: 문서의 특정 페이지를 별도의 이미지로 저장하려면 어떻게 해야 하나요?**  
A: 단일 페이지 인덱스를 사용해 `setPageSet` 메서드를 호출합니다.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: JPEG 이미지를 저장할 때 사용자 지정 설정을 적용하려면 어떻게 해야 하나요?**  
A: `ImageSaveOptions`를 통해 밝기, 대비, 해상도와 같은 속성을 조정합니다.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: 이미지 저장을 사용자 지정하기 위해 콜백을 사용하려면 어떻게 해야 하나요?**  
A: `IPageSavingCallback`을 구현하고 `setPageSavingCallback`에 할당합니다.

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

## 결론
이제 **save page as jpeg**, 이미지 추출, 이미지 밝기 제어, Java에서 이미지 해상도 설정, Aspose.Words for Java를 사용한 멀티페이지 TIFF 파일 생성 등 모든 작업을 수행할 수 있는 완전한 도구 상자를 갖추었습니다. 프로젝트 요구에 맞게 다양한 `ImageSaveOptions` 설정을 실험해 보고, 보다 광범위한 문서 조작 기능을 위해 Aspose.Words API를 탐색해 보세요.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}