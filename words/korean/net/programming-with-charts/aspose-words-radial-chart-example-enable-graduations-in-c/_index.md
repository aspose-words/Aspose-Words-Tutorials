---
category: general
date: 2026-10-13
description: Aspose.Words 방사형 차트 예제는 C#와 Aspose.Words 24.9+를 사용하여 방사형 차트에 눈금을 활성화하는
  방법을 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: ko
lastmod: 2026-10-13
og_description: C#와 최신 24.9+ 라이브러리를 사용하여 방사형 차트에 눈금을 활성화하는 Aspose.Words 방사형 차트 예제.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words 방사형 차트 예제 – C#에서 눈금 활성화
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words 방사형 차트 예제: C#에서 눈금 활성화'
url: /ko/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words 방사형 차트 예제: C#에서 눈금 활성화

**aspose.words 방사형 차트 예제**를 찾고 계시다면, 올바른 곳에 오셨습니다. 이 튜토리얼에서는 Aspose.Words for .NET API를 사용하여 방사형 차트의 눈금을 켜는 정확한 단계를 안내합니다.

방사형 차트는 하루 중 시간대 메트릭이나 계절적 추세와 같은 순환 데이터를 시각화하는 데 유용합니다. 기본적으로 원형 축 주변의 눈금(틱 마크)은 숨겨져 있어 차트를 읽기 어려울 수 있습니다. 눈금을 활성화하는 것은 한 줄의 변경으로 가능하지만, 올바른 객체 모델과 해당 기능을 지원하는 버전을 알아야 합니다.

이 가이드에서 배울 내용:

* 이미 방사형 차트가 포함된 Word 문서를 로드하는 방법.  
* Aspose.Words 차트 API를 통해 차트 셰이프에 접근하는 방법.  
* **눈금 표시**를 켜는 방법(**Aspose.Words 버전 24.9**부터 사용 가능).  
* 수정된 문서를 저장하고 결과를 확인하는 방법.

전체 실행 가능한 코드를 포함하고 있으니, 새 콘솔 프로젝트에 복사‑붙여넣기만 하면 바로 효과를 확인할 수 있습니다.

