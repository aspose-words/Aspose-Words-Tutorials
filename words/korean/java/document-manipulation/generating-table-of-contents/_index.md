---
title: Java용 Aspose.Words에서 목차 생성
linktitle: 목차 생성
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java를 사용하여 목차(TOC)를 생성하고 사용자 지정하는 방법을 알아보세요. 체계적이고 전문적인 문서를 손쉽게 만드세요.
weight: 21
url: /ko/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 목차 생성


## Aspose.Words for Java에서 목차 생성 소개

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 목차(TOC)를 생성하는 과정을 안내해 드리겠습니다. TOC는 체계적인 문서를 만드는 데 중요한 기능입니다. TOC의 모양과 레이아웃을 사용자 지정하는 방법을 다루겠습니다.

## 필수 조건

시작하기 전에 Aspose.Words for Java가 설치되었고 Java 프로젝트에 설정되어 있는지 확인하세요.

## 1단계: 새 문서 만들기

먼저, 작업할 새 문서를 만들어 보겠습니다.

```java
Document doc = new Document();
```

## 2단계: TOC 스타일 사용자 정의

TOC의 모양을 사용자 지정하려면 TOC와 관련된 스타일을 수정할 수 있습니다. 이 예에서는 1차 TOC 항목을 굵게 표시합니다.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## 3단계: 문서에 콘텐츠 추가

문서에 콘텐츠를 추가할 수 있습니다. 이 콘텐츠는 TOC를 생성하는 데 사용됩니다.

## 4단계: TOC 생성

TOC를 생성하려면 문서의 원하는 위치에 TOC 필드를 삽입합니다. 이 필드는 문서의 제목과 스타일에 따라 자동으로 채워집니다.

```java
// 문서의 원하는 위치에 TOC 필드를 삽입합니다.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## 5단계: 문서 저장

마지막으로 TOC를 포함하여 문서를 저장합니다.

```java
doc.save("your_output_path_here");
```

## TOC에서 탭 정지 사용자 지정

TOC에서 탭 정지를 사용자 지정하여 페이지 번호의 레이아웃을 제어할 수도 있습니다. 탭 정지를 변경하는 방법은 다음과 같습니다.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // 이 문단에서 사용된 첫 번째 탭을 가져와서 페이지 번호를 정렬합니다.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // 오래된 탭을 제거하세요.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //수정된 위치(예: 왼쪽으로 50단위)에 새 탭을 삽입합니다.
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

이제 페이지 번호 정렬을 위한 탭 정지가 조정된 사용자 지정 목차가 문서에 생겼습니다.


## 결론

이 튜토리얼에서는 Word 문서 작업을 위한 강력한 라이브러리인 Aspose.Words for Java를 사용하여 목차(TOC)를 생성하는 방법을 살펴보았습니다. 잘 구성된 TOC는 긴 문서를 구성하고 탐색하는 데 필수적이며 Aspose.Words는 TOC를 손쉽게 만들고 사용자 정의할 수 있는 도구를 제공합니다.

## 자주 묻는 질문

### TOC 항목의 서식을 어떻게 변경합니까?

 TOC 수준과 관련된 스타일을 수정할 수 있습니다.`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`여기서 X는 TOC 수준입니다.

### TOC에 레벨을 더 추가하려면 어떻게 해야 하나요?

TOC에 더 많은 수준을 포함하려면 TOC 필드를 수정하고 원하는 수준 수를 지정하면 됩니다.

### 특정 TOC 항목에 대한 탭 정지 위치를 변경할 수 있나요?

네, 위의 코드 예제에서 보듯이 문단을 반복하면서 탭 정지 위치를 적절히 수정하여 특정 TOC 항목에 대한 탭 정지 위치를 변경할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
