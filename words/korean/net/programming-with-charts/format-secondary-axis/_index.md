---
title: Aspose.Words for .NET을 사용하여 Word 선 차트에서 보조 X축을 서식 지정하고 표시 단위를 천 단위로 설정합니다.
weight: 710
limit:
description: Aspose.Words for .NET을 사용하여 Word 선 차트를 만들고, 보조 X축을 추가한 뒤 표시 단위를 천 단위로 설정하고 사용자 지정 숫자 형식을 적용합니다.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 Word 선 차트를 만들고, 보조 X축을 추가한 뒤 표시 단위를 천 단위로
    설정하고 사용자 지정 숫자 형식을 적용합니다.
  headline: Aspose.Words for .NET을 사용하여 Word 선 차트에서 보조 X축을 서식 지정하고 표시 단위를 천 단위로 설정합니다.
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 선 차트를 만들고, 보조 X축을 추가한 뒤 표시 단위를 천 단위로
    설정하고 사용자 지정 숫자 형식을 적용합니다.
  name: Aspose.Words for .NET을 사용하여 Word 선 차트에서 보조 X축을 서식 지정하고 표시 단위를 천 단위로 설정합니다.
  steps:
  - name: 새 Document와 DocumentBuilder를 생성하여 Word 파일 작성을 시작합니다.
    text: 새 Document와 DocumentBuilder를 생성하여 Word 파일 작성을 시작합니다.
  - name: 문서에 크기 500×300인 선 차트를 삽입하고 Chart 객체를 가져옵니다.
    text: 문서에 크기 500×300인 선 차트를 삽입하고 Chart 객체를 가져옵니다.
  - name: Aspose.Words가 자동으로 추가하는 기본 데모 시리즈를 제거합니다.
    text: Aspose.Words가 자동으로 추가하는 기본 데모 시리즈를 제거합니다.
  - name: X축에 사용할 카테고리 레이블 배열을 정의합니다.
    text: X축에 사용할 카테고리 레이블 배열을 정의합니다.
  - name: 레이블과 값을 사용하여 "Main Data"라는 이름의 기본 데이터 시리즈를 추가합니다.
    text: 레이블과 값을 사용하여 "Main Data"라는 이름의 기본 데이터 시리즈를 추가합니다.
  - name: Line 유형의 보조 시리즈 그룹을 생성하고 이를 보조 축 그룹에 할당합니다.
    text: Line 유형의 보조 시리즈 그룹을 생성하고 이를 보조 축 그룹에 할당합니다.
  - name: 보조 X축의 표시 단위를 천 단위로 설정하여 값이 K로 표시되도록 합니다.
    text: 보조 X축의 표시 단위를 천 단위로 설정하여 값이 K로 표시되도록 합니다.
  - name: 보조 X축 눈금 레이블에 사용자 지정 숫자 형식 "#,##0.0"을 적용합니다.
    text: 보조 X축 눈금 레이블에 사용자 지정 숫자 형식 "#,##0.0"을 적용합니다.
  - name: 선택적으로 보조 그룹에 보조 데이터 시리즈를 추가합니다.
    text: 선택적으로 보조 그룹에 보조 데이터 시리즈를 추가합니다.
  - name: 문서를 .docx 파일로 저장합니다.
    text: 문서를 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: 아니요 – `AxisX` 설정은 `ChartSeriesGroup`에 속하므로, 시리즈를 추가하기 전이나 후에 `secondaryGroup.AxisX.DisplayUnit.Unit`
      및 `secondaryGroup.AxisX.NumberFormat.FormatCode`를 설정할 수 있습니다; 구성은 언제든지 그룹의 축에
      적용됩니다.
    question: 보조 X축의 표시 단위와 숫자 형식을 설정하기 전에 보조 시리즈를 추가해야 하나요?
  - answer: 예 – `AxisBuiltInUnit` 값을 원하는 대로 할당하면 됩니다. 예를 들어 `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;`와 같이 설정하면 축 값이 천이 아니라 백만 단위로 표시됩니다.
    question: 보조 X축에 천이 아닌 백만과 같은 다른 내장 단위를 사용할 수 있나요?
  - answer: 아니요 – 형식 코드는 수정한 축(`secondaryGroup.AxisX.NumberFormat.FormatCode`)에만 적용되므로
      기본 X축은 기본 서식을 유지합니다.
    question: 사용자 지정 형식 \"#,##0.0\"이 기본 X축 레이블에 영향을 미칩니까?
  - answer: 차트에 기본 데모 시리즈가 추가된 상태로 남아, 추가한 시리즈와 함께 표시되어 불필요한 선과 카테고리 불일치가 발생할 수 있습니다.
      컬렉션을 비우면 의도한 데이터만 표시됩니다.
    question: '`lineChart.Series.Clear();`로 데모 시리즈를 삭제하는 것을 잊으면 어떻게 되나요?'
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: 보조 X축 서식 지정 및 단위 천으로 설정
og_description: Word 선 차트에 보조 X축을 추가하고 사용자 지정 패턴으로 레이블을 천 단위로 서식 지정합니다.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 선 차트에 보조 X축을 추가하고 레이블을 천 단위로 표시하도록 서식 지정하는 방법을 안내합니다.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 선 차트에서 보조 X축을 서식 지정하고 표시 단위를 천 단위로 설정합니다.
이 튜토리얼에서는 선 차트가 포함된 Word 문서를 만들고, 보조 X축을 추가한 뒤 해당 축을 천 단위로 표시하도록 구성하는 과정을 단계별로 안내합니다. 또한 보조 축 레이블에 사용자 지정 숫자 형식을 적용하는 방법을 배워 데이터 표시 방식을 정확히 제어할 수 있습니다. 단계별로 따라 하면 Word 보고서에서 다중 축 차트의 가독성을 높일 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: 보조 X축의 표시 단위와 숫자 형식을 설정하기 전에 보조 시리즈를 추가해야 하나요?**  
A: 아니요 – `AxisX` 설정은 `ChartSeriesGroup`에 속하므로, 시리즈를 추가하기 전이나 후에 `secondaryGroup.AxisX.DisplayUnit.Unit` 및 `secondaryGroup.AxisX.NumberFormat.FormatCode`를 설정할 수 있습니다; 구성은 언제든지 그룹의 축에 적용됩니다.

**Q: 보조 X축에 천이 아닌 백만과 같은 다른 내장 단위를 사용할 수 있나요?**  
A: 예 – `AxisBuiltInUnit` 값을 원하는 대로 할당하면 됩니다. 예를 들어 `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;`와 같이 설정하면 축 값이 천이 아니라 백만 단위로 표시됩니다.

**Q: 사용자 지정 형식 \"#,##0.0\"이 기본 X축 레이블에 영향을 미칩니까?**  
A: 아니요 – 형식 코드는 수정한 축(`secondaryGroup.AxisX.NumberFormat.FormatCode`)에만 적용되므로 기본 X축은 기본 서식을 유지합니다.

**Q: `lineChart.Series.Clear();`로 데모 시리즈를 삭제하는 것을 잊으면 어떻게 되나요?**  
A: 차트에 기본 데모 시리즈가 추가된 상태로 남아, 추가한 시리즈와 함께 표시되어 불필요한 선과 카테고리 불일치가 발생할 수 있습니다. 컬렉션을 비우면 의도한 데이터만 표시됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}