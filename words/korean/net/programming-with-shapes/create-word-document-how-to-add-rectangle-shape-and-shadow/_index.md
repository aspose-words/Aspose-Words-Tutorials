---
category: general
date: 2026-03-19
description: C#와 Aspose.Words를 사용해 워드 문서를 만들고, 도형 추가, 사각형 도형 삽입, 그림자 적용, 그리고 몇 분 안에
  docx 형식으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: ko
og_description: Aspose.Words를 사용해 워드 문서를 만들고, 사각형 도형을 추가한 뒤 외부 그림자를 적용하여 docx 형식으로
  저장합니다. 단계별 가이드.
og_title: 워드 문서 만들기 – 사각형 도형 및 그림자 추가
tags:
- Aspose.Words
- C#
- Document Automation
title: 워드 문서 만들기 – 사각형 도형 및 그림자 추가 방법
url: /ko/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서 만들기 – 사각형 모양 및 그림자 추가 방법

프로그래밍으로 **create word document**를 만들어야 할 때, 어디서 시작해야 할지 궁금했던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 처음으로 사용자 정의 그래픽이 포함된 .docx 파일을 생성하려 할 때 같은 장벽에 부딪힙니다. 이 튜토리얼에서는 전체 과정을 단계별로 살펴보겠습니다—모양을 추가하는 방법, 특히 **add rectangle shape**를 추가하고, 스타일리시한 **add shadow to shape**를 적용한 뒤, 마지막으로 **save document as docx**를 수행합니다.

가이드가 끝날 때쯤이면, 어떤 .NET 프로젝트에든 바로 넣어 사용할 수 있는 C# 스니펫을 얻게 됩니다. 애매한 참고 자료가 아니라, 완전하고 실행 가능한 예제만을 제공합니다.

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework에서도 작동합니다).
- Aspose.Words for .NET 설치 (NuGet 패키지 `Aspose.Words`).
- C# 구문에 대한 기본적인 이해—특별한 지식은 필요 없습니다.

라이브러리가 없으면, 다음을 실행하세요:

```bash
dotnet add package Aspose.Words
```

그게 전부입니다—추가 SDK도, COM 인터옵도 필요 없으며, 단일 NuGet 참조만 있으면 됩니다.

---

## 단계 1: Word 문서 만들기 (주 목표)

우리가 먼저 필요한 것은 깨끗한 캔버스입니다. `Document` 클래스를 Microsoft Word의 새 페이지라고 생각하면 됩니다; 이 클래스는 섹션, 단락 및 나중에 추가할 모든 요소를 보유합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

왜 빈 `Document`부터 시작할까요? 템플릿에서 숨겨진 서식이 들어오는 것을 방지하기 위해서입니다. 제 경험상, 처음부터 시작하면 나중에 모양을 삽입할 때 발생할 수 있는 불가사의한 레이아웃 변동을 피할 수 있습니다.

---

## 단계 2: 사각형 모양 삽입 – 시각 요소 추가

이제 문서가 준비되었으니, 첫 번째 단락에 **add rectangle shape**를 추가해 봅시다. `Shape` 객체는 다재다능합니다; `ShapeType.Rectangle`, `Ellipse` 또는 사용자 정의 그림을 선택할 수 있습니다. 최소한의 코드는 다음과 같습니다:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**내부에서 무슨 일이 일어나고 있나요?**

- `ShapeType.Rectangle`는 Aspose에 단순한 박스를 원한다는 것을 알려줍니다.
- `WrapType.Inline`은 사각형이 텍스트 흐름에 따라 이동하도록 보장합니다. 이는 일반적인 워드 프로세싱 상황에서 기대하는 동작입니다.
- `FirstParagraph`에 추가함으로써 새 단락을 수동으로 삽입할 필요가 없습니다; 문서가 비어 있으면 Aspose가 자동으로 단락을 생성합니다.

> **프로 팁:** 모양을 텍스트 *뒤에* 배치해야 한다면 `WrapType`을 `WrapType.Transparent`로 바꾸세요. 이 작은 변화가 시각적인 차이를 크게 만들 수 있습니다.

---

## 단계 3: 외부 그림자 적용 – 외관 강화

평평한 사각형은… 말 그대로 평평합니다. **add shadow to shape**를 추가하면 추가 이미지 없이 깊이를 부여할 수 있습니다. Aspose의 `ShadowFormat`을 사용하면 한 줄 코드로 구현됩니다.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

왜 이러한 특정 값을 사용하는 걸까요?

- `5.0`의 **Blur**는 대부분의 모니터에서 전문적으로 보이는 부드러운 깃털 모양 가장자리를 제공합니다.
- `3.0`의 **Distance**와 `45`의 **Angle**은 왼쪽 위에서 오는 자연스러운 광원을 만들어 주며, 이는 일반적인 디자인 관례입니다.
- `Color.Gray`는 밝은 테마와 어두운 테마 모두에서 잘 작동합니다; 더 강한 대비가 필요하면 `Color.Black`으로 교체할 수 있습니다.

