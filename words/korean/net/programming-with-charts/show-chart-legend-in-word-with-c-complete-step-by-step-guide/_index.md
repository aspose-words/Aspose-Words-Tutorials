---
category: general
date: 2026-06-02
description: C#를 사용하여 Word 문서에 차트 범례를 표시하세요. 범례 추가, 미리 설정된 차트 스타일 적용, 그리고 몇 분 안에 Word
  차트 시각화를 맞춤 설정하는 방법을 배워보세요.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: ko
og_description: Word 문서에서 차트 범례를 즉시 표시합니다. 이 가이드는 범례 추가, 사전 설정 차트 스타일 적용 및 예외 상황 처리
  방법을 안내합니다.
og_title: Word에서 차트 범례 표시 – 전체 C# 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: C#를 사용하여 Word에서 차트 범례 표시 – 완전 단계별 가이드
url: /ko/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에서 차트 범례 표시 – 완전 단계별 가이드

Word 문서에 포함된 차트에 **범례를 추가하는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 많은 보고서에서 범례가 없으면 데이터가 이해하기 어려워 보이며, 이를 수정하는 것이 번거로워서는 안 됩니다.  

이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 파일에 **차트 범례를 표시**하고, 사전 설정 차트 스타일을 적용하며, 범례가 정확히 원하는 위치에 나타나도록 합니다. 끝까지 진행하면 언제든지 C# 프로젝트에 삽입할 수 있는 실행 가능한 샘플을 얻게 됩니다.

## 이 가이드에서 다루는 내용

전체 워크플로우를 단계별로 살펴봅니다:

1. 이미 차트가 포함된 기존 *.docx* 파일을 로드합니다.  
2. 첫 번째 차트(또는 대상 차트)를 가져옵니다.  
3. **사전 설정 차트 스타일 적용**으로 시각을 전문적으로 보이게 합니다.  
4. **차트 범례 표시**, 오른쪽에 배치하고 Waterfall 차트와 같은 특수 경우를 처리합니다.  
5. 수정된 문서를 저장합니다.

외부 도구 없이, UI를 수동으로 조작할 필요 없이—순수 코드만 사용합니다. 전제 조건은 Aspose.Words NuGet 패키지(버전 23.10 이상) 참조와 C#에 대한 기본적인 이해뿐입니다.

---

## Prerequisites

- .NET 6.0 이상(.NET Framework 4.7.2에서도 샘플이 작동합니다).  
- Aspose.Words for .NET 라이브러리 설치(`Install-Package Aspose.Words`).  
- 최소 하나의 차트가 포함된 Word 파일(`input.docx`).  
- Visual Studio, Rider 또는 선호하는 IDE.

---

## Step 1: Set Up the Project and Load the Document

먼저 콘솔 앱을 만들고(또는 기존 프로젝트에 코드를 통합) `using` 지시문을 추가한 뒤 `.docx` 파일을 로드합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **왜 중요한가:** 문서를 로드하는 것이 기본입니다. `Document` 인스턴스가 없으면 Aspose.Words가 제공하는 차트 객체에 접근할 수 없습니다.

---

## Step 2: Retrieve the Target Chart

차트는 문서 트리 내부의 노드로 저장됩니다. `GetChild` 메서드는 깊은 검색을 수행하여 차트가 헤더, 본문, 푸터 등 어디에 있든 첫 번째 차트를 가져올 수 있게 해줍니다.

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **팁:** 차트가 여러 개 있는 경우 인덱스 `0`을 `1`, `2` 등으로 바꾸거나 `doc.GetChildNodes(NodeType.Chart, true)`를 반복하세요.

---

## Step 3: Apply a Preset Visual Style

멋진 차트는 종종 스타일에서 시작됩니다. Aspose.Words는 수십 개의 내장 스타일을 제공하며, `ChartStyle.Style12`는 깔끔하고 현대적인 옵션입니다.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **작동 방식:** `Style` 속성은 UI에서 보는 Word 내장 차트 스타일에 매핑됩니다. 사전 설정을 선택하면 색상, 글꼴, 마커 등을 수동으로 설정할 필요가 없습니다.

---

## Step 4: Enable the Legend and Position It

이제 쇼의 스타—**차트 범례 표시**입니다. 범례를 켜고 차트 오른쪽에 고정합니다.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **왜 오른쪽인가?** 범례를 오른쪽에 배치하면 데이터 영역이 넓어져, 특히 막대형이나 세로형 차트에 유용합니다.

