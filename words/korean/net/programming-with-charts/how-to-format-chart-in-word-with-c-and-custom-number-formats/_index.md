---
category: general
date: 2026-10-13
description: C#를 사용해 Word 차트의 축에 통화와 같은 사용자 지정 숫자 형식을 적용하여 차트를 서식 지정하는 방법. 단계별 코드
  예제가 포함되어 있습니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: ko
lastmod: 2026-10-13
og_description: C#를 사용하여 Word에서 차트를 서식 지정하는 방법은 차트 축에 사용자 지정 숫자 서식을 적용하여 값이 통화, 백분율
  또는 필요에 따라 원하는 패턴으로 표시되도록 합니다. 단계별 가이드를 따라 보세요.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: C#를 사용하여 Word에서 차트 서식 지정 – 사용자 정의 숫자 형식
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: C#와 사용자 정의 숫자 형식으로 Word 차트 서식 지정하는 방법
url: /ko/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 사용자 지정 숫자 형식을 사용하여 Word에서 차트 서식 지정하는 방법

Word에서 C#를 사용하여 차트 서식을 지정하는 것은 데이터를 전문적으로 제시해야 할 때 흔히 요구되는 작업입니다. 이 가이드에서는 **Aspose.Words for .NET**을 사용하여 차트 축에 사용자 지정 숫자 형식을 적용하는 방법을 보여드리며, 값이 정확히 원하는 대로 표시됩니다.

DOCX 파일을 로드하고, 첫 번째 차트를 찾으며, 현재 형식을 읽은 다음, 두 자리 소수점이 있는 통화와 같은 새로운 패턴을 설정하는 방법을 배우게 됩니다. 또한 추가 시리즈에 대한 차트 축 형식을 변경하는 방법과 필요 시 형식을 재설정하는 방법도 다룹니다.

## 사전 요구 사항

* .NET 6.0 이상이 설치되어 있어야 합니다  
* Visual Studio 2022(또는 .NET을 지원하는 기타 IDE) 프로젝트  
* **Aspose.Words for .NET** NuGet 패키지(`Aspose.Words`)  
* 하나 이상의 차트가 포함된 Word 문서(`input.docx`)

다음 명령으로 패키지를 추가할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

## Aspose.Words를 사용하여 Word에서 차트 서식 지정하는 방법

다음 전체 프로그램은 **차트** 축 값을 서식 지정하는 데 필요한 모든 단계를 보여줍니다. 파일을 `Program.cs`로 저장하고 명령줄이나 IDE에서 실행하십시오.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### 각 단계에 대한 설명

| 단계 | 왜 중요한가 | 핵심 코드 |
|------|------------|----------|
| **문서 로드** | `Document` 객체가 필요합니다 Word 파일을 다루기 위해. | `new Document("input.docx")` |
| **차트 가져오기** | `Chart` 객체는 `Shape` 노드로 저장됩니다; 캐스팅을 통해 차트 전용 API를 사용할 수 있습니다. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **X‑값 접근** | 축 서식은 데이터 시리즈의 값 컬렉션에 적용됩니다. | `chart.ChartData.Series[0].XValues` |
| **현재 형식 읽기** | 기존 `FormatCode`를 알면 교체하거나 추가할지 결정하는 데 도움이 됩니다. | `xValues.FormatCode` |
| **사용자 지정 형식 설정** | `FormatCode` 속성은 Excel 호환 패턴을 허용하므로 통화, 백분율, 날짜 등을 지정할 수 있습니다. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **문서 저장** | 변경 사항을 저장하면 새로운 축 형식이 DOCX 파일에 기록됩니다. | `doc.Save("output_formatted.docx")` |

프로그램을 실행하면 `output_formatted.docx`가 생성됩니다. Word에서 열면 차트의 X축 값이 일반 숫자 대신 **$1,234.00**, **$2,345.00**, …와 같이 표시됩니다.

## 차트 축에 사용자 지정 숫자 형식 적용

Y축이나 추가 시리즈에 **사용자 지정 숫자 형식 적용**이 필요하면, 절차는 동일합니다—다른 컬렉션을 대상으로 하면 됩니다:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **팁:** 형식 문자열 안에 이중 따옴표를 사용하여 리터럴 문자를 삽입합니다(예: 통화의 경우 `"$"`). 위와 같이 따옴표를 이스케이프하십시오.

