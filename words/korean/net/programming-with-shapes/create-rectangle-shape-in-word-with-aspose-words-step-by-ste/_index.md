---
category: general
date: 2026-02-18
description: Aspose.Words를 사용하여 사각형 모양을 만들고 그림자 추가, 모양 크기 설정 및 Word 문서 저장 방법을 몇 분
  안에 배워보세요.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: ko
og_description: Word 파일에 사각형 모양을 만들고, 그림자 추가 방법을 배우며, 모양 크기를 설정하고, Aspose.Words를 사용하여
  C#로 문서를 저장합니다.
og_title: Word에서 사각형 모양 만들기 – 완전 Aspose.Words 튜토리얼
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words를 사용하여 Word에서 사각형 도형 만들기 – 단계별 가이드
url: /ko/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word에서 사각형 도형 만들기 – 단계별 가이드

Word 파일에 **사각형 도형을 만들고** 싶었지만 어디서 시작해야 할지 몰랐던 적 있나요? 여러분만 그런 것이 아닙니다—개발자들은 종종 “도형에 그림자를 추가하면서 문서를 편집 가능하게 유지하려면 어떻게 해야 하나요?” 라고 묻습니다. 이 튜토리얼에서는 그 질문에 답하고 **그림자 추가**, **도형 크기 설정**, **Word 문서 저장**을 한 흐름으로 보여드립니다.

새 문서를 초기화하는 단계(예, **문서 만드는 방법**)부터 최종 *.docx* 파일을 디스크에 저장하는 단계까지 모든 과정을 안내합니다. 외부 참조 없이, 오늘 바로 Visual Studio에 복사‑붙여넣기 해서 실행할 수 있는 자체 포함 예제입니다.

---

## 전제 조건

- .NET 6+ (또는 .NET Framework 4.7+). Aspose.Words는 최신 .NET 런타임에서 동작합니다.
- 유효한 Aspose.Words 라이선스(또는 무료 평가 키) – 그렇지 않으면 워터마크가 표시됩니다.
- Visual Studio, Rider 또는 선호하는 C# 편집기.
- 기본적인 C# 지식—콘솔 앱을 실행할 수 있으면 충분합니다.

> **프로 팁:** Mac을 사용한다면 .NET 6과 VS Code에서 동일한 코드를 실행할 수 있습니다—`Aspose.Words` NuGet 패키지만 참조하면 됩니다.

---

## 1단계: 문서 초기화 – **문서 만드는 방법**의 기반

무언가를 그리기 전에 빈 캔버스가 필요합니다. Aspose.Words에서는 이를 `Document`라고 부릅니다.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **왜 중요한가:** `Document` 객체는 전체 *.docx* 파일을 나타냅니다. 추가하는 모든 도형, 단락, 섹션은 이 객체의 자식이 됩니다. 깨끗한 문서에서 시작하면 숨겨진 스타일이 사각형에 영향을 주는 일을 방지할 수 있습니다.

---

## 2단계: 사각형 정의 및 **도형 크기 설정**

사각형은 `ShapeType.Rectangle`을 가진 `Shape`에 불과합니다. 원하는 크기를 명시적으로 지정해 정확히 원하는 모양이 되도록 합니다.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **숫자의 의미:** Aspose.Words는 포인트 단위(1 pt = 1/72 in)를 사용합니다. 레이아웃에 맞게 값을 조정하세요; 일반적인 A4 페이지에서는 200 pt가 적당한 너비입니다.

---

## 3단계: **그림자 추가** – 도형을 돋보이게 만들기

그림자는 도형이 페이지에서 “떠 있다”는 시각적 힌트를 제공합니다. `Shadow` 속성을 사용해 색상, 거리, 투명도, 흐림 정도를 조절합니다.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **투명도를 사용하는 이유:** 완전히 불투명한 그림자는 거칠게 보일 수 있습니다. 0.4 정도로 설정하면 효과가 미묘하고 전문적으로 보입니다.

---

## 4단계: 사각형 위치 지정 – 주변 텍스트와 인라인 흐름

