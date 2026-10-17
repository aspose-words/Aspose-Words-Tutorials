---
title: Aspose.Words for .NET을 사용하여 Word 문서 푸터에 페이지 번호 추가
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 Word 문서의 기본 푸터에 자동으로 업데이트되는 페이지 번호를 추가합니다.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aspose.Words for .NET을 사용하여 Word 문서의 기본 푸터에 자동으로 업데이트되는 페이지 번호를 추가합니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서 푸터에 페이지 번호 추가
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 문서의 기본 푸터에 자동으로 업데이트되는 페이지 번호를 추가합니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서 푸터에 페이지 번호 추가
  steps:
  - name: 새 Document 객체와 이에 연결된 DocumentBuilder를 생성합니다.
    text: 새 Document 객체와 이에 연결된 DocumentBuilder를 생성합니다.
  - name: builder의 커서를 첫 번째 섹션의 기본 푸터로 이동합니다.
    text: builder의 커서를 첫 번째 섹션의 기본 푸터로 이동합니다.
  - name: 단락 정렬을 가운데로 설정하여 푸터 텍스트가 중앙에 배치되도록 합니다.
    text: 단락 정렬을 가운데로 설정하여 푸터 텍스트가 중앙에 배치되도록 합니다.
  - name: '"Page " 라벨을 쓰고 현재 페이지 번호를 표시하는 PAGE 필드를 삽입합니다.'
    text: '"Page " 라벨을 쓰고 현재 페이지 번호를 표시하는 PAGE 필드를 삽입합니다.'
  - name: '" of " 를 쓰고 전체 페이지 수를 표시하는 NUMPAGES 필드를 삽입합니다.'
    text: '" of " 를 쓰고 전체 페이지 수를 표시하는 NUMPAGES 필드를 삽입합니다.'
  - name: 문서를 .docx 파일로 저장합니다.
    text: 문서를 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: 아니요. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)`는 builder를 *첫
      번째* 섹션의 기본 푸터로만 이동시키므로, 필드는 그곳에만 삽입됩니다.
    question: 문서에 섹션이 두 개 이상 있는 경우, 이 코드가 모든 섹션의 푸터에 페이지 번호를 추가합니까?
  - answer: '필드를 쓰기 전에 `builder.ParagraphFormat.Alignment`를 다른 `ParagraphAlignment`
      값(예: `ParagraphAlignment.Right`)으로 설정합니다.'
    question: 푸터에 있는 페이지 번호 단락의 정렬을 어떻게 변경할 수 있나요?
  - answer: '`InsertField`는 필드 코드를 받고 선택적인 필드 결과를 받습니다; `null`을 전달하면 Aspose.Words에게
      런타임에 Word가 결과를 계산하도록 지시합니다.'
    question: '`InsertField("PAGE", null)`의 `null` 인자는 무엇을 의미합니까?'
  - answer: 예—필드를 삽입하기 전에 `HeaderFooterType.FooterPrimary`를 `HeaderFooterType.HeaderPrimary`(또는
      다른 헤더 유형)로 교체하면 됩니다.
    question: 같은 "Page X of Y" 필드를 푸터가 아니라 헤더에 배치할 수 있나요?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Word 푸터에 자동 페이지 번호 삽입
og_description: Aspose.Words for .NET을 사용하여 Word 푸터에 실시간 페이지 번호를 추가하는 단계별 코드.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서 푸터에 자동 페이지 번호를 추가하는 방법을 보여주는 가이드
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서 푸터에 페이지 번호 추가
이 튜토리얼은 Aspose.Words Document와 DocumentBuilder를 사용하여 Word 문서의 기본 푸터에 자동으로 업데이트되는 페이지 번호를 삽입하는 방법을 보여줍니다. 페이지 번호를 프로그래밍 방식으로 추가하면 수동 편집 없이 전체 파일에 일관된 페이지 매김을 보장할 수 있습니다. 예제 코드는 .NET 환경에서 바로 실행할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 문서에 섹션이 두 개 이상 있는 경우, 이 코드가 모든 섹션의 푸터에 페이지 번호를 추가합니까?**  
A: 아니요. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)`는 builder를 *첫 번째* 섹션의 기본 푸터로만 이동시키므로, 필드는 그곳에만 삽입됩니다.

**Q: 푸터에 있는 페이지 번호 단락의 정렬을 어떻게 변경할 수 있나요?**  
A: 필드를 쓰기 전에 `builder.ParagraphFormat.Alignment`를 다른 `ParagraphAlignment` 값(예: `ParagraphAlignment.Right`)으로 설정합니다.

**Q: `InsertField("PAGE", null)`의 `null` 인자는 무엇을 의미합니까?**  
A: `InsertField`는 필드 코드를 받고 선택적인 필드 결과를 받습니다; `null`을 전달하면 Aspose.Words에게 런타임에 Word가 결과를 계산하도록 지시합니다.

**Q: 같은 "Page X of Y" 필드를 푸터가 아니라 헤더에 배치할 수 있나요?**  
A: 예—필드를 삽입하기 전에 `HeaderFooterType.FooterPrimary`를 `HeaderFooterType.HeaderPrimary`(또는 다른 헤더 유형)로 교체하면 됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}