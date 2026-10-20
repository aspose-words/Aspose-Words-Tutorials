---
title: Aspose.Words for .NET을 사용하여 Word에서 페이지 크기를 변경할 때 차트를 비례적으로 크기 조정하기
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 문서를 A4로 변경할 때 Word 열 차트를 자동으로 크기 조정하는 방법을 배웁니다.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 문서를 A4로 변경할 때 Word 열 차트를 자동으로 크기 조정하는 방법을
    배웁니다.
  headline: Aspose.Words for .NET을 사용하여 Word에서 페이지 크기를 변경할 때 차트를 비례적으로 크기 조정하기
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 문서를 A4로 변경할 때 Word 열 차트를 자동으로 크기 조정하는 방법을
    배웁니다.
  name: Aspose.Words for .NET을 사용하여 Word에서 페이지 크기를 변경할 때 차트를 비례적으로 크기 조정하기
  steps:
  - name: 새 Document 객체와 이를 편집할 DocumentBuilder를 생성합니다.
    text: 새 Document 객체와 이를 편집할 DocumentBuilder를 생성합니다.
  - name: 432×252 포인트 크기의 열 차트를 삽입하고 해당 Chart 객체를 가져옵니다.
    text: 432×252 포인트 크기의 열 차트를 삽입하고 해당 Chart 객체를 가져옵니다.
  - name: 차트 제목 텍스트를 "Quarterly Revenue" 로 설정하고 표시합니다.
    text: 차트 제목 텍스트를 "Quarterly Revenue" 로 설정하고 표시합니다.
  - name: 원래 차트 크기가 유지된 상태로 문서를 파일에 저장합니다.
    text: 원래 차트 크기가 유지된 상태로 문서를 파일에 저장합니다.
  - name: 문서의 용지 크기를 A4로 변경하고 레이아웃을 새로 고칩니다.
    text: 문서의 용지 크기를 A4로 변경하고 레이아웃을 새로 고칩니다.
  - name: 원래 가로세로 비율을 유지하면서 페이지 너비의 80 %에 해당하는 새로운 차트 너비를 계산합니다.
    text: 원래 가로세로 비율을 유지하면서 페이지 너비의 80 %에 해당하는 새로운 차트 너비를 계산합니다.
  - name: 해당 shape에 차트가 포함되어 있으면, 계산된 너비와 높이를 적용하여 크기를 조정합니다.
    text: 해당 shape에 차트가 포함되어 있으면, 계산된 너비와 높이를 적용하여 크기를 조정합니다.
  - name: 차트가 새 페이지 크기에 맞게 크기가 조정된 후 문서를 저장합니다.
    text: 차트가 새 페이지 크기에 맞게 크기가 조정된 후 문서를 저장합니다.
  type: HowTo
- questions:
  - answer: 예. `docBuilder.PageSetup.PaperSize`를 변경해도 기존 shape가 자동으로 조정되지 않으므로, 예시와
      같이 `chartContainer.Width`와 `Height`를 직접 재계산하여 할당해야 합니다.
    question: 문서의 용지 크기를 변경한 후 차트를 수동으로 크기 조정해야 하나요?
  - answer: '`originalAspectRatio = chartContainer.Height / chartContainer.Width`를
      저장하고, 새로운 너비를 결정한 뒤 `newChartHeight = newChartWidth * originalAspectRatio`를
      계산하여 비율을 유지합니다.'
    question: 코드가 차트를 크기 조정할 때 원래 가로‑세로 비율을 어떻게 유지하나요?
  - answer: '`UpdatePageLayout()`은 레이아웃 엔진이 페이지 차원을 다시 평가하도록 강제하여, 차트 크기를 재계산하기 전에
      `docBuilder.PageSetup.PageWidth`가 새로운 A4 너비를 반영하도록 합니다.'
    question: '`myDoc.UpdatePageLayout()`을 A4 용지 크기로 설정한 후 호출하는 이유는 무엇인가요?'
  - answer: '`if (chartContainer.HasChart)` 조건문은 차트가 없을 때 `Width`와 `Height` 할당을 방지하여
      런타임 예외가 발생하는 것을 막습니다.'
    question: 삽입된 shape에 실제로 차트가 포함되어 있지 않으면 어떻게 되나요?
  - answer: 물론입니다—`0.8` 곱셈자를 원하는 비율로 교체하면 됩니다; 나머지 크기 조정 로직은 여전히 원래 가로세로 비율을 유지합니다.
    question: 80 % 스케일링 팩터를 다른 값으로 변경할 수 있나요?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: A4로 전환할 때 Word 차트 크기 조정
og_description: 문서를 A4로 변경한 후 차트를 자동으로 크기 조정하여 비례를 유지합니다.
og_image_alt: Aspose.Words for .NET을 사용하여 A4 크기의 Word 문서에 맞게 자동으로 크기가 조정된 열 차트를 보여주는 스크린샷
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word에서 페이지 크기를 변경할 때 차트를 비례적으로 크기 조정하기
이 튜토리얼은 Word 문서에 열 차트를 삽입하고, 문서의 페이지 크기를 A4로 전환한 뒤 차트가 새로운 페이지 너비에 비례하도록 자동으로 크기가 조정되는 방법을 보여줍니다. 단계별로 진행하면 차트가 수동으로 스케일링하지 않아도 크기가 조정되어 다양한 페이지 형식에서도 일관된 레이아웃을 유지하는 것을 확인할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: 문서의 용지 크기를 변경한 후 차트를 수동으로 크기 조정해야 하나요?**  
A: 예. `docBuilder.PageSetup.PaperSize`를 변경해도 기존 shape가 자동으로 조정되지 않으므로, 예시와 같이 `chartContainer.Width`와 `Height`를 직접 재계산하여 할당해야 합니다.

**Q: 코드가 차트를 크기 조정할 때 원래 가로‑세로 비율을 어떻게 유지하나요?**  
A: `originalAspectRatio = chartContainer.Height / chartContainer.Width`를 저장하고, 새로운 너비를 결정한 뒤 `newChartHeight = newChartWidth * originalAspectRatio`를 계산하여 비율을 유지합니다.

**Q: `myDoc.UpdatePageLayout()`을 A4 용지 크기로 설정한 후 호출하는 이유는 무엇인가요?**  
A: `UpdatePageLayout()`은 레이아웃 엔진이 페이지 차원을 다시 평가하도록 강제하여, 차트 크기를 재계산하기 전에 `docBuilder.PageSetup.PageWidth`가 새로운 A4 너비를 반영하도록 합니다.

**Q: 삽입된 shape에 실제로 차트가 포함되어 있지 않으면 어떻게 되나요?**  
A: `if (chartContainer.HasChart)` 조건문은 차트가 없을 때 `Width`와 `Height` 할당을 방지하여 런타임 예외가 발생하는 것을 막습니다.

**Q: 80 % 스케일링 팩터를 다른 값으로 변경할 수 있나요?**  
A: 물론입니다—`0.8` 곱셈자를 원하는 비율로 교체하면 됩니다; 나머지 크기 조정 로직은 여전히 원래 가로세로 비율을 유지합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}