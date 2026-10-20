---
title: Aspose.Words for .NET을 사용하여 Word 문서에 샘플 열 차트를 삽입합니다.
weight: 410
limit:
description: Word 파일을 만들고 DocumentBuilder.InsertChart로 기본 열 차트를 삽입한 뒤 차트 객체에 접근하고 .docx로 저장하는 단계별 가이드입니다.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Word 파일을 만들고 DocumentBuilder.InsertChart로 기본 열 차트를 삽입한 뒤 차트 객체에 접근하고
    .docx로 저장하는 단계별 가이드입니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서에 샘플 열 차트를 삽입합니다.
  type: TechArticle
- description: Word 파일을 만들고 DocumentBuilder.InsertChart로 기본 열 차트를 삽입한 뒤 차트 객체에 접근하고
    .docx로 저장하는 단계별 가이드입니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서에 샘플 열 차트를 삽입합니다.
  steps:
  - name: 빈 Word 문서를 만들고 이를 편집할 DocumentBuilder를 생성합니다.
    text: 빈 Word 문서를 만들고 이를 편집할 DocumentBuilder를 생성합니다.
  - name: 문서에 크기가 432 × 252 포인트인 열 차트를 삽입합니다.
    text: 문서에 크기가 432 × 252 포인트인 열 차트를 삽입합니다.
  - name: 필요에 따라 추가 맞춤 설정을 위해 삽입된 Shape에서 Chart 객체를 가져옵니다.
    text: 필요에 따라 추가 맞춤 설정을 위해 삽입된 Shape에서 Chart 객체를 가져옵니다.
  - name: 삽입된 열 차트가 포함된 문서를 .docx 파일로 저장합니다.
    text: 삽입된 열 차트가 포함된 문서를 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: 크기는 포인트 단위로 지정됩니다(1 포인트 = 1/72 인치). 따라서 432 pt는 약 6인치, 252 pt는 약 3.5인치에
      해당합니다.
    question: InsertChart에서 너비와 높이 매개변수(432, 252)에 사용되는 단위는 무엇인가요?
  - answer: 예—삽입 후 `chartContainer.Chart`를 통해 Chart 객체에 접근할 수 있으며, SeriesCollection,
      Categories, Values를 수정하여 샘플 데이터를 교체할 수 있습니다.
    question: 기본 데이터셋으로 InsertChart를 호출한 후 차트 데이터를 변경할 수 있나요?
  - answer: '`InsertChart` 호출에서 `ChartType.Column`을 `ChartType.Line`과 같은 다른 enum 값으로
      바꾸기만 하면 됩니다.'
    question: '같은 코드를 사용해 다른 차트 유형(예: 선 차트)을 삽입할 수 있나요?'
  - answer: 아니요—`docBuilder.InsertChart`가 차트를 자동으로 `Shape`에 삽입합니다; `wordDoc.Save`를
      호출하면 차트가 문서와 함께 저장됩니다.
    question: 문서를 저장하기 전에 차트를 삽입하기 위해 추가 메서드를 호출해야 하나요?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Word 문서에 샘플 열 차트를 삽입합니다.
og_description: Aspose.Words for .NET을 사용하여 몇 분 안에 Word 문서에 준비된 열 차트를 추가합니다.
og_image_alt: Aspose.Words for .NET을 사용해 삽입된 샘플 열 차트가 포함된 Word 문서를 보여주는 스크린샷
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 샘플 열 차트를 삽입합니다.
이 튜토리얼은 새 Word 문서를 만들고 DocumentBuilder.InsertChart를 사용하여 기본 열 차트를 삽입하는 과정을 단계별로 안내합니다. 또한 포함된 Chart 객체를 가져와 추가로 조작하는 방법을 확인할 수 있습니다. 마지막으로 문서를 .docx 파일로 저장하는 방법을 보여줍니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: InsertChart에서 너비와 높이 매개변수(432, 252)에 사용되는 단위는 무엇인가요?**  
A: 크기는 포인트 단위로 지정됩니다(1 포인트 = 1/72 인치). 따라서 432 pt는 약 6인치, 252 pt는 약 3.5인치에 해당합니다.

**Q: 기본 데이터셋으로 InsertChart를 호출한 후 차트 데이터를 변경할 수 있나요?**  
A: 예—삽입 후 `chartContainer.Chart`를 통해 Chart 객체에 접근할 수 있으며, SeriesCollection, Categories, Values를 수정하여 샘플 데이터를 교체할 수 있습니다.

**Q: 같은 코드를 사용해 다른 차트 유형(예: 선 차트)을 삽입할 수 있나요?**  
A: `InsertChart` 호출에서 `ChartType.Column`을 `ChartType.Line`과 같은 다른 enum 값으로 바꾸기만 하면 됩니다.

**Q: 문서를 저장하기 전에 차트를 삽입하기 위해 추가 메서드를 호출해야 하나요?**  
A: 아니요—`docBuilder.InsertChart`가 차트를 자동으로 `Shape`에 삽입합니다; `wordDoc.Save`를 호출하면 차트가 문서와 함께 저장됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}