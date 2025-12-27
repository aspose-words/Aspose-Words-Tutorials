---
date: 2025-12-27
description: Aspose.Words for Java를 사용하여 방향을 설정하고, txt 파일을 로드하고, 공백을 제거하며, txt를 docx로
  변환하는 방법을 배워보세요.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 방향을 설정하고 텍스트 파일을 로드하는 방법
url: /ko/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java로 방향 설정 및 텍스트 파일 로드 방법

## Aspose.Words for Java로 텍스트 파일 로드 소개

이 가이드에서는 일반 텍스트 문서를 로드할 때 **방향 설정 방법**을 알아보고, Aspose.Words for Java를 사용하여 **txt 로드**, **공백 제거**, **txt를 docx로 변환**하는 실용적인 방법을 확인할 수 있습니다. 문서 변환 서비스를 구축하거나 목록 감지를 세밀하게 제어해야 할 경우, 이 튜토리얼은 명확한 설명과 바로 실행 가능한 코드를 통해 모든 단계를 안내합니다.

## 빠른 답변
- **로드된 TXT 파일의 텍스트 방향을 어떻게 설정합니까?** `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)`를 사용하거나 `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`를 지정합니다.
- **Aspose.Words가 일반 텍스트에서 번호 매기기 목록을 감지할 수 있나요?** 예 – `TxtLoadOptions`에서 `DetectNumberingWithWhitespaces`를 활성화합니다.
- **앞뒤 공백을 어떻게 제거합니까?** `TxtLeadingSpacesOptions.TRIM`와 `TxtTrailingSpacesOptions.TRIM`을 설정합니다.
- **TXT 파일을 한 줄로 DOCX로 변환할 수 있나요?** `TxtLoadOptions`로 TXT를 로드하고 `Document.save("output.docx")`를 호출합니다.
- **필요한 Java 버전은 무엇인가요?** Aspose.Words 24.x에 대해 Java 8 이상이면 충분합니다.

## Aspose.Words에서 “방향 설정”이란 무엇인가요?
텍스트 파일에 오른쪽‑왼쪽 스크립트(예: 히브리어 또는 아랍어)가 포함된 경우, 라이브러리는 읽기 순서를 알아야 합니다. `DocumentDirection` 열거형을 사용하면 **방향을** 수동으로 설정하거나 Aspose가 자동으로 감지하도록 할 수 있어 올바른 레이아웃과 양방향(bidi) 서식을 보장합니다.

## TXT 파일 로드에 Aspose.Words를 사용하는 이유
- **정확한 목록 감지** – 번호 매기기, 글머리표 및 공백 구분 목록을 처리합니다.
- **세밀한 공백 처리** – 앞뒤 공백을 제거하거나 보존합니다.
- **자동 텍스트 방향 감지** – 다국어 문서에 최적입니다.
- **한 번에 변환** – `.txt`를 로드하고 `.docx`, `.pdf` 또는 지원되는 다른 형식으로 저장합니다.

## 사전 요구 사항
- Java 8 이상.
- Aspose.Words for Java 라이브러리(프로젝트에 Maven/Gradle 의존성을 추가하거나 JAR 파일을 포함).
- Java I/O 스트림에 대한 기본 지식.

## 단계별 가이드

### 단계 1: 목록 감지 (txt 로드 방법)
텍스트 문서를 로드하고 목록을 자동으로 감지하려면 `TxtLoadOptions` 인스턴스를 생성하고 목록 감지를 활성화합니다. 아래 코드는 여러 목록 스타일을 보여주며 공백을 인식한 번호 매기기를 활성화합니다.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **프로 팁:** 기본 목록 감지만 필요하면 공백 옵션을 건너뛸 수 있습니다 – Aspose는 여전히 표준 `1.` 및 `1)` 패턴을 인식합니다.

### 단계 2: 공백 옵션 처리 (공백 제거 방법)
앞뒤 공백은 종종 서식 오류를 일으킵니다. `TxtLeadingSpacesOptions`와 `TxtTrailingSpacesOptions`를 사용하여 이 동작을 제어합니다.

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

> **중요한 이유:** 공백을 제거하면 결과 DOCX에서 원치 않는 들여쓰기를 방지하여 문서를 수동 후처리 없이 깔끔하게 유지합니다.

### 단계 3: 텍스트 방향 제어 (방향 설정 방법)
오른쪽‑왼쪽 언어의 경우, 로드하기 전에 문서 방향을 설정합니다. 아래 예제는 히브리어 텍스트 파일을 로드하고 방향을 확인하기 위해 bidi 플래그를 출력합니다.

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

> **흔한 실수:** `DocumentDirection`을 설정하지 않으면 문자 순서가 뒤섞여 아랍어/히브리어 텍스트가 깨져 보일 수 있습니다.

