---
title: Aspose.Words for .NET을 사용하여 Word에서 차트 제목을 업데이트하고 범례 표시 여부를 전환하기
weight: 810
limit:
description: Aspose.Words for .NET을 사용하여 Word 문서에서 차트 제목을 변경하고 범례 표시 여부를 제어하는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 Word 문서에서 차트 제목을 변경하고 범례 표시 여부를 제어하는 방법을
    배웁니다.
  headline: Aspose.Words for .NET을 사용하여 Word에서 차트 제목을 업데이트하고 범례 표시 여부를 전환하기
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 문서에서 차트 제목을 변경하고 범례 표시 여부를 제어하는 방법을
    배웁니다.
  name: Aspose.Words for .NET을 사용하여 Word에서 차트 제목을 업데이트하고 범례 표시 여부를 전환하기
  steps:
  - name: 사용자가 제공한 차트 제목과 범례를 표시할지 여부를 정의합니다.
    text: 사용자가 제공한 차트 제목과 범례를 표시할지 여부를 정의합니다.
  - name: 새 Word 문서를 만들고, 내용을 추가하기 위해 DocumentBuilder를 생성합니다.
    text: 새 Word 문서를 만들고, 내용을 추가하기 위해 DocumentBuilder를 생성합니다.
  - name: 문서에 432 × 252 pt 크기의 열 차트를 삽입하고, 해당 Shape에 실제로 차트가 포함되어 있는지 확인합니다.
    text: 문서에 432 × 252 pt 크기의 열 차트를 삽입하고, 해당 Shape에 실제로 차트가 포함되어 있는지 확인합니다.
  - name: 차트 객체를 가져와서 제목 텍스트를 사용자 값으로 설정하고, 제목이 표시되도록 합니다.
    text: 차트 객체를 가져와서 제목 텍스트를 사용자 값으로 설정하고, 제목이 표시되도록 합니다.
  - name: '범례를 구성합니다: 요청 시 오른쪽에 표시하고, 그렇지 않으면 숨기며, 플롯 영역 위에 겹치도록 허용합니다.'
    text: '범례를 구성합니다: 요청 시 오른쪽에 표시하고, 그렇지 않으면 숨기며, 플롯 영역 위에 겹치도록 허용합니다.'
  - name: 수정된 문서를 CustomChart.docx 파일명으로 디스크에 저장합니다.
    text: 수정된 문서를 CustomChart.docx 파일명으로 디스크에 저장합니다.
  type: HowTo
- questions:
  - answer: '`displayLegend`가 `true`일 때, 코드는 `chartLegend.Position`을 `LegendPosition.Right`로
      설정하여 플롯 영역 오른쪽에 범례가 표시되게 합니다; `Overlay` 속성은 `true`로 유지되므로 범례가 차트와 겹쳐 공간을 절약할
      수 있습니다.'
    question: '`displayLegend`를 `true`로 설정하면 생성된 차트에서 무엇이 변경됩니까?'
  - answer: '`chartTitle.Text`를 할당한 후 `chartTitle.Show = false`로 설정하거나(또는 `Show`를
      `true`로 설정하지 않으면) 차트 제목이 Word 문서에 렌더링되지 않게 됩니다.'
    question: 사용자가 차트 제목을 제공하지 않을 경우 차트 제목을 숨기려면 어떻게 해야 하나요?
  - answer: 예—`InsertChart`는 차트를 포함해야 하는 `Shape`를 반환하지만, `HasChart`를 확인하면 해당 Shape에
      실제로 `Chart` 객체가 있는지 보장합니다; 그렇지 않으면 코드가 `InvalidOperationException`을 발생시킵니다.
    question: '`InsertChart` 호출 후 `chartContainer.HasChart`를 확인해야 합니까?'
  - answer: 물론 가능합니다; `LegendPosition` 열거형의 원하는 값을(`LegendPosition.Top`, `LegendPosition.Bottom`,
      `LegendPosition.Left` 등) `chartLegend.Position`에 할당하면 필요에 따라 범례 위치를 변경할 수 있습니다.
    question: 범례를 오른쪽이 아닌 다른 위치에 배치할 수 있나요?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Word에서 차트 제목 및 범례 변경
og_description: Aspose.Words for .NET을 사용하여 Word 문서에서 사용자 정의 차트 제목을 설정하고 범례 표시를 제어하는 방법을 배웁니다.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서에서 차트 제목을 업데이트하고 범례를 전환하는 코드를 보여주는 가이드
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word에서 차트 제목을 업데이트하고 범례 표시 여부를 전환하기
이 튜토리얼은 Aspose.Words for .NET을 사용하여 Word 문서 내부의 차트를 프로그래밍 방식으로 수정하는 방법을 보여줍니다. 열 차트를 삽입하고, 차트 제목을 사용자가 제공한 텍스트로 교체하며, 사용자 선호도에 따라 범례의 표시 여부와 오버레이를 제어하는 방법을 배웁니다. 이러한 단계들을 통해 수동 편집 없이 차트 표시를 동적으로 맞춤 설정할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `displayLegend`를 `true`로 설정하면 생성된 차트에서 무엇이 변경됩니까?**  
A: `displayLegend`가 `true`일 때, 코드는 `chartLegend.Position`을 `LegendPosition.Right`로 설정하여 플롯 영역 오른쪽에 범례가 표시되게 합니다; `Overlay` 속성은 `true`로 유지되므로 범례가 차트와 겹쳐 공간을 절약할 수 있습니다.

**Q: 사용자가 차트 제목을 제공하지 않을 경우 차트 제목을 숨기려면 어떻게 해야 하나요?**  
A: `chartTitle.Text`를 할당한 후 `chartTitle.Show = false`로 설정하거나(또는 `Show`를 `true`로 설정하지 않으면) 차트 제목이 Word 문서에 렌더링되지 않게 됩니다.

**Q: `InsertChart` 호출 후 `chartContainer.HasChart`를 확인해야 합니까?**  
A: 예—`InsertChart`는 차트를 포함해야 하는 `Shape`를 반환하지만, `HasChart`를 확인하면 해당 Shape에 실제로 `Chart` 객체가 있는지 보장합니다; 그렇지 않으면 코드가 `InvalidOperationException`을 발생시킵니다.

**Q: 범례를 오른쪽이 아닌 다른 위치에 배치할 수 있나요?**  
A: 물론 가능합니다; `LegendPosition` 열거형의 원하는 값을(`LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left` 등) `chartLegend.Position`에 할당하면 필요에 따라 범례 위치를 변경할 수 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}