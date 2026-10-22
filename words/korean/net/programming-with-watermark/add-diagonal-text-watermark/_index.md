---
title: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 글꼴로 대각선 텍스트 워터마크 만들기
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 Word .docx에 사용자 정의 글꼴로 대각선 텍스트 워터마크를 추가하는 단계별 코드.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET을 사용하여 Word .docx에 사용자 정의 글꼴로 대각선 텍스트 워터마크를 추가하는
    단계별 코드.
  headline: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 글꼴로 대각선 텍스트 워터마크 만들기
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word .docx에 사용자 정의 글꼴로 대각선 텍스트 워터마크를 추가하는
    단계별 코드.
  name: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 글꼴로 대각선 텍스트 워터마크 만들기
  steps:
  - name: '`document`라는 이름의 새 빈 Word 문서 인스턴스를 생성합니다.'
    text: '`document`라는 이름의 새 빈 Word 문서 인스턴스를 생성합니다.'
  - name: '`watermarkSettings`를 Arial 48pt 회색 글꼴, 대각선 레이아웃, 불투명 렌더링으로 구성합니다.'
    text: '`watermarkSettings`를 Arial 48pt 회색 글꼴, 대각선 레이아웃, 불투명 렌더링으로 구성합니다.'
  - name: 앞서 정의한 설정을 사용하여 텍스트 워터마크 \"Private\"를 `document`에 적용합니다.
    text: 앞서 정의한 설정을 사용하여 텍스트 워터마크 \"Private\"를 `document`에 적용합니다.
  - name: 워터마크가 적용된 문서를 저장할 파일 경로를 정의합니다.
    text: 워터마크가 적용된 문서를 저장할 파일 경로를 정의합니다.
  - name: 수정된 `document`를 지정된 경로에 .docx 파일로 저장합니다.
    text: 수정된 `document`를 지정된 경로에 .docx 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent`는 워터마크를 부분 투명도로 렌더링할지 여부를 결정합니다; `false`로 설정하면 워터마크가
      완전히 불투명해지고, `true`로 설정하면 기본 반투명 효과가 적용됩니다.'
    question: '`TextWatermarkOptions`에서 **IsSemitrasparent** 플래그는 무엇을 제어하나요?'
  - answer: 예—`document.Watermark.SetText`를 호출하기 전에 `Layout` 속성을 `WatermarkLayout.Horizontal`(또는
      다른 열거값)으로 설정하면 됩니다.
    question: 워터마크 방향을 대각선이 아니라 가로로 변경할 수 있나요?
  - answer: Word는 워터마크에 기본 글꼴을 사용하게 되므로 텍스트는 표시되지만 의도한 스타일과 다르게 보일 수 있습니다.
    question: '지정한 `FontFamily`(예: \"Arial\")가 대상 컴퓨터에 설치되어 있지 않으면 어떻게 되나요?'
  - answer: '`Document document = new Document(\"Existing.docx\");` 로 기존 파일을 로드한 뒤,
      `TextWatermarkOptions`를 구성하고 예시와 같이 `document.Watermark.SetText`를 호출합니다.'
    question: 새 파일을 만드는 대신 기존 `.docx` 파일에 워터마크를 추가할 수 있나요?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: 사용자 정의 글꼴로 대각선 텍스트 워터마크 추가
og_description: 몇 분 만에 자신만의 글꼴로 기울어진 텍스트 워터마크를 Word 파일에 삽입하는 방법을 배워보세요.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 글꼴로 대각선 텍스트 워터마크를 추가하는 방법을 보여주는 가이드
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 사용자 정의 글꼴로 대각선 텍스트 워터마크 만들기
이 튜토리얼은 새 Word 문서를 만들고, 선택한 글꼴 설정으로 대각선 텍스트 워터마크를 구성한 뒤, Document.Watermark.SetText API를 통해 적용하고, 결과를 .docx 파일로 저장하는 과정을 단계별로 안내합니다. 완료하면 브랜드나 소유권을 강조하는 전문적인 워터마크가 적용된 문서를 얻게 됩니다. 단계별 코드는 .NET 프로젝트에 바로 복사해 사용할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: `TextWatermarkOptions`에서 **IsSemitrasparent** 플래그는 무엇을 제어하나요?**  
A: `IsSemitrasparent`는 워터마크를 부분 투명도로 렌더링할지 여부를 결정합니다; `false`로 설정하면 워터마크가 완전히 불투명해지고, `true`로 설정하면 기본 반투명 효과가 적용됩니다.

**Q: 워터마크 방향을 대각선이 아니라 가로로 변경할 수 있나요?**  
A: 예—`document.Watermark.SetText`를 호출하기 전에 `Layout` 속성을 `WatermarkLayout.Horizontal`(또는 다른 열거값)으로 설정하면 됩니다.

**Q: 지정한 `FontFamily`(예: \"Arial\")가 대상 컴퓨터에 설치되어 있지 않으면 어떻게 되나요?**  
A: Word는 워터마크에 기본 글꼴을 사용하게 되므로 텍스트는 표시되지만 의도한 스타일과 다르게 보일 수 있습니다.

**Q: 새 파일을 만드는 대신 기존 `.docx` 파일에 워터마크를 추가할 수 있나요?**  
A: `Document document = new Document(\"Existing.docx\");` 로 기존 파일을 로드한 뒤, `TextWatermarkOptions`를 구성하고 예시와 같이 `document.Watermark.SetText`를 호출합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}