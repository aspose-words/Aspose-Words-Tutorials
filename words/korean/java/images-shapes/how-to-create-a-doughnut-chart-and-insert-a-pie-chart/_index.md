---
category: general
date: 2026-10-26
description: Java에서 단계별 코드를 사용해 도넛 차트를 만들고 파이 차트를 삽입하세요. 유연한 차트 시각화를 위한 전체 워크플로우를
  배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: ko
lastmod: 2026-10-26
og_description: 이 가이드를 통해 Java에서 도넛 차트를 만들고, 유연한 시각화를 위해 파이 차트를 삽입하는 방법도 보여줍니다.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: 도넛 차트 만들기 및 파이 차트 삽입 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: 도넛 차트를 만들고 파이 차트를 삽입하는 방법
url: /ko/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 도넛 차트 만들기 및 파이 차트 삽입 방법

Java에서 **도넛 차트 만들기**가 필요하다면, 이 튜토리얼이 정확한 단계를 안내합니다. 또한 동일한 빌더 API를 사용해 **파이 차트 삽입** 방법을 보여주어 시각 스타일을 손쉽게 전환할 수 있습니다. 가이드를 끝까지 따라하면 두 차트 유형을 모두 생성하고 일반적인 커스터마이징을 시연하는 완전한 실행 가능한 프로그램을 얻을 수 있습니다.

튜토리얼 내용:

* 선택한 라이브러리가 제공하는 차트 빌더 초기화  
* 도넛 차트를 만들고 구멍 크기 설정  
* 파이 차트를 삽입하고 강조를 위해 슬라이스를 분리(Explode)  
* 시리즈가 없거나 지원되지 않는 차트 유형과 같은 엣지 케이스 처리 팁

최근 JDK(8 이상)와 차트 라이브러리 JAR만 클래스패스에 있으면 됩니다. 외부 서비스는 필요하지 않습니다.

---

## Prerequisites

| 항목 | 이유 |
|------|------|
| Java Development Kit (JDK) 8+ | 예제를 컴파일하고 실행하는 데 필요합니다. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | 코드에서 사용하는 `ChartBuilder`, `ChartType`, 시리즈 조작 메서드를 제공합니다. |
| An IDE or a text editor | Java 소스 파일을 작성하고 실행하기 위해 필요합니다. |

라이브러리 JAR가 프로젝트 빌드 경로에 추가되었는지 확인하세요. Maven을 사용하는 경우 적절한 의존성을 추가하고, 그렇지 않다면 `libs` 폴더에 JAR를 넣고 컴파일 시 참조합니다.

---

## Step 1: Set up the chart builder

첫 번째 단계는 차트 객체를 생성할 `ChartBuilder`(또는 동등한) 인스턴스를 만드는 것입니다. 이 객체는 팩토리 역할을 하며 차트가 배치될 워크시트 또는 캔버스를 보유합니다.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Why this matters:**  
빌더는 차트를 특정 워크시트에 연결하여 이후 생성되는 모든 차트 객체가 동일한 그리기 영역을 공유하도록 합니다. 이 단계를 건너뛰면 시각 요소의 대상 위치가 지정되지 않습니다.

---

## Step 2: **Create doughnut chart**

