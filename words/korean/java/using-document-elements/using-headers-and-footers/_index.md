---
"description": "Aspose.Words for Java에서 머리글과 바닥글을 사용하는 방법을 단계별로 배워보세요. 전문가 수준의 문서를 손쉽게 제작할 수 있습니다."
"linktitle": "헤더와 푸터 사용"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 헤더와 푸터 사용하기"
"url": "/ko/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 헤더와 푸터 사용하기


이 포괄적인 가이드에서는 Aspose.Words for Java에서 머리글과 바닥글을 사용하는 방법을 안내합니다. 머리글과 바닥글은 문서 서식 지정에 필수적인 요소이며, Aspose.Words는 필요에 따라 머리글과 바닥글을 만들고 사용자 지정할 수 있는 강력한 도구를 제공합니다.

이제 각 단계를 자세히 살펴보겠습니다.

## 1. Aspose.Words 소개

Aspose.Words는 Word 문서를 프로그래밍 방식으로 생성, 조작 및 렌더링할 수 있는 강력한 Java API입니다. 머리글과 바닥글을 포함한 다양한 문서 서식 기능을 제공합니다.

## 2. Java 환경 설정

Aspose.Words를 사용하기 전에 Java 개발 환경이 올바르게 설정되어 있는지 확인하세요. 필요한 설정 지침은 Aspose.Words 설명서 페이지에서 확인할 수 있습니다. [Aspose.Words Java 문서](https://reference.aspose.com/words/java/).

## 3. 새 문서 만들기

머리글과 바닥글을 사용하려면 Aspose.Words를 사용하여 새 문서를 만들어야 합니다. 다음 코드는 이 작업을 수행하는 방법을 보여줍니다.

```java
// 새 문서를 만드는 Java 코드
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. 페이지 설정 이해

페이지 설정은 문서 레이아웃을 제어하는 데 매우 중요합니다. 다음을 사용하여 머리글 및 바닥글과 관련된 다양한 속성을 지정할 수 있습니다. `PageSetup` 클래스. 예를 들어:

```java
// 페이지 속성 설정
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. 첫 페이지 헤더/바닥글의 차이

Aspose.Words를 사용하면 문서의 첫 페이지에 다른 머리글과 바닥글을 적용할 수 있습니다. `pageSetup.setDifferentFirstPageHeaderFooter(true);` 이 기능을 활성화하려면.

## 6. 헤더 작업

### 6.1. 헤더에 텍스트 추가

헤더에 텍스트를 추가할 수 있습니다. `DocumentBuilder`. 예를 들면 다음과 같습니다.

```java
// 첫 번째 페이지 헤더에 텍스트 추가
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. 헤더에 이미지 삽입

헤더에 이미지를 삽입하려면 다음을 사용할 수 있습니다. `insertImage` 방법입니다. 예를 들면 다음과 같습니다.

```java
// 헤더에 이미지 삽입
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. 헤더 스타일 사용자 정의

위의 예시와 같이 글꼴, 정렬 등 다양한 속성을 설정하여 헤더 스타일을 사용자 정의할 수 있습니다.

## 7. 바닥글 작업

### 7.1. 바닥글에 텍스트 추가

헤더와 유사하게 다음을 사용하여 바닥글에 텍스트를 추가할 수 있습니다. `DocumentBuilder`. 예를 들면 다음과 같습니다.

```java
// 기본 바닥글에 텍스트 추가
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// 필요에 따라 텍스트와 필드를 삽입하세요
```

### 7.2. 바닥글에 이미지 삽입

바닥글에 이미지를 삽입하려면 다음을 사용하세요. `insertImage` 방법은 헤더와 같습니다.

### 7.3. 바닥글 스타일 사용자 정의

다음을 사용하여 바닥글 스타일을 사용자 정의하세요. `DocumentBuilder`헤더를 사용자 지정하는 것과 유사합니다.

## 8. 페이지 번호 매기기

다음과 같은 필드를 사용하여 머리글과 바닥글에 페이지 번호를 포함할 수 있습니다. `PAGE` 그리고 `NUMPAGES`. 이러한 필드는 페이지를 추가하거나 제거하면 자동으로 업데이트됩니다.

## 9. 바닥글의 저작권 정보

문서의 바닥글에 저작권 정보를 추가하려면 코드 조각에 표시된 대로 두 개의 셀이 있는 표를 사용하여 하나는 왼쪽에, 다른 하나는 오른쪽에 정렬할 수 있습니다.

## 10. 여러 섹션 작업

Aspose.Words를 사용하면 문서 내 여러 섹션을 작업할 수 있습니다. 각 섹션마다 다른 페이지 설정과 머리글/바닥글을 설정할 수 있습니다.

## 11. 가로 방향

필요한 경우 특정 섹션의 방향을 가로 모드로 변경할 수 있습니다.

## 12. 이전 섹션의 머리글/바닥글 복사

복잡한 문서를 만들 때 이전 섹션의 머리글과 바닥글을 복사하면 시간을 절약할 수 있습니다.

## 13. 문서 저장

문서를 만들고 사용자 지정한 후에는 다음을 사용하여 저장하는 것을 잊지 마세요. `doc.save()` 방법.

## 완전한 소스 코드
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // 첫 번째 페이지의 머리글/바닥글을 다른 페이지와 다르게 할지 여부를 지정합니다.
        // PageSetup.OddAndEvenPagesHeaderFooter 속성을 사용하여 지정할 수도 있습니다.
        // 홀수 페이지와 짝수 페이지에 다른 머리글/바닥글을 추가합니다.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // 헤더의 상단/왼쪽 모서리에 위치가 지정된 이미지를 삽입합니다.
        // 페이지의 위쪽/왼쪽 가장자리로부터의 거리는 10포인트로 설정됩니다.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // 우리는 두 개의 셀이 있는 표를 사용하여 줄에 있는 텍스트의 한 부분(페이지 번호 포함)을 만듭니다.
        // 왼쪽에 정렬하고, 저작권이 있는 텍스트의 나머지 부분은 오른쪽에 정렬합니다.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // PAGE 및 NUMPAGES 필드를 사용하여 현재 페이지 번호와 여러 페이지를 자동으로 계산합니다.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // 두 번째 페이지에 기본 머리글/바닥글이 표시되도록 페이지 나누기를 합니다.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // 이 섹션에는 다른 첫 페이지 머리글/바닥글이 필요하지 않습니다. 문서에는 제목 페이지가 하나만 필요합니다.
        // 그리고 이 페이지의 헤더/푸터는 이미 이전 섹션에서 정의되었습니다.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // 이 섹션에는 이전 섹션의 머리글/바닥글이 표시됩니다.
        // 기본적으로 이 페이지 너비를 취소하려면 currentSection.HeadersFooters.LinkToPrevious(false)를 호출합니다.
        // 새로운 섹션의 경우 다르므로 바닥글 표의 셀 너비도 다르게 설정해야 합니다.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // 이 섹션에 이미 설정된 헤더/푸터 세트를 사용하려면
        // 하지만 약간의 사소한 수정을 거치면 헤더/바닥글을 복사하는 것이 편리할 수 있습니다.
        // 이전 섹션에서 필요한 수정 사항을 원하는 곳에 적용합니다.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
copyHeadersFootersFromPreviousSection 메서드의 소스 코드
```java
    /// <요약>
    //이전 섹션의 머리글/바닥글을 복제하여 지정된 섹션에 복사합니다.
    /// </요약>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## 결론

이 튜토리얼에서는 Aspose.Words for Java에서 머리글과 바닥글을 사용하는 기본적인 방법을 다루었습니다. 머리글과 바닥글을 만들고, 사용자 지정하고, 스타일을 지정하는 방법은 물론, 기타 필수적인 문서 서식 지정 기법도 살펴보았습니다.

자세한 내용 및 고급 기능은 다음을 참조하세요. [Aspose.Words Java 문서](https://reference.aspose.com/words/java/).

## 자주 묻는 질문

### 1. 문서 바닥글에 페이지 번호를 추가하려면 어떻게 해야 하나요?
페이지 번호를 추가하려면 다음을 삽입하세요. `PAGE` Aspose.Words를 사용하여 바닥글에 필드를 추가합니다.

### 2. Aspose.Words는 Java 개발 환경과 호환됩니까?
네, Aspose.Words는 Java 개발을 지원합니다. 필요한 설정이 제대로 되어 있는지 확인하세요.

### 3. 헤더와 푸터의 글꼴과 스타일을 사용자 지정할 수 있나요?
물론입니다. 글꼴, 정렬 및 기타 스타일을 사용자 지정하여 헤더와 푸터를 시각적으로 매력적으로 만들 수 있습니다.

### 4. 홀수 페이지와 짝수 페이지에 서로 다른 머리글을 사용하는 것이 가능합니까?
네, 사용할 수 있습니다 `PageSetup.OddAndEvenPagesHeaderFooter` 홀수 및 짝수 페이지에 대해 서로 다른 헤더를 지정합니다.

### 5. Aspose.Words for Java를 시작하려면 어떻게 해야 하나요?
시작하려면 다음을 방문하세요. [Aspose.Words Java 문서](https://reference.aspose.com/words/java/) API 사용에 대한 포괄적인 지침을 확인하세요.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}