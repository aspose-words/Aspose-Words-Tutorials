---
date: 2026-01-16
description: Aspose.Words for Java를 사용하여 인치를 포인트로 변환하는 방법, Java에서 문서 메타데이터를 읽는 방법,
  Java에서 사용자 정의 속성을 추가하는 방법, 그리고 Java에서 페이지 여백을 설정하는 방법을 배워보세요.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: 인치를 포인트로 변환 – Aspose.Words for Java의 문서 속성 사용
url: /ko/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 인치를 포인트로 변환 – Aspose.Words for Java의 문서 속성 활용

이 튜토리얼에서는 페이지 여백을 설정할 때 **인치를 포인트로 변환**하는 방법, Java에서 문서 메타데이터를 읽는 방법, 사용자 정의 속성을 추가하는 방법, 그리고 Aspose.Words for Java를 사용해 내장 문서 속성을 다루는 방법을 알아봅니다. 보고서, 청구서, 법률 문서를 생성하든, 이러한 기술을 마스터하면 Word 파일의 외관과 메타데이터를 세밀하게 제어할 수 있습니다.

## 빠른 답변
- **인치를 포인트로 변환하려면?** Aspose.Words의 `ConvertUtil.inchToPoint(value)`를 사용합니다.  
- **Java에서 문서 메타데이터를 읽을 수 있나요?** 네 – `doc.getBuiltInDocumentProperties()` 또는 `doc.getCustomDocumentProperties()`를 호출하면 됩니다.  
- **Java에서 사용자 정의 속성을 추가하려면?** `doc.getCustomDocumentProperties().add(name, value)`를 사용합니다.  
- **여백을 포인트 단위로 설정하는 메서드는?** `PageSetup.setTopMargin`, `setBottomMargin` 등은 포인트 값을 받습니다.  
- **북마크에 링크를 연결할 수 있나요?** 네 – 사용자 정의 속성 컬렉션의 `addLinkToContent`를 사용합니다.

## 문서 속성 소개

문서 속성은 모든 Word 파일에서 중요한 역할을 합니다. 제목, 작성자, 주제, 키워드와 같은 정보와 다운스트림 처리에 필요한 사용자 정의 메타데이터를 저장합니다. Aspose.Words for Java에서는 내장 속성과 사용자 정의 속성을 모두 조작할 수 있으며, **인치를 포인트로 변환**과 같이 측정 단위를 변환해 레이아웃 세부 사항(여백 등)을 제어할 수도 있습니다.

## “인치를 포인트로 변환”이란?

Word에서는 레이아웃 측정값을 포인트 단위로 표현합니다(1포인트 = 1/72인치). 인치를 포인트로 변환하면 익숙한 임페리얼 단위로 여백, 들여쓰기, 간격 등을 정의하면서 API는 내부적으로 포인트를 사용하게 됩니다.

## Java에서 문서 메타데이터를 관리하는 이유

메타데이터를 삽입하면 검색, 분류, 워크플로 자동화가 쉬워집니다. 예를 들어 계약서에 “Authorized” 플래그를 붙이거나 감사 추적을 위해 개정 번호를 저장할 수 있습니다. 프로그램matically 메타데이터를 읽고 쓰면 대량 문서 배치에서도 일관성을 유지할 수 있습니다.

## 사전 요구 사항
- Java 17+ (또는 호환 JDK)
- 프로젝트에 추가된 Aspose.Words for Java 라이브러리 (Maven/Gradle)
- 접근 가능한 디렉터리에 위치한 샘플 `.docx` 파일(예: `Properties.docx`)

## 단계별 가이드

### 내장 문서 속성 열거
다음은 문서를 열고 Title, Author, Keywords와 같은 모든 내장 속성을 출력하는 간단한 테스트 예제입니다.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** 이 스니펫을 사용해 이전 단계에서 메타데이터가 올바르게 기록되었는지 확인하세요.

### 사용자 정의 문서 속성 추가 (add custom properties java)
사용자 정의 속성을 통해 Boolean, String, Date, Number 등 필요한 모든 데이터 유형을 저장할 수 있습니다.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Why this matters:** **Authorized**와 같은 플래그를 추가하면 문서 내용을 변경하지 않고도 후속 승인 워크플로를 구동할 수 있습니다.