---

## Step 5: Handle Waterfall Charts (Special Case)

Waterfall 차트는 약간 다르게 동작합니다; 기본적으로 범례가 숨겨질 수 있습니다. 다음 가드 절은 차트 유형이 Waterfall인 경우 범례가 보이도록 보장합니다.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **예외 상황 주의:** 일부 오래된 Word 버전은 Waterfall 차트에 대해 `HasLegend`를 무시하므로, `Legend.Show`를 명시적으로 설정하면 가시성을 보장합니다.

---

## Step 6: Save the Modified Document

마지막으로 변경 사항을 디스크에 기록합니다. 원본 파일을 덮어쓰거나 새 파일을 만들 수 있습니다.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

프로그램을 실행하면 오른쪽에 보이는 범례와 `Style12` 스타일이 적용된 `output.docx`가 생성됩니다. Word에서 파일을 열어 결과를 확인하세요.

---

## Full Working Example (All Steps Combined)

아래는 완전한 실행 가능한 코드입니다. `Program.cs`(또는 任意 C# 파일)에 복사‑붙여넣기하고 파일 경로를 조정하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**예상 출력:** `output.docx`를 열면 원본 차트에 오른쪽 정렬된 범례가 표시되고, 최신 `Style12` 스타일이 적용됩니다. 모든 데이터 시리즈에 라벨이 명확히 표시되어 차트를 즉시 이해할 수 있습니다.

---

## Frequently Asked Questions (FAQ)

### How to add legend to a specific chart (not the first one)?

`GetChild(NodeType.Chart, 0, true)`의 `0` 인덱스를 대상 차트의 0 기반 위치로 바꾸거나 모든 차트 노드를 순회하십시오:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Can I place the legend at the bottom instead of the right?

물론입니다. `LegendPosition` 열거형을 변경하면 됩니다:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### What if the chart already has a legend but I want to hide it?

`HasLegend`를 `false`로 설정하십시오:

```csharp
chart.HasLegend = false;
```

### Does this work with Word 2010, 2016, and later?

예. Aspose.Words는 기본 Word 버전을 추상화하므로 동일한 코드를 모든 최신 .docx 파일에서 사용할 수 있습니다.

---

## Pro Tips & Common Pitfalls

- **프로 팁:** 스타일을 적용한 후에도 `Chart.Series` 컬렉션을 통해 개별 요소(색상, 데이터 레이블)를 조정할 수 있습니다. 스타일은 견고한 기본값을 제공합니다.  
- **주의할 점:** 차트가 표 셀 안에 있으면 범례가 좁게 표시될 수 있습니다. 범례를 배치하기 전에 차트 크기(`chart.Width`, `chart.Height`)를 늘리는 것을 고려하세요.  
- **성능 참고:** 수백 MB 규모의 대형 문서를 로드하면 메모리를 많이 사용합니다. 차트 조작만 필요할 경우 `LoadOptions`에 `LoadFormat.Docx`를 지정해 오버헤드를 줄이세요.

---

## Next Steps

이제 Word에서 **범례 추가 방법**과 **사전 설정 차트 스타일 적용**을 알았으니 다음을 탐색해 볼 수 있습니다:

- **맞춤 차트 색상** (`chart.Series[i].Format.Fill.ForeColor`).  
- **데이터 레이블 서식** (`chart.Series[i].HasDataLabel = true`).  
- **차트를 이미지로 내보내기** (`chart.ToImage()`), 다른 곳에 삽입할 때 유용합니다.  

이 주제들은 모두 동일한 객체 모델을 기반으로 하므로 학습 곡선이 완만합니다.

---

## Conclusion

우리는 C#를 사용하여 Word 문서에 **차트 범례 표시**를 위한 깔끔하고 완전한 솔루션을 시연했습니다. 문서를 로드하고, 차트를 가져오며, 사전 설정 스타일을 적용하고, 범례를 활성화하고, Waterfall 차트의 특수 상황을 처리함으로써 비즈니스 보고서에 바로 사용할 수 있는 다듬어진 차트를 얻을 수 있습니다.  

다른 `ChartStyle` 값이나 범례 위치를 자유롭게 실험해 보세요—데이터 시각화는 최고의 프레젠테이션을 받을 자격이 있습니다. 문제가 발생하면 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!

---

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있도록 돕습니다.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}