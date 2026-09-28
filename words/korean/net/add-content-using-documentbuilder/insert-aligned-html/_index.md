---
title: Aspose.Words for .NET을 사용하여 Word 문서에 정렬된 HTML 삽입
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 특정 정렬이 적용된 HTML을 Word 문서에 삽입하는 방법을 배웁니다.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 정렬된 HTML 삽입
이 튜토리얼은 Aspose.Words for .NET의 DocumentBuilder를 사용해 HTML 마크업을 Word 문서에 삽입하고 정렬을 제어하는 방법을 보여줍니다. HTML을 삽입하고 단락 정렬(왼쪽, 가운데, 오른쪽)을 설정한 뒤 결과 문서를 저장하는 과정을 확인할 수 있습니다. 이 예제는 웹 스타일 형식을 유지하면서 프로그래밍 방식으로 Word 파일을 생성해야 하는 개발자에게 적합합니다.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: InsertHtml을 사용하여 새 문서가 아니라 기존 Word 문서에 HTML을 추가할 수 있나요?**  
A: 예. 기존 파일에서 Document를 생성하고, DocumentBuilder 커서를 HTML을 삽입하고 싶은 위치에 배치합니다(예: builder.MoveToDocumentEnd() 사용). 그런 다음 builder.InsertHtml에 마크업을 전달하여 호출합니다.

**Q: InsertHtml이 정렬을 위해 인식하는 HTML 속성은 무엇인가요?**  
A: InsertHtml은 &lt;p&gt;, &lt;div&gt;, 제목 태그와 같은 블록 레벨 요소의 "align" 속성을 존중하여, 결과 Word 문서에서 해당 단락 정렬을 적용합니다.

**Q: HTML 문자열에 지원되지 않는 태그나 CSS가 포함되어 있으면 어떻게 되나요?**  
A: 지원되지 않는 태그는 무시되고 내부 텍스트는 일반 텍스트로 삽입됩니다; Aspose.Words가 인식하지 못하는 인라인 CSS 스타일도 무시되므로 지원되는 HTML 하위 집합만 렌더링됩니다.

**Q: 문서를 저장하기 전에 DocumentBuilder를 닫아야 하나요?**  
A: 명시적으로 닫을 필요는 없습니다; HTML을 삽입한 후 원하는 파일 이름과 형식으로 doc.Save를 바로 호출하면 되며, Builder의 리소스는 자동으로 해제됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}