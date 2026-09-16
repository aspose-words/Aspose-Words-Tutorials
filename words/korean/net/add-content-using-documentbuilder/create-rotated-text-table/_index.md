---
title: Aspose.Words for .NET을 사용하여 Word 문서에 회전 텍스트 테이블 만들기
weight: 110
limit:
description: Aspose.Words for .NET을 사용하여 고정 열 너비, 회전 텍스트, 정확한 행 높이 및 채워진 셀을 가진 Word 테이블을 만드는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Aspose.Words for .NET을 사용하여 고정 열 너비, 회전 텍스트, 정확한 행 높이 및 채워진 셀을 가진 Word
    테이블을 만드는 방법을 배웁니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서에 회전 텍스트 테이블 만들기
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 고정 열 너비, 회전 텍스트, 정확한 행 높이 및 채워진 셀을 가진 Word
    테이블을 만드는 방법을 배웁니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서에 회전 텍스트 테이블 만들기
  steps:
  - name: 테이블을 구성하는 데 사용할 새 Document와 DocumentBuilder를 인스턴스화합니다.
    text: 테이블을 구성하는 데 사용할 새 Document와 DocumentBuilder를 인스턴스화합니다.
  - name: 새 테이블을 시작하고 첫 번째 셀을 삽입한 뒤 열 너비를 고정하여 자동 조정되지 않도록 합니다.
    text: 새 테이블을 시작하고 첫 번째 셀을 삽입한 뒤 열 너비를 고정하여 자동 조정되지 않도록 합니다.
  - name: 현재 셀의 내용을 수직으로 가운데 정렬하고 첫 번째 행 첫 번째 셀의 텍스트를 씁니다.
    text: 현재 셀의 내용을 수직으로 가운데 정렬하고 첫 번째 행 첫 번째 셀의 텍스트를 씁니다.
  - name: 첫 번째 행의 두 번째 셀을 삽입하고 해당 텍스트를 씁니다.
    text: 첫 번째 행의 두 번째 셀을 삽입하고 해당 텍스트를 씁니다.
  - name: 첫 번째 행을 닫아 레이아웃을 완료합니다.
    text: 첫 번째 행을 닫아 레이아웃을 완료합니다.
  - name: 두 번째 행의 첫 번째 셀을 시작하고 행 높이를 정확히 100포인트로 설정한 뒤 텍스트를 위쪽으로 회전시키고 셀의 텍스트를 씁니다.
    text: 두 번째 행의 첫 번째 셀을 시작하고 행 높이를 정확히 100포인트로 설정한 뒤 텍스트를 위쪽으로 회전시키고 셀의 텍스트를 씁니다.
  - name: 두 번째 행의 두 번째 셀을 삽입하고 텍스트를 아래쪽으로 회전시킨 뒤 셀의 텍스트를 씁니다.
    text: 두 번째 행의 두 번째 셀을 삽입하고 텍스트를 아래쪽으로 회전시킨 뒤 셀의 텍스트를 씁니다.
  - name: 두 번째 행을 닫아 테이블의 두 번째 줄을 완성합니다.
    text: 두 번째 행을 닫아 테이블의 두 번째 줄을 완성합니다.
  - name: 테이블 구성을 종료하여 테이블 구조를 마무리합니다.
    text: 테이블 구성을 종료하여 테이블 구조를 마무리합니다.
  - name: 완성된 문서를 .docx 파일로 저장합니다.
    text: 완성된 문서를 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: 열 너비를 고정한 후 다음 셀을 삽입하기 전에 `builder.CellFormat.Width = <valueInPoints>;`를
      사용하여 각 셀에 너비를 할당하면 테이블이 해당 정확한 너비를 유지합니다.
    question: '`table.AutoFit(AutoFitBehavior.FixedColumnWidths)`를 호출한 후 특정 열 너비를
      어떻게 설정할 수 있나요?'
  - answer: '`builder.CellFormat.VerticalAlignment`은 셀 수준 설정이므로 두 번째 행의 셀에 대해 다시 설정해야
      합니다(예: `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`)
      콘텐츠를 쓰기 전에.'
    question: 수직 정렬이 첫 번째 행에는 적용되지만 두 번째 행에는 적용되지 않는 이유는 무엇인가요?
  - answer: 예—각 `builder.EndRow();` 호출 전에 `builder.RowFormat.Height`와 `builder.RowFormat.HeightRule
      = HeightRule.Exactly`를 설정하면 다음 행에 다른 높이 값을 지정할 수 있습니다.
    question: 각 행에 서로 다른 정확한 높이를 지정할 수 있나요? 가능하다면 어떻게 해야 하나요?
  - answer: 다음 셀에 쓰기 전에 `builder.CellFormat.Orientation = TextOrientation.Horizontal;`을
      할당하여 방향을 초기화합니다.
    question: '`TextOrientation.Upward` 또는 `Downward`를 사용한 후 텍스트 방향을 기본값으로 되돌리려면 어떻게
      해야 하나요?'
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Aspose.Words를 사용하여 Word에 회전 텍스트 테이블 만들기
og_description: 수직으로 회전된 텍스트와 정확한 행 높이를 가진 고정 너비 테이블을 만드는 단계별 코드.
og_image_alt: Aspose.Words for .NET을 사용하여 만든 고정 열 너비, 셀 내 회전 텍스트 및 정의된 행 높이를 가진 테이블이 포함된 Word 문서의 스크린샷
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 회전 텍스트 테이블 만들기
이 튜토리얼은 Word 문서를 생성하고 열이 고정 너비를 가지고 행이 정확한 높이를 가지며 셀 텍스트가 수직으로 회전된 테이블을 추가하는 방법을 보여줍니다. 수직 정렬 설정, 텍스트 방향 적용, 각 셀에 내용을 채우는 방법을 배우고 최종적으로 Aspose.Words for .NET을 사용해 문서를 저장합니다.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`를 호출한 후 특정 열 너비를 어떻게 설정할 수 있나요?**  
A: 열 너비를 고정한 후 다음 셀을 삽입하기 전에 `builder.CellFormat.Width = <valueInPoints>;`를 사용하여 각 셀에 너비를 할당하면 테이블이 해당 정확한 너비를 유지합니다.

**Q: 수직 정렬이 첫 번째 행에는 적용되지만 두 번째 행에는 적용되지 않는 이유는 무엇인가요?**  
A: `builder.CellFormat.VerticalAlignment`은 셀 수준 설정이므로 두 번째 행의 셀에 대해 다시 설정해야 합니다(예: `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) 콘텐츠를 쓰기 전에.

**Q: 각 행에 서로 다른 정확한 높이를 지정할 수 있나요? 가능하다면 어떻게 해야 하나요?**  
A: 예—각 `builder.EndRow();` 호출 전에 `builder.RowFormat.Height`와 `builder.RowFormat.HeightRule = HeightRule.Exactly`를 설정하면 다음 행에 다른 높이 값을 지정할 수 있습니다.

**Q: `TextOrientation.Upward` 또는 `Downward`를 사용한 후 텍스트 방향을 기본값으로 되돌리려면 어떻게 해야 하나요?**  
A: 다음 셀에 쓰기 전에 `builder.CellFormat.Orientation = TextOrientation.Horizontal;`을 할당하여 방향을 초기화합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}