도형을 단락 내 문자처럼 동작하게 하려면 `WrapType`을 `Inline`으로 설정합니다. 이렇게 하면 문서를 나중에 편집할 때 레이아웃이 예측 가능해집니다.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **예외 상황:** 사각형을 텍스트 위에 떠 있게 하고 싶다면(예: 워터마크) `WrapType`을 `Square` 또는 `BehindText`로 변경하세요.

---

## 5단계: 도형을 문서 본문에 삽입

이제 실제로 첫 번째 단락에 사각형을 배치합니다. 문서에 아직 내용이 없으면 `FirstParagraph`가 자동으로 생성됩니다.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **팁:** 먼저 새 단락을 만든 뒤 그 안에 도형을 추가할 수도 있습니다—주변에 텍스트가 필요할 때 유용합니다.

---

## 6단계: **Word 문서 저장** – 최종 단계

모든 것이 준비되면 파일을 저장하는 코드는 한 줄이면 충분합니다. 원하는 경로를 지정하면 되며, 예제에서는 여러분이 직접 교체해야 할 자리표시자를 사용했습니다.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **결과:** 생성된 *.docx* 파일을 Microsoft Word에서 열면, 첫 번째 단락과 인라인으로 배치된 200 pt 너비, 100 pt 높이의 검은 그림자 사각형이 보일 것입니다.

---

## 예상 출력

**ShadowShape.docx**를 열면 문서는 다음과 같이 표시됩니다:

- 사각형 도형이 포함된 단일 단락.
- 사각형에 5 pt 오프셋의 은은한 검은 그림자 적용.
- 도형 크기가 2단계에서 설정한 치수와 일치.
- 별도의 텍스트는 없으며, 필요 시 직접 추가할 수 있음.

도형이 보이지 않을 경우, 올바른 Aspose.Words 버전을 참조했는지와 라이선스(또는 평가판)가 활성화되어 있는지 다시 확인하세요.

---

## 자주 묻는 질문 및 변형

| Question | Answer |
|----------|--------|
| *Can I change the shadow color to something other than black?* | Absolutely—set `rectangleShape.Shadow.Color = Color.Blue;` or any `System.Drawing.Color`. |
| *What if I need a larger rectangle?* | Adjust `Width` and `Height` values. Remember they’re in points; 72 pt = 1 in. |
| *Is it possible to place the shape at an absolute position?* | Yes—use `WrapType = WrapType.Absolute` and set `Top`/`Left` properties. |
| *Does this work with .NET Core?* | It does. Aspose.Words is cross‑platform; just install the NuGet package for .NET Standard. |
| *Can I add text inside the rectangle?* | Not directly; you’d need to insert a `TextBox` shape instead of a plain rectangle. |

---

## 전체 작업 예제 (복사‑붙여넣기 바로 사용)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

프로그램을 실행하고 `C:\Temp\ShadowShape.docx` 경로를 확인하면, 설명한 대로 그림자가 있는 사각형을 확인할 수 있습니다.

---

## 결론

이제 Aspose.Words를 사용해 Word 파일에 **사각형 도형을 만들고**, **도형 크기 설정**, **그림자 추가**, 그리고 **Word 문서 저장**까지 하는 방법을 알게 되었습니다. **문서 만드는 방법**부터 결과를 저장하는 전체 흐름이 몇 줄의 C# 코드에 담겨 있으며, 더 복잡한 레이아웃에도 확장할 수 있습니다.

다음 도전 과제는 무엇인가요? 사각형을 둥근 모서리 도형으로 바꾸어 보거나, 다양한 그림자 색상을 실험하거나, 도형을 표 셀 안에 삽입해 보세요. 각 변형은 여기서 다룬 핵심 개념을 강화해 줍니다.

이 가이드가 도움이 되었다면 공유하고, 여러분만의 변형을 댓글로 남기거나, 이미지 삽입이나 표 생성 등 Aspose.Words를 활용한 다른 튜토리얼도 살펴보세요. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}