---
title: 차트 축에 날짜 시간 값 추가
linktitle: 차트 축에 날짜 시간 값 추가
second_title: Aspose.Words 문서 처리 API
description: 이 포괄적인 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 차트 축에 날짜 및 시간 값을 추가하는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 차트 축에 날짜 시간 값 추가

## 소개

문서에서 차트를 만드는 것은 데이터를 시각화하는 강력한 방법이 될 수 있습니다. 시계열 데이터를 다룰 때 차트의 축에 날짜 및 시간 값을 추가하는 것은 명확성을 위해 매우 중요합니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 차트의 축에 날짜 및 시간 값을 추가하는 과정을 안내해 드리겠습니다. 이 단계별 가이드는 환경을 설정하고, 코드를 작성하고, 프로세스의 각 부분을 이해하는 데 도움이 됩니다. 시작해 볼까요!

## 필수 조건

시작하기 전에 다음과 같은 전제 조건이 충족되었는지 확인하세요.

1. Visual Studio나 .NET IDE: .NET 코드를 작성하고 실행하려면 개발 환경이 필요합니다.
2.  Aspose.Words for .NET: Aspose.Words for .NET 라이브러리가 설치되어 있어야 합니다. 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
3. C#에 대한 기본 지식: 이 튜토리얼에서는 사용자가 C# 프로그래밍에 대한 기본적인 이해가 있다고 가정합니다.
4.  유효한 Aspose 라이센스: 다음에서 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.aspose.com/temporary-license/).

## 네임스페이스 가져오기

시작하려면 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요. 이 단계는 Aspose.Words 클래스와 메서드에 액세스하는 데 중요합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1단계: 문서 디렉토리 설정

먼저, 문서를 저장할 디렉토리를 정의해야 합니다. 이는 파일을 구성하고 코드가 올바르게 실행되는 데 중요합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 새 문서 및 DocumentBuilder 만들기

 다음으로, 새 인스턴스를 만듭니다.`Document` 클래스와`DocumentBuilder` 객체. 이러한 객체는 문서를 빌드하고 조작하는 데 도움이 됩니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3단계: 문서에 차트 삽입

 이제 다음을 사용하여 문서에 차트를 삽입하세요.`DocumentBuilder` 객체. 이 예에서는 막대형 차트를 사용하지만 다른 유형도 선택할 수 있습니다.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 4단계: 기존 시리즈 지우기

차트에서 기존 시리즈를 지워서 빈 슬레이트로 시작하도록 합니다. 이 단계는 사용자 지정 데이터에 필수적입니다.

```csharp
chart.Series.Clear();
```

## 5단계: 시리즈에 날짜 및 시간 값 추가

차트 시리즈에 날짜 및 시간 값을 추가합니다. 이 단계에서는 날짜 및 해당 값에 대한 배열을 만드는 것이 포함됩니다.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## 6단계: X축 구성

X축에 대한 스케일링과 눈금을 설정합니다. 이렇게 하면 날짜가 올바르게 적절한 간격으로 표시됩니다.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## 7단계: 문서 저장

마지막으로, 문서를 지정된 디렉토리에 저장합니다. 이 단계에서 프로세스가 완료되고, 이제 문서에는 X축에 날짜 및 시간 값이 있는 차트가 포함되어야 합니다.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## 결론

Aspose.Words for .NET을 사용하면 문서의 차트 축에 날짜 및 시간 값을 추가하는 것은 간단한 프로세스입니다. 이 튜토리얼에 설명된 단계를 따르면 시계열 데이터를 효과적으로 시각화하는 명확하고 유익한 차트를 만들 수 있습니다. 보고서, 프레젠테이션 또는 자세한 데이터 표현이 필요한 문서를 준비하든 Aspose.Words는 성공하는 데 필요한 도구를 제공합니다.

## 자주 묻는 질문

### Aspose.Words for .NET에서 다른 차트 유형을 사용할 수 있나요?

네, Aspose.Words는 선형, 막대형, 원형 등 다양한 차트 유형을 지원합니다.

### 차트의 모양을 어떻게 사용자 지정할 수 있나요?

차트의 속성에 액세스하여 스타일, 색상 등을 설정하여 모양을 사용자 지정할 수 있습니다.

### 차트에 여러 시리즈를 추가할 수 있나요?

 물론입니다! 다음을 호출하여 차트에 여러 시리즈를 추가할 수 있습니다.`Series.Add` 다른 데이터로 여러 번 방법을 변경합니다.

### 차트 데이터를 동적으로 업데이트해야 하는 경우에는 어떻게 해야 하나요?

요구 사항에 맞게 시리즈 및 축 속성을 프로그래밍 방식으로 조작하여 차트 데이터를 동적으로 업데이트할 수 있습니다.

### Aspose.Words for .NET에 대한 더 자세한 문서는 어디에서 찾을 수 있나요?

 더 자세한 문서를 찾을 수 있습니다[여기](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
