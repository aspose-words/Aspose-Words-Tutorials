---
date: 2026-02-14
description: Aspose.Words for Java를 사용하여 인라인 수식을 표시하고, 수학 방정식을 삽입하며, Office Math 객체를
  손쉽게 조작하는 방법을 배워보세요.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java에서 Office Math를 사용하여 인라인 수식 표시
url: /ko/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 Office Math를 사용한 인라인 수식 표시

이 포괄적인 튜토리얼에서는 Aspose.Words for Java의 Office Math 객체를 사용하여 **인라인 수식 표시** 방법을 알아봅니다. 보고서에 **수식 삽입**이 필요하거나 복잡한 수식의 서식을 미세 조정하고 싶을 때, 이 가이드는 Word 문서를 로드하는 단계부터 최종 결과를 저장하는 단계까지 모든 과정을 상세히 안내합니다.

## Quick Answers
- **“display math inline”이란 무엇인가요?** 수식이 별도의 줄이 아니라 텍스트 흐름 안에 나타납니다.  
- **수식 객체를 나타내는 클래스는?** Aspose.Words API의 `OfficeMath`.  
- **정렬을 변경할 수 있나요?** 예, `setJustification`을 사용하여 LEFT, CENTER, RIGHT 중 선택할 수 있습니다.  
- **이 기능에 라이선스가 필요한가요?** 프로덕션 환경에서는 유효한 Aspose.Words for Java 라이선스가 필요합니다.  
- **데모에 사용된 버전은?** 최신 Aspose.Words for Java 릴리스(2026)와 호환됩니다.

## What is “display math inline”?
인라인 수식 표시란 수식이 단락 텍스트의 일부로 취급되어 주변 단어와 자연스럽게 줄 바꿈되는 것을 의미합니다. 읽기 흐름을 끊지 않아야 하는 짧은 수식에 적합합니다.

## Why use Office Math objects in Aspose.Words for Java?
- **정밀한 제어**: 수식 레이아웃을 인라인 또는 디스플레이 형태로 정확히 지정 가능.  
- **프로그래밍 방식 조작**: Word를 직접 열지 않고도 수식을 다룰 수 있음.  
- **플랫폼 간 일관된 렌더링**: 자동화된 보고서 생성에 최적.

## Prerequisites
시작하기 전에 다음을 준비하세요:

- 프로젝트에 Aspose.Words for Java가 설치되고 참조되어 있어야 합니다.  
- Office Math 수식이 포함된 Word 파일(예: `OfficeMath.docx`).  
- 평가 모드가 아닌 경우 유효한 라이선스 파일.

## Step‑by‑Step Guide

### Load the Document
먼저 작업하려는 Office Math 수식이 들어 있는 문서를 로드합니다:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Access the Office Math Object
문서에서 첫 번째 Office Math 노드를 가져옵니다:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Set Display Type (Inline vs. Display)
수식이 주변 텍스트와 인라인으로 표시될지, 별도 줄에 표시될지를 제어합니다. **인라인 수식 표시**를 위해서는 `INLINE` 열거형을, 별도 줄을 원한다면 `DISPLAY`를 사용합니다:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*수식을 인라인으로 유지하려면 `DISPLAY`를 `INLINE`으로 교체하세요.*

### Set Justification
수식의 정렬을 조정합니다. 아래 예시는 왼쪽 정렬이며, `CENTER` 또는 `RIGHT`도 선택 가능합니다:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Save the Modified Document
마지막으로 변경 내용을 새로운 파일에 저장합니다:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Complete Source Code for Using Office Math Objects in Aspose.Words for Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Common Issues & Troubleshooting
- **수식을 찾을 수 없음:** 문서에 실제로 Office Math 객체가 포함되어 있는지 확인하세요. 없으면 `doc.getChild`가 `null`을 반환합니다.  
- **Display type이 적용되지 않음:** 최신 버전의 Aspose.Words를 사용하고 있는지 확인하세요. 오래된 릴리스에서는 `OfficeMathDisplayType` 지원이 제한될 수 있습니다.  
- **라이선스 예외:** 라이선스 오류가 발생하면 `Document` 인스턴스를 만들기 전에 라이선스 파일이 올바르게 로드되었는지 다시 확인하세요.

## Frequently Asked Questions

**Q: Aspose.Words for Java에서 Office Math 객체의 목적은 무엇인가요?**  
A: Office Math 객체를 사용하면 수식을 프로그래밍 방식으로 표현하고 조작할 수 있어, 표시 및 서식에 대한 완전한 제어가 가능합니다.

**Q: 문서 내에서 Office Math 수식의 정렬을 다르게 할 수 있나요?**  
A: 예, `setJustification` 메서드를 사용해 왼쪽, 오른쪽, 가운데 정렬을 선택할 수 있습니다.

**Q: 복잡한 수학 문서를 처리하는 데 Aspose.Words for Java가 적합한가요?**  
A: 물론입니다. 라이브러리는 복잡한 수식, 중첩 분수, 행렬 등 다양한 수학 표현을 완벽히 지원합니다.

**Q: Aspose.Words for Java에 대해 더 알아보고 싶다면?**  
A: 포괄적인 문서와 다운로드는 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)에서 확인하세요.

**Q: Aspose.Words for Java를 어디서 다운로드할 수 있나요?**  
A: 다음 사이트에서 다운로드할 수 있습니다: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Last Updated:** 2026-02-14  
**Tested With:** Aspose.Words for Java 24.12 (latest as of Feb 2026)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}