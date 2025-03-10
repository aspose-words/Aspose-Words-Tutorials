---
title: 차트의 데이터 레이블 번호 형식 지정
linktitle: 차트의 데이터 레이블 번호 형식 지정
second_title: Aspose.Words 문서 처리 API
description: 이 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 차트에서 데이터 레이블을 서식 지정하는 방법을 알아보세요. Word 문서를 손쉽게 개선하세요.
weight: 10
url: /ko/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 차트의 데이터 레이블 번호 형식 지정

## 소개

매력적이고 유익한 문서를 만드는 데는 종종 잘 포맷된 데이터 레이블이 있는 차트를 포함하는 것이 포함됩니다. 정교한 차트로 Word 문서를 향상시키고자 하는 .NET 개발자라면 Aspose.Words for .NET이 이를 달성하는 데 도움이 되는 환상적인 라이브러리입니다. 이 튜토리얼은 Aspose.Words for .NET을 사용하여 차트에서 숫자 레이블을 포맷하는 과정을 단계별로 안내합니다.

## 필수 조건

코드를 살펴보기 전에 꼭 갖춰야 할 몇 가지 전제 조건이 있습니다.

-  Aspose.Words for .NET: Aspose.Words for .NET 라이브러리가 설치되어 있는지 확인하세요. 아직 설치하지 않았다면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: .NET 개발 환경을 설정해야 합니다. Visual Studio를 적극 권장합니다.
- C#에 대한 기본 지식: 이 튜토리얼은 C# 코드를 작성하고 이해하는 것을 포함하므로 C# 프로그래밍에 대한 지식이 필수적입니다.
-  임시 라이센스: Aspose.Words를 아무런 제한 없이 사용하려면 다음을 얻을 수 있습니다.[임시 면허](https://purchase.aspose.com/temporary-license/).

이제 차트의 숫자 라벨 서식을 지정하는 단계별 과정을 살펴보겠습니다.

## 네임스페이스 가져오기

우선, Aspose.Words for .NET에서 작업하는 데 필요한 네임스페이스를 가져와야 합니다. C# 파일의 맨 위에 다음 줄을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1단계: 문서 디렉토리 설정

Word 문서를 조작하기 전에 문서를 저장할 디렉토리를 지정해야 합니다. 이는 나중에 저장 작업을 위해 필수적입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 문서 디렉토리의 실제 경로를 포함합니다.

## 2단계: Document 및 DocumentBuilder 초기화

 다음 단계는 새 것을 초기화하는 것입니다`Document` 그리고`DocumentBuilder` . 그`DocumentBuilder` 문서의 내용을 구성할 수 있는 도우미 클래스입니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3단계: 문서에 차트 삽입

 이제 다음을 사용하여 문서에 차트를 삽입해 보겠습니다.`DocumentBuilder`이 튜토리얼에서는 선형 차트를 예로 들어보겠습니다.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

여기서는 특정 너비와 높이를 가진 선형 차트를 삽입하고 차트 제목을 설정합니다.

## 4단계: 기본 시리즈 지우기 및 새 시리즈 추가

기본적으로 차트에는 미리 생성된 시리즈가 있습니다. 이를 지우고 특정 데이터 포인트가 있는 자체 시리즈를 추가해야 합니다.

```csharp
// 기본 생성된 시리즈를 삭제합니다.
chart.Series.Clear();

// 사용자 정의 데이터 포인트로 새로운 시리즈를 추가합니다.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## 5단계: 데이터 레이블 활성화

차트에 데이터 레이블을 표시하려면 시리즈에 대해 데이터 레이블을 활성화해야 합니다.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## 6단계: 데이터 레이블 서식 지정

이 튜토리얼의 핵심은 데이터 레이블을 포맷하는 것입니다. 각 데이터 레이블에 개별적으로 다른 숫자 포맷을 적용할 수 있습니다.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // 통화 형식
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // 날짜 형식
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // 백분율 형식
```

 또한 데이터 레이블의 형식을 소스 셀에 연결할 수 있습니다. 연결되면`NumberFormat` 일반으로 재설정되고 소스 셀에서 상속됩니다.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## 7단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

이렇게 하면 지정된 이름으로 문서가 저장되고, 서식이 지정된 데이터 레이블이 있는 차트가 보존됩니다.

## 결론

Aspose.Words for .NET을 사용하여 차트의 데이터 레이블을 서식 지정하면 Word 문서의 가독성과 전문성을 크게 향상시킬 수 있습니다. 이 단계별 가이드를 따르면 이제 차트를 만들고, 데이터 시리즈를 추가하고, 필요에 맞게 데이터 레이블을 서식 지정할 수 있습니다. Aspose.Words for .NET은 Word 문서의 광범위한 사용자 지정 및 자동화를 허용하는 강력한 도구로, .NET 개발자에게 귀중한 자산입니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 C#을 사용하여 프로그래밍 방식으로 Word 문서를 만들고, 조작하고, 변환하기 위한 강력한 라이브러리입니다.

### Aspose.Words for .NET으로 다른 유형의 차트를 서식 지정할 수 있나요?
네, Aspose.Words for .NET은 막대형, 세로형, 원형 등 다양한 차트 유형을 지원합니다.

### Aspose.Words for .NET에 대한 임시 라이선스를 받으려면 어떻게 해야 하나요?
임시면허를 취득할 수 있습니다[여기](https://purchase.aspose.com/temporary-license/).

### Excel에서 데이터 레이블을 소스 셀에 연결할 수 있나요?
네, 데이터 레이블을 소스 셀에 연결하여 소스 셀에서 숫자 서식을 상속받을 수 있습니다.

### Aspose.Words for .NET에 대한 더 자세한 문서는 어디에서 찾을 수 있나요?
 포괄적인 문서를 찾을 수 있습니다[여기](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
