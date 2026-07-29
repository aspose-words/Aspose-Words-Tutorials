---
category: general
date: 2026-07-29
description: Word 문서에서 차트를 편집하는 방법—차트 레이블 위치 변경, 막대 차트 레이블 조정, 차트 데이터 레이블 수정, 차트 레이블
  글꼴 변경을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: ko
lastmod: 2026-07-29
og_description: Word에서 차트를 빠르게 편집하는 방법. 차트 레이블 위치 변경, 막대 차트 레이블 조정, 차트 데이터 레이블 수정,
  차트 레이블 글꼴 변경을 마스터하세요.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Word에서 차트 편집 방법 – 레이블 및 글꼴 변경
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Word에서 차트 편집 방법: 레이블 위치, 글꼴 및 기타 변경'
url: /ko/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 차트 편집하기: 레이블 위치, 글꼴 등 변경

Word 문서에서 차트를 편집하는 것은 보고서를 깔끔하게 보이게 하고 싶을 때 흔히 필요한 작업입니다. **차트 레이블 위치**를 변경하거나 레이블을 읽기 쉽게 만들기 위해 끝없는 메뉴를 뒤져야 했던 적이 있나요? 당신만 그런 것이 아닙니다—대부분의 개발자는 보고서 자동화 과정에서 이 문제에 부딪힙니다. 이 가이드에서는 C#와 Aspose.Words 라이브러리를 사용하여 **막대 차트 레이블 조정**, **차트 데이터 레이블 수정**, **차트 레이블 글꼴 변경**을 정확히 수행하는 완전한 실행 가능한 예제를 단계별로 살펴보겠습니다.

## 배울 내용

- 이미 막대 차트가 포함된 .docx 파일을 로드합니다.  
- 첫 번째 차트 도형을 가져와 데이터‑레이블 컬렉션에 접근합니다.  
- **차트 레이블 위치**를 변경하여 막대를 더 깔끔하게 보이게 합니다.  
- **막대 차트 레이블**의 글꼴 크기를 조정하여 가독성을 높입니다.  
- 수정된 문서를 디스크에 저장합니다.  

외부 도구 없이, 수동 UI 작업 없이—순수 코드만으로 .NET 프로젝트에 바로 넣을 수 있습니다. 끝까지 진행하면 수십 개의 문서에 재사용 가능한 자체 포함 솔루션을 얻게 됩니다.

> **Prerequisites**  
> - .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 작동합니다).  
> - Aspose.Words for .NET (NuGet을 통해 제공).  
> - 이미 막대 차트가 포함된 Word 파일(`BarChart.docx`).  

위 항목 중 누락된 것이 있다면 지금 바로 최신 Aspose.Words 패키지를 받아 주세요:

```bash
dotnet add package Aspose.Words
```

---

## How to Edit Chart: Retrieve the Chart from the Word Document

**how to edit chart** 객체를 다루는 첫 번째 단계는 문서를 로드하고 차트 도형을 찾는 것입니다. Aspose.Words는 차트를 `Shape` 노드로 취급하므로 `GetChild`와 `NodeType.Shape`를 사용해 첫 번째 차트를 가져올 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> `Chart` 객체에 직접 접근하면 Word에서 파일을 열어 레이블을 수동으로 조정하는 오버헤드를 피할 수 있습니다. 이는 **modify chart data labels** 자동화의 핵심입니다.

## Adjust Bar Chart Labels: Change Chart Label Position

