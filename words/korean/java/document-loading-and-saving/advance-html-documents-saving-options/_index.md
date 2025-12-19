---
date: 2025-12-19
description: Aspose.Words Java를 사용하여 HTML을 내보내는 방법을 배우고, Word를 HTML로 저장하고 효율적으로 변환하는
  고급 옵션을 다룹니다.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Aspose.Words Java를 사용한 HTML 내보내기 방법: 고급 옵션'
url: /ko/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java를 사용하여 HTML 내보내기: 고급 옵션

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 Word 문서에서 **HTML을 내보내는 방법**을 알아봅니다. 웹 게시를 위해 **Word를 HTML로 저장**하거나 하위 처리용 **Word를 HTML로 변환**해야 할 경우, 고급 저장 옵션을 통해 출력에 대한 세밀한 제어가 가능합니다. 각 옵션을 단계별로 살펴보고, 사용 시점을 설명하며, 이러한 설정이 차이를 만드는 실제 시나리오를 보여드립니다.

## 빠른 답변
- **HTML 내보내기의 주요 클래스는 무엇인가요?** `HtmlSaveOptions`  
- **폰트를 HTML에 직접 포함할 수 있나요?** 예, `exportFontsAsBase64`를 `true`로 설정합니다.  
- **Word‑특정 라운드트립 데이터를 유지하려면 어떻게 해야 하나요?** `exportRoundtripInformation`을 활성화합니다.  
- **벡터 그래픽에 가장 적합한 형식은 무엇인가요?** SVG 출력을 위해 `convertMetafilesToSvg`를 사용합니다.  
- **CSS 클래스 이름 충돌을 방지할 수 있나요?** 예, `addCssClassNamePrefix`를 사용합니다.

## 1. 소개
Asposeords for Java는 개발자가 Word 문서를 프로그래밍 방식으로 조작할 수 있게 해주는 강력한 API입니다. 이 가이드는 특정 웹 또는 통합 요구 사항을 충족하도록 변환 프로세스를 맞춤화할 수 있는 고급 HTML 문서 저장 옵션에 중점을 둡니다.

## 2. 라운드트립 정보 내보내기
라운드트립 정보를 보존하면 레이아웃이나 서식 세부 정보를 잃지 않고 HTML을 Word 문서로 다시 변환할 수 있습니다.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### 사용 시점
- HTML → Word → HTML와 같은 가역 변환 파이프라인이 필요할 때.  
- 원본 Word 구조를 유지해야 하는 협업 편집 시나리오에 이상적입니다.

## 3. 폰트를 Base64로 내보내기
폰트를 HTML에 직접 포함하면 외부 폰트 의존성을 없애고 브라우저 간 시각적 일관성을 보장합니다.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### 전문가 팁
대상 환경이 외부 리소스에 대한 접근이 제한된 경우(예: 이메일 뉴스레터) 이 옵션을 사용하십시오.

## 4. 리소스 내보내기
CSS 및 폰트 리소스가 출력되는 방식을 제어하고, 해당 자산에 대한 사용자 지정 폴더 또는 URL 별칭을 지정합니다.

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

### 왜 중요한가
CSS를 외부 파일로 분리하면 HTML 크기가 줄어들고 캐싱이 가능해져 페이지 로드 속도가 빨라집니다.

## 5. 메타파일을 EMF 또는 WMF로 변환
메타파일(예: EMF/WMF)은 브라우저가 신뢰성 있게 렌더링할 수 있는 형식으로 변환됩니다.

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

### 사용 사례
대상 브라우저가 이러한 벡터 형식을 지원하고 무손실 스케일링이 필요할 경우 EMF/WMF를 선택하십시오.

## 6. 메타파일을 SVG로 변환
SVG는 최고의 확장성을 제공하며 최신 브라우저에서 널리 지원됩니다.

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

### 장점
SVG 파일은 가볍고 문서가 해상도에 독립적이어서 반응형 웹 디자인에 최적입니다.

