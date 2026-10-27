---
title: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 열 차트 삽입
weight: 310
limit:
description: Word 파일을 만들고, 열 차트를 삽입한 뒤 데이터를 사용자 정의 배열로 교체하고, 제목을 추가한 뒤 저장합니다—모두 Aspose.Words for .NET을 사용합니다.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Word 파일을 만들고, 열 차트를 삽입한 뒤 데이터를 사용자 정의 배열로 교체하고, 제목을 추가한 뒤 저장합니다—모두
    Aspose.Words for .NET을 사용합니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 열 차트 삽입
  type: TechArticle
- description: Word 파일을 만들고, 열 차트를 삽입한 뒤 데이터를 사용자 정의 배열로 교체하고, 제목을 추가한 뒤 저장합니다—모두
    Aspose.Words for .NET을 사용합니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 열 차트 삽입
  steps:
  - name: 새 Document를 만들고, 해당 Document에 연결된 DocumentBuilder를 생성합니다.
    text: 새 Document를 만들고, 해당 Document에 연결된 DocumentBuilder를 생성합니다.
  - name: 문서에 크기 432x252 포인트인 열 차트를 삽입하고 해당 Chart 객체를 가져옵니다.
    text: 문서에 크기 432x252 포인트인 열 차트를 삽입하고 해당 Chart 객체를 가져옵니다.
  - name: 차트에서 자동으로 생성된 샘플 시리즈를 제거합니다.
    text: 차트에서 자동으로 생성된 샘플 시리즈를 제거합니다.
  - name: X축 카테고리 레이블과 각 시리즈에 대한 범례 항목을 정의합니다.
    text: X축 카테고리 레이블과 각 시리즈에 대한 범례 항목을 정의합니다.
  - name: 각 행이 하나의 시리즈 값을 보관하는 2차원 배열을 생성합니다.
    text: 각 행이 하나의 시리즈 값을 보관하는 2차원 배열을 생성합니다.
  - name: 각 시리즈를 순회하면서 매트릭스에서 해당 행 값을 추출하고, 해당 범례 항목과 X축 레이블을 사용하여 차트에 시리즈를 추가합니다.
    text: 각 시리즈를 순회하면서 매트릭스에서 해당 행 값을 추출하고, 해당 범례 항목과 X축 레이블을 사용하여 차트에 시리즈를 추가합니다.
  - name: 차트 제목 텍스트를 'Half‑Yearly Revenue'로 설정하고 표시하도록 합니다.
    text: 차트 제목 텍스트를 'Half‑Yearly Revenue'로 설정하고 표시하도록 합니다.
  - name: 사용자 정의 차트가 포함된 문서를 .docx 파일로 저장합니다.
    text: 사용자 정의 차트가 포함된 문서를 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add`는 값 배열의 길이가 X축 레이블 수와 동일해야 하며, 각 범례 항목당 정확히 하나의 시리즈를
      추가해야 합니다; 일치하지 않을 경우 런타임에 `ArgumentException`이 발생합니다.'
    question: '`dataMatrix`의 행이나 열이 `legendEntries` 또는 `xLabels`의 길이와 일치하지 않으면 어떻게
      됩니까?'
  - answer: '예—`docBuilder.InsertChart`에서 `ChartType.Column`을 다른 `ChartType`(예: `ChartType.Line`)으로
      교체하면 이후의 `Series.Add` 호출이 동일한 방식으로 새 차트를 채웁니다.'
    question: 같은 데이터 채우기 로직으로 라인 차트와 같은 다른 차트 유형을 사용할 수 있나요?
  - answer: '`InsertChart`가 반환하는 `Shape`의 `Width`와 `Height` 속성을 조정합니다(예: `chartContainer.Width
      = 500; chartContainer.Height = 300;`).'
    question: 차트를 삽입한 후 크기를 어떻게 변경합니까?
  - answer: 시리즈를 추가한 후 각 시리즈에 대해 `chartObj.Series[i].HasDataLabel = true;`를 설정하거나,
      `chartObj.Series`를 순회하면서 `HasDataLabel`을 활성화하면 차트에 값이 표시됩니다.
    question: 차트의 각 열에 데이터 레이블을 표시하는 빠른 방법이 있나요?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Word 문서에 사용자 정의 열 차트 추가
og_description: 차트의 기본 데이터를 자신의 배열로 교체하고 몇 초 만에 제목을 설정합니다.
og_image_alt: Aspose.Words for .NET을 사용해 만든 사용자 정의 열 차트가 포함된 Word 문서를 보여주는 스크린샷
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 열 차트 삽입
이 튜토리얼에서는 Word 문서를 만들고, 열 차트를 삽입한 뒤 기본 데이터를 지우고, 2차원 배열의 사용자 정의 값으로 차트를 채워 각 행을 시리즈, 각 열을 카테고리로 매핑하는 과정을 단계별로 안내합니다. 또한 파일을 저장하기 전에 차트 제목을 추가하는 방법도 보여줍니다. 이 단계를 따라 하면 Word 파일에 완전히 맞춤화된 차트를 직접 만들 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: `dataMatrix`의 행이나 열이 `legendEntries` 또는 `xLabels`의 길이와 일치하지 않으면 어떻게 됩니까?**  
A: `Chart.Series.Add`는 값 배열의 길이가 X축 레이블 수와 동일해야 하며, 각 범례 항목당 정확히 하나의 시리즈를 추가해야 합니다; 일치하지 않을 경우 런타임에 `ArgumentException`이 발생합니다.

**Q: 같은 데이터 채우기 로직으로 라인 차트와 같은 다른 차트 유형을 사용할 수 있나요?**  
A: 예—`docBuilder.InsertChart`에서 `ChartType.Column`을 다른 `ChartType`(예: `ChartType.Line`)으로 교체하면 이후의 `Series.Add` 호출이 동일한 방식으로 새 차트를 채웁니다.

**Q: 차트를 삽입한 후 크기를 어떻게 변경합니까?**  
A: `InsertChart`가 반환하는 `Shape`의 `Width`와 `Height` 속성을 조정합니다(예: `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: 차트의 각 열에 데이터 레이블을 표시하는 빠른 방법이 있나요?**  
A: 시리즈를 추가한 후 각 시리즈에 대해 `chartObj.Series[i].HasDataLabel = true;`를 설정하거나, `chartObj.Series`를 순회하면서 `HasDataLabel`을 활성화하면 차트에 값이 표시됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}