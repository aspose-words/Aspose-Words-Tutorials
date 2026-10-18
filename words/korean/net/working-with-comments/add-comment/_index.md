---
title: Aspose.Words for .NET을 사용하여 Word 문서의 특정 단락에 Comment를 삽입합니다.
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 Word 문서에서 선택한 단락에 작성자 댓글을 추가하고 DOCX로 저장하는 단계별 가이드입니다.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET을 사용하여 Word 문서에서 선택한 단락에 작성자 댓글을 추가하고 DOCX로 저장하는
    단계별 가이드입니다.
  headline: Aspose.Words for .NET을 사용하여 Word 문서의 특정 단락에 Comment를 삽입합니다.
  type: TechArticle
- description: Aspose.Words for .NET을 사용하여 Word 문서에서 선택한 단락에 작성자 댓글을 추가하고 DOCX로 저장하는
    단계별 가이드입니다.
  name: Aspose.Words for .NET을 사용하여 Word 문서의 특정 단락에 Comment를 삽입합니다.
  steps:
  - name: 새 Document와 DocumentBuilder를 인스턴스화하여 Word 파일 작성을 시작합니다.
    text: 새 Document와 DocumentBuilder를 인스턴스화하여 Word 파일 작성을 시작합니다.
  - name: DocumentBuilder.Writeln을 사용하여 문서에 세 개의 별도 텍스트 단락을 추가합니다.
    text: DocumentBuilder.Writeln을 사용하여 문서에 세 개의 별도 텍스트 단락을 추가합니다.
  - name: 문서에 두 개 미만의 단락이 있을 경우 첫 번째 단락으로 대체하면서 두 번째 단락을 안전하게 가져옵니다.
    text: 문서에 두 개 미만의 단락이 있을 경우 첫 번째 단락으로 대체하면서 두 번째 단락을 안전하게 가져옵니다.
  - name: 작성자 정보를 포함한 Comment를 생성하고 텍스트를 설정한 뒤, 선택한 단락에 첨부합니다.
    text: 작성자 정보를 포함한 Comment를 생성하고 텍스트를 설정한 뒤, 선택한 단락에 첨부합니다.
  - name: 수정된 문서를 현재 폴더에 'sample.docx'라는 이름의 DOCX 파일로 저장합니다.
    text: 수정된 문서를 현재 폴더에 'sample.docx'라는 이름의 DOCX 파일로 저장합니다.
  type: HowTo
- questions:
  - answer: '`if` 블록은 `paraList.Count`가 2보다 작을 때 첫 번째 단락(`paraList[0]`)으로 대체하므로, 댓글이
      두 번째 단락이 없는 대신 해당 단일 단락에 첨부됩니다.'
    question: 문서에 단락이 하나만 포함된 경우 코드가 어떻게 동작합니까?
  - answer: 두 번째와 세 번째 인수로 `Comment` 생성자에 전달됩니다 – `new Comment(wordDoc, \"Jordan\",
      \"JH\", DateTime.Now)` – 여기서 "Jordan"은 작성자 이름이고 "JH"는 이니셜입니다.
    question: 이 예제에서 댓글 작성자 이름과 이니셜은 어떻게 설정됩니까?
  - answer: 이 코드 조각에서는 `AppendChild`를 통해 댓글이 전체 `Paragraph`에 연결되지만, 텍스트 범위에 댓글을 달려면
      원하는 `Run` 노드 주변에 `CommentRangeStart`와 `CommentRangeEnd`를 생성하고 그 사이에 `Comment`
      노드를 추가해야 합니다.
    question: 전체 단락이 아니라 특정 텍스트 조각에 댓글을 첨부할 수 있나요?
  - answer: '`AppendChild`는 `Comment` 노드를 단락의 자식 컬렉션에 추가하고, Aspose.Words는 문서를 저장할
      때 필요한 댓글 시작/끝 마커를 자동으로 생성합니다.'
    question: 댓글 마커를 직접 삽입해야 하나요, 아니면 `AppendChild`가 이를 처리하나요?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Word 단락에 댓글을 삽입합니다.
og_description: 특정 단락에 작성자 댓글을 추가하고 Aspose.Words를 사용하여 파일을 DOCX로 내보냅니다.
og_image_alt: Aspose.Words for .NET을 사용하여 Word 문서의 단락에 댓글을 추가하는 방법을 보여주는 가이드
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서의 특정 단락에 Comment를 삽입합니다.
Aspose.Words for .NET을 사용하면 프로그래밍 방식으로 Word 파일에 댓글을 추가할 수 있습니다. 이 튜토리얼에서는 새 문서를 만들고, 세 개의 단락을 삽입하고, 두 번째 단락을 찾아 작성자 및 날짜 정보를 포함한 댓글을 첨부하는 과정을 단계별로 안내합니다. 마지막으로 댓글을 보존한 채 문서를 DOCX 파일로 저장합니다.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: 문서에 단락이 하나만 포함된 경우 코드가 어떻게 동작합니까?**  
A: `if` 블록은 `paraList.Count`가 2보다 작을 때 첫 번째 단락(`paraList[0]`)으로 대체하므로, 댓글이 두 번째 단락이 없는 대신 해당 단일 단락에 첨부됩니다.

**Q: 이 예제에서 댓글 작성자 이름과 이니셜은 어떻게 설정됩니까?**  
A: 두 번째와 세 번째 인수로 `Comment` 생성자에 전달됩니다 – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – 여기서 "Jordan"은 작성자 이름이고 "JH"는 이니셜입니다.

**Q: 전체 단락이 아니라 특정 텍스트 조각에 댓글을 첨부할 수 있나요?**  
A: 이 코드 조각에서는 `AppendChild`를 통해 댓글이 전체 `Paragraph`에 연결되지만, 텍스트 범위에 댓글을 달려면 원하는 `Run` 노드 주변에 `CommentRangeStart`와 `CommentRangeEnd`를 생성하고 그 사이에 `Comment` 노드를 추가해야 합니다.

**Q: 댓글 마커를 직접 삽입해야 하나요, 아니면 `AppendChild`가 이를 처리하나요?**  
A: `AppendChild`는 `Comment` 노드를 단락의 자식 컬렉션에 추가하고, Aspose.Words는 문서를 저장할 때 필요한 댓글 시작/끝 마커를 자동으로 생성합니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}