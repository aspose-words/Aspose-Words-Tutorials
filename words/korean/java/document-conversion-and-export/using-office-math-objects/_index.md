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

## 빠른 답변
- **“디스플레이 수학 인라인”이란 무엇입니까?** 수식이 별도의 이란의 줄이 아니라 약간의 압축된 내용입니다.
- **수식을 모으는 클래스는?** Aspose.Words API의 `OfficeMath`.
- **정렬을 찾을 수 있습니까?** 예, `setJustification`을 사용하여 LEFT, CENTER, RIGHT 중 선택할 수 있습니다.
- **이 능력에 능력이 필요합니까?** 명상 환경에서는 Aspose.Words for Java 능력이 필요합니다.
- **데모에 사용된 버전은?** 최신 Aspose.Words for Java 릴리스(2026)와 호환됩니다.

## '수학 인라인 표시'란 무엇인가요?
인라인 수식 표시란 수식이 간단한 텍스트의 일부로 취급하여 이웃의 새빨간 줄 바꿈되는 것을 의미합니다. 지루함을 없애기 위해 단기적인 수식에 적합합니다.

## Aspose.Words for Java에서 Office Math 개체를 사용하는 이유는 무엇입니까?
- **정밀한 제어**: 수식어를 인라인 또는 디스플레이 방식으로 정확하게 입력할 수 있습니다.
- **프로그래밍 방식으로 관계**: 단어를 직접적으로 열지할 수 있는 수식을 가질 수 있습니다.
- **플랫폼 간 역할을 하기**:

## 전제조건
시작하기 전에 다음을 준비하세요:

- 프로젝트에 Aspose.Words for Java가 설치되어야 합니다.
- Office Math 수식이 포함된 Word 파일(예: `OfficeMath.docx`).
- 평가가 좋지 않은 경우에는 파일입니다.

## 단계별 가이드

### 문서 로드
먼저 작업하려는 Office Math 수식이 들어 있는 문서를 로드합니다:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Office 수학 객체 접근
문서에서 첫 번째 Office Math 노드를 가져옵니다:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### 표시 유형 설정 (인라인 또는 표시)
수식이 주변 텍스트와 인라인으로 표시될지, 별도 줄에 표시될지를 제어합니다. **인라인 수식 표시**를 위해서는 `INLINE` 열거형을, 별도 줄을 원한다면 `DISPLAY`를 사용합니다:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*수식을 인라인으로 유지하려면 `DISPLAY`를 `INLINE`으로 교체하세요.*

### 정렬 설정
수식의 정렬을 조정합니다. 아래 예시는 왼쪽 정렬이며, `CENTER` 또는 `RIGHT`도 선택 가능합니다:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### 수정된 문서 저장
마지막으로 변경 내용을 새로운 파일에 저장합니다:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Aspose.Words for Java에서 Office 수학 객체를 사용하는 전체 소스 코드

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## 일반적인 문제 및 문제 해결
- **수식을 찾을 수 없음:** 문서에 실제로 Office Math가 포함되어 있는지 확인하세요. 없으면 `doc.getChild`가 `null`을 반환합니다.
- **디스플레이 유형이 적용되지 않습니다:** 최신 버전의 Aspose.Words를 사용하고 있는지 확인하세요. 오래된 출시에서는 `OfficeMathDisplayType` 지원이 제한될 수 있습니다.
- **라이선스 예외:** 인스턴스 오류가 발생하면 `Document`를 생성한 후에 인스턴스 파일을 로드하여 다시 확인하세요.

## 자주 묻는 질문

**Q: Aspose.Words for Java에서 Office Math를 찾는 목적은 무엇입니까?**
A: Office Math를 사용하면 수식을 프로그래밍 방식으로 표현하고 조작할 수 있어 표시 및 서식에 대한 완전한 제어가 가능합니다.

**Q: 문서 내에서 Office Math 수식의 반대를 다르게 할 수 있습니까?**
A: 예, `setJustification` 메서드를 왼쪽, 오른쪽, 나머지를 대신할 수 있습니다.

**Q: 복잡한 수학을 처리하는 데 Aspose.Words for Java가 적합합니까?**
A: 물론입니다. 라이브러리는 많게는 분수, 많게는 많은 수를 표현하는 데 도움이 됩니다.

**Q: Aspose.Words for Java에 대해 더 많은 내용이 있나요?**
A: 전반적인 문서 다운로드는 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)에서 확인하세요.

**Q: Aspose.Words for Java를 다운로드할 수 있나요?**
A: 다음 사이트에서 다운로드할 수 있습니다: [Java용 Aspose.Words 다운로드](https://releases.aspose.com/words/java/).

---

**최종 업데이트:** 2026-02-14
**테스트 대상:** Java 24.12용 Aspose.Words(2026년 2월 최신)
**저자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}