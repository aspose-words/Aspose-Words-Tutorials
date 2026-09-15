---
category: general
date: 2026-09-14
description: C#를 사용하여 Word에서 도형을 숨기는 방법을 배우세요—워드 문서 생성 코드, 사각형 도형 삽입, 그리고 프로그래밍으로
  Word에서 도형을 숨기는 방법을 포함합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: ko
lastmod: 2026-09-14
og_description: C#를 사용해 Word에서 도형을 숨기는 방법—워드 문서 코드를 생성하고 사각형 도형을 삽입하는 방법까지 단계별로 안내합니다.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: C# 코드를 사용하여 Word 문서에서 도형 숨기기
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# 코드를 사용하여 Word 문서에서 도형을 숨기는 방법
url: /ko/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# 코드로 Word 문서에서 도형 숨기기

Word 파일에서 **도형을 숨기는 방법**이 필요하다면, 이 튜토리얼이 완전한 솔루션을 제공합니다. Word 문서를 생성하고, 사각형 도형을 삽입한 뒤, 타원을 추가하고 해당 타원을 숨겨서 파일을 열었을 때 사각형만 보이도록 하는 과정을 확인할 수 있습니다.

외부 참조 없이 코드와 설명만으로 모든 것을 다룹니다. 끝까지 따라 하면 프로그래밍으로 생성하는 모든 Word 문서에 숨겨진 그래픽을 삽입할 수 있게 됩니다.

## 사전 요구 사항

- .NET 6.0 이상 (.NET Framework 4.7+에서도 동작)
- Aspose.Words for .NET (무료 평가판 또는 정식 라이선스)  
  NuGet으로 설치: `dotnet add package Aspose.Words`
- C#와 Visual Studio(또는 선호하는 IDE)에 대한 기본 지식

## 1단계: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 애플리케이션을 만들고 필요한 `using` 문을 추가합니다. 이 임포트는 `Document`, `DocumentBuilder`, 그리고 도형 조작에 필요한 그리기 클래스를 사용할 수 있게 해줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**왜 중요한가** – 올바른 네임스페이스를 가져와야 컴파일 오류를 방지하고, 도형 생성 및 가시성 제어를 위한 API를 사용할 수 있습니다.

## 2단계: 새 Word 문서와 빌더 만들기

`Document`는 파일을 나타내고, `DocumentBuilder`는 내용을 추가하기 위한 유창한 API를 제공합니다. 여기서 **도형을 숨기는 방법** 로직을 적용합니다: 도형을 만들기 전에 문서 컨텍스트가 필요합니다.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**설명** – `Document` 객체는 빈 상태로 시작합니다. `DocumentBuilder`는 첫 번째 단락의 시작에 위치해 도형이나 텍스트를 삽입할 준비가 되어 있습니다.

## 3단계: 보이는 사각형 도형 삽입

문서를 열었을 때 계속 보일 도형이 사각형입니다. 크기, 위치, 서식을 도형 객체를 통해 직접 제어할 수 있습니다.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**왜 이 단계인가** – 사각형을 추가함으로써 **insert rectangle shape word** 요구 사항을 충족합니다. `FillColor`와 `LineColor`를 설정하면 최종 문서에서 도형을 쉽게 확인할 수 있습니다.

## 4단계: 타원 도형 삽입 및 숨기기

이제 숨길 도형을 추가합니다. `Hidden` 속성은 Word에게 UI에 도형을 렌더링하지 않도록 지시하지만, 문서 구조에는 여전히 존재합니다.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**설명** – `Hidden = true` 설정이 **hide shape in word**의 핵심입니다. Word는 일반 보기와 인쇄 시 이 플래그를 존중하지만, 필요하다면 프로그래밍적으로 여전히 접근할 수 있습니다.

## 5단계: 문서 저장

마지막으로 문서를 디스크에 기록합니다. 쓰기 권한이 있는 폴더를 선택하고, 튜토리얼 목적을 명확히 나타내는 파일 이름을 지정하세요.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**결과** – Microsoft Word에서 `ShapeVisibility.docx`를 열면 연한 파란색 사각형만 보입니다. 숨겨진 타원은 나타나지 않아 **Word 파일에서 도형을 숨기는 방법**을 성공적으로 마스터했음을 확인할 수 있습니다.

## 전체 작동 예제

모든 스니펫을 합치면 하나의 실행 가능한 프로그램이 됩니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 예상 출력

- **시각적**: `ShapeVisibility.docx`를 열면 왼쪽 여백 근처에 연한 파란색 사각형이 표시됩니다. 타원은 보이지 않습니다.
- **프로그램적**: 숨겨진 타원은 문서 XML(`&lt;w:drawing&gt;` 요소) 안에 `w:hidden` 속성이 설정된 채로 남아 있으며, 파일을 zip으로 열어 `document.xml`을 확인하면 확인할 수 있습니다.

## 흔히 묻는 질문 및 예외 상황

| Question | Answer |
|----------|--------|
| *Can I hide multiple shapes?* | Yes. Set `Hidden = true` on each shape you want to conceal. |
| *Will hidden shapes print?* | By default Word does not print hidden objects. If you need them printed, clear the `Hidden` flag before printing. |
| *Is the hidden property supported in older Word versions?* | The `Hidden` attribute is part of the Office Open XML standard and works in Word 2007 and later. |
| *What if I need to toggle visibility at runtime?* | Retrieve the shape via `document.GetChildNodes(NodeType.Shape, true)` and flip the `Hidden` property based on your logic. |

## 전문가 팁

- **Performance**: If you generate many documents, reuse a single `DocumentBuilder` instance instead of creating a new one for each file.
- **Version control**: Store the generated `.docx` files in a version‑controlled folder; hidden shapes can act as metadata markers for downstream processing.
- **Testing**: Automate a quick visual test by converting the DOCX to PDF with Aspose.Words (`document.Save("out.pdf")`). The PDF will also hide the ellipse, confirming that the hidden flag propagates through format conversions.

## 결론

이제 C#을 사용해 Word 문서에서 **도형을 숨기는 방법**을 알게 되었습니다. 튜토리얼을 통해 문서 생성, **insert rectangle shape word**, 타원 추가, 그리고 `Hidden` 플래그 적용을 통해 **hide shape in word** 동작을 구현했습니다. 완전한 실행 코드를 활용해 자동 보고서나 템플릿 워크플로우에 숨겨진 그래픽을 손쉽게 통합할 수 있습니다.

### 다음 단계

- 회전, 그림자, 텍스트 래핑 등 다른 도형 속성을 탐색해 보세요.  
- 숨겨진 도형을 사용자 정의 문서 속성과 결합해 기계가 읽을 수 있는 메타데이터를 삽입하세요.  
- 표, 차트, 콘텐츠 컨트롤을 위한 **create word document code** 패턴을 살펴보며 자동화 도구 상자를 확장하세요.

다양한 도형 유형과 가시성 설정을 실험해 보세요—다음 Word 자동화 프로젝트가 몇 줄의 코드만큼 가까워졌습니다!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 도와줍니다.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}