---
title: Java용 Aspose.Words에서 문서 속성 사용
linktitle: 문서 속성 사용
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java로 문서 관리를 최적화하세요. 이 포괄적인 튜토리얼에서 문서 속성 작업, 사용자 정의 메타데이터 추가 등을 알아보세요.
weight: 32
url: /ko/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서 속성 사용


## 문서 속성 소개

문서 속성은 모든 문서의 중요한 부분입니다. 문서 자체에 대한 추가 정보(예: 제목, 작성자, 주제, 키워드 등)를 제공합니다. Aspose.Words for Java에서는 기본 제공 및 사용자 지정 문서 속성을 모두 조작할 수 있습니다.

## 문서 속성 열거

### 내장된 속성

기본 제공 문서 속성을 검색하고 작업하려면 다음 코드 조각을 사용할 수 있습니다.

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

이 코드는 문서의 이름과 "제목", "작성자", "키워드"와 같은 속성을 포함한 기본 제공 속성을 표시합니다.

### 사용자 정의 속성

사용자 지정 문서 속성을 사용하려면 다음 코드 조각을 사용하면 됩니다.

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

이 코드 조각은 부울 값, 문자열, 날짜, 개정 번호, 숫자 값을 비롯한 사용자 지정 문서 속성을 추가하는 방법을 보여줍니다.

## 문서 속성 제거

특정 문서 속성을 제거하려면 다음 코드를 사용할 수 있습니다.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

이 코드는 문서에서 사용자 정의 속성 "승인된 날짜"를 제거합니다.

## 콘텐츠에 대한 링크 구성

어떤 경우에는 문서 내에 링크를 만들고 싶을 수 있습니다. 방법은 다음과 같습니다.

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

    // 콘텐츠 속성에 연결된 항목을 추가합니다.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

이 코드 조각은 문서에 책갈피를 만들고 해당 책갈피에 연결되는 사용자 지정 문서 속성을 추가하는 방법을 보여줍니다.

## 측정 단위 간 변환

Aspose.Words for Java에서는 측정 단위를 쉽게 변환할 수 있습니다. 다음은 그 방법의 예입니다.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // 여백을 인치로 설정합니다.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

이 코드 조각은 인치 단위를 포인트로 변환하여 다양한 여백과 거리를 설정합니다.

## 제어 문자 사용

제어 문자는 텍스트를 다룰 때 유용할 수 있습니다. 텍스트에서 제어 문자를 대체하는 방법은 다음과 같습니다.

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // "\r" 제어 문자를 "\r\n"으로 바꾸세요.
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

이 예에서 우리는 캐리지 리턴(`\r`) 캐리지 리턴과 줄 바꿈(`\r\n`).

## 결론

문서 속성은 Aspose.Words for Java에서 문서를 효과적으로 관리하고 구성하는 데 중요한 역할을 합니다. 기본 제공 속성, 사용자 지정 속성 또는 제어 문자를 사용하든, 문서 관리 기능을 향상시키는 데 사용할 수 있는 다양한 도구가 있습니다.

## 자주 묻는 질문

### 내장된 문서 속성에 어떻게 액세스합니까?

 Java용 Aspose.Words의 내장 문서 속성에 액세스하려면 다음을 사용할 수 있습니다.`getBuiltInDocumentProperties` 방법에 대한`Document` 객체. 이 메서드는 반복할 수 있는 내장 속성 컬렉션을 반환합니다.

### 문서에 사용자 정의 문서 속성을 추가할 수 있나요?

 예, 다음을 사용하여 문서에 사용자 정의 문서 속성을 추가할 수 있습니다.`CustomDocumentProperties` 컬렉션. 문자열, 부울, 날짜 및 숫자 값을 포함한 다양한 데이터 유형으로 사용자 정의 속성을 정의할 수 있습니다.

### 특정 사용자 정의 문서 속성을 제거하려면 어떻게 해야 합니까?

 특정 사용자 정의 문서 속성을 제거하려면 다음을 사용할 수 있습니다.`remove` 방법에 대한`CustomDocumentProperties`컬렉션에서 제거하려는 속성의 이름을 매개변수로 전달합니다.

### 문서 내의 콘텐츠에 링크를 연결하는 목적은 무엇인가요?

문서 내의 콘텐츠에 링크하면 문서의 특정 부분에 대한 동적 참조를 만들 수 있습니다. 이는 대화형 문서나 섹션 간의 교차 참조를 만드는 데 유용할 수 있습니다.

### Aspose.Words for Java에서 서로 다른 측정 단위를 어떻게 변환할 수 있나요?

 Aspose.Words for Java에서는 다음을 사용하여 다양한 측정 단위 간을 변환할 수 있습니다.`ConvertUtil` 클래스. 인치에서 포인트, 포인트에서 센티미터 등과 같은 단위를 변환하는 방법을 제공합니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
