---
date: 2026-02-01
description: Aspose.Words for Java를 사용하여 표를 서식 지정하고, 표 스타일을 적용하며, 표 테두리를 설정하고, 표를
  자동 맞춤하는 방법을 배웁니다. 이 가이드는 전문적인 스타일링으로 Word 표를 만드는 과정을 안내합니다.
linktitle: Formatting Tables and Table Styles
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용한 표 서식 지정 및 표 스타일 적용 방법
url: /ko/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용한 표 서식 지정 및 표 스타일 적용 방법

## 소개

Word 문서에서 **표 서식 지정 방법**이 필요할 때, Aspose.Words for Java는 표를 프로그래밍 방식으로 생성, 스타일 지정 및 미세 조정할 수 있는 완전한 도구 세트를 제공합니다. 간단한 보고서든 복잡한 인보이스든, 표 서에서는 표 테두리 설정, 셀 색상 적용, 자동 맞춤 표 기능 사용, 사전 정의된 표 스타일 적용 방법을 쉬운 Java 코드와 함께 배웁니다.

## 빠른 답변
 `DocumentBuilder`는 표를 만들고 채우는 데 사용됩니다.  
- **전체 표에 테두리를 설정하려면 어떻게 하나요?** `table.setBorders(LineStyle.SINGLE, thickness, Color)`를 사용합니다.  
- **내장 스타일을 적용할 수 있나요?** 예, `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`를 호출합니다.  
- **열을 자동 크기 조정하는 메서드는 무엇인가요?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **조건부 서식 지정이 가능한가요?** 코드에서 조건에 따라 셀 색상이나 테두리를 프로그래밍 방식으로 변경할 수 있습니다.

## Aspose.Words에서 표 서식 지정이란?

표 서식 지정은 시각적 속성(테두리, 색상, 셀 여백 및 전체 스타일)을 정의하여 표가 깔끔하게 보이고 문서의 디자인 언어와 일치하도록 Word 표의 모든 측면을 제어할 수 있습니다.

## 표 스타일을 적용하는 이유

표 스타일을 적용하면 각 속성을 수동으로 설정할 필요가 없습니다. **MEDIUM_SHADING_1_ACCENT_1**과 같은 스타일은 헤더 행, 조건

1. **Java Development Kit (JDK) 8+** – Aspose.Words를 실행하는 데 필요합니다.  
2. **IDE** – IntelliJ IDEA, Eclipse 또는 Java 호환 편집기.  
3. **Aspose.Words for Java 라이브러리** – 최신 버전을 [here](https://releases.aspose.com/words/java/)에서 다운로드합니다.  
4. **기본 Java 지식** – 아래 코드 스니펫을 이해하기 위해 필요합니다.

## 패키지 가져오기

시작하려면 Aspose.Words 네임스페이스를 가져옵니다:

```java
import com.aspose.words.*;
```

이 단일 가져오기로 표를 만들고 서식 지정하는 데 필요한 모든 클래스에 접근할 수 있습니다.

## 단계 1: 표 서식 지정

### 문서 로드

먼저 빈 문서를 만들고 콘텐츠 삽입을 도와줄 `DocumentBuilder`를 생성합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 표 만들기 및 서식 지정

이제 표를 만들고 전체 표에 테두리를 설정한 뒤, **표 테두리 설정** 및 **워드 표 만들기** 셀에 서로 다른 배경 색상을 적용하는 방법을 보여줍니다.

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### 셀 테두리 사용자 지정

특정 셀을 강조해야 할 경우, 이전 서식을 지우고 더 두꺼운 테두리를 적용할 수 있습니다.

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### 설명

- **Set Borders:** `table.setBorders`는 전체 표에 2포인트 두께의 단일 선 테두리를 정의합니다.  
- **Cell Shading:** 배경 색상(빨강, 초록보이게 합니다.  
- **Cell Borders 셀을 강조하는 방법을 보여줍니다.

## 단계 2: 표 스타일 적용

### 문서 및 표 만들기

스타일을 적용하기 전에 표에 최소 하나의 행이 있어야 합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### 표 스타일 적용

여기서는 내장 스타일을 적용하고 밴드 행 및 강조된 첫 번째 열과 같은 특정 스타일 옵션을 활성화합니다.

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### 표 데이터 추가

이제 샘플 데이터로 표를 채웁니다. **auto fit table**을 사용하여 열 너비가 자동으로 조정되는 것을 확인하세요.

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### 설명

- **Set Table Style:** `MEDIUM_SHADING_1_ACCENT_1`은 깔끔하고 음영이 적용된 모습을 제공합니다.  
- **Style Options:** 첫 번째 열, 행 밴드 및 첫 번째 행이 자동으로 서식 지정됩니다.  
- **AutoFit:** `AUTO_FIT_TO_CONTENTS`는 표가 포함된 데이터에 따라 크기가 조정되도록 보장합니다.

## 일반적인 문제 및 해결책

| **before** adding rows를 호출하거나 수정 후 builder를 새로 고쳐야 합니다. |
| Shading not applied to merged cells | 색상을 적용하고 `builder.getCellFormat().getShading()`을 사용합니다. |
| Table width exceeds page. |
| Conditional formatting needed | 색상이나 테두리를 적용합니다. |

## 자주 묻는 질문

**Q: 기본 옵션에 포함되지 않은 사용자 정의 표 스타일을 사용할 수 있나요?**  
A: 예, Aspose.Words for Java를 사용하여 표에 사용자 정의 스타일을 정의하고 적용할 수 있습니다. 사용자 정의 스타일 생성에 대한 자세한 내용은 [documentation](https://reference.aspose.com/words/java/)을 확인하세요.

**Q: 표에 조건부 서식을 어떻게 적용할 수 있나요 메서드(예: `setBackgroundPatternColor`, `getBorders().setLineWidth`)를 호출하면 셀을 동적으로 스타일링할 수 있습니다.

**Q: 표에서 병합된 셀을 서식 지정할 수 있나요?**  
A: 물론입니다. `Cell.merge`로 셀을 병합한 후, 결과 셀에 색상이나 테두리를 적용하면 변경 사항이 반영됩니다.

**Q: 표 레이아웃을 동적으로 조정할 수 있나요?**  
A: 예, 셀 너비, 표 너비를 수정하고 런타임에 `autoFit`을 적용하여 콘텐츠나 사용자 입력에 따라 레이아웃을 조정할 수 있습니다.

**Q: 표 서식 지정에 대한 추가 정보를 어디서 얻을 수 있나요?**  
A: 더 깊은 예제와 API 참조는 [Aspose.Words API documentation](https://reference.aspose.com/words/java/)을 방문하세요.

---

**Last Updated:** 2026-02-01  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}