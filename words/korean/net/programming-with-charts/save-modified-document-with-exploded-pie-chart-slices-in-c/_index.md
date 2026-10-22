---
category: general
date: 2026-10-13
description: '파이 차트를 사용자 정의한 후 수정된 문서를 저장합니다: 슬라이스를 분리하고, 첫 번째 슬라이스의 각도를 변경하며, C#에서
  백분율 레이블을 표시합니다.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: ko
lastmod: 2026-10-13
og_description: C#에서 파이 차트를 사용자 정의한 후 수정된 문서를 저장하세요. 파이 차트 조각을 분리하고, 첫 번째 조각의 각도를
  변경하며, 백분율 레이블을 표시하는 방법을 배워보세요.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: 분리된 파이 차트 조각이 있는 수정된 문서 저장 – C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: C#에서 폭발된 파이 차트 조각이 포함된 수정된 문서 저장
url: /ko/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 폭발된 파이 차트 조각이 포함된 수정된 문서 저장

Word 파이 차트를 조정한 후 **save modified document**가 필요하다면, 이 가이드가 정확히 방법을 알려줍니다. 파이 차트 조각을 폭발시키고, 첫 번째 조각 각도를 변경하며, 백분율 레이블을 표시하는 방법을 몇 줄의 C# 코드로 배울 수 있습니다.

차트를 사용자 정의하는 것은 보고서, 청구서 또는 대시보드를 프로그래밍 방식으로 생성할 때 흔히 요구되는 작업입니다. 이 튜토리얼을 마치면 DOCX 파일을 로드하고 차트 모양을 수정한 뒤 **save modified document**를 배포용으로 저장할 수 있게 됩니다.

## Prerequisites

- .NET 6.0 이상 (.NET Framework 4.6+에서도 작동합니다)
- Aspose.Words for .NET 23.10 이상 (무료 체험판 또는 정식 라이선스)
- 단일 파이 차트가 포함된 Word 파일 (`input.docx`)
- Visual Studio 2022 또는 기타 C# IDE

> **Tip:** Aspose.Words NuGet 패키지는 `dotnet add package Aspose.Words` 로 추가됩니다.

## Step 1: 차트가 포함된 Word 문서 로드

첫 번째 단계는 원본 DOCX 파일을 여는 것입니다. `Document` 클래스는 메모리 내 전체 Word 파일을 나타냅니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

문서를 로드하면 차트를 포함한 모든 노드, 특히 차트를 호스팅하는 Shape에 대한 전체 접근 권한을 얻을 수 있습니다.

## Step 2: 문서에서 첫 번째 차트 Shape 가져오기

차트는 `Shape` 노드 안에 저장됩니다. `GetChild` 를 사용하여 첫 번째 차트를 찾을 수 있습니다.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

문서에 차트가 여러 개 있는 경우 인덱스(`0`)를 조정하거나 컬렉션을 순회하세요. 이 코드는 수정할 `Chart` 객체에 대한 참조를 확보합니다.

## Step 3: 파이 차트 조각 폭발시키기

조각을 폭발시키면 파이의 나머지 부분과 분리되어 차트를 더 쉽게 읽을 수 있습니다. `Explode` 속성은 전체 시리즈에 적용됩니다.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

`Explode` 를 `true` 로 설정하면 전체 시리즈에 대해 **exploded pie chart slices**가 적용되어 모든 조각이 돋보이게 됩니다.

## Step 4: 첫 번째 조각 각도 변경