## 7. CSS 클래스 이름 접두사 추가
생성된 모든 CSS 클래스 이름에 접두사를 붙여 스타일 충돌을 방지합니다.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### 실용적인 팁
HTML을 기존 페이지에 삽입할 때 CSS 충돌을 방지하려면 고유한 접두사(예: 프로젝트 이름)를 사용하십시오.

## 8. MHTML 리소스를 위한 CID URL 내보내기
MHTML로 저장할 때, 이메일 호환성을 높이기 위해 Content‑ID URL을 사용해 리소스를 내보낼 수 있습니다.

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

### 사용 시점
이메일에 첨부할 수 있는 단일 자체 포함 HTML 파일을 생성할 때 이상적입니다.

## 9. 폰트 이름 해결
HTML이 올바른 폰트 패밀리를 참조하도록 보장하여 플랫폼 간 일관성을 향상시킵니다.

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

### 도움이 되는 이유
원본 문서가 클라이언트 머신에 설치되지 않은 폰트를 사용하는 경우, 이 옵션은 웹 안전 대체 폰트로 교체합니다.

## 10. 텍스트 입력 폼 필드를 텍스트로 내보내기
폼 필드를 인터랙티브 HTML 입력 요소가 아닌 일반 텍스트로 렌더링합니다.

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

### 사용 사례
아카이브 또는 인쇄 목적을 위해 폼의 읽기 전용 표현이 필요할 때.

## 일반적인 함정 및 문제 해결
| 문제 | 일반적인 원인 | 해결 방법 |
|------|---------------|-----------|
| 출력에 폰트가 누락됨 | `exportFontsAsBase64`가 활성화되지 않음 | `setExportFontsAsBase64(true)` 설정 |
| 삽입 후 CSS 손상 | `EXTERNAL`을 사용했지만 CSS 파일을 제공하지 않음 | 지정된 `resourceFolderAlias`에 CSS 파일이 배포되었는지 확인 |
| HTML 크기 과다 | 많은 이미지를 Base64로 삽입 | `setExportFontResources(true)`를 사용해 외부 이미지 리소스로 전환하고 `resourceFolder`를 구성 |
| 구형 브라우저에서 SVG가 렌더링되지 않음 | 브라우저가 SVG를 지원하지 않음 | EMF/WMF로도 내보내어 PNG 대체 파일을 제공 |

## 자주 묻는 질문

**Q: 폰트를 Base64로 임베드하면서 외부 CSS를 유지할 수 있나요?**  
A: 예. `exportFontsAsBase64(true)`를 설정하고 `CssStyleSheetType.EXTERNAL`을 유지하여 폰트 데이터를 스타일 규칙과 분리합니다.

**Q: 기존 HTML을 Word 문서로 다시 변환하려면 어떻게 해야 하나요?**  
A: `Document doc = new Document("input.html");` 로 HTML을 로드한 뒤 `doc.save("output.docx");` 로 저장합니다. 초기 내보내기 시 `exportRoundtripInformation`을 사용해 라운드트립 데이터를 보존합니다.

**Q: SVG 변환을 사용할 때 성능에 영향을 미치나요?**  
A: 큰 메타파일을 SVG로 변환하면 처리 시간이 늘어날 수 있지만, 결과 HTML은 일반적으로 더 작고 브라우저에서 더 빠르게 렌더링됩니다.

**Q: 이러한 옵션이 Aspose.Words for .NET에서도 작동하나요?**  
A: 동일한 개념이 .NET API에도 존재하지만 메서드 이름이 약간 다를 수 있습니다(예: `HtmlSaveOptions`는 플랫폼 간에 공유됩니다).

**Q: 이메일에 적합한 HTML을 만들려면 어떤 옵션을 선택해야 하나요?**  
A: `SaveFormat.MHTML`과 `exportCidUrlsForMhtmlResources`를 사용하여 모든 리소스를 이메일 본문에 직접 포함합니다.

**마지막 업데이트:** 2025-12-19  
**테스트 환경:** Aspose.Words for Java 24.12  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}