---
title: Aspose.Words for .NET을 사용하여 하이퍼링크 주석을 추가하고 PDF 주석으로 내보내기
weight: 110
limit:
description: Aspose.Words for .NET을 사용하여 Word 파일에 하이퍼링크 주석을 추가하고 이를 PDF 주석으로 내보내는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 Word 파일에 하이퍼링크 주석을 추가하고 이를 PDF 주석으로 내보내는
    방법을 배웁니다.
  headline: Aspose.Words for .NET을 사용하여 하이퍼링크 주석을 추가하고 PDF 주석으로 내보내기
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 파일에 하이퍼링크 주석을 추가하고 이를 PDF 주석으로 내보내는
    방법을 배웁니다.
  name: Aspose.Words for .NET을 사용하여 하이퍼링크 주석을 추가하고 PDF 주석으로 내보내기
  steps:
  - name: 새로운 빈 Document 객체와 이를 작업할 DocumentBuilder를 생성합니다.
    text: 새로운 빈 Document 객체와 이를 작업할 DocumentBuilder를 생성합니다.
  - name: 다음에 추가될 주석이 들어갈 보이는 텍스트 한 줄을 작성합니다.
    text: 다음에 추가될 주석이 들어갈 보이는 텍스트 한 줄을 작성합니다.
  - name: Jane Doe가 작성한 Comment를 생성하고 이를 문서의 첫 번째 단락에 첨부합니다.
    text: Jane Doe가 작성한 Comment를 생성하고 이를 문서의 첫 번째 단락에 첨부합니다.
  - name: 주석 안에 단락을 추가하고 Aspose.Words Library 웹사이트로 연결되는 파란색 밑줄 하이퍼링크를 삽입합니다.
    text: 주석 안에 단락을 추가하고 Aspose.Words Library 웹사이트로 연결되는 파란색 밑줄 하이퍼링크를 삽입합니다.
  - name: 문서가 주석을 PDF 주석으로 렌더링하도록 구성하고 레이아웃을 새로 고칩니다.
    text: 문서가 주석을 PDF 주석으로 렌더링하도록 구성하고 레이아웃을 새로 고칩니다.
  - name: 생성된 PDF를 저장하기 위해 현재 디렉터리에 "Output" 폴더를 만듭니다.
    text: 생성된 PDF를 저장하기 위해 현재 디렉터리에 "Output" 폴더를 만듭니다.
  - name: PdfSaveOptions를 사용하여 준비된 문서를 PDF 파일로 저장합니다.
    text: PdfSaveOptions를 사용하여 준비된 문서를 PDF 파일로 저장합니다.
  - name: PDF 파일이 존재하고 데이터가 포함되어 있는지 확인한 후, 결과를 콘솔에 출력합니다.
    text: PDF 파일이 존재하고 데이터가 포함되어 있는지 확인한 후, 결과를 콘솔에 출력합니다.
  type: HowTo
- questions:
  - answer: '`InsertHyperlink`의 세 번째 매개변수는 링크를 필드로 처리할지 여부를 지정합니다; `false`로 설정하면 필드
      코드를 필요로 하지 않고 PDF 주석에서 작동하는 일반 하이퍼링크가 삽입됩니다.'
    question: '`InsertHyperlink`의 세 번째 인수(`false`)는 무엇을 제어합니까?'
  - answer: '`Save`를 호출하기 전에 `myDocument.LayoutOptions.CommentDisplayMode`를 `CommentDisplayMode.ShowInBalloons`로
      설정하면 PDF에 주석이 일반 Word 주석으로 포함되어 말풍선 형태로 표시됩니다.'
    question: 주석을 PDF 주석이 아니라 Word 문서에서 말풍선 형태로 표시하려면 어떻게 해야 하나요?
  - answer: 예—단락에 추가하는 각 `Comment`는 자체 `InsertHyperlink` 호출을 포함할 수 있으며, 문서를 저장할 때
      모든 하이퍼링크가 별개의 PDF 주석으로 보존됩니다.
    question: 주석을 하나 이상 추가하면, 각각의 하이퍼링크가 내보낸 PDF에서 모두 작동합니까?
  - answer: 생성된 PDF를 열고, 주석 주석(보통 메모 아이콘으로 표시)을 찾아 클릭하여 주석 텍스트를 표시한 다음, 파란색 밑줄 링크를
      클릭합니다; 그러면 웹 브라우저에서 대상 URL이 열려야 합니다.
    question: PDF가 생성된 후 주석 안의 하이퍼링크가 실제로 작동하는지 어떻게 확인합니까?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: 하이퍼링크 주석 삽입 및 PDF로 내보내기
og_description: Word 주석에 클릭 가능한 링크를 삽입하고 이를 PDF 주석으로 변환하는 방법을 배웁니다.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서에 클릭 가능한 하이퍼링크가 포함된 주석을 추가하고 이를 PDF 주석으로 내보내는 방법을 보여주는 가이드
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 하이퍼링크 주석을 추가하고 PDF 주석으로 내보내기
이 튜토리얼에서는 Word 문서를 생성하고, 외부 웹사이트로 연결되는 클릭 가능한 하이퍼링크가 포함된 주석을 삽입한 뒤, 해당 주석을 PDF 주석으로 표시하도록 구성하고, 문서를 PDF로 내보내며, 결과 PDF 파일을 확인하는 방법을 보여줍니다. 단계별 코드를 통해 풍부하고 링크가 활성화된 주석을 추가하고 PDF로 변환할 때 이를 보존할 수 있어 독자와 인터랙티브한 메모를 쉽게 공유할 수 있습니다.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: `InsertHyperlink`의 세 번째 인수(`false`)는 무엇을 제어합니까?**  
A: `InsertHyperlink`의 세 번째 매개변수는 링크를 필드로 처리할지 여부를 지정합니다; `false`로 설정하면 필드 코드를 필요로 하지 않고 PDF 주석에서 작동하는 일반 하이퍼링크가 삽입됩니다.

**Q: 주석을 PDF 주석이 아니라 Word 문서에서 말풍선 형태로 표시하려면 어떻게 해야 하나요?**  
A: `Save`를 호출하기 전에 `myDocument.LayoutOptions.CommentDisplayMode`를 `CommentDisplayMode.ShowInBalloons`로 설정하면 PDF에 주석이 일반 Word 주석으로 포함되어 말풍선 형태로 표시됩니다.

**Q: 주석을 하나 이상 추가하면, 각각의 하이퍼링크가 내보낸 PDF에서 모두 작동합니까?**  
A: 예—단락에 추가하는 각 `Comment`는 자체 `InsertHyperlink` 호출을 포함할 수 있으며, 문서를 저장할 때 모든 하이퍼링크가 별개의 PDF 주석으로 보존됩니다.

**Q: PDF가 생성된 후 주석 안의 하이퍼링크가 실제로 작동하는지 어떻게 확인합니까?**  
A: 생성된 PDF를 열고, 주석 주석(보통 메모 아이콘으로 표시)을 찾아 클릭하여 주석 텍스트를 표시한 다음, 파란색 밑줄 링크를 클릭합니다; 그러면 웹 브라우저에서 대상 URL이 열려야 합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}