때때로 첫 번째 조각을 사용자 정의 각도에서 시작하도록 해야 할 때가 있습니다. 예를 들어 디자인 가이드라인에 맞추기 위해서입니다.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle` 속성은 **changes first slice** 방향을 바꾸어 전체 파이를 회전시켜 첫 번째 조각이 30 도에서 시작하도록 합니다.

## Step 5: 파이 조각에 백분율 레이블 표시

각 조각의 수치 기여도를 표시하는 것은 보고서에서 자주 요구됩니다. `DataLabel.ShowPercentage` 플래그를 켜면 백분율 값이 표시됩니다.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

이 단계는 차트에 직접 **show percentage labels**를 표시하며, **display percentages pie** 요구 사항도 만족합니다.

## Step 6: 수정된 문서 저장

모든 사용자 정의가 적용된 후 변경 사항을 새 파일에 저장합니다. `Save` 메서드는 업데이트된 DOCX를 디스크에 기록합니다.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

이제 **save modified document**가 폭발된 파이 차트, 회전된 첫 번째 조각 및 표시된 백분율 레이블을 포함합니다.

![폭발된 파이 차트가 표시된 수정된 문서](/images/pie-chart-exploded.png "폭발된 파이 차트 조각과 백분율 레이블이 포함된 수정된 문서")

*스크린샷은 문서를 저장한 후 최종 출력 결과를 보여줍니다.*

## Full, runnable example

전체 코드를 한데 모아 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 완전한 프로그램을 제공합니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Expected result

`output.docx` 를 열면 파이 차트가 다음과 같이 표시됩니다:

- 모든 조각이 약간 분리되어 있습니다 (**exploded pie chart slices**)
- 첫 번째 조각이 30도 오프셋에서 시작합니다 (**change first slice**)
- 각 조각이 백분율로 기여도를 표시합니다 (**show percentage labels**, **display percentages pie**)
- 원본을 변경하지 않고 **save modified document**가 완료되었습니다.

## Common questions and edge cases

| 질문 | 답변 |
|----------|--------|
| **문서에 차트가 전혀 없는 경우는 어떻게 해야 하나요?** | `GetChild` 후 `null` 여부를 확인합니다. 차트가 없으면 프로그래밍 방식으로 추가하거나 명확한 메시지를 표시하고 중단할 수 있습니다. |
| **단일 조각만 폭발시킬 수 있나요?** | 가능합니다. `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` 와 같이 `i` 를 조각 인덱스로 지정하면 됩니다. |
| **레이블 형식을 어떻게 변경하나요? (예: 값 + % 표시)** | `chart.PieChart.DataLabel.ShowValue = true;` 를 설정하고 필요에 따라 `chart.PieChart.DataLabel.ShowPercentage = true;` 를 추가하면 두 정보를 모두 표시할 수 있습니다. |
| **저장 후 차트 스타일이 유지되나요?** | Aspose.Words는 **save modified document** 시 색상 및 글꼴을 포함한 모든 스타일을 그대로 유지합니다. |
| **같은 파일에 여러 차트를 처리할 수 있나요?** | `NodeType.Shape` 인 `Shape` 노드를 모두 순회하고 `shape.HasChart` 로 필터링하면 됩니다. 각 차트에 동일한 단계를 적용하세요. |

## Conclusion

이제 Word에서 파이 차트를 프로그래밍 방식으로 사용자 정의한 뒤 **save modified document**하는 방법을 알게 되었습니다. 이 가이드는 **exploded pie chart slices**, **change first slice**, **show percentage labels**, **display percentages pie** 요구 사항을 모두 충족하도록 파이 차트 조각을 폭발시키고, 첫 번째 조각 각도를 변경하며, 백분율 레이블을 표시하는 방법을 다루었습니다.

다음과 같은 주제도 살펴보세요:

- 데이터 시리즈를 동적으로 추가하기 (`chart.Series.Add(...)`)  
- 범례 위치 및 차트 제목 사용자 정의  
- 차트 스타일을 유지하면서 DOCX를 PDF로 변환  

다양한 각도, 폭발 설정 또는 레이블 형식을 실험하여 보고서 요구에 맞게 조정해 보세요. 즐거운 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방법을 탐색하도록 돕습니다.

- [Aspose.Words를 사용한 C#에서 편집된 문서 저장 방법 – 단계별 가이드](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aspose.Words for .NET을 사용하여 Word 문서에서 차트 시리즈 데이터 업데이트](/words/english/net/programming-with-charts/modify-chart-series/)
- [Word 문서에 열 차트 삽입](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}