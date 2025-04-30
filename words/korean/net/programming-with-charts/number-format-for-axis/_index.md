---
"description": "Aspose.Words for .NET을 사용하여 차트 축 번호 서식을 지정하는 방법을 단계별 가이드를 통해 알아보세요. 문서의 가독성과 전문성을 손쉽게 높여 보세요."
"linktitle": "차트의 축에 대한 숫자 형식"
"second_title": "Aspose.Words 문서 처리 API"
"title": "차트의 축에 대한 숫자 형식"
"url": "/ko/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 차트의 축에 대한 숫자 형식

## 소개

안녕하세요! 문서에서 차트를 다루다가 축의 숫자 서식을 변경하여 더욱 전문적으로 보이도록 하고 싶었던 적이 있으신가요? 잘 오셨습니다! 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 바로 그런 작업을 하는 방법을 자세히 알아보겠습니다. 이 강력한 라이브러리를 사용하면 Word 문서를 파이 차트처럼 간편하게 관리할 수 있습니다. 오늘은 사용자 지정 숫자 서식을 사용하여 차트 축을 새롭게 꾸며보는 방법을 중점적으로 살펴보겠습니다.

## 필수 조건

시작하기 전에 필요한 모든 것을 준비했는지 확인해 보세요. 간단한 체크리스트는 다음과 같습니다.

- Aspose.Words for .NET: 설치되어 있는지 확인하세요. 설치되어 있지 않으면 [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- .NET Framework: 호환되는 .NET Framework가 설치되어 있는지 확인하세요.
- 개발 환경: Visual Studio와 같은 IDE가 완벽하게 작동합니다.
- C#에 대한 기본 지식: 이를 통해 코딩 예제를 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

먼저 프로젝트에 필요한 네임스페이스를 가져와야 합니다. 이는 집을 짓기 전에 기초를 다지는 것과 같습니다. 코드 파일 맨 위에 다음 using 지시문을 추가하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

이제 이 과정을 간단하고 따라하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: 문서 설정

제목: 문서 초기화

먼저 새 문서와 문서 작성 도구를 만들어야 합니다. 이 단계는 마치 걸작을 시작하기 전에 캔버스와 붓을 준비하는 것과 같다고 생각하시면 됩니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

여기, `dataDir` 는 최종 파일을 저장할 문서 디렉토리의 경로입니다. `Document` 그리고 `DocumentBuilder` Aspose.Words의 클래스로, Word 문서를 만들고 조작하는 데 도움이 됩니다.

## 2단계: 차트 삽입

제목: 문서에 차트 추가

다음으로, 문서에 차트를 추가해 보겠습니다. 여기서 마법이 시작됩니다. 빈 캔버스 역할을 할 세로 막대형 차트를 삽입해 보겠습니다.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

그만큼 `InsertChart` 이 방법은 지정된 유형(이 경우 열)과 크기의 차트를 문서에 삽입합니다.

## 3단계: 차트 시리즈 사용자 지정

제목: 차트에 데이터 채우기

이제 차트에 데이터를 추가해야 합니다. 이 단계는 차트에 의미 있는 정보를 채우는 것과 같습니다.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

여기서는 5개의 데이터 포인트가 포함된 "Aspose Series 1"이라는 새로운 시리즈를 추가합니다. `Series.Clear` 이 방법을 사용하면 새 시리즈를 추가하기 전에 기존 데이터가 모두 제거됩니다.

## 4단계: 축 번호 서식 지정

제목: 축 번호 꾸미기

마지막으로, Y축의 숫자를 더 읽기 쉽게 서식을 지정해 보겠습니다. 이는 마치 작품에 마무리 작업을 하는 것과 같습니다.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

그만큼 `FormatCode` 속성을 사용하면 축의 숫자에 대한 사용자 지정 형식을 설정할 수 있습니다. 이 예에서는 `#,##0` 큰 숫자가 천 단위일 경우 쉼표로 표시합니다.

## 5단계: 문서 저장

제목: 당신의 걸작을 저장하세요

이제 모든 설정이 완료되었으니 문서를 저장할 차례입니다. 이 단계는 작업의 최종 결과물을 공개하는 중요한 단계입니다.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

여기서, `Save` 이 방법은 문서를 지정된 경로에 파일 이름으로 저장합니다. `WorkingWithCharts.NumberFormatForAxis.docx`.

## 결론

자, 이제 Aspose.Words for .NET을 사용하여 차트의 Y축 숫자 서식을 성공적으로 지정했습니다. 이제 차트가 더욱 전문적으로 보일 뿐만 아니라 가독성도 향상됩니다. Aspose.Words는 프로그래밍 방식으로 멋진 Word 문서를 만드는 데 도움이 되는 다양한 기능을 제공합니다. 자, 더 자세히 살펴보고 무엇을 할 수 있는지 확인해 보는 건 어떠세요?

## 자주 묻는 질문

### Aspose.Words for .NET이란 무엇인가요?
Aspose.Words for .NET은 개발자가 Word 문서를 프로그래밍 방식으로 만들고, 조작하고, 변환할 수 있는 강력한 라이브러리입니다.

### 축 번호 외에 차트의 다른 측면도 서식을 지정할 수 있나요?
물론입니다! Aspose.Words for .NET을 사용하면 제목과 레이블의 서식을 지정하고 차트의 모양까지 사용자 지정할 수 있습니다.

### Aspose.Words for .NET에 대한 무료 평가판이 있나요?
네, 당신은 얻을 수 있습니다 [무료 체험은 여기를 클릭하세요](https://releases.aspose.com/).

### C# 외의 다른 .NET 언어와 함께 Aspose.Words for .NET을 사용할 수 있나요?
네, Aspose.Words for .NET은 VB.NET 및 F#을 포함한 모든 .NET 언어와 호환됩니다.

### 더 자세한 문서는 어디에서 찾을 수 있나요?
자세한 문서는 다음에서 확인할 수 있습니다. [.NET 문서 페이지용 Aspose.Words](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}