만약 *내부* 그림자가 필요하다면(예: 움푹 들어간 버튼), `ShadowType.OuterShadow`를 `ShadowType.InnerShadow`로 바꾸면 됩니다. 동일한 속성들이 그대로 적용됩니다.

---

## 단계 4: 문서를 DOCX로 저장 – 작업 내용 유지

재미있는 작업도 좋지만, 결국 디스크에 파일이 필요합니다. **save document as docx** 단계는 간단합니다:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

몇 가지 참고 사항:

- `SaveFormat.Docx` 열거형은 최신 Office Open XML 형식을 보장하며, Word 2007 이상과 호환됩니다.
- 파일을 웹 응답으로 직접 스트리밍해야 한다면, 파일 경로를 `MemoryStream`으로 교체하고 HTTP 응답에 기록하십시오.

코드를 실행한 후, Microsoft Word에서 `ShadowedRectangle.docx`를 열어 보세요. 첫 번째 단락에 인라인으로 배치된 부드러운 그림자가 있는 회색 사각형이 보일 것입니다—우리가 목표로 했던 바로 그 결과입니다.

---

## 모양 추가 방법 – 대체 접근법

위 예시는 *인라인* 방식을 사용했지만, 때때로 텍스트 위에 떠 있는 모양이 필요할 수 있습니다. 이때 **how to add shape**와 다양한 래핑 옵션이 중요해집니다.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

여기서는 `WrapType`을 `Square`로 바꾸고 페이지 중앙에 모양을 배치했습니다. 이 패턴은 표지 페이지나 장식 배너에 유용합니다. 기억하세요: 떠 있는 모양은 Word가 추가 위치 데이터를 저장하기 때문에 파일 크기가 약간 증가합니다.

---

## 예상 출력 및 검증

생성된 파일을 열면 다음과 같이 보일 것입니다:

- 회색 사각형이 포함된 단일 단락.
- 사각형의 크기는 대략 2.8 × 1.4 인치.
- 오른쪽 아래로 오프셋된 미묘한 외부 그림자.

모양이 단락 *외부*에 나타난다면, `WrapType`을 다시 확인하세요. 그림자가 너무 거칠게 보이면 `Blur` 값을 낮추거나 `Color`를 더 밝은 색으로 바꾸세요.

---

## 일반적인 함정 및 회피 방법

| 문제 | 발생 원인 | 해결 방법 |
|-------|----------------|-----|
| 저장 후 모양이 사라짐 | `WrapType`이 `Inline`으로 설정되었지만 단락이 제거됨 | 단락이 존재하는지 확인하고, `doc.FirstSection.Body.FirstParagraph`를 사용해 보장하세요. |
| 그림자가 픽셀화됨 | `Blur` 값을 매우 낮게 사용함 | 부드러운 가장자리를 위해 `Blur` 값을 최소 `3.0`으로 늘리세요. |
| 파일 크기 급증 | 모양과 함께 고해상도 이미지를 많이 추가함 | 이미지를 추가한 경우 저장 전에 `doc.RemoveUnusedResources()`를 사용하세요. |
| 다크 모드에서 색상이 표시되지 않음 | 모양 자체에 어두운 `Color`를 사용함 | 가시성을 높이기 위해 대비되는 색(예: `Color.White`)을 선택하세요. |

---

## 전체 작동 예제

아래는 지금까지 논의한 모든 내용을 포함한 완전한 복사‑붙여넣기 가능한 코드입니다. 콘솔 앱으로 자유롭게 실행해 보세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**각 블록에 대한 설명**은 주석으로 인라인에 포함되어 있어, SEO 독자와 자체 포함 답변을 선호하는 AI 어시스턴트 모두에게 만족을 줍니다.

---

## 결론

우리는 이제 **create word document**를 처음부터 만들고, **how to add shape**를 배워서, 특히 **add rectangle shape**를 추가하고, **add shadow to shape**를 적용한 뒤, 마지막으로 **save document as docx**를 수행했습니다. 단계는 간단하고, 코드는 간결하며, 결과는 깔끔합니다.

더 나아가고 싶다면, 사각형을 사용자 정의 이미지로 교체하거나, 다양한 그림자 색상을 실험하거나, 여러 모양 섹션이 포함된 전체 보고서를 생성해 보세요. Aspose.Words API는 인보이스부터 마케팅 브로셔까지 모든 것을 처리할 수 있을 만큼 유연합니다.

다른 모양 유형에 대한 질문이 있거나 이를 ASP.NET Core 서비스에 통합하는 데 도움이 필요하면 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!

![사각형 모양 및 그림자가 있는 단어 문서 만들기](placeholder-image.png "사각형 모양 및 그림자가 있는 단어 문서 만들기

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}