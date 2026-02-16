---
date: 2026-02-16
description: Aspose.Words for Java에서 차트에 여러 시리즈를 추가하고, 축 눈금 표시를 변경하며, 사용자 지정 숫자 형식을
  적용하고, 선형 및 열 차트가 포함된 차트 Word 문서를 생성하는 방법을 배웁니다.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java에서 차트에 여러 시리즈 추가
url: /ko/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 차트에 여러 시리즈 추가하기

## Aspose.Words for Java에서 차트 사용 소개

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 **여러 시리즈를 차트에 추가하는 방법**, 축 눈금 표시를 사용자 지정하고 사용자 정의 숫자 형식을 적용하는 이유, 그리고 차트가 풍부한 Word 문서를 생성하는 방법을 배웁니다. 재무 데이터에 대한 라인 차트이든, 판매 실적에 대한 컬럼 차트이든, 아래 단계들을 따라 프로그래밍 방식으로 차트를 만들고, 스타일을 지정하며, 미세 조정할 수 있습니다.

## 빠른 답변
- **여러 시리즈를 어떻게 추가하나요?** 표시하려는 각 시리즈마다 `chart.getSeries().add(...)`를 사용합니다.  
- **축 눈금 표시를 변경할 수 있나요?** 예 – 축 객체에서 `setMajorTickMark()`와 `setMinorTickMark()`를 사용합니다.  
- **데이터 레이블에 어떤 형식을 적용할 수 있나요?** Excel과 호환되는 모든 숫자 형식, 예: `"$"#,##0.00` 또는 `0.00%`.  
- **지원되는 차트 유형은 무엇인가요?** 라인, 컬럼, 영역, 버블, 스캐터 등 `ChartType`을 통해 다양한 차트를 지원합니다.  
- **프로덕션에서 라이선스가 필요한가요?** 전체 기능을 사용하려면 유효한 Aspose.Words for Java 라이선스가 필요합니다.

## 차트에서 “여러 시리즈 추가”란 무엇인가요?
여러 시리즈를 추가한다는 것은 동일한 차트 영역에 두 개 이상의 데이터 집합을 삽입하여 서로 다른 카테고리나 기간을 나란히 비교할 수 있게 하는 것입니다. 각 시리즈는 자체 라인, 컬럼 또는 마커 집합으로 표시되어 독자에게 보다 풍부한 시각적 스토리를 제공합니다.

## Aspose.Words for Java로 차트 Word 문서를 생성하는 이유
- **전체 제어**: Word를 직접 열지 않고도 차트 유형, 레이아웃, 스타일을 완벽히 제어합니다.  
- **프로그래밍 방식 생성**: 자동 보고 파이프라인에 쉽게 통합됩니다.  
- **크로스‑플랫폼**: Java가 지원되는 모든 환경에서 동작합니다.  
- **풍부한 API**: 축, 데이터 레이블, 숫자 형식 등을 자유롭게 커스터마이징할 수 있습니다.

## 사전 요구 사항
- Java Development Kit (JDK) 8 이상.  
- 프로젝트에 추가된 Aspose.Words for Java 라이브러리 (Maven/Gradle 또는 JAR).  
- 프로덕션용 유효한 Aspose 라이선스 (평가용은 선택 사항).

## 단계별 가이드

### 단계 1: 라인 차트를 만들고 **여러 시리즈 추가**
아래 코드는 라인 차트를 생성하고 기본 시리즈를 제거한 뒤, 사용자 정의 데이터 레이블이 있는 세 개의 서로 다른 시리즈를 추가하는 핵심 코드입니다.

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

> **팁:** `chart.getSeries().add(...)`를 필요에 따라 여러 번 호출하면 **여러 시리즈**를 추가할 수 있습니다 – 각 호출은 동일 차트에 새로운 라인(또는 컬럼 등)을 생성합니다.

### 단계 2: **컬럼 차트 만들기** (create column chart java)
다음 스니펫은 간단한 컬럼 차트를 삽입하는 방법을 보여줍니다. 이는 카테고리를 나란히 비교할 때 유용합니다.

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

