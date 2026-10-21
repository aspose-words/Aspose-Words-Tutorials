---
category: general
date: 2026-10-13
description: C#를 사용하여 Word 문서의 차트 레이블을 프로그래밍 방식으로 조정하는 방법을 배웁니다. 이 가이드는 Aspose.Words
  차트 조작 및 레이블 정렬을 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: ko
lastmod: 2026-10-13
og_description: C#를 사용하여 Word 문서에서 차트 레이블을 프로그래밍 방식으로 조정합니다. 레이블 위치, 정렬 및 기타 설정을 변경하는
  전체 튜토리얼을 확인하세요.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Word에서 차트 레이블을 프로그래밍 방식으로 조정하기 – C# 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: C#를 사용하여 Word 문서의 차트 레이블을 프로그래밍 방식으로 조정하기
url: /ko/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word 문서에서 차트 레이블을 프로그래밍 방식으로 조정하기

Word 문서에서 **차트 레이블을 프로그래밍 방식으로 조정**해야 하는 경우, 이 가이드는 C#를 사용하여 정확히 수행하는 방법을 보여줍니다. 보고서를 생성하거나, 대시보드를 자동화하거나, 템플릿을 맞춤화할 때, .docx 파일 내부 차트의 레이블 위치와 정렬을 변경하는 전체 실행 가능한 예제를 확인할 수 있습니다.

또한 **Aspose.Words 차트 조작** 기술을 사용하는 방법, 여러 시리즈를 처리하는 방법, 그리고 **C# 차트 데이터 레이블** 객체 작업 시 흔히 발생하는 문제를 피하는 방법을 배울 수 있습니다.

## 사전 요구 사항