![Aspose.Words 방사형 차트 예제 (눈금 포함)](https://example.com/images/radial-chart-graduations.png "Aspose.Words 방사형 차트 예제 – 눈금이 활성화된 모습")

## 사전 요구 사항

시작하기 전에 다음을 확인하세요:

| 요구 사항 | 이유 |
|-------------|----------------|
| .NET 6.0 이상 | Aspose.Words for .NET 24.9+는 .NET Standard 2.0을 대상으로 하며 .NET 6+에서 작동합니다. |
| Aspose.Words for .NET **24.9** 이상 | `IsGraduationsVisible` 속성은 버전 24.9에서 도입되었습니다. 이전 버전에서는 `MissingMemberException`이 발생합니다. |
| 방사형 차트가 포함된 Word 문서(`RadialChart.docx`) | 예제는 기존 차트를 조작합니다; 차트를 처음부터 만드는 것은 별도 주제입니다. |
| C# IDE (Visual Studio, Rider, VS Code) | .NET 프로젝트를 컴파일할 수 있는 IDE면 모두 사용 가능합니다. |
| NuGet 패키지 `Aspose.Words` | `dotnet add package Aspose.Words --version 24.9.0`(또는 최신 버전)으로 설치합니다. |

> **프로 팁:** 24.9로 업그레이드할 수 없는 경우에도 다른 차트 속성은 수정할 수 있지만, 눈금은 API에 해당 플래그가 없으므로 계속 숨겨진 상태로 남습니다.

## Aspose.Words 방사형 차트 예제 – 단계별 가이드

다음 섹션에서는 과정을 개별 단계로 나누어 쉽게 따라 할 수 있도록 설명합니다. 각 단계마다 필요한 정확한 코드와 해당 단계가 필요한 이유를 간단히 설명합니다.

### 단계 1: 방사형 차트가 포함된 문서 로드

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**왜 중요한가:**  
`Document`는 **Aspose.Words 차트 API**의 진입점입니다. DOCX 파일을 메모리로 로드하여 모든 노드(단락, 표, 차트 셰이프 등)에 접근할 수 있게 합니다. 파일을 찾을 수 없으면 `Document`가 `FileNotFoundException`을 발생시키므로, 실제 서비스에서는 예외 처리가 필요합니다.

### 단계 2: 문서에서 첫 번째 차트 셰이프 가져오기

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**왜 중요한가:**  
차트는 `Shape` 노드로 저장됩니다. `GetChild` 메서드에 `NodeType.Shape`를 지정하면 DOM을 순회하며 첫 번째 일치하는 셰이프를 반환합니다. 이를 `Chart`로 캐스팅하면 `RadialChart`와 같은 차트‑전용 속성에 접근할 수 있습니다. null‑체크를 통해 문서에 차트가 없을 경우 명확한 오류를 제공하므로, 템플릿을 재사용할 때 흔히 발생하는 문제를 방지합니다.

### 단계 3: 방사형 차트에 눈금 활성화

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**왜 중요한가:**  
`IsGraduationsVisible`은 원형 축 주변의 눈금을 제어합니다. `true`로 설정하면 차트에 눈금이 표시되어 값을 정확히 파악하려는 사용자에게 가독성이 향상됩니다. 이 속성은 `RadialChart` 아래에 있으며, `Chart`의 하위 타입입니다. 비방사형 차트(예: 막대 차트)에서 사용하면 `RadialChart` 속성이 `null`이 되므로, 복잡한 시나리오에서는 차트 유형을 먼저 확인해야 합니다.

#### 비방사형 차트 처리 (선택 사항)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

이 방어 코드는 소스 문서에 다양한 차트 유형이 포함될 수 있을 때 코드를 견고하게 만들어 줍니다.

### 단계 4: 수정된 문서 저장

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**왜 중요한가:**  
`Save`를 호출하면 메모리상의 DOM이 .docx 파일로 기록되어 차트에 적용한 변경 사항이 영구히 저장됩니다. 출력 파일은 Microsoft Word, LibreOffice 등 DOCX를 지원하는 모든 뷰어에서 열 수 있습니다. 이제 눈금이 표시된 방사형 차트를 확인할 수 있습니다.

## 전체 실행 가능한 예제

아래 코드는 .NET 콘솔 프로젝트의 `Program.cs`에 그대로 붙여넣을 수 있는 완전한 프로그램입니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### 예상 결과

`RadialChart_Graduations.docx`를 Word에서 열면, 방사형 차트에 원형 축 주변에 눈금(Graduations)이 표시됩니다. 앞서 보여드린 스크린샷과 동일한 모습이며, 데이터 시리즈, 범례, 제목 등 차트의 다른 요소는 그대로 유지됩니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 해결 방법 |
|-----------|----------|
| **구버전 Aspose.Words (< 24.9)** | 최신 NuGet 패키지로 업그레이드하세요. `IsGraduationsVisible` 속성은 이전 릴리스에 존재하지 않습니다. |
| **문서에 차트가 여러 개** | `doc.GetChild(NodeType.Shape, index, true)`에서 적절한 `index`를 사용하거나 `doc.GetChildNodes(NodeType.Shape, true)`를 순회하면서 `ChartType.Radial`로 필터링하세요. |
| **프로그램matically 차트 생성** | `DocumentBuilder`를 사용해 차트를 삽입한 뒤 `RadialChart.IsGraduationsVisible`을 설정합니다. |

## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하며, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용해 Word 문서에서 차트 시리즈 데이터 업데이트](/words/english/net/programming-with-charts/modify-chart-series/)
- [Aspose.Words for .NET을 사용해 Word 문서에서 차트 시리즈 제거](/words/english/net/programming-with-charts/remove-chart-series/)
- [Aspose.Words for .NET을 사용해 컬럼 차트에서 플롯 영역 테두리 숨기기](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}