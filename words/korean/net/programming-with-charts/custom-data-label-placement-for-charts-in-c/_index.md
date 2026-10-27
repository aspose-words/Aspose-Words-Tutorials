---
category: general
date: 2026-08-04
description: C#에서 차트용 맞춤 데이터 레이블 배치를 사용하면 차트 조각에 레이블을 중앙에 배치할 수 있습니다. Aspose.Words
  차트 API를 활용한 단계별 가이드를 따라 보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: ko
lastmod: 2026-08-04
og_description: C#에서 차트용 사용자 지정 데이터 레이블 배치에서는 Word 차트의 각 슬라이스에 모든 데이터 레이블을 중앙에 배치하는
  방법을 보여줍니다. Aspose.Words와 함께 차트 데이터 레이블 위치 지정의 마스터가 되세요.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: C# 차트용 사용자 지정 데이터 레이블 배치 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: C# 차트에서 사용자 정의 데이터 레이블 배치
url: /ko/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 차트용 사용자 정의 데이터 레이블 배치

**Custom Data‑Label Placement for Charts**(을) 사용하면 Word 문서 내 차트에서 각 레이블이 정확히 어디에 표시되는지 제어할 수 있습니다. 이 튜토리얼에서는 C#와 Aspose.Words 차트 API를 사용해 각 슬라이스의 모든 데이터 레이블을 중앙에 배치하는 방법을 배웁니다.

전체 실행 가능한 예제를 제공하며, `.docx` 파일을 로드하고 첫 번째 차트 도형에 접근한 뒤 모든 레이블의 `Position`을 `Center`로 변경하고 업데이트된 문서를 저장합니다. 외부 참조는 필요하지 않으며, Aspose.Words for .NET 라이브러리와 기본 C# 개발 환경만 있으면 됩니다.

**배우게 될 내용**

* 차트가 포함된 Word 문서를 로드하는 방법  
* Aspose.Words 차트 API를 사용해 차트 도형을 찾는 방법  
* 차트의 모든 시리즈에 **차트 데이터 레이블 위치 지정**을 적용하는 방법  
* 레이블이 중앙에 배치된 상태로 문서를 저장하는 방법  

**전제 조건**

* .NET 6.0(또는 그 이상) 설치  
* Visual Studio 2022(또는 기타 C# IDE)  
* `Aspose.Words` NuGet 패키지에 대한 참조  
* 최소 하나의 차트가 포함된 Word 파일(`Chart.docx`)  

---

## Custom Data‑Label Placement for Charts – step 1: 문서 로드

첫 번째 작업은 차트가 들어 있는 Word 파일을 여는 것입니다. `Document`는 Aspose.Words와 함께 모든 조작을 시작하는 진입점입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Why this step matters*: 문서를 로드하지 않으면 차트 객체에 접근할 수 없습니다. 파일에 차트가 없을 경우 명확한 오류를 반환하도록 검증을 수행해 나중에 발생할 수 있는 null‑reference 오류를 방지합니다.

---

## Aspose.Words 차트 API를 사용해 차트 도형에 접근하기

Aspose.Words는 차트를 `Shape` 내부에 중첩된 `Chart` 객체로 취급합니다. 적절한 자식 노드를 캐스팅하여 가져올 수 있습니다.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Why this step matters*: `Chart`에 직접 접근하면 시리즈, 데이터 포인트 및 레이블 속성을 완전히 제어할 수 있습니다. 도형이 차트가 아닌 경우, 코드가 조기에 중단되고 유용한 메시지를 출력합니다.

---

## C#에서 차트 데이터 레이블 위치 지정 설정

이제 모든 시리즈와 모든 데이터 레이블을 순회하면서 `Position`을 `Center`로 설정합니다. 이것이 **Custom Data‑Label Placement for Charts**의 핵심입니다.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tip**: 다른 위치가 필요하면(예: 컬럼 차트의 `InsideEnd`) 열거형 값을 해당 값으로 변경하면 됩니다. `ChartDataLabelPosition` 열거형은 Word에서 지원하는 모든 표준 위치를 포함합니다.

*Why this step matters*: `label.Position`을 변경하면 기본 OOXML 표현이 업데이트되어, 문서를 Microsoft Word에서 열었을 때 레이블이 중앙에 표시됩니다.

---

## 업데이트된 레이블과 함께 Word 문서 저장하기

차트를 수정한 후 변경 사항을 파일에 다시 저장합니다. 원본을 덮어쓰거나 새 사본을 만들 수 있습니다.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Why this step matters*: 저장은 업데이트된 OOXML을 디스크에 기록합니다. `ChartLabelsCentered.docx`를 Word에서 열면 모든 슬라이스 레이블이 중앙에 배치된 것을 확인할 수 있으며, **Custom Data‑Label Placement for Charts**가 성공했음을 증명합니다.

---

## 엣지 케이스 및 변형

| 상황 | 처리 방법 |
|-----------|---------------|
| **Multiple charts**가 동일 문서에 존재하는 경우 | `doc.GetChildNodes(NodeType.Shape, true)`를 순회하면서 각 `shape.HasChart`를 확인합니다. |
| **Different chart types**(pie, doughnut, bar) | 파이형 차트에는 `ChartDataLabelPosition.Center`가 그대로 작동합니다. 막대/컬럼 차트에서는 `InsideEnd` 또는 `OutsideEnd`를 선호할 수 있습니다. |
| **Label text**에 서식이 필요한 경우 | `label.TextProperties`에 접근해 글꼴 크기, 색상, 굵기 등을 설정합니다. |
| **.NET Core**에서 실행하는 경우 | .NET Standard 버전의 Aspose.Words를 참조하십시오; API는 동일합니다. |

---

## 완전한 작동 예제

아래는 콘솔 애플리케이션에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 필요한 `using` 지시문과 오류 처리를 모두 포함하고 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**예상 결과**: Microsoft Word에서 `ChartLabelsCentered.docx`를 열면 차트의 각 슬라이스에 데이터 레이블이 슬라이스 중앙에 표시되어 보다 깔끔한 시각적 효과를 제공합니다.

---

## 결론

이제 C#에서 **Custom Data‑Label Placement for Charts** 솔루션을 완전히 구현했습니다. 문서를 로드하고, Aspose.Words 차트 API를 통해 차트에 접근한 뒤, 모든 레이블에 `ChartDataLabelPosition.Center`를 설정하고 파일을 저장하면 Word 기반 차트의 레이블 위치를 자동화할 수 있습니다.

다음 단계로 `InsideEnd`나 `OutsideEnd`와 같은 다른 **chart data label positioning** 옵션을 살펴보거나, **C# chart manipulation**을 활용해 색상을 변경하고, 범례를 추가하거나, 차트를 처음부터 생성해 보는 것을 권장합니다. 이러한 확장은 여기서 다룬 기술을 직접 기반으로 하며, Word 문서 차트 자동화 역량을 한층 넓혀줄 것입니다. 즐거운 코딩 되세요!

## 다음에 배울 내용

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [차트 데이터 레이블 사용자 정의](/words/english/net/programming-with-charts/chart-data-label/)
- [차트 데이터 레이블 숫자 서식 지정](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [차트 데이터 레이블](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}