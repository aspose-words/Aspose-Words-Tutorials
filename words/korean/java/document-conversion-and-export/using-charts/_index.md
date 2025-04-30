---
"description": "Aspose.Words for Java에서 차트를 만들고 사용자 지정하는 방법을 알아보세요. 데이터 시각화를 위한 차트 유형, 서식 및 축 속성을 살펴보세요."
"linktitle": "차트 사용"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 차트 사용하기"
"url": "/ko/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 차트 사용하기


## Aspose.Words for Java에서 차트 사용 소개

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 차트를 만드는 방법을 살펴보겠습니다. 다양한 유형의 차트를 만들고, 축 속성을 사용자 정의하고, 데이터 레이블을 서식 지정하는 방법 등을 배우게 됩니다. 시작해 볼까요!

## 선형 차트 만들기

선형 차트를 만들려면 다음 코드를 사용하세요.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// 기본으로 생성된 시리즈를 삭제합니다.
chart.getSeries().clear();

// 데이터와 데이터 레이블이 있는 시리즈를 추가합니다.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// 또는 소스 셀에 형식 코드를 연결합니다.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## 다른 유형의 차트 만들기

비슷한 기법을 사용하여 세로 막대형, 영역형, 거품형, 분산형 등 다양한 유형의 차트를 만들 수 있습니다. 간단한 세로 막대형 차트를 삽입하는 예시는 다음과 같습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// 기본으로 생성된 시리즈를 삭제합니다.
chart.getSeries().clear();

// 카테고리를 만들고 데이터를 추가합니다.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## 축 속성 사용자 정의

축 유형 변경, 눈금 설정, 레이블 서식 지정 등 축 속성을 사용자 지정할 수 있습니다. 다음은 XY 축 속성을 정의하는 예입니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// 기본 시리즈를 지우고 데이터를 추가하세요.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// 날짜 대신 범주를 X축으로 변경하세요.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Y축의 표시 단위(백)로 측정됩니다.
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

## 데이터 레이블 서식 지정

데이터 레이블의 서식을 다양한 숫자 형식으로 지정할 수 있습니다. 예를 들어 다음과 같습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// 기본 시리즈를 지우고 데이터를 추가하세요.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 추가 차트 사용자 정의

경계, 레이블 간 간격 단위, 차트 축 숨기기 등을 조정하여 차트를 더욱 세부적으로 사용자 지정할 수 있습니다. 제공된 코드 조각을 통해 이러한 옵션에 대해 자세히 알아보세요.

## 결론

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 차트를 만드는 방법을 살펴보았습니다. 다양한 유형의 차트를 만들고, 축 속성을 사용자 정의하고, 데이터 레이블을 서식 지정하는 방법 등을 알아보았습니다. Aspose.Words for Java는 문서에 데이터를 시각적으로 표현하여 정보를 표현하는 방식을 향상시키는 강력한 도구를 제공합니다.

## 자주 묻는 질문

### 차트에 여러 시리즈를 추가하려면 어떻게 해야 하나요?

차트에 여러 시리즈를 추가하려면 다음을 사용하십시오. `chart.getSeries().add()` 메서드입니다. 시리즈 이름, 범주 및 데이터 값을 반드시 지정하세요.

### 사용자 지정 숫자 서식을 사용하여 데이터 레이블을 어떻게 서식 지정할 수 있나요?

데이터 레이블을 형식화하려면 다음을 수행하세요. `DataLabels` 시리즈의 속성 및 원하는 형식 코드 설정 `getNumberFormat().setFormatCode()`.

### 차트의 축 속성을 사용자 지정하려면 어떻게 해야 하나요?

축 속성(유형, 눈금 표시, 레이블 등)을 사용자 정의하려면 다음을 수행하세요. `ChartAxis` 같은 속성 `setCategoryType()`, `setCrosses()`, 그리고 `setMajorTickMark()`.

### 산점형 차트나 영역형 차트 등 다른 유형의 차트는 어떻게 만들 수 있나요?

적절한 차트 유형을 지정하여 다양한 차트 유형을 만들 수 있습니다. `ChartType` 차트를 삽입할 때 `builder.insertChart(ChartType.TYPE, width, height)`.

### 차트 축을 숨기려면 어떻게 해야 하나요?

차트 축을 설정하여 숨길 수 있습니다. `setHidden(true)` 축의 속성.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}