이제 정의된 크기의 도넛 차트를 생성합니다. 구멍 크기는 차트 중앙이 얼마나 비어 있는지를 결정하며, 일반 파이를 도넛 형태로 변환합니다.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explanation:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` 은 차트 객체를 만들고 워크시트에 공간을 예약합니다.  
* `setHoleSize(30)` 은 중앙을 30 % 비우는 도넛 차트로 변환합니다.  
* `add("{10, 20, 30, 40}", true)` 은 네 개의 데이터 포인트를 제공하며, `true` 플래그는 값을 단일 시리즈로 처리하도록 라이브러리에 알려줍니다.

**Edge case:** 선택한 차트 유형이 구멍을 지원하지 않을 경우(예: 막대 차트) `getDoughnutChart()` 호출 시 예외가 발생합니다. 구멍 크기를 조정하기 전에 차트 유형을 반드시 확인하세요.

---

## Step 3: **Insert pie chart**

도넛 차트가 준비되면 동일한 빌더를 사용해 **파이 차트 삽입** 방법을 시연합니다. 이 단계는 두 차트 유형 간의 유사성을 강조하고 슬라이스를 강조하는 방법을 보여줍니다.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explanation:**  

* `ChartType.PIE` 은 빌더에게 클래식 파이 차트를 만들도록 지시합니다.  
* `setExplode(10)` 은 첫 번째 슬라이스를 반경의 10 %만큼 오프셋시켜 주요 데이터 포인트를 강조하는 일반적인 기법입니다.  

**Tip:** `setExplode` 메서드는 파이 차트의 첫 번째 시리즈에만 적용됩니다. 여러 시리즈가 있는 경우 올바른 인덱스를 지정해야 합니다.

---

## Step 4: Save the workbook

마지막으로 워크북을 파일에 저장하여 Excel이나 호환 뷰어에서 차트를 확인할 수 있게 합니다.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Why save now:** 워크북을 저장하면 모든 그리기 작업이 최종 확정됩니다. 저장하기 전에 파일을 열면 빈 문서나 불완전한 문서가 나타날 수 있습니다.

**Result:** *DoughnutAndPieChart.xlsx* 파일을 열면 왼쪽에 30 % 구멍이 있는 도넛 차트, 오른쪽에 첫 슬라이스가 분리된 파이 차트가 표시됩니다.

---

## Step 5: Common variations and troubleshooting

| 상황 | 조정 방법 |
|-----------|------------|
| **다른 차트 크기** | `insertChart` 의 너비와 높이 인수를 변경합니다. |
| **여러 데이터 시리즈** | `add` 를 여러 번 호출하거나 2‑D 배열 문자열을 전달합니다. |
| **동적 구멍 크기** | 데이터 범위에 따라 구멍 크기를 계산한 뒤 `setHoleSize` 를 호출합니다. |
| **여러 슬라이스 분리** | `chart.getSeries().get(i).setExplode(percent)` 를 루프 돌면서 원하는 슬라이스마다 오프셋합니다. |
| **라이브러리가 도넛 차트를 지원하지 않음** | 파이 차트를 만든 뒤 흰색 원을 오버레이하여 수동으로 도넛 효과를 만들 수 있지만 정확도는 떨어집니다. |

**Pro tip:** 대용량 워크북을 다룰 때 차트를 삽입한 뒤 `builder.flush()`(가능한 경우)를 호출하면 내부 버퍼가 해제되어 메모리 누수를 방지할 수 있습니다.

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "Java에서 도넛 차트 예제 만들기")

*이미지는 두 차트가 나란히 배치된 최종 워크북 레이아웃을 보여줍니다.*

---

## Conclusion

이제 Java에서 유창한 빌더 API를 사용해 **도넛 차트 만들기**와 **파이 차트 삽입** 방법을 알게 되었습니다. 전체 예제는 초기화, 크기 설정, 구멍 크기 지정, 슬라이스 분리 및 파일 출력까지 다룹니다. 여기서부터 색상, 범례, 데이터 레이블 등 추가 커스터마이징을 탐색하여 보고서 요구사항에 맞출 수 있습니다.

**Next steps**

* **chart customization Java**와 같은 기능(그라디언트 채우기, 데이터 레이블 등)을 실험해 보세요.  
* 차트 생성을 웹 서비스에 통합해 요청 시 워크북을 반환하도록 구현해 보세요.  
* 다른 라이브러리(예: JFreeChart)와 빌더 접근 방식을 비교해 프로젝트에 가장 적합한 방식을 선택하세요.

행복한 차트 만들기!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하도록 돕습니다.

- [Java로 Word 문서에 도넛 차트 만들기](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Java에서 도넛 차트를 편집한 후 Word 문서 저장하기](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Java에서 파이 차트 삽입 – 슬라이스 분리, 회전 및 강조](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}