---
title: Aspose.Words for .NET을 사용하여 Word 문서에 수평선 형태 삽입
weight: 110
limit:
description: Aspose.Words for .NET을 사용하여 Word 문서에 수평선 형태를 삽입하는 단계별 가이드.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 수평선 형태 삽입
Aspose.Words for .NET을 사용해 Word 문서에 수평선 형태를 삽입하는 방법을 배웁니다. 이 튜토리얼에서는 새 문서를 만들고, 텍스트 한 줄을 추가하고, DocumentBuilder로 수평선 형태를 배치한 뒤 파일을 저장하는 과정을 단계별로 안내합니다. 수평선은 콘텐츠 사이에 간단한 시각적 구분선을 제공합니다.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: DocumentBuilder.InsertHorizontalRule()로 삽입한 수평선의 외관(색상, 두께)을 변경할 수 있나요?**
A: InsertHorizontalRule는 기본 서식이 적용된 내장 수평선 형태를 생성합니다; 외관을 수정하려면 삽입된 Shape 객체(builder.CurrentParagraph.LastChild)를 가져와 LineFormat 속성을 조정해야 합니다.

**Q: 이미 줄 바꿈으로 끝나는 단락 뒤에 InsertHorizontalRule()를 호출하면 어떻게 되나요?**
A: 이 메서드는 규칙을 별도의 단락으로 삽입하므로, 앞선 줄 바꿈은 규칙 앞에 빈 단락을 만들 뿐이며, 규칙은 여전히 자체 라인에 표시됩니다.

**Q: DocumentBuilder를 사용해 동일 문서에 여러 개의 수평선을 삽입할 수 있나요?**
A: 네, builder.InsertHorizontalRule()를 호출할 때마다 현재 커서 위치에 새로운 수평선 형태가 추가되어 문서 전체에 여러 규칙을 배치할 수 있습니다.

**Q: InsertHorizontalRule()는 DOCX 외에 PDF와 같은 다른 형식으로 문서를 저장할 때도 작동하나요?**
A: 수평선은 문서 모델에 Shape로 저장되므로 PDF, XPS 또는 기타 지원되는 형식으로 저장할 때도 출력에 올바르게 렌더링됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}