## 사용자 지정 숫자 형식 – Word 로케일 처리

Word는 숫자 형식을 해석할 때 문서의 로케일을 따릅니다. 문서가 미국이 아닌 로케일을 사용한다면 형식 문자열을 조정해야 할 수 있습니다:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

독일어 설정이 된 문서에서 형식을 테스트하면 값이 **€ 1.234,00**와 같이 표시되는 것을 확인할 수 있습니다.

## 차트 속성을 프로그래밍 방식으로 설정하는 방법

축 서식 지정 외에도, 종종 **차트** 제목, 범례 또는 데이터 레이블을 설정하고 싶습니다. 아래는 축을 서식 지정한 후 차트 제목을 설정하는 간단한 코드 조각입니다:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

이를 사용자 지정 숫자 형식과 결합하면 보고용으로 완전하게 다듬어진 차트를 얻을 수 있습니다.

## 사용자 입력에 따라 차트 축 형식을 동적으로 변경하기

실제 애플리케이션에서는 사용자가 런타임에 형식을 선택하도록 할 수 있습니다. 다음 메서드는 서식 지정 로직을 캡슐화합니다:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

`SetAxisFormat(chart, 0, "\"$\"#,##0.00")`를 호출하면 통화 형식이 되고, `SetAxisFormat(chart, 0, "0%")`를 호출하면 백분율 형식이 됩니다. 이 접근 방식은 메인 코드를 깔끔하게 유지하고 향후 확장을 지원합니다.

## 엣지 케이스 및 일반적인 함정

| 상황 | 주의할 점 | 권장 해결책 |
|------|----------|-------------|
| 문서에 **차트가 없음** | `GetChild`가 `null`을 반환하여 캐스트 예외가 발생합니다. | `null`인지 확인한 후 캐스팅하십시오(예제 참조). |
| 동일 문서에 **여러 차트** | 코드는 항상 첫 번째 차트(`index 0`)를 가져옵니다. | `doc.GetChildNodes(NodeType.Shape, true)`를 순회하고 `ShapeType.Chart`로 필터링하십시오. |
| X값이 **없는 시리즈**(예: 파이 차트) | `XValues`에 접근하면 `ArgumentOutOfRangeException`이 발생할 수 있습니다. | 서식 지정 전에 `Series[i].XValues`가 비어 있지 않은지 확인하십시오. |
| 로케일 불일치 | 통화 기호가 잘못 표시될 수 있습니다. | 적절한 로케일 기호를 사용하여 `xValues.FormatCode`를 명시적으로 설정하십시오. |

## 예상 출력

샘플 프로그램을 실행한 후 **output_formatted.docx**를 엽니다. 차트의 X축은 선택한 사용자 지정 형식으로 숫자를 표시해야 합니다. 통화 예시의 경우 축 레이블은 다음과 같습니다:

```
$1,000.00
$2,000.00
$3,000.00
```

Y값에 백분율 형식을 적용했다면, Y축 레이블은 다음과 같이 표시됩니다:

```
10%
20%
30%
```

## 결론

이 튜토리얼에서는 C#를 사용하여 Word에서 차트 축 값에 **사용자 지정 숫자 형식 적용**을 통해 **차트 서식 지정** 방법을 보여주었습니다. 이제 통화, 백분율 또는 기타 숫자 패턴을 설정하기 위한 재사용 가능한 패턴과 로케일 처리, 다중 시리즈, 동적 사용자 입력에 대한 가이드를 갖추게 되었습니다.

다음으로 **차트** 제목, 데이터 레이블을 설정하거나 `ChartRenderer`를 사용해 차트를 이미지로 내보내는 방법을 살펴볼 수 있습니다. 이러한 주제는 여기서 다룬 개념을 직접 확장하여 완전 자동화된 보고 솔루션을 만드는 데 도움이 됩니다.

---

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [차트 축의 숫자 형식](/words/english/net/programming-with-charts/number-format-for-axis/)
- [차트 데이터 레이블의 숫자 형식 지정](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Aspose.Words for .NET를 사용하여 Word 라인 차트에서 보조 X축을 형식 지정하고 표시 단위를 천 단위로 설정](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}