### 단계 3: **축 눈금 표시 변경** (change axis tick marks)
X축과 Y축을 커스터마이징하면 가독성이 향상됩니다. 아래 코드는 눈금 표시를 변경하고, 순서를 반전시키며, 사용자 정의 교차점을 설정하는 방법을 보여줍니다.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 단계 4: **사용자 정의 숫자 형식 적용** (apply custom number format)
Excel에서 지원하는 모든 패턴으로 축 숫자나 데이터 레이블을 포맷할 수 있습니다. 아래 예시는 Y축을 천 단위 구분 기호 패턴으로 포맷하는 간결한 예시입니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### 단계 5: 최종 Word 문서 생성 (generate chart word document)
시리즈, 축, 레이블 구성을 마친 후 위 스니펫에 표시된 대로 `doc.save(...)`를 호출하면 됩니다. 생성된 `.docx` 파일에는 완전한 기능을 갖춘 차트가 포함되어 있어 Microsoft Word에서 열고 편집할 수 있습니다.

## 일반적인 사용 사례
- **재무 대시보드** – 매출, 비용, 이익을 나타내는 라인 차트에 여러 시리즈 사용.  
- **판매 보고서** – 지역별 분기 매출을 비교하는 컬럼 차트.  
- **프로젝트 추적** – 시간 경과에 따른 진행 상황을 시각화하는 영역 또는 스캐터 차트.  

## 추가 차트 커스터마이징
기본 기능 외에도 범위 조정, 축 숨기기(`axis.setHidden(true)`), 색상 변경, 레전드 추가 등 다양한 옵션을 사용할 수 있습니다. 전체 옵션 목록은 Aspose.Words for Java API 레퍼런스를 참고하세요.

## 결론
이 가이드에서는 차트에 **여러 시리즈를 추가**하고, 라인 및 컬럼 차트를 만들며, **축 눈금 표시를 변경**하고, **사용자 정의 숫자 형식을 적용**한 뒤, **차트가 풍부한 Word 문서를 생성**하는 방법을 다루었습니다. Aspose.Words for Java를 사용하면 코드‑우선 방식으로 전문적인 데이터 시각화를 문서에 직접 삽입할 수 있는 강력한 도구를 제공합니다.

## 자주 묻는 질문

**Q: 차트에 여러 시리즈를 어떻게 추가하나요?**  
A: 표시하려는 각 시리즈마다 `chart.getSeries().add()`를 호출합니다. 각 호출은 자체 라인, 컬럼 또는 마커 그룹으로 표시되는 새로운 데이터 집합을 생성합니다.

**Q: 데이터 레이블에 사용자 정의 숫자 형식을 어떻게 적용하나요?**  
A: 시리즈의 `DataLabels` 객체에 접근한 뒤 `getNumberFormat().setFormatCode("your pattern")`를 사용합니다. `isLinkedToSource(true)`를 통해 소스 셀에 형식을 연결할 수도 있습니다.

**Q: 축 눈금 표시를 어떻게 변경하나요?**  
A: `ChartAxis`에서 `setMajorTickMark()`와 `setMinorTickMark()`를 사용합니다. 옵션에는 `CROSS`, `INSIDE`, `OUTSIDE`, `NONE` 등이 있습니다.

**Q: 스캐터 차트나 영역 차트와 같은 다른 차트 유형을 만들 수 있나요?**  
A: 예 – `builder.insertChart(...)` 호출 시 원하는 `ChartType`(예: `ChartType.SCATTER`, `ChartType.AREA`)을 지정하면 됩니다.

**Q: 필요 없는 축을 숨기려면 어떻게 하나요?**  
A: 숨기려는 `ChartAxis`에 대해 `axis.setHidden(true)`를 호출합니다.

---

**마지막 업데이트:** 2026-02-16  
**테스트 환경:** Aspose.Words for Java 24.11  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}