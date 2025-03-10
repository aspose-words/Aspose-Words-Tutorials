---
title: Shape를 사용하여 차트 만들기 및 사용자 지정
linktitle: Shape를 사용하여 차트 만들기 및 사용자 지정
second_title: Aspose.Words 문서 처리 API
description: 이 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 차트를 만들고 사용자 지정하는 방법을 알아보세요. 데이터 시각화에 완벽합니다.
weight: 10
url: /ko/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Shape를 사용하여 차트 만들기 및 사용자 지정

## 소개

문서에서 차트를 만들고 사용자 지정하는 것은 오늘날의 데이터 중심 세계에서 중요한 기술입니다. 차트는 데이터를 시각화하여 복잡한 정보를 더 쉽게 이해할 수 있도록 도와줍니다. Aspose.Words for .NET은 Word 문서를 프로그래밍 방식으로 만들고 조작할 수 있는 강력한 라이브러리입니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 선형 차트를 만들고 사용자 지정하는 과정을 안내합니다. 이 가이드를 마치면 전문가 수준의 차트를 쉽게 만들 수 있습니다.

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

-  Aspose.Words for .NET 라이브러리: 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- Visual Studio: .NET을 지원하는 모든 버전.
- C#에 대한 기본 지식: C#의 기본을 이해하면 튜토리얼을 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

시작하려면 필요한 네임스페이스를 가져와야 합니다. 이 단계는 Aspose.Words for .NET에서 제공하는 클래스와 메서드를 사용할 수 있게 해주므로 필수적입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1단계: 새 문서 만들기

먼저, 새로운 Word 문서를 만들어야 합니다. 이 문서는 차트의 캔버스 역할을 할 것입니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 차트 삽입

 다음으로, 문서에 선형 차트를 삽입합니다.`DocumentBuilder.InsertChart` 이 목적을 위해서는 다음 방법이 사용됩니다.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## 3단계: 차트 제목 사용자 지정

차트 제목을 사용자 지정하면 표시되는 데이터에 대한 컨텍스트를 제공하는 데 도움이 될 수 있습니다. 다음 코드를 사용하여 제목을 표시하고 텍스트를 설정할 수 있습니다.

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// 제목 텍스트에 null이나 빈 값을 지정하면 자동 생성된 제목이 표시됩니다.
```

## 4단계: 범례 위치 조정

범례는 차트에서 다양한 데이터 시리즈를 식별하는 데 도움이 됩니다. 다음과 같이 위치 및 오버레이 설정을 사용자 지정할 수 있습니다.

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## 5단계: 문서 저장

마지막으로 문서를 저장해야 합니다. 이 단계는 모든 변경 사항이 파일에 기록되도록 보장합니다.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## 결론

이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에서 선형 차트를 만들고 사용자 지정하는 방법을 다루었습니다. 단계별 가이드를 따르면 이제 데이터를 효과적으로 전달하는 시각적으로 매력적인 차트를 만들 수 있습니다. Aspose.Words for .NET은 광범위한 사용자 지정 옵션을 제공하여 차트를 특정 요구 사항에 맞게 조정할 수 있습니다.

## 자주 묻는 질문

### Aspose.Words for .NET을 사용하여 다른 유형의 차트를 만들 수 있나요?

 네, Aspose.Words for .NET은 막대형 차트, 원형 차트 등 다양한 차트 유형을 지원합니다. 설명서를 탐색할 수 있습니다.[여기](https://reference.aspose.com/words/net/) 자세한 내용은.

### 구매하기 전에 Aspose.Words for .NET을 어떻게 사용할 수 있나요?

 무료 평가판은 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/). 이를 통해 구매하기 전에 라이브러리와 기능을 테스트해 볼 수 있습니다.

### 문제가 발생하면 지원을 받을 수 있는 방법이 있나요?

 물론입니다. Aspose 커뮤니티 포럼을 통해 지원을 받을 수 있습니다.[여기](https://forum.aspose.com/c/words/8)커뮤니티와 Aspose 직원은 매우 반응이 좋습니다.

### Aspose.Words for .NET 라이선스를 어떻게 구매합니까?

 Aspose 웹사이트에서 직접 라이센스를 구매할 수 있습니다.[여기](https://purchase.aspose.com/buy)다양한 요구 사항에 맞는 다양한 라이센싱 옵션이 있습니다.

### 단기 프로젝트를 위해 임시 라이센스가 필요한 경우 어떻게 해야 합니까?

 Aspose에서는 요청할 수 있는 임시 라이센스를 제공합니다.[여기](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
