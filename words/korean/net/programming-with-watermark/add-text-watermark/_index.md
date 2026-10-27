---
title: Aspose.Words for .NET을 사용하여 Word 문서에 빨간 대각선 텍스트 워터마크 추가
weight: 110
limit:
description: Aspose.Words for .NET을 사용하여 배치에서 생성되는 모든 Word 파일에 빨간 대각선 텍스트 워터마크를 자동으로 적용합니다.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aspose.Words for .NET을 사용하여 배치에서 생성되는 모든 Word 파일에 빨간 대각선 텍스트 워터마크를
    자동으로 적용합니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서에 빨간 대각선 텍스트 워터마크 추가
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 배치에서 생성되는 모든 Word 파일에 빨간 대각선 텍스트 워터마크를
    자동으로 적용합니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서에 빨간 대각선 텍스트 워터마크 추가
  steps:
  - name: \"GeneratedReports\" 폴더를 생성하여 출력 파일을 저장합니다.
    text: \"GeneratedReports\" 폴더를 생성하여 출력 파일을 저장합니다.
  - name: 세 개의 개별 문서를 생성하는 루프를 시작합니다.
    text: 세 개의 개별 문서를 생성하는 루프를 시작합니다.
  - name: 새로운 빈 Word 문서 객체를 생성합니다.
    text: 새로운 빈 Word 문서 객체를 생성합니다.
  - name: DocumentBuilder를 사용하여 문서에 제목 줄과 설명을 씁니다.
    text: DocumentBuilder를 사용하여 문서에 제목 줄과 설명을 씁니다.
  - name: 워터마크의 모양을 정의합니다(글꼴, 크기, 색상 및 대각선 레이아웃 포함).
    text: 워터마크의 모양을 정의합니다(글꼴, 크기, 색상 및 대각선 레이아웃 포함).
  - name: 텍스트 \"PROTECTED\"가 포함된 설정된 빨간 대각선 워터마크를 문서에 적용합니다.
    text: 텍스트 \"PROTECTED\"가 포함된 설정된 빨간 대각선 워터마크를 문서에 적용합니다.
  - name: 워터마크가 적용된 문서를 고유한 파일 이름으로 \"GeneratedReports\" 폴더에 저장합니다.
    text: 워터마크가 적용된 문서를 고유한 파일 이름으로 \"GeneratedReports\" 폴더에 저장합니다.
  - name: 현재 문서를 처리한 후 루프를 종료합니다.
    text: 현재 문서를 처리한 후 루프를 종료합니다.
  type: HowTo
- questions:
  - answer: IsSemitrasparent는 워터마크가 부분 투명도로 렌더링되는지를 결정합니다; **true**로 설정하면 텍스트가 반투명해져
      기본 내용이 더 잘 보이게 됩니다.
    question: '**IsSemitrasparent** 옵션은 무엇을 제어하며, 이를 **true**로 설정하면 어떤 효과가 있나요?'
  - answer: 예—**document.Watermark.SetText**를 호출하기 전에 **TextWatermarkOptions**의 **Layout**
      속성을 **WatermarkLayout.Horizontal**로 설정합니다.
    question: 워터마크 방향을 대각선이 아닌 가로로 변경할 수 있나요?
  - answer: '이 스니펫은 새로운 **Document** 인스턴스를 생성하지만, 기존 파일(예: `new Document(\"Existing.docx\")`)을
      열고 **document.Watermark.SetText**를 호출하여 동일한 워터마크를 적용할 수 있습니다.'
    question: 이 코드가 기존 Word 파일에 워터마크를 추가하나요, 아니면 새로 만든 문서에만 적용되나요?
  - answer: '**TextWatermarkOptions**의 **Color** 속성에 **Color.FromArgb(red, green,
      blue)**를 사용하여 사용자 정의 색상을 지정합니다. 예: 보라색을 위해 `Color = Color.FromArgb(128, 0, 128)`를
      사용합니다.'
    question: 미리 정의된 **Color.Red** 대신 사용자 정의 RGB 색상을 워터마크에 사용하려면 어떻게 해야 하나요?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Word 문서에 빨간 대각선 텍스트 워터마크 추가
og_description: Aspose.Words를 사용하여 배치의 각 Word 문서에 빨간 대각선 워터마크를 자동 적용하는 방법을 확인하세요.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서에 빨간 대각선 텍스트 워터마크를 추가하는 방법을 안내합니다.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 빨간 대각선 텍스트 워터마크 추가
이 튜토리얼은 배치 보고서 생성 중에 생성되는 각 Word 문서에 빨간 대각선 텍스트 워터마크를 자동으로 삽입하는 방법을 보여줍니다. Aspose.Words for .NET의 Document 및 DocumentBuilder 클래스를 사용하여 파일이 생성될 때 프로그래밍 방식으로 워터마크를 적용하므로, 수동 작업 없이 모든 문서에 동일한 브랜딩 또는 기밀성 알림이 포함됩니다.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: **IsSemitrasparent** 옵션은 무엇을 제어하며, 이를 **true**로 설정하면 어떤 효과가 있나요?**  
A: IsSemitrasparent는 워터마크가 부분 투명도로 렌더링되는지를 결정합니다; **true**로 설정하면 텍스트가 반투명해져 기본 내용이 더 잘 보이게 됩니다.

**Q: 워터마크 방향을 대각선이 아닌 가로로 변경할 수 있나요?**  
A: 예—**document.Watermark.SetText**를 호출하기 전에 **TextWatermarkOptions**의 **Layout** 속성을 **WatermarkLayout.Horizontal**로 설정합니다.

**Q: 이 코드가 기존 Word 파일에 워터마크를 추가하나요, 아니면 새로 만든 문서에만 적용되나요?**  
A: 이 스니펫은 새로운 **Document** 인스턴스를 생성하지만, 기존 파일(예: `new Document(\"Existing.docx\")`)을 열고 **document.Watermark.SetText**를 호출하여 동일한 워터마크를 적용할 수 있습니다.

**Q: 미리 정의된 **Color.Red** 대신 사용자 정의 RGB 색상을 워터마크에 사용하려면 어떻게 해야 하나요?**  
A: **TextWatermarkOptions**의 **Color** 속성에 **Color.FromArgb(red, green, blue)**를 사용하여 사용자 정의 색상을 지정합니다. 예: 보라색을 위해 `Color = Color.FromArgb(128, 0, 128)`를 사용합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}