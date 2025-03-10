---
title: Word 문서에 산점도 삽입
linktitle: Word 문서에 산점도 삽입
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word에 산점도를 삽입하는 방법을 알아보세요. 시각적 데이터 표현을 문서에 통합하기 위한 간단한 단계입니다.
weight: 10
url: /ko/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 산점도 삽입

## 소개

이 튜토리얼에서는 Aspose.Words for .NET을 활용하여 Word 문서에 산점도를 삽입하는 방법을 알아봅니다. 산점도는 두 변수에 따라 데이터 포인트를 효과적으로 표시할 수 있는 강력한 시각적 도구로, 문서를 더욱 매력적이고 유익하게 만들어줍니다.

## 필수 조건

Aspose.Words for .NET을 사용하여 산점 차트를 만드는 단계로 들어가기 전에 다음 필수 구성 요소가 있는지 확인하세요.

1.  Aspose.Words for .NET 설치: Aspose.Words for .NET을 다운로드하여 설치하세요.[여기](https://releases.aspose.com/words/net/).
   
2. C#에 대한 기본 지식: C# 프로그래밍 언어와 .NET 프레임워크에 대한 지식이 있으면 좋습니다.

## 네임스페이스 가져오기

시작하려면 C# 프로젝트에 필요한 네임스페이스를 가져와야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

이제 Aspose.Words for .NET을 사용하여 Word 문서에 산점도를 삽입하는 과정을 살펴보겠습니다.

## 1단계: Document 및 DocumentBuilder 초기화

 먼저 새 인스턴스를 초기화합니다.`Document` 수업과`DocumentBuilder` 문서 작성을 시작하는 클래스입니다.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 산점도 삽입

 사용하세요`InsertChart` 의 방법`DocumentBuilder` 문서에 산점도를 삽입하는 클래스입니다.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## 3단계: 차트에 데이터 시리즈 추가

이제 분산형 차트에 데이터 시리즈를 추가합니다. 이 예는 특정 데이터 포인트가 있는 시리즈를 추가하는 것을 보여줍니다.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## 4단계: 문서 저장

 마지막으로, 다음을 사용하여 수정된 문서를 원하는 위치에 저장합니다.`Save` 의 방법`Document` 수업.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서에 산점도를 삽입하는 방법을 성공적으로 배웠습니다. 산점도는 데이터 관계를 시각화하는 데 탁월한 도구이며 Aspose.Words를 사용하면 문서에 손쉽게 통합하여 명확성과 이해도를 높일 수 있습니다.

## 자주 묻는 질문

### Aspose.Words를 사용하여 산점도의 모양을 사용자 정의할 수 있나요?
네, Aspose.Words를 사용하면 색상, 축, 레이블 등 차트 속성을 광범위하게 사용자 지정할 수 있습니다.

### Aspose.Words는 다양한 버전의 Microsoft Word와 호환됩니까?
Aspose.Words는 다양한 버전의 Microsoft Word를 지원하여 플랫폼 간 호환성을 보장합니다.

### Aspose.Words는 다른 유형의 차트를 지원합니까?
네, Aspose.Words는 막대형 차트, 선형 차트, 원형 차트 등 다양한 차트 유형을 지원합니다.

### 프로그래밍 방식으로 분산형 차트의 데이터를 동적으로 업데이트할 수 있습니까?
물론입니다. Aspose.Words API 호출을 사용하여 차트 데이터를 동적으로 업데이트할 수 있습니다.

### Aspose.Words에 대한 추가 도움이나 지원은 어디에서 받을 수 있나요?
 추가 지원이 필요하면 다음을 방문하세요.[Aspose.Words 지원 포럼](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
