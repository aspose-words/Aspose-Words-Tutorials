---
title: Aspose.Words for .NET을 사용하여 Word 문서에 정렬된 HTML 삽입
weight: 210
limit:
description: Aspose.Words for .NET을 사용하여 왼쪽, 가운데, 오른쪽 정렬된 원시 HTML을 Word 문서에 삽입하는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 정렬된 HTML 삽입
이 대화형 튜토리얼에서는 Aspose.Words for .NET을 사용하여 원시 HTML을 Word 문서에 삽입하면서 정렬(왼쪽, 가운데, 오른쪽)을 제어하는 방법을 보여줍니다. Document와 DocumentBuilder를 활용하면 HTML 문자열을 삽입하고 원하는 단락 정렬을 몇 줄의 코드만으로 적용할 수 있습니다. HTML 서식을 유지하고 콘텐츠를 문서 내 정확한 위치에 배치해야 할 때 이 예제가 이상적입니다.

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

**Q: DocumentBuilder.InsertHtml에 전달된 HTML 문자열에 Aspose.Words가 지원하지 않는 <script>나 <iframe>과 같은 태그가 포함되어 있으면 어떻게 되나요?**
A: 지원되지 않는 태그는 무시됩니다; Aspose.Words는 렌더링할 수 있는 HTML의 일부만 파싱하므로 <script>, <iframe> 및 유사한 요소는 제거되고 나머지 콘텐츠는 삽입됩니다.

**Q: InsertHtml를 사용할 때 인라인 CSS 스타일(예: <span style\="color:red;\">)이 유지됩니까?**
A: 예, InsertHtml는 색상, 글꼴 크기, 배경 등 많은 인라인 CSS 속성을 인식하여 해당 Word 서식으로 변환합니다.

**Q: InsertHtml가 <div>나 <h1>과 같은 블록 레벨 요소에 대해 자동으로 새 단락을 생성합니까?**
A: 블록 레벨 요소는 Word 단락에 매핑되므로 각 <div>, <p>, <h1> 등은 문서에서 별개의 단락이 됩니다.

**Q: 기존 문서의 시작이 아니라 특정 위치에 HTML을 삽입하려면 어떻게 해야 하나요?**
A: InsertHtml를 호출하기 전에 DocumentBuilder 커서를 원하는 노드(예: builder.MoveToDocumentEnd() 또는 builder.MoveToParagraph(index))로 이동하면 HTML이 현재 커서 위치에 삽입됩니다.

**Q: 문서에 이미 텍스트가 있는 경우 InsertHtml를 호출하면 기존 콘텐츠가 덮어쓰여집니까?**
A: 아니요, InsertHtml는 빌더의 현재 위치에 파싱된 HTML을 삽입하며, 사전에 커서를 해당 노드로 이동하거나 노드를 삭제하지 않는 한 기존 노드를 삭제하지 않습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}