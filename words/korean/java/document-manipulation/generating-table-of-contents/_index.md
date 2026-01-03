---
date: 2026-01-03
description: Aspose.Words for Java를 사용하여 목차를 삽입하면서 페이지 번호를 조정하는 방법을 배워보세요. TOC 스타일을
  맞춤 설정하고 문서를 손쉽게 만들 수 있습니다.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java로 페이지 번호 조정 및 목차 생성
url: /ko/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 페이지 번호 조정 및 Aspose.Words for Java에서 목차 생성

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 **페이지 번호를 조정**하고 **목차(TOC)를 삽입**하는 방법을 알아봅니다. 잘 구성된 TOC는 긴 문서를 쉽게 탐색할 수 있게 해 주며, 페이지 번호 정렬을 미세 조정하면 독자에게 전문적인 경험을 제공합니다. 문서 생성, TOC 스타일 사용자 정의, 탭 스톱을 조정하여 페이지 번호를 원하는 위치에 정확히 맞추는 과정을 단계별로 안내합니다.

## 빠른 답변
- **“페이지 번호 조정”은 무엇을 의미하나요?** TOC에서 페이지 번호를 정렬하는 탭 스톱을 수정하는 것입니다.  
- **목차를 자동으로 삽입할 수 있나요?** 예 – `FieldToc` 클래스를 사용합니다.  
- **코드를 실행하려면 라이선스가 필요합니까?** 개발에는 무료 체험판으로 충분하지만, 운영 환경에서는 라이선스가 필요합니다.  
- **지원되는 Aspose 버전은 무엇인가요?** 예제는 최신 Aspose.Words for Java 릴리스와 함께 작동합니다.  
- **TOC 스타일을 사용자 정의할 수 있나요?** 물론입니다 – 글꼴, 굵기 등을 변경할 수 있습니다.

## Aspose.Words에서 목차란 무엇인가요?
목차(TOC)는 문서에서 헤딩 스타일(예: Heading 1, Heading 2)을 스캔하여 페이지 번호가 포함된 항목 목록을 생성하는 필드입니다. Aspose.Words를 사용하면 이 필드를 프로그래밍 방식으로 삽입하고 외관을 완전히 제어할 수 있습니다.

## 왜 TOC에서 페이지 번호를 조정해야 할까요?
탭 스톱을 조정하면 페이지 번호가 표시되는 위치를 정확하게 제어할 수 있으며, 이는 다음과 같은 이유로 중요합니다:

- 깔끔하고 열 정렬된 레이아웃 유지.  
- 기업 스타일 가이드에 맞추기.  
- 인쇄 및 디지털 문서의 가독성 향상.

## 사전 요구 사항
- 프로젝트에 Aspose.Words for Java를 추가 (Maven/Gradle).  
- Java 구문에 대한 기본적인 이해.

## 단계별 가이드

### 단계 1: 새 문서 만들기
먼저, 내용과 TOC를 담을 빈 `Document` 객체를 인스턴스화합니다.

```java
Document doc = new Document();
```

### 단계 2: TOC 스타일 사용자 정의
각 TOC 레벨의 모양을 변경할 수 있습니다. 이 예제에서는 첫 번째 레벨 항목을 굵게 만들어 일반적인 서식 요구 사항을 만족합니다.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### 단계 3: 문서에 내용 추가
헤딩(`Heading1`, `Heading2` 등)과 일반 단락을 삽입합니다. TOC 필드는 이후에 이러한 헤딩을 자동으로 감지합니다. *(코드는 간결성을 위해 생략 – TOC 생성에 초점)*

### 단계 4: TOC 필드 삽입
TOC를 원하는 위치에 배치합니다—보통 문서 시작 부분에 삽입합니다.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### 단계 5: 문서 저장
문서를 디스크에 저장합니다. DOCX, PDF, HTML 등 지원되는 형식 중 원하는 것을 선택할 수 있습니다.

```java
doc.save("your_output_path_here");
```

## TOC에서 탭 스톱 사용자 정의 (페이지 번호 조정)
기본 탭 스톱이 페이지 번호를 원하는 대로 정렬하지 않을 경우, 모든 TOC 단락을 순회하며 탭 위치를 수정할 수 있습니다.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

이제 TOC 항목이 페이지 번호를 정확히 원하는 위치에 표시하여 문서가 깔끔하게 보입니다.

## 일반적인 문제 및 팁
- **TOC에 헤딩이 누락됨:** 헤딩이 기본 스타일(`Heading1`, `Heading2` 등)을 사용하고 있는지 확인하거나 사용자 정의 스타일을 TOC 레벨에 매핑하십시오.  
- **탭 스톱이 적용되지 않음:** 해당 단락이 실제로 TOC 스타일(`TOC_1`‑`TOC_9`)에 속하는지 확인하십시오.  
- **대용량 문서에서 성능:** TOC를 삽입한 후 `doc.updateFields()`를 호출하여 한 번에 항목을 새로 고칩니다.

## 자주 묻는 질문

**Q: TOC 항목의 서식을 어떻게 변경하나요?**  
A: `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`를 사용합니다. 여기서 *X*는 레벨(1‑9)이며, 해당 스타일의 글꼴, 색상 또는 단락 설정을 수정합니다.

**Q: TOC에 레벨을 더 추가하려면 어떻게 해야 하나요?**  
A: 예를 들어 `FieldToc` 스위치 `\o "1-3"`을 조정하여 추가 헤딩 레벨을 포함하고, 해당 `TOC_X` 스타일을 업데이트합니다.

**Q: 특정 TOC 항목의 탭 스톱 위치를 변경할 수 있나요?**  
A: 예 – “탭 스톱 사용자 정의” 섹션에 표시된 대로 단락을 순회하며 각 탭 스톱을 개별적으로 수정합니다.

**Q: PDF 출력에서도 TOC를 생성할 수 있나요?**  
A: 물론입니다. TOC가 생성된 후 문서를 PDF(`doc.save("output.pdf")`)로 저장하면 필드가 자동으로 렌더링됩니다.

**Q: `updateFields()`를 수동으로 호출해야 하나요?**  
A: `FieldToc`를 삽입하면 Aspose.Words가 저장 시 자동으로 업데이트하지만, `doc.updateFields()`를 호출하면 디버깅을 위해 즉시 결과를 확인할 수 있습니다.

## 결론
Aspose.Words for Java를 사용하여 **페이지 번호를 조정**, **목차를 삽입**, 그리고 **TOC 스타일을 사용자 정의**하는 방법을 배웠습니다. 이러한 기술을 통해 깔끔하고 탐색이 쉬우며 전문적으로 서식이 지정된 문서를 만들어 어떤 출판 표준도 충족할 수 있습니다.

---  

**마지막 업데이트:** 2026-01-03  
**테스트 환경:** Aspose.Words for Java (latest release)  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}