## Aspose.Words for Java로 텍스트 파일 로드를 위한 전체 소스 코드
아래는 목록 감지, 공백 처리 및 방향 제어를 결합한 전체 실행 가능한 소스 코드입니다. 이를 하나의 클래스로 복사‑붙여넣기하고 세 개의 테스트 메서드를 개별적으로 실행할 수 있습니다.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## 일반적인 문제와 해결책
| 문제 | 원인 | 해결 방법 |
|-------|-------|-----|
| 목록이 감지되지 않음 | `DetectNumberingWithWhitespaces`가 공백 구분 목록에 대해 `false`로 남아 있음 | `loadOptions.setDetectNumberingWithWhitespaces(true)` 활성화 |
| 로드 후 추가 들여쓰기 | 앞쪽 공백이 보존됨 | `TxtLeadingSpacesOptions.TRIM` 설정 |
| 히브리어 텍스트가 뒤집혀 표시됨 | 문서 방향이 설정되지 않았거나 `LEFT_TO_RIGHT`로 설정됨 | `DocumentDirection.AUTO` 또는 `RIGHT_TO_LEFT` 사용 |
| 출력 DOCX가 비어 있음 | 두 번째 로드 전에 입력 스트림이 재설정되지 않음 | 각 로드 호출마다 `ByteArrayInputStream`을 다시 생성 |

## 자주 묻는 질문

### Q: Aspose.Words for Java란 무엇인가요?
Aspose.Words for Java는 개발자가 Java 애플리케이션에서 프로그래밍 방식으로 Word 문서를 생성, 조작 및 변환할 수 있도록 하는 강력한 문서 처리 라이브러리입니다. 간단한 텍스트 로드부터 복잡한 서식 및 변환에 이르기까지 다양한 기능을 지원합니다.

### Q: Aspose.Words for Java를 어떻게 시작할 수 있나요?
1. Aspose.Words for Java 라이브러리를 다운로드하고 설치합니다.  
2. 자세한 정보와 예제는 [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) 문서를 참고하십시오.  
3. 샘플 코드와 튜토리얼을 살펴보며 라이브러리를 효과적으로 사용하는 방법을 배우세요.

### Q: Aspose.Words for Java를 사용해 텍스트 문서를 어떻게 로드하나요?
`TxtLoadOptions` 클래스를 `Document` 생성자와 함께 사용합니다. 위 단계별 섹션에서 보여준 것처럼 목록 감지, 공백 처리 또는 텍스트 방향과 같은 옵션을 지정합니다.

### Q: 로드한 텍스트 문서를 다른 형식으로 변환할 수 있나요?
예. TXT 파일을 `Document` 객체에 로드한 후 `doc.save("output.pdf")`, `doc.save("output.docx")` 또는 지원되는 다른 형식으로 저장하면 됩니다.

### Q: 로드한 텍스트 문서에서 공백을 어떻게 처리하나요?
`TxtLeadingSpacesOptions`와 `TxtTrailingSpacesOptions`를 사용하여 앞뒤 공백을 제어합니다. 원치 않는 공백을 제거하려면 `TRIM`으로, 원본 간격을 유지해야 하면 `PRESERVE`로 설정합니다.

### Q: Aspose.Words for Java에서 텍스트 방향의 의미는 무엇인가요?
텍스트 방향은 오른쪽‑왼쪽 스크립트(히브리어, 아랍어 등)의 올바른 렌더링을 보장합니다. `DocumentDirection`을 설정하면 결과 문서에서 양방향(bidi) 텍스트가 정확히 표시됩니다.

### Q: Aspose.Words for Java에 대한 추가 리소스와 지원은 어디서 찾을 수 있나요?
[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)을 방문하여 API 레퍼런스, 코드 샘플 및 자세한 가이드를 확인하세요. 또한 Aspose 커뮤니티 포럼에 참여하거나 특정 질문에 대해 Aspose 지원팀에 문의할 수 있습니다.

### Q: Aspose.Words for Java는 상업 프로젝트에 적합한가요?
예. 개인 및 상업용 모두에 대한 라이선스 옵션을 제공합니다. 프로젝트에 맞는 적절한 플랜을 선택하려면 Aspose 웹사이트에서 라이선스 조건을 확인하십시오.

## 결론
이제 Aspose.Words for Java를 사용해 일반 텍스트를 풍부한 Word 문서로 변환할 때 **txt 파일 로드**, **목록 감지**, **공백 제거**, **방향 설정**을 할 수 있는 완전한 도구 모음이 준비되었습니다. 이러한 패턴을 적용해 문서 워크플로를 자동화하고, 다국어 지원을 향상시키며, 매번 깔끔하고 전문적인 결과물을 보장하세요.

---

**마지막 업데이트:** 2025-12-27  
**테스트 환경:** Aspose.Words for Java 24.12  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}