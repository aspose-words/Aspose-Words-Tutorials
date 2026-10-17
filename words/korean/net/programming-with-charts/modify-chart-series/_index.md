---
title: Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터를 업데이트합니다.
weight: 610
limit:
description: Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터 포인트를 수정하고 차트를 새로 고치는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터 포인트를 수정하고 차트를 새로 고치는
    방법을 배웁니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터를 업데이트합니다.
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터 포인트를 수정하고 차트를 새로 고치는
    방법을 배웁니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터를 업데이트합니다.
  steps:
  - name: 새 Document를 생성하고 DocumentBuilder를 사용해 열 차트를 삽입한 뒤, 초기 파일로 저장합니다.
    text: 새 Document를 생성하고 DocumentBuilder를 사용해 열 차트를 삽입한 뒤, 초기 파일로 저장합니다.
  - name: 저장된 파일을 열고 차트 모양을 찾아 기존 Chart 객체를 얻습니다.
    text: 저장된 파일을 열고 차트 모양을 찾아 기존 Chart 객체를 얻습니다.
  - name: 첫 번째 시리즈의 값을 Clear하고 새로운 포인트를 추가한 뒤, 두 번째 시리즈에서는 첫 번째 포인트를 제거하고 새로운 포인트를
      추가하여 조정합니다.
    text: 첫 번째 시리즈의 값을 Clear하고 새로운 포인트를 추가한 뒤, 두 번째 시리즈에서는 첫 번째 포인트를 제거하고 새로운 포인트를
      추가하여 조정합니다.
  - name: 수정된 문서를 업데이트된 차트가 포함된 새 파일로 저장합니다.
    text: 수정된 문서를 업데이트된 차트가 포함된 새 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: '`document.GetChildNodes(NodeType.Shape, true)`를 사용해 모든 Shape를 가져온 다음
      `s.HasChart`로 필터링하고 첫 번째(또는 필요한) 차트를 선택합니다 – 이렇게 하면 관련 없는 그림이나 텍스트 상자를 선택하는
      것을 방지할 수 있습니다.'
    question: 다른 모양이 포함될 수 있는 문서에서 차트 모양을 신뢰성 있게 찾으려면 어떻게 해야 하나요?
  - answer: '`ClearValues()`는 기존 데이터 포인트를 제거합니다; 이를 호출하지 않으면 새로운 포인트가 기존 포인트에 추가되어
      카테고리가 중복되거나 총계가 잘못될 수 있습니다.'
    question: 시리즈에 새로운 포인트를 추가하기 전에 `ClearValues()`를 호출해야 하는 이유는 무엇인가요?
  - answer: '차트의 X축 카테고리가 텍스트(예: "Group A")인 경우 `FromString`을 사용하고, 날짜나 측정값과 같이 숫자
      값을 기대하는 경우 `FromDouble`을 사용합니다.'
    question: X축 값에 대해 `ChartXValue.FromString`을 사용해야 할 때와 `ChartXValue.FromDouble`을
      사용해야 할 때는 언제인가요?
  - answer: 존재하지 않는 시리즈에 접근하려고 하면 `ArgumentOutOfRangeException`이 발생합니다; 특정 인덱스를 참조하기
      전에 항상 `existingChart.Series.Count`를 확인하세요.
    question: 차트에 시리즈가 하나만 있을 때 `existingChart.Series[1]`에 접근하면 어떻게 되나요?
  - answer: '`openedDoc`을 저장하면 충분합니다. 왜냐하면 수정된 차트를 포함하고 있는 문서 인스턴스가 `openedDoc`이기
      때문이며, 원본 `document`는 초기 파일을 만들 때만 사용되었습니다.'
    question: 차트를 수정한 후 원본 `document`를 다시 저장해야 하나요, 아니면 `openedDoc`을 저장하는 것으로 충분한가요?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Word에서 차트 시리즈 데이터 편집
og_description: Aspose.Words for .NET을 사용하여 Word 파일에서 차트 시리즈 값을 변경하는 단계별 가이드.
og_image_alt: Aspose.Words for .NET을 사용해 시리즈 데이터를 업데이트하기 전후의 열 차트가 포함된 Word 문서를 보여주는 가이드.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서의 차트 시리즈 데이터를 업데이트합니다.
이 튜토리얼은 열 차트가 포함된 Word 문서를 생성한 뒤 파일을 다시 열어 기존 차트 시리즈를 가져오고 데이터 포인트를 수정하여 차트가 새로운 값을 표시하도록 문서를 저장하는 방법을 보여줍니다. 단계별 코드를 따라 하면 Aspose.Words for .NET으로 차트 데이터를 프로그래밍 방식으로 조정하는 것이 얼마나 간단한지 확인할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: 다른 모양이 포함될 수 있는 문서에서 차트 모양을 신뢰성 있게 찾으려면 어떻게 해야 하나요?**  
A: `document.GetChildNodes(NodeType.Shape, true)`를 사용해 모든 Shape를 가져온 다음 `s.HasChart`로 필터링하고 첫 번째(또는 필요한) 차트를 선택합니다 – 이렇게 하면 관련 없는 그림이나 텍스트 상자를 선택하는 것을 방지할 수 있습니다.

**Q: 시리즈에 새로운 포인트를 추가하기 전에 `ClearValues()`를 호출해야 하는 이유는 무엇인가요?**  
A: `ClearValues()`는 기존 데이터 포인트를 제거합니다; 이를 호출하지 않으면 새로운 포인트가 기존 포인트에 추가되어 카테고리가 중복되거나 총계가 잘못될 수 있습니다.

**Q: X축 값에 대해 `ChartXValue.FromString`을 사용해야 할 때와 `ChartXValue.FromDouble`을 사용해야 할 때는 언제인가요?**  
A: 차트의 X축 카테고리가 텍스트(예: "Group A")인 경우 `FromString`을 사용하고, 날짜나 측정값과 같이 숫자 값을 기대하는 경우 `FromDouble`을 사용합니다.

**Q: 차트에 시리즈가 하나만 있을 때 `existingChart.Series[1]`에 접근하면 어떻게 되나요?**  
A: 존재하지 않는 시리즈에 접근하려고 하면 `ArgumentOutOfRangeException`이 발생합니다; 특정 인덱스를 참조하기 전에 항상 `existingChart.Series.Count`를 확인하세요.

**Q: 차트를 수정한 후 원본 `document`를 다시 저장해야 하나요, 아니면 `openedDoc`을 저장하는 것으로 충분한가요?**  
A: `openedDoc`을 저장하면 충분합니다. 왜냐하면 수정된 차트를 포함하고 있는 문서 인스턴스가 `openedDoc`이기 때문이며, 원본 `document`는 초기 파일을 만들 때만 사용되었습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}