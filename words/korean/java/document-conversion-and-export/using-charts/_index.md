---
date: 2025-12-13
description: Aspose.Words for Java를 사용하여 열 차트를 만들고 차트 데이터 레이블을 서식 지정하는 방법을 배웁니다. 여러
  시리즈 추가, 축 유형 변경 및 차트 축 숨기기를 탐색합니다.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 열 차트 만드는 방법
url: /ko/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 열 차트 만들기

이 튜토리얼에서는 Aspose.Words for Java를 사용해 Word 문서 안에 **열 차트** 시각화를 직접 생성합니다. 다양한 차트 유형 만들기, 여러 시리즈 추가, 차트 데이터 레이블 서식 지정, 축 유형 변경, 필요에 따라 차트 축을 숨겨 깔끔하게 보이게 하는 방법을 단계별로 안내합니다. 마지막까지 따라하면 문서에 풍부한 차트를 삽입할 수 있는 실무 수준의 방법을 익히게 됩니다.

## 빠른 답변
- **차트를 만들기 위한 기본 클래스는?** `DocumentBuilder`와 `insertChart`.
- **새 시리즈를 추가하는 메서드는?** `chart.getSeries().add(...)`.
- **차트 데이터 레이블을 어떻게 서식 지정하나요?** `getDataLabels().get(...).getNumberFormat().setFormatCode(...)` 사용.
- **축을 숨길 수 있나요?** 네, 축 객체에 `setHidden(true)`를 호출하면 됩니다.
- **Aspose.Words에 라이선스가 필요합니까?** 프로덕션 사용 시 라이선스가 필요하며, 무료 체험판을 제공하고 있습니다.

## 열 차트란 무엇이며 왜 사용하나요?

열 차트는 범주형 데이터를 수직 막대로 표시하여 그룹 간 값을 비교하기에 적합합니다(예: 지역별 매출, 월별 지출 등). Java 애플리케이션에서 Aspose.Words를 사용해 열 차트를 생성하면 Excel이나 외부 도구 없이도 Word / DOCX 파일에 직접 시각화를 삽입할 수 있습니다.

## 열 차트 만들기

아래는 간단한 열 차트를 생성하는 예제입니다. 원본 코드와 동일하며 이해를 돕기 위해 설명 주석만 추가했습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### 여러 시리즈 추가

`chart.getSeries().add(...)`를 반복 호출하면 **여러 시리즈**를 열 차트에 추가할 수 있습니다. 각 시리즈는 자체 카테고리와 값을 가질 수 있어 여러 데이터 세트를 나란히 비교할 수 있습니다.

## 사용자 지정 데이터 레이블이 있는 선 차트 만들기

열 차트 대신 선 차트가 필요하다면 동일한 패턴을 적용하면 됩니다. 이 예제는 **차트 데이터 레이블 서식 지정**을 다양한 숫자 형식으로 적용하는 방법도 보여줍니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### 데이터 레이블 추가

`series1.hasDataLabels(true)` 호출은 시리즈에 **데이터 레이블**을 추가하고, `setShowValue(true)`는 차트에 실제 값을 표시합니다.

## 축 유형 변경 및 축 속성 사용자 지정

축 유형을 변경(예: 날짜 축에서 범주 축으로)하면 데이터 포인트가 표시되는 방식을 제어할 수 있습니다. 또한 **차트 축 숨기기**를 통해 미니멀리즘 디자인을 구현하는 방법도 포함되어 있습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 축 유형 변경

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **축 유형**을 날짜 기반 축에서 범주형 축으로 바꾸어 레이블 배치를 자유롭게 제어할 수 있습니다.

## 차트 데이터 레이블 서식 지정(숫자 형식)

축이나 데이터 레이블에 직접 숫자 서식을 적용할 수 있습니다. 이 예제는 Y축 숫자를 천 단위 구분 기호가 포함된 형식으로 포맷합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 추가 차트 사용자 지정

기본 기능 외에도 차트 경계 조정, 레이블 간 간격 단위 설정, 특정 축 숨기기 등 다양한 옵션을 활용할 수 있습니다. 전체 속성 목록은 Aspose.Words for Java API 문서를 참고하세요.

## 자주 묻는 질문

**Q: 차트에 여러 시리즈를 어떻게 추가하나요?**  
A: 표시하려는 각 시리즈마다 `chart.getSeries().add()`를 사용합니다. 각 호출에 고유한 이름, 카테고리 배열, 값 배열을 전달할 수 있습니다.

**Q: 사용자 지정 숫자 형식으로 차트 데이터 레이블을 어떻게 서식 지정하나요?**  
A: 시리즈의 `DataLabels` 객체에 접근한 뒤 `getNumberFormat().setFormatCode("your format")`을 호출합니다. `isLinkedToSource(true)`를 사용해 형식을 원본 셀에 연결할 수도 있습니다.

**Q: 차트 축을 숨기려면 어떻게 하나요?**  
A: 숨기려는 `ChartAxis`에 `setHidden(true)`를 호출합니다(예: `chart.getAxisY().setHidden(true)`).

**Q: 축 유형을 가장 효율적으로 변경하는 방법은?**  
A: 범주형 축은 `setCategoryType(AxisCategoryType.CATEGORY)`, 날짜 축은 `AxisCategoryType.DATE`를 사용합니다.

**Q: 시리즈에 데이터 레이블을 추가하려면?**  
A: `series.hasDataLabels(true)`로 활성화한 뒤 `series.getDataLabels().setShowValue(true)`로 표시 여부를 설정합니다.

## 결론

Aspose.Words for Java를 사용해 **열 차트** 시각화를 만드는 모든 과정을 살펴보았습니다. 기본 차트 삽입, 여러 시리즈 추가, 차트 데이터 레이블 서식 지정, 축 유형 변경, 차트 축 숨기기 등을 통해 깔끔하고 전문적인 데이터 기반 Word 문서를 만들 수 있습니다. 이러한 기술을 보고서나 문서 자동 생성 파이프라인에 적용해 보세요.

---

**마지막 업데이트:** 2025-12-13  
**테스트 환경:** Aspose.Words for Java 24.12 (최신)  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}