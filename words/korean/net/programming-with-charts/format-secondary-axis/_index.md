---
title: Aspose.Words for .NET을 사용하여 Word 차트에서 보조 Y축을 통화 형식으로 지정하기
weight: 710
limit:
description: Aspose.Words for .NET을 사용하여 Word 라인 차트에 보조 Y축을 추가하고 통화 형식으로 지정하는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 Word 라인 차트에 보조 Y축을 추가하고 통화 형식으로 지정하는 방법을
    배웁니다.
  headline: Aspose.Words for .NET을 사용하여 Word 차트에서 보조 Y축을 통화 형식으로 지정하기
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 라인 차트에 보조 Y축을 추가하고 통화 형식으로 지정하는 방법을
    배웁니다.
  name: Aspose.Words for .NET을 사용하여 Word 차트에서 보조 Y축을 통화 형식으로 지정하기
  steps:
  - name: 새 빈 Word 문서를 만들고 이를 편집하기 위해 DocumentBuilder를 생성합니다.
    text: 새 빈 Word 문서를 만들고 이를 편집하기 위해 DocumentBuilder를 생성합니다.
  - name: 문서에 크기 450×250 포인트인 라인 차트를 삽입하고 해당 Chart 객체를 가져옵니다.
    text: 문서에 크기 450×250 포인트인 라인 차트를 삽입하고 해당 Chart 객체를 가져옵니다.
  - name: Aspose가 새 차트에 추가하는 기본 플레이스홀더 시리즈를 제거합니다.
    text: Aspose가 새 차트에 추가하는 기본 플레이스홀더 시리즈를 제거합니다.
  - name: 분기 라벨을 정의하고 샘플 값을 가진 기본 데이터 시리즈를 차트에 추가합니다.
    text: 분기 라벨을 정의하고 샘플 값을 가진 기본 데이터 시리즈를 차트에 추가합니다.
  - name: Line 유형의 보조 시리즈 그룹을 생성하고 이를 보조 축 그룹에 할당합니다.
    text: Line 유형의 보조 시리즈 그룹을 생성하고 이를 보조 축 그룹에 할당합니다.
  - name: 보조 X축을 숨겨 보조 Y축만 보이도록 합니다.
    text: 보조 X축을 숨겨 보조 Y축만 보이도록 합니다.
  - name: 보조 Y축 제목을 표시하고 텍스트를 "Sales (USD)"로 설정합니다.
    text: 보조 Y축 제목을 표시하고 텍스트를 "Sales (USD)"로 설정합니다.
  - name: 보조 Y축 숫자 형식을 소수점 두 자리 통화 패턴으로 설정하고 원본 서식과 연결을 해제합니다.
    text: 보조 Y축 숫자 형식을 소수점 두 자리 통화 패턴으로 설정하고 원본 서식과 연결을 해제합니다.
  - name: 보조 그룹에 보조 시리즈를 추가하여 보조 Y축에 플롯될 데이터를 제공합니다.
    text: 보조 그룹에 보조 시리즈를 추가하여 보조 Y축에 플롯될 데이터를 제공합니다.
  - name: 완성된 문서를 현재 디렉터리의 ProfitChart.docx 파일로 저장합니다.
    text: 완성된 문서를 현재 디렉터리의 ProfitChart.docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: 차트는 Aspose.Words가 삽입하는 기본 플레이스홀더 시리즈를 유지하므로, 사용자 정의 "Main Series"가 원치
      않는 데이터 포인트와 함께 표시됩니다.
    question: '`lineChart.Series.Clear()` 호출을 생략하면 어떻게 되나요?'
  - answer: '`secondarySeriesGroup.AxisX.Hidden = false;` 로 설정합니다(또는 `true` 로 설정하는
      줄을 생략하면 됩니다).'
    question: 보조 X축을 숨기지 않고 표시하려면 어떻게 해야 하나요?
  - answer: 예 – 형식 문자열을 변경하면 됩니다. 예를 들어 유로화는 `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` 와 같이 설정하거나 로케일에 맞게 패턴을 조정하세요.
    question: 보조 Y축에 다른 통화 기호나 형식을 사용할 수 있나요?
  - answer: '`IsLinkedToSource` 가 true이면 축이 기본 데이터 소스로부터 숫자 형식을 상속받아 사용자 지정 `FormatCode`
      를 무시합니다; false 로 설정하면 차트가 지정한 형식을 사용하도록 강제합니다.'
    question: 사용자 지정 숫자 형식을 적용할 때 `IsLinkedToSource = false` 로 설정해야 하는 이유는 무엇인가요?
  - answer: 예, `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` 로 지정하면(기본값은
      `Right`) 축이 그려지는 측면을 제어할 수 있습니다.
    question: 보조 Y축을 차트의 왼쪽으로 이동시킬 수 있나요?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: 차트의 보조 축을 통화 형식으로 지정하기
og_description: Word 라인 차트에 보조 Y축을 추가하고 소수점 두 자리 통화 형식으로 스타일링하는 방법을 배웁니다.
og_image_alt: Aspose.Words for .NET을 사용하여 보조 Y축이 통화 형식으로 지정된 Word 라인 차트를 보여주는 스크린샷
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 차트에서 보조 Y축을 통화 형식으로 지정하기
이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서를 만들고, 라인 차트를 삽입하고, 보조 Y축을 추가한 뒤 해당 축을 소수점 두 자리 통화 형식으로 지정하고, 보조 데이터 시리즈를 연결하는 방법을 보여줍니다. 보조 축을 통화 형식으로 지정하면 기본 시리즈와 함께 재무 데이터를 명확하게 표시할 수 있습니다. 단계별 코드를 따라 하면 생성된 문서에 차트가 직접 렌더링되는 것을 확인할 수 있습니다.

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

**Q: `lineChart.Series.Clear()` 호출을 생략하면 어떻게 되나요?**  
A: 차트는 Aspose.Words가 삽입하는 기본 플레이스홀더 시리즈를 유지하므로, 사용자 정의 "Main Series"가 원치 않는 데이터 포인트와 함께 표시됩니다.

**Q: 보조 X축을 숨기지 않고 표시하려면 어떻게 해야 하나요?**  
A: `secondarySeriesGroup.AxisX.Hidden = false;` 로 설정합니다(또는 `true` 로 설정하는 줄을 생략하면 됩니다).

**Q: 보조 Y축에 다른 통화 기호나 형식을 사용할 수 있나요?**  
A: 예 – 형식 문자열을 변경하면 됩니다. 예를 들어 유로화는 `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` 와 같이 설정하거나 로케일에 맞게 패턴을 조정하세요.

**Q: 사용자 지정 숫자 형식을 적용할 때 `IsLinkedToSource = false` 로 설정해야 하는 이유는 무엇인가요?**  
A: `IsLinkedToSource` 가 true이면 축이 기본 데이터 소스로부터 숫자 형식을 상속받아 사용자 지정 `FormatCode` 를 무시합니다; false 로 설정하면 차트가 지정한 형식을 사용하도록 강제합니다.

**Q: 보조 Y축을 차트의 왼쪽으로 이동시킬 수 있나요?**  
A: 예, `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` 로 지정하면(기본값은 `Right`) 축이 그려지는 측면을 제어할 수 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}