### 사용자 정의 속성 삭제
더 이상 필요하지 않은 속성은 깔끔하게 삭제할 수 있습니다.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### 콘텐츠 링크 구성 (북마크 연결)
북마크를 만든 뒤 해당 북마크를 가리키는 사용자 정의 속성을 추가하면 동적 교차 참조가 가능합니다.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### 측정 단위 변환 (set page margins java)
핵심 키워드가 빛을 발하는 부분입니다. 여백을 인치 단위로 지정한 뒤 `ConvertUtil`을 사용해 **인치를 포인트로 변환**합니다.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Note:** `ConvertUtil`은 `pointToInch`, `mmToPoint` 등 다양한 레이아웃 처리를 위한 변환 메서드도 제공합니다.

### 제어 문자 사용 (read document metadata java)
제어 문자를 활용하면 텍스트 스트림을 정리할 수 있습니다. 이 예제는 캐리지 리턴(`\r`)을 Windows 줄바꿈(`\r\n`)으로 교체합니다.

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## 일반적인 문제 및 해결책
| Issue | Cause | Fix |
|-------|-------|-----|
| 변환 후 여백이 잘못 표시됨 | 잘못된 단위 사용(예: cm 대신 인치) | 인치 값에 대해 `ConvertUtil.inchToPoint`를 호출했는지 확인 |
| 사용자 정의 속성이 나타나지 않음 | 속성을 문서 저장 후에 추가함 | 속성을 추가한 뒤 `doc.save(...)`를 호출 |
| 북마크 링크가 깨짐 | 북마크 이름 오타 | `addLinkToContent`에 사용된 북마크 이름이 정확히 일치하는지 확인 |

## FAQ's

### 내장 문서 속성에 어떻게 접근하나요?

Aspose.Words for Java에서 내장 문서 속성에 접근하려면 `Document` 객체의 `getBuiltInDocumentProperties` 메서드를 사용하면 됩니다. 이 메서드는 반복 가능한 내장 속성 컬렉션을 반환합니다.

### 문서에 사용자 정의 문서 속성을 추가할 수 있나요?

네, `CustomDocumentProperties` 컬렉션을 이용해 문자열, 불리언, 날짜, 숫자 등 다양한 데이터 유형의 사용자 정의 속성을 추가할 수 있습니다.

### 특정 사용자 정의 문서 속성을 어떻게 삭제하나요?

`CustomDocumentProperties` 컬렉션의 `remove` 메서드에 삭제하려는 속성 이름을 전달하면 해당 속성을 제거할 수 있습니다.

### 문서 내 콘텐츠에 링크를 연결하는 목적은 무엇인가요?

문서 내 콘텐츠에 링크를 연결하면 특정 부분에 대한 동적 참조를 만들 수 있습니다. 이는 인터랙티브 문서나 섹션 간 교차 참조를 구현할 때 유용합니다.

### Aspose.Words for Java에서 측정 단위를 어떻게 변환하나요?

`ConvertUtil` 클래스를 사용하면 인치를 포인트로, 포인트를 센티미터로 등 다양한 단위 변환 메서드를 활용할 수 있습니다.

## Frequently Asked Questions

**Q: DocumentInfo를 사용해 전체 파일을 로드하지 않고 Java에서 문서 메타데이터를 읽는 방법은?**  
A: `DocumentInfo`를 이용하면 핵심 속성을 전체 문서를 완전히 로드하지 않고도 가져올 수 있습니다.

**Q: 기존 문서의 페이지 여백을 Java 코드로 설정할 수 있나요?**  
A: 네—문서를 연 뒤 `PageSetup` 여백을 수정하고(필요 시 인치를 포인트로 변환) 저장하면 됩니다.

**Q: 사용자 정의 속성을 PDF 메타데이터로 내보낼 수 있나요?**  
A: PDF로 저장할 때 Aspose.Words가 자동으로 사용자 정의 문서 속성을 PDF 커스텀 메타데이터에 매핑합니다.

**Q: 제어 문자가 PDF 변환에 영향을 미치나요?**  
A: 변환 과정에서 보존되지만, 일관성을 위해 줄바꿈을 정규화하는 것이 좋습니다.

**Q: `ConvertUtil`을 사용하려면 어떤 Aspose.Words 버전이 필요하나요?**  
A: `ConvertUtil`은 Aspose.Words 16.5부터 제공되며, 최신 버전이면 모두 지원합니다.

## 결론

**인치를 포인트로 변환**, Java에서 문서 메타데이터를 읽기, 사용자 정의 속성을 추가하기를 마스터하면 Word 파일의 시각적 레이아웃과 숨겨진 데이터를 완벽히 제어할 수 있습니다. 이러한 기능을 활용하면 자동화된 문서 파이프라인 구축, 규정 준수 강화, 풍부한 보고서 생성이 가능해지며, 모두 Aspose.Words for Java로 구현할 수 있습니다.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}