* .NET 6.0 (또는 이후 버전) 설치  
* Visual Studio 2022 (또는 기타 C# IDE)  
* The **Aspose.Words for .NET** NuGet 패키지 (`Install-Package Aspose.Words`)  
* 하나 이상의 차트를 포함하는 Word 문서 (`input.docx`)  

이 항목들은 우리가 수정할 **Word 문서 차트 예제**에 필요합니다.

## 1단계: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 프로젝트를 만들고 필요한 `using` 지시문을 추가합니다. 이는 **차트 레이블을 프로그래밍 방식으로 조정**하기 위한 환경을 준비합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*왜 이 단계인가?*  
문서를 로드하면 차트가 shape 노드로 저장되는 내부 **Word 문서 차트 예제** 트리에 접근할 수 있습니다.

## 2단계: 첫 번째 차트 Shape 찾기

차트는 `Shape` 노드로 저장됩니다. 다음 코드는 문서에서 첫 번째 차트를 가져오며, 이는 레이블 조정을 위한 대상입니다.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*왜 이 단계인가?*  
`GetChild` 메서드는 재귀적으로 (`true`) 검색하고 `Shape` 유형의 첫 번째 노드를 반환합니다. `Chart`로 캐스팅하면 차트 전용 API를 사용할 수 있습니다.

## 3단계: 수정하려는 데이터 레이블에 접근하기

차트의 각 시리즈는 데이터 레이블 컬렉션을 가집니다. 간단한 차트에서는 첫 번째 레이블만으로 충분한 경우가 많습니다. 아래 코드는 해당 레이블에 접근하는 방법을 보여줍니다.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*왜 이 단계인가?*  
`ChartSeries`는 포인트 시리즈를 나타냅니다. `DataLabelCollection`은 해당 시리즈의 레이블을 보관하며, 위치와 정렬을 정밀하게 제어할 수 있게 합니다.

## 4단계: 레이블 위치와 정렬 변경

이제 위치, 가로 정렬 및 세로 정렬을 설정하여 **차트 레이블을 프로그래밍 방식으로 조정**합니다. 이러한 속성은 Word UI에서 보는 옵션에 해당합니다.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*왜 이러한 설정인가?*  

* `OutsideEnd`는 레이블을 각 막대 또는 열의 끝 바로 바깥에 배치하여 가독성을 높입니다.  
* `HorizontalAlignment.Center`는 텍스트를 포인트 위에 중앙에 배치하고, `VerticalAlignment.Top`은 레이블의 상단을 데이터 포인트와 맞추어 다른 요소와 겹치는 것을 방지합니다.

### 팁
차트에 여러 시리즈가 있는 경우 `chart.Series`를 반복하면서 각 `DataLabelCollection`에 동일한 설정을 적용하십시오. 이렇게 하면 전체 차트에 일관된 모양을 유지할 수 있습니다.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## 5단계: 수정된 문서 저장

레이블을 조정한 후 변경 사항을 새 파일에 저장합니다. 이는 **차트 레이블 위치 수정** 프로세스를 완료합니다.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`output.docx`를 열면 모든 차트 레이블이 데이터 포인트의 바깥 끝으로 이동하고, 가로로는 중앙에, 세로로는 위쪽에 정렬된 것을 확인할 수 있습니다.

## 엣지 케이스 및 변형

| Situation | What to watch for | Recommended approach |
|-----------|-------------------|----------------------|
| **여러 차트**가 같은 문서에 있는 경우 | `GetChild`는 첫 번째 차트만 반환합니다. | `doc.GetChildNodes(NodeType.Shape, true)`를 사용하여 모든 차트 Shape를 반복합니다. |
| **데이터 레이블이 없는 시리즈** | `DataLabelCollection`이 비어 있을 수 있습니다. | 컬렉션에 접근하기 전에 `series.HasDataLabels`를 확인하십시오. |
| **다양한 차트 유형** (pie, line, scatter) | 모든 `DataLabelPosition` 값이 유효한 것은 아닙니다. | 자동으로 최적 위치를 결정하는 차트에는 `DataLabelPosition.Auto`를 사용하십시오. |
| **현지화** | 정렬 상수는 언어에 구애받지 않지만, 렌더링된 텍스트는 오른쪽에서 왼쪽으로 표시되는 지원이 필요할 수 있습니다. | RTL 언어가 필요하면 `dataLabel.TextDirection`을 설정하십시오. |

## 전체 실행 가능한 예제

아래는 복사·붙여넣기·실행할 수 있는 전체 프로그램입니다. `YOUR_DIRECTORY`를 실제 폴더 경로로 교체하십시오.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**예상 결과:** `output.docx`를 열면 각 차트 레이블이 데이터 포인트 밖에 배치되고, 가로로는 중앙에, 세로로는 위쪽에 정렬된 것을 확인할 수 있습니다—이는 당신이 스크립트한 **차트 레이블을 프로그래밍 방식으로 조정**한 효과와 정확히 일치합니다.

## 결론

이제 C#를 사용하여 Word 문서에서 **차트 레이블을 프로그래밍 방식으로 조정**하는 방법을 알게 되었습니다. 이 튜토리얼에서는 다음을 다루었습니다:

* **Aspose.Words 차트 조작**을 사용한 문서 로드  
* **C# 차트 데이터 레이블**에 접근  
* **차트 레이블 위치 수정** 및 정렬 변경  
* 파일 저장 및 일반적인 엣지 케이스 처리  

여기서부터 레이블 폰트 사용자 정의, 조건부 서식 추가, 또는 배치 프로세스에서 여러 차트 업데이트와 같은 고급 시나리오를 탐색할 수 있습니다. 다양한 `DataLabelPosition` 옵션을 실험하여 보고서에 가장 적합한 스타일을 찾아보세요.

---

*자동 보고 파이프라인을 강화할 준비가 되셨나요? 레이블에 사용자 정의 숫자 형식을 추가하거나 차트를 이미지로 내보내 PDF에 활용해 보세요.*

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET를 사용하여 열 차트에서 균일 데이터 레이블 설정](/words/english/net/programming-with-charts/uniform-data-labels/)
- [차트에서 데이터 레이블의 기본 옵션 설정](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Aspose.Words for .NET를 사용하여 Word 문서의 차트 시리즈 데이터 업데이트](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}