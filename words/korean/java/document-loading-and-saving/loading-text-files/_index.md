---
"description": "Aspose.Words for Java의 강력한 기능을 활용하세요. 텍스트 문서 불러오기, 목록 관리, 공백 처리, 텍스트 방향 제어 방법을 배워보세요."
"linktitle": "텍스트 파일 로딩"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Aspose.Words for Java를 사용하여 텍스트 파일 로드하기"
"url": "/ko/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 텍스트 파일 로드하기


## Aspose.Words for Java를 사용한 텍스트 파일 로딩 소개

이 가이드에서는 Aspose.Words for Java를 사용하여 텍스트 파일을 로드하고 Word 문서처럼 처리하는 방법을 살펴보겠습니다. 목록 감지, 공백 처리, 텍스트 방향 제어 등 다양한 측면을 다룹니다.

## 1단계: 목록 감지

텍스트 문서를 로드하고 목록을 감지하려면 다음 단계를 따르세요.

```java
// 목록으로 해석될 수 있는 부분을 포함한 문자열 형태의 일반 텍스트 문서를 만듭니다.
// 로드 시, 처음 세 개의 목록은 항상 Aspose.Words에 의해 감지됩니다.
// 그리고 로드 후에 List 객체가 생성됩니다.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// 네 번째 목록은 목록 번호와 목록 항목 내용 사이에 공백이 있습니다.
// LoadOptions 개체의 "DetectNumberingWithWhitespaces"가 true로 설정된 경우에만 목록으로 감지됩니다.
// 숫자로 시작하는 문단이 실수로 목록으로 감지되는 것을 방지합니다.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// LoadOptions를 매개변수로 적용하면서 문서를 로드하고 결과를 확인합니다.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

이 코드는 다양한 목록 형식을 사용하여 텍스트 문서를 로드하고 사용하는 방법을 보여줍니다. `DetectNumberingWithWhitespaces` 목록을 올바르게 감지하는 옵션.

## 2단계: 공간 옵션 처리

텍스트 문서를 로드할 때 앞뒤 공백을 제어하려면 다음 코드를 사용할 수 있습니다.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

이 예에서는 텍스트 문서를 로드하고 다음을 사용하여 앞뒤 공백을 제거합니다. `TxtLeadingSpacesOptions.TRIM` 그리고 `TxtTrailingSpacesOptions.TRIM`.

## 3단계: 텍스트 방향 제어

텍스트 문서를 로드할 때 텍스트 방향을 지정하려면 다음 코드를 사용할 수 있습니다.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

이 코드는 문서 방향을 자동 감지로 설정합니다(`DocumentDirection.AUTO`) 히브리어 텍스트가 포함된 텍스트 문서를 불러옵니다. 필요에 따라 문서 방향을 조정할 수 있습니다.

## Aspose.Words for Java를 사용하여 텍스트 파일을 로드하기 위한 전체 소스 코드

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// 목록으로 해석될 수 있는 부분을 포함한 문자열 형태의 일반 텍스트 문서를 만듭니다.
	// 로드 시, 처음 세 개의 목록은 항상 Aspose.Words에 의해 감지됩니다.
	// 그리고 로드 후에 List 객체가 생성됩니다.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// 네 번째 목록은 목록 번호와 목록 항목 내용 사이에 공백이 있습니다.
	// LoadOptions 개체의 "DetectNumberingWithWhitespaces"가 true로 설정된 경우에만 목록으로 감지됩니다.
	// 숫자로 시작하는 문단이 실수로 목록으로 감지되는 것을 방지합니다.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// LoadOptions를 매개변수로 적용하면서 문서를 로드하고 결과를 확인합니다.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## 결론

이 가이드에서는 Aspose.Words for Java를 사용하여 텍스트 파일을 로드하고, 목록을 감지하고, 공백을 처리하고, 텍스트 방향을 제어하는 방법을 살펴보았습니다. 이러한 기술을 사용하면 Java 애플리케이션에서 텍스트 문서를 효과적으로 조작할 수 있습니다.

## 자주 묻는 질문

### Java용 Aspose.Words란 무엇인가요?

Aspose.Words for Java는 개발자가 Java 애플리케이션에서 Word 문서를 프로그래밍 방식으로 생성, 조작 및 변환할 수 있도록 지원하는 강력한 문서 처리 라이브러리입니다. 텍스트, 표, 이미지 및 기타 문서 요소 작업을 위한 다양한 기능을 제공합니다.

### Java용 Aspose.Words를 어떻게 시작할 수 있나요?

Java용 Aspose.Words를 시작하려면 다음 단계를 따르세요.
1. Java용 Aspose.Words 라이브러리를 다운로드하여 설치하세요.
2. 설명서를 참조하세요 [Java API 참조를 위한 Aspose.Words](https://reference.aspose.com/words/java/) 자세한 정보와 예를 확인하세요.
3. 샘플 코드와 튜토리얼을 살펴보고 라이브러리를 효과적으로 사용하는 방법을 알아보세요.

### Aspose.Words for Java를 사용하여 텍스트 문서를 로드하려면 어떻게 해야 하나요?

Aspose.Words for Java를 사용하여 텍스트 문서를 로드하려면 다음을 사용할 수 있습니다. `TxtLoadOptions` 수업과 `Document` 클래스. 필요에 따라 공백 및 텍스트 방향 처리에 대한 적절한 옵션을 지정해야 합니다. 자세한 예시는 이 문서의 단계별 가이드를 참조하세요.

### 로드된 텍스트 문서를 다른 형식으로 변환할 수 있나요?

네, Aspose.Words for Java를 사용하면 로드된 텍스트 문서를 DOCX, PDF 등 다양한 형식으로 변환할 수 있습니다. `Document` 변환을 수행하는 클래스입니다. 구체적인 변환 예시는 설명서를 참조하세요.

### 로드된 텍스트 문서에서 공백을 어떻게 처리합니까?

로드된 텍스트 문서에서 앞뒤 공백이 처리되는 방식을 제어할 수 있습니다. `TxtLoadOptions`. 다음과 같은 옵션 `TxtLeadingSpacesOptions` 그리고 `TxtTrailingSpacesOptions` 필요에 따라 공간을 잘라내거나 유지할 수 있습니다. 이 가이드의 "공간 옵션 처리" 섹션을 참조하세요.

### Aspose.Words for Java에서 텍스트 방향의 중요성은 무엇입니까?

텍스트 방향은 히브리어나 아랍어와 같이 여러 문자나 언어가 혼합된 문서에 필수적입니다. Aspose.Words for Java는 텍스트 방향을 지정하는 옵션을 제공하여 이러한 언어의 텍스트가 올바르게 렌더링되고 서식이 적용되도록 합니다. 이 가이드의 "텍스트 방향 제어" 섹션에서는 텍스트 방향을 설정하는 방법을 설명합니다.

### Aspose.Words for Java에 대한 추가 리소스와 지원은 어디에서 찾을 수 있나요?

추가 리소스, 문서 및 지원을 보려면 다음을 방문하세요. [Java 문서용 Aspose.Words](https://reference.aspose.com/words/java/)Aspose.Words 커뮤니티 포럼에 참여하거나 Aspose 지원팀에 문의하여 특정 문제나 문의 사항에 대한 도움을 받으실 수도 있습니다.

### Aspose.Words for Java는 상업 프로젝트에 적합합니까?

네, Aspose.Words for Java는 개인 및 상업 프로젝트 모두에 적합합니다. 다양한 사용 시나리오에 맞는 라이선스 옵션을 제공합니다. Aspose 웹사이트에서 라이선스 조건과 가격을 확인하여 프로젝트에 적합한 라이선스를 선택하세요.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}