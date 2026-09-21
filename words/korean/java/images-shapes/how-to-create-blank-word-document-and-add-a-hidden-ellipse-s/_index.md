---
category: general
date: 2026-09-21
description: C#를 사용하여 숨겨진 타원이 포함된 빈 Word 문서를 만들기. Word에서 도형을 숨기는 방법과 프로그래밍으로 숨겨진 도형을
  생성하는 방법을 배우세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: ko
lastmod: 2026-09-21
og_description: C#를 사용하여 숨겨진 타원을 포함한 빈 Word 문서를 만들기. 이 가이드는 Word에서 도형을 숨기는 방법과 프로그래밍으로
  숨겨진 도형을 만드는 방법을 보여줍니다.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: C#에서 숨겨진 타원형 모양이 포함된 빈 Word 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: C#에서 빈 Word 문서를 만들고 숨겨진 타원 도형을 추가하는 방법
url: /ko/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 빈 Word 문서를 만들고 숨겨진 타원 도형을 추가하는 방법

빈 **Word 문서**에 보이지 않는 그래픽을 포함해야 할 때, 이 가이드는 정확한 절차를 보여줍니다. 튜토리얼을 마치면 레이아웃에는 보이지 않지만 실제로는 타원 도형이 숨겨진 .docx 파일을 얻게 됩니다.

우리는 Aspose.Words for .NET을 사용하여 문서를 만들고, 타원을 삽입하고, 숨긴 뒤 파일을 저장합니다. 이 단계에서는 **타원 만들기** 객체, **Word에서 도형 숨기기** 방법, 그리고 모든 .NET 프로젝트에서 작동하는 **숨겨진 도형 만들기** 코드를 다룹니다.

