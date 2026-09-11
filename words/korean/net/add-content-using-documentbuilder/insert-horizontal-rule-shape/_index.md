---
title: Aspose.Words for .NET을 사용하여 Word 문서에 가로 구분선 형태 삽입
weight: 110
limit:
description: Aspose.Words for .NET과 DocumentBuilder를 사용하여 Word 문서에 가로 구분선 형태를 추가하는 방법을 배웁니다.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET을 사용하여 Word 문서에 가로 구분선 형태 삽입
이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 프로그래밍 방식으로 Word 문서에 가로 구분선 형태를 삽입하는 방법을 배웁니다. Document와 DocumentBuilder 클래스를 이용해 새 문서를 만들고, 텍스트 단락을 추가한 뒤 원하는 위치에 가로 선 형태를 배치합니다. 가로 구분선은 섹션 구분이나 시각적 강조에 유용한 시각적 구분자를 제공합니다.

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

**Q: `builder.InsertHorizontalRule()`가 문서에서 정확히 어느 위치에 선을 삽입하나요?**  
A: `InsertHorizontalRule`는 `DocumentBuilder`의 현재 커서 위치에 가로 구분선 형태를 삽입합니다; 별도의 라인에 놓고 싶다면 삽입하기 전에 `builder.Writeln()`을 호출하세요.

**Q: 삽입된 가로 구분선의 두께, 색상 또는 너비를 변경할 수 있나요?**  
A: `InsertHorizontalRule`는 기본 스타일의 구분선을 추가하며 형식 옵션을 제공하지 않습니다; 이러한 속성을 사용자 정의하려면 `Shape`를 직접 삽입해야 합니다(예: `builder.InsertShape(ShapeType.HorizontalLine)`) 그리고 그 `LineFormat` 속성을 설정하세요.

**Q: 같은 문서에 가로 구분선을 두 개 이상 추가할 수 있나요?**  
A: 예—새 구분선이 필요할 때마다 `builder.InsertHorizontalRule()`를 호출하면 됩니다; 각 호출은 builder의 현재 위치에 별개의 형태를 생성합니다.

**Q: 저장된 .docx 파일을 Microsoft Word에서 열면 가로 구분선이 표시됩니까?**  
A: 물론입니다; 구분선은 .docx 파일 내부에 형태로 저장되므로 Word에서 생성된 문서와 동일하게 표시됩니다.

**Q: `doc.Save(...)`를 호출하기 전에 `dataDir` 폴더가 존재하지 않으면 어떻게 되나요?**  
A: `doc.Save`는 `DirectoryNotFoundException`을 발생시킵니다; 저장하기 전에 대상 디렉터리가 존재하는지 확인하거나 프로그래밍 방식으로 생성하세요.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}