---
title: 차트에서 단일 차트 데이터 포인트 사용자 정의
linktitle: 차트에서 단일 차트 데이터 포인트 사용자 정의
second_title: Aspose.Words 문서 처리 API
description: 자세한 단계별 가이드에서 Aspose.Words for .NET을 사용하여 단일 차트 데이터 포인트를 사용자 지정하는 방법을 알아보세요. 고유한 마커와 크기로 차트를 강화하세요.
weight: 10
url: /ko/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 차트에서 단일 차트 데이터 포인트 사용자 정의

## 소개

고유한 데이터 포인트로 차트를 돋보이게 하는 방법을 궁금해하신 적이 있나요? 글쎄요, 오늘은 당신의 행운의 날입니다! Aspose.Words for .NET을 사용하여 단일 차트 데이터 포인트를 사용자 지정하는 방법을 알아보겠습니다. 유익할 뿐만 아니라 재미있고 따라하기 쉬운 단계별 튜토리얼을 따라가며 안전띠를 매세요.

## 필수 조건

시작하기에 앞서, 모든 필수 사항이 준비되었는지 확인해 보겠습니다.

-  .NET 라이브러리용 Aspose.Words: 최신 버전을 사용하고 있는지 확인하세요.[여기에서 다운로드하세요](https://releases.aspose.com/words/net/).
- .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
- C#에 대한 기본적인 이해: C# 프로그래밍에 대한 기본적인 이해가 도움이 됩니다.
- 통합 개발 환경(IDE): Visual Studio를 권장합니다.

## 네임스페이스 가져오기

우선, 작업을 시작하기 위해 필요한 네임스페이스를 가져와 보겠습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1단계: Document 및 DocumentBuilder 초기화

좋습니다. 새 문서와 DocumentBuilder를 초기화하여 시작해 보겠습니다. 이것이 차트의 캔버스가 될 것입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 여기,`dataDir` 문서를 저장할 디렉토리 경로입니다.`DocumentBuilder` 클래스는 문서 구성에 도움이 됩니다.

## 2단계: 차트 삽입

다음으로, 문서에 선형 차트를 삽입해 보겠습니다. 이것은 데이터 포인트를 사용자 정의하기 위한 놀이터가 될 것입니다.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 그만큼`InsertChart` 이 방법은 차트 유형, 너비, 높이를 매개변수로 사용합니다. 이 경우 너비가 432이고 높이가 252인 선형 차트를 삽입합니다.

## 3단계: 차트 시리즈에 액세스

이제 차트 내에서 시리즈에 접근할 시간입니다. 차트에는 여러 시리즈가 있을 수 있으며, 각 시리즈에는 데이터 포인트가 포함됩니다.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

여기서는 차트의 처음 두 시리즈에 접근하고 있습니다. 

## 4단계: 데이터 포인트 사용자 지정

마법이 일어나는 곳은 바로 여기입니다! 시리즈 내의 특정 데이터 포인트를 사용자 지정해 보겠습니다.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

우리는 첫 번째 시리즈에서 데이터 포인트를 가져오고 있습니다. 이제 이 포인트를 사용자 지정해 보겠습니다.

### 데이터 포인트 00 사용자 정의

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 을 위한`dataPoint00`, 폭발을 설정하고(파이 차트에 유용함), 마커 기호를 원으로 변경하고, 마커 크기를 15로 설정합니다.

### 데이터 포인트 01 사용자 정의

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 을 위한`dataPoint01`, 마커 기호를 다이아몬드로 바꾸고 마커 크기를 20으로 설정합니다.

### 시리즈 1의 데이터 포인트 사용자 정의

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 세 번째 데이터 포인트의 경우`series1`값이 음수이면 반전시키고, 마커 기호를 별표로 바꾸고, 마커 크기를 20으로 설정합니다.

## 5단계: 문서 저장

마지막으로 모든 사용자 정의 내용을 담은 문서를 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 이 줄은 지정된 디렉토리에 문서를 이름으로 저장합니다.`WorkingWithCharts.SingleChartDataPoint.docx`.

## 결론

이제 Aspose.Words for .NET을 사용하여 차트의 개별 데이터 포인트를 성공적으로 사용자 지정했습니다. 몇 가지 속성을 조정하면 차트를 훨씬 더 유익하고 시각적으로 매력적으로 만들 수 있습니다. 그러니 계속해서 다양한 마커와 크기를 실험하여 데이터에 가장 적합한 것이 무엇인지 확인하세요.

## 자주 묻는 질문

### 다른 유형의 차트에서 데이터 포인트를 사용자 정의할 수 있나요?

물론입니다! 막대 차트, 파이 차트 등 다양한 차트 유형에서 데이터 포인트를 사용자 지정할 수 있습니다. 이 프로세스는 다른 차트 유형에서도 비슷합니다.

### 데이터 포인트에 사용자 정의 라벨을 추가할 수 있나요?

 예, 다음을 사용하여 데이터 포인트에 사용자 정의 레이블을 추가할 수 있습니다.`ChartDataPoint.Label` 속성. 이를 통해 각 데이터 포인트에 대한 더 많은 컨텍스트를 제공할 수 있습니다.

### 시리즈에서 데이터 포인트를 제거하려면 어떻게 해야 하나요?

 다음을 사용하여 데이터 포인트의 가시성을 false로 설정하여 데이터 포인트를 제거할 수 있습니다.`dataPoint.IsVisible = false`.

### 이미지를 데이터 포인트의 마커로 사용할 수 있나요?

Aspose.Words에서는 이미지를 직접 마커로 사용할 수는 없지만, 사용자 정의 모양을 만들어 마커로 사용할 수 있습니다.

### 차트의 데이터 포인트에 애니메이션을 적용할 수 있나요?

Aspose.Words for .NET은 차트 데이터 포인트에 대한 애니메이션을 지원하지 않습니다. 그러나 다른 도구를 사용하여 애니메이션 차트를 만들고 Word 문서에 임베드할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