이제 `Chart` 인스턴스를 얻었으니 `DataLabelCollection`을 순회해 보겠습니다. 목표는 **차트 레이블 위치**를 변경하여 각 레이블이 막대의 바닥에 깔끔히 들어가게 하는 것입니다. 레이블이 위에 떠 있는 어색함을 없앨 수 있습니다.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase`는 수직 막대 차트에 잘 맞습니다. 가로 막대 차트를 다루는 경우 `InsideEnd`를 시도해 보세요. 위치를 실험하는 비용은 저렴합니다—코드를 다시 실행하고 저장된 문서를 열기만 하면 됩니다.

## Change Chart Label Font: Adjust Font Size for Readability

작은 글꼴은 보고서 가독성을 크게 저해합니다. **차트 레이블 글꼴**을 변경하려면 각 `ChartDataLabel`의 `Font.Size` 속성을 설정하면 됩니다. 대부분 인쇄 보고서에 적합한 9 pt로 늘려 보겠습니다.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> 글꼴 크기 조정은 **modify chart data labels** 모범 사례의 일부입니다. 큰 글꼴은 접근성을 향상시키고 수동 후처리 필요성을 줄여줍니다.

## Save the Updated Document

위치와 글꼴을 조정한 후, **how to edit chart**의 마지막 단계는 변경 사항을 저장하는 것입니다. Aspose.Words는 이를 한 줄 코드로 처리합니다.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

`BarChartCustomLabels.docx`를 Word에서 열면 레이블이 막대 안에 딱 맞게 배치되고 9 pt의 선명한 글꼴로 표시됩니다. 이제 작은 숫자를 눈으로 보기 위해 눈을 가늘게 뜨는 일은 없습니다.

---

## Full Working Example (All Steps in One File)

아래는 전체 흐름—문서 로드부터 업데이트된 버전 저장까지—을 보여주는 완전한 실행 가능한 콘솔 프로그램입니다. 새 .NET 콘솔 프로젝트에 복사‑붙여넣기하고 **F5**를 눌러 실행하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** when you run the program:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

생성된 파일을 열면 **adjust bar chart labels**가 막대 안에 배치되고 편안한 글꼴 크기로 표시되는 것을 확인할 수 있습니다.

---

## Common Questions & Edge Cases

### What if the document contains multiple charts?

위 코드는 *첫 번째* 차트(`GetChild(NodeType.Shape, 0, true)`)만 가져옵니다. 모든 차트를 편집하려면 단일 조회를 루프로 교체하세요:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### How to **change chart label font** for a specific series only?

각 `ChartSeries`는 자체 `DataLabelCollection`을 가지고 있습니다. 인덱스로 시리즈를 지정하면 됩니다:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Does this work with pie or line charts?

예—`ChartDataLabelPosition`은 `InsideEnd`, `OutsideEnd`, `BestFit` 같은 값을 지원합니다. 파이 차트의 경우 레이블 가독성을 위해 `OutsideEnd`를 선호할 수 있습니다.

### What about localization (e.g., different decimal separators)?

Aspose.Words는 문서의 로케일 설정을 따릅니다. 특정 형식을 강제해야 한다면 저장하기 전에 `label.NumberFormat`을 조정하세요.

---

## Recap & Next Steps

우리는 **how to edit chart** 객체를 시작부터 끝까지 다루었습니다: 파일 로드, 차트 가져오기, **차트 레이블 위치** 변경, **막대 차트 레이블** 조정, **차트 데이터 레이블** 수정, 그리고 **차트 레이블 글꼴** 변경 후 저장까지. 완전한 예제는 프로덕션에 바로 사용할 수 있으며 어떤 자동화 파이프라인에도 삽입할 수 있습니다.

다음 단계 아이디어를 고려해 보세요:

- **데이터 레이블 색상 추가** (`dataLabel.Font.Color = Color.Blue;`).  
- **값을 백분율로 표시** (`dataLabel.NumberFormat = "0%";`).  
- **기존 차트를 로드하는 대신 프로그래밍 방식으로 차트 생성**.  

이 모든 작업은 오늘 사용한 동일한 API 표면을 기반으로 하므로 익숙하게 느낄 것입니다.

문제에 부딪혔다면 아래에 댓글을 남기거나 Aspose.Words 문서에서 차트‑커스터마이징 옵션을 더 자세히 확인하세요. 즐거운 코딩 되시고, 아름답게 라벨링된 차트를 마음껏 활용하시기 바랍니다!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 연관된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [차트 데이터 레이블 사용자 정의](/words/english/net/programming-with-charts/chart-data-label/)
- [차트에서 데이터 레이블 숫자 형식 지정](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [차트 데이터 레이블](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}