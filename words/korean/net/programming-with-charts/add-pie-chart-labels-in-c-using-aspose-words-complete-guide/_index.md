---
category: general
date: 2026-07-20
description: Aspose.Words for .NET을 사용하여 파이 차트 레이블을 추가합니다. 파이 차트 레이블을 변경하고, 백분율 레이블을
  표시하며, 차트 시리즈 레이블을 빠르게 업데이트하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: ko
lastmod: 2026-07-20
og_description: Aspose.Words를 사용하여 C#에서 파이 차트 레이블을 추가합니다. 몇 단계만으로 파이 차트 레이블을 변경하고,
  백분율 레이블을 표시하며, 차트 시리즈 레이블을 업데이트하는 방법을 마스터하세요.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: C#에서 파이 차트 레이블 추가 – Aspose.Words 전체 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Aspose.Words를 사용한 C# 파이 차트 레이블 추가 – 완전 가이드
url: /ko/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 Aspose.Words를 사용하여 파이 차트 레이블 추가 – 완전 가이드

C#를 사용하여 Word 문서에 **파이 차트 레이블**을 추가해야 하나요? Aspose.Words를 사용하면 파일 내부에서 **파이 차트 레이블을 변경**하고 **파이 차트 백분율을 표시**할 수 있어 Word에서 수동으로 조정할 필요가 없습니다.  

이 튜토리얼에서는 **백분율 레이블 표시**, 레이블 위치 재조정, 그리고 동적 데이터를 위한 **차트 시리즈 레이블 업데이트**까지 정확한 단계를 안내합니다. 끝까지 진행하면 .NET 프로젝트 어디에든 삽입할 수 있는 재사용 가능한 스니펫을 얻게 됩니다.

> **빠른 미리보기:** 가이드를 따라 하면 저장된 `.docx` 파일을 열었을 때 각 조각에 백분율이 표시된 파이 차트가 조각 외부에 레이블이 배치된 모습을 확인할 수 있습니다.

---

## 필요 사항

- **Aspose.Words for .NET** (2026년 현재 최신 버전). NuGet에서 가져올 수 있습니다: `Install-Package Aspose.Words`.
- 이미 파이 차트 또는 도넛 차트가 포함된 **Word 문서** (예: `Chart.docx`).
- **C#**와 Visual Studio(또는 선호하는 IDE)에 대한 기본적인 이해.

그게 전부입니다—추가 라이브러리도, COM 인터옵도 필요 없으며 순수 관리 코드만 사용합니다.

---

## 파이 차트 레이블 추가 – 전체 구현

아래는 문서를 로드하고 첫 번째 파이 차트를 수정한 뒤 결과를 저장하는 **완전하고 실행 가능한** C# 콘솔 프로그램입니다. 모든 라인에 주석이 달려 있어 **무엇을** 하는지뿐만 아니라 **왜** 하는지도 이해할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### 예상 결과

Microsoft Word에서 `ChartWithCustomLabels.docx`를 열면 **각 조각 외부에 백분율 레이블이 배치된** 파이 차트를 확인할 수 있습니다. 레이블은 “35 %”, “20 %” 등과 같이 표시되어 차트를 즉시 이해할 수 있게 합니다.

---

## 파이 차트 레이블 변경: 위치 지정 및 서식

백분율을 표시하지 않고 **파이 차트 레이블만 변경**하려면 `Position` 속성을 다음 중 하나로 조정하면 됩니다:

| Position Enum | 시각 효과 |
|---------------|-----------|
| `InsideEnd`   | 레이블이 조각 내부 가장자리 쪽에 배치됩니다. |
| `Center`      | 레이블이 조각 중앙에 나타납니다(작은 파이에 적합). |
| `OutsideEnd`  | 레이블이 조각 외부에 배치되고 리더 라인으로 연결됩니다(기본값). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Pro tip:** `OutsideEnd`는 조각이 많이 있을 때 가장 효과적이며 텍스트 겹침을 방지합니다.

---

## 파이 차트에 백분율 레이블 표시

`ShowPercentage` 속성은 **불리언 플래그**입니다. 이를 `true`로 설정하면 Aspose.Words가 기본 데이터 소스를 기반으로 각 조각의 기여도를 계산합니다.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

원시 숫자 **와** 백분율을 모두 표시하려면 `ShowValue`와 함께 사용할 수 있습니다:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

두 플래그가 모두 활성화되면 레이블은 “45 % (120)”와 같이 표시됩니다.

---

## 동적 데이터를 위한 차트 시리즈 레이블 업데이트

보통 차트를 실시간으로 생성합니다—예를 들어 월별 매출이나 설문 결과 등. 프로그램matically **차트 시리즈 레이블을 업데이트**하려면 데이터 레이블을 다루기 전에 `Series` 컬렉션을 수정합니다:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

이 스니펫은 첫 번째 시리즈에 국한되지 않고 모든 시리즈에 대해 **차트 시리즈 레이블을 업데이트**하는 방법을 보여줍니다. 실제 데이터와 예측 데이터를 결합한 보고서를 만들 때 유용합니다.

---

## 엣지 케이스 및 일반적인 함정

| 상황 | 주의할 점 | 해결 방법 |
|------|-----------|-----------|
| **차트가 파이/도넛이 아님** | `Position`이 시각적으로 적용되지 않을 수 있습니다. | `chart.Type`이 `ChartType.Pie` 또는 `ChartType.Doughnut`인지 확인하세요. |
| **차트를 찾을 수 없음** | `GetChild`가 `null`을 반환합니다. | 가드 절을 추가하고(코드 참고) 유용한 메시지를 로그에 남기세요. |
| **구버전 Word** | 일부 레이블 기능이 무시됩니다. | 최신 형식인 `.docx`로 저장하여 전체 지원을 보장하세요. |
| **조각 수가 많음** | `OutsideEnd`를 사용해도 레이블이 겹칠 수 있습니다. | 조각 수를 줄이거나 차트 크기를 늘리는 것을 고려하세요. |

---

## 전체 작업 예제 (복사‑붙여넣기)

아래는 **전체 프로그램**이며 새 콘솔 프로젝트에 복사해 바로 사용할 수 있습니다. `YOUR_DIRECTORY`를 `Chart.docx`가 들어 있는 폴더 경로로 교체하면 됩니다.



## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}