## Prerequisites

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 SDK 이상  
* Visual Studio 2022 (또는 기타 C# 편집기)  
* Aspose.Words for .NET 라이선스 또는 무료 평가판  
* C# 구문에 대한 기본적인 이해  

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Aspose.Words로 빈 Word 문서 만들기

첫 번째 단계는 빈 Word 파일을 생성하는 것입니다. 이렇게 하면 나중에 숨겨진 그래픽을 삽입할 수 있는 깨끗한 캔버스를 확보하게 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**왜 빈 문서부터 시작하는가** – 빈 파일에서 시작하면 원하지 않는 내용이 숨겨진 도형에 영향을 주는 것을 방지할 수 있습니다. 또한 파일 크기를 최소화하여 나중에 템플릿으로 사용할 때 유리합니다.

## 빈 문서에 타원 만들기

다음으로 `DocumentBuilder`를 사용해 내용을 추가합니다. 빌더를 이용하면 도형을 원하는 정확한 위치에 배치할 수 있습니다.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**설명** – `ShapeType.Ellipse`는 Aspose.Words에게 원형에 가까운 도형을 그리도록 지시합니다. 너비와 높이는 포인트 단위(1 pt ≈ 1/72 인치)이며, 디자인 요구에 맞게 값을 조정할 수 있습니다.

## Word에서 도형 숨기기 (레이아웃에 표시되지 않게)

숨겨진 도형은 여전히 문서 XML에 존재하므로 메타데이터, 조건부 서식, 혹은 이후 프로그래밍적 수정에 활용할 수 있습니다. 도형을 숨기려면 `Hidden` 속성을 `true`로 설정합니다.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**왜 도형을 숨기는가** – 숨겨진 도형은 레이아웃 엔진에 의해 무시되므로 페이지는 완전히 빈 것처럼 보입니다. 그러나 도형 데이터는 그대로 남아 있어 마커, 북마크, 혹은 하위 프로세스가 읽을 수 있는 사용자 정의 XML을 저장하는 데 유용합니다.

## 숨겨진 도형이 포함된 문서 저장하기

마지막으로 파일을 디스크에 씁니다. 저장된 `.docx` 파일을 Microsoft Word에서 열면 눈에 보이는 내용은 없지만 숨겨진 타원은 여전히 존재합니다.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**검증 방법** – 생성된 파일을 Word에서 연 뒤 `Alt+F9`를 눌러 필드 코드를 토글하고, `Ctrl+A` → `Ctrl+Shift+F9`를 눌러 숨겨진 객체를 확인합니다. 페이지에는 아무 것도 보이지 않지만 문서 XML(`word/document.xml`)에 타원이 포함된 것을 확인할 수 있습니다.

---

## 전체 실행 가능한 예제

아래는 새 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. 모든 `using` 지시문과 `Main` 메서드를 포함하고 있어 추가 설정 없이 바로 실행할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**예상 출력** – 프로그램을 실행하면 콘솔에 파일 경로가 출력되고, 결과 Word 파일에는 보이는 객체가 없습니다. `.docx`가 ZIP 아카이브라는 점을 이용해 압축 해제 도구로 확인하면 `word/document.xml` 안에 `<w:pict>` 요소가 타원을 설명하고 있는 것을 찾을 수 있습니다.

---

## 일반적인 변형 및 엣지 케이스

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **다른 도형** | `ShapeType.Ellipse`를 `ShapeType.Rectangle`, `ShapeType.Line` 등으로 교체 | 동일한 워크플로우를 유지하면서 다른 그래픽을 숨길 수 있습니다. |
| **여러 숨겨진 도형** | `InsertShape`를 여러 번 호출하고 각 도형에 `Hidden = true` 설정 | 마커나 플레이스홀더 컬렉션을 삽입할 때 유용합니다. |
| **조건부 가시성** | `shape.Visible = false`와 `shape.Hidden = true`를 함께 사용 | 일부 구버전 Word는 `Visible`을 다르게 처리하므로 두 속성을 모두 설정하면 모든 경우를 커버합니다. |
| **스트림에 저장** | `doc.Save(path)`를 `doc.Save(stream, SaveFormat.Docx)`로 교체 | 문서를 HTTP로 직접 전송하거나 데이터베이스에 저장할 때 활용됩니다. |
| **스타일 적용** | 삽입 후 `ellipse.FillColor`, `ellipse.LineWeight` 등을 숨기기 전에 수정 | 도형 스타일이 XML에 보존되어 나중에 숨김을 해제할 때 활용할 수 있습니다. |

**Pro tip:** 대상 Word 버전(예: Word 2019, Word 365)에서 숨겨진 도형을 반드시 테스트하세요. 복잡한 페이지 레이아웃과 상호 작용할 때 렌더링 버그가 발생할 수 있습니다.

---

## Frequently asked questions

**Q: 도형을 숨기면 문서 크기에 영향을 줍니까?**  
A: 도형 XML은 수백 바이트 정도 추가되므로 대부분의 사용 사례에서는 무시할 수 있을 정도입니다. 파일 크기는 사실상 완전 빈 문서와 동일합니다.

**Q: 나중에 프로그래밍으로 도형을 다시 보이게 할 수 있나요?**  
A: 가능합니다. 문서를 로드하고 `doc.GetChildNodes(NodeType.Shape, true)`로 도형을 찾은 뒤 `shape.Hidden = false`로 설정하면 됩니다.

**Q: 숨겨진 도형이 인쇄될 때 나타나요?**  
A: 나타나지 않습니다. 숨겨진 객체는 인쇄 레이아웃에서 제외되므로 인쇄된 페이지는 여전히 빈 채입니다.

**Q: 이 방법은 Office Open XML(OOXML) 전용인가요?**  
A: `Hidden` 속성은 OOXML 사양의 일부이므로 OOXML을 완전 구현한 모든 워드 프로세서(Word, LibreOffice, Google Docs 등)에서 해당 플래그를 인식합니다.

---

## Conclusion

이제 **빈 Word 문서 만들기**, **타원 만들기**, **Word에서 도형 숨기기**, 그리고 **Aspose.Words for .NET을 사용한 숨겨진 도형 만들기** 방법을 알게 되었습니다. 튜토리얼에서는 빈 파일 초기화부터 도형 삽입, 숨김, 저장까지 전체 흐름을 다루었으며 검증 단계와 일반적인 변형도 소개했습니다.

다음 단계로 시도해 볼 수 있는 내용:

* 메타데이터용 숨겨진 텍스트 상자 추가 (`hide shape in word` 기법을 텍스트에 적용)  
* 숨겨진 도형과 함께 구조화된 데이터를 저장하기 위한 사용자 정의 XML 파트 활용  
* 숨겨진 도형이 포함된 문서를 PDF로 변환하면서 숨김 요소 유지  

다양한 도형과 가시성 설정을 실험해 보면서 Word 파일 내부에 경량 데이터 저장소로서 숨겨진 콘텐츠를 활용해 보세요.

Happy coding!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하는 주제로, 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}