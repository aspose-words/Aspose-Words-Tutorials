---
category: general
date: 2026-02-26
description: Aspose.Words를 사용하여 Word에 사각형 모양을 만들고, 모양을 Word에 추가하고, 그림자를 적용하며, 투명도를
  설정하는 방법을 몇 분 안에 배워보세요.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: ko
og_description: Aspose.Words를 사용하여 Word에서 사각형 모양을 만들기. Word에 도형을 추가하고, 도형에 그림자를 적용하며,
  도형 투명도를 빠르게 설정하는 방법을 배우세요.
og_title: Word에서 사각형 도형 만들기 – 전체 Aspose.Words 가이드
tags:
- Aspose.Words
- C#
- Word Automation
title: Word에서 사각형 도형 만들기 – 전체 Aspose.Words 가이드
url: /ko/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

same structure.

Let's craft translation.

Start with shortcodes unchanged.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 사각형 도형 만들기 – 전체 Aspose.Words 가이드

Word 문서에 **사각형 도형을 만들**고 싶지만 어디서 시작해야 할지 몰랐던 적이 있나요? 혼자가 아닙니다—보고서나 인보이스를 자동화할 때 많은 개발자들이 이 문제에 부딪히곤 합니다. 이번 튜토리얼에서는 **Word에 도형을 추가**하고, 은은한 그림자를 적용하며, 도형의 투명도를 제어하는 완전한 실행 예제를 단계별로 살펴보겠습니다. 모두 Aspose.Words for .NET을 사용합니다.

가이드를 끝까지 따라오면, 깔끔한 사각형에 정교한 그림자가 들어간 `.docx` 파일을 얻게 됩니다—브랜딩, 강조 표시, 혹은 문서를 조금 더 전문적으로 보이게 하는 데 완벽합니다. 별도의 외부 도구는 필요 없으며, C# 몇 줄만 있으면 됩니다.

## 필요 사항

- **Aspose.Words for .NET** (2026년 초 최신 버전). NuGet(`Install-Package Aspose.Words`)에서 받을 수 있습니다.
- .NET 개발 환경 (Visual Studio, Rider, 혹은 C# 확장 기능이 설치된 VS Code).
- C# 문법에 대한 기본적인 이해—특별한 것이 아니라 일반적인 `using` 구문과 객체 생성 정도면 충분합니다.

위 사항을 이미 갖추고 있다면, 바로 시작해봅시다.

## 사각형 도형 만들기 – 핵심 단계

아래는 전체 소스 코드입니다. 새 콘솔 프로젝트에 복사‑붙여넣기하고 **F5**를 눌러 실행하면 지정한 폴더에 `ShadowDemo.docx`가 생성됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### 왜 이렇게 동작하나요

- **`Document`**는 진입점이며 전체 Word 파일을 나타냅니다.
- **`Shape`**와 `ShapeType.Rectangle`은 Aspose에 사각형 그리기 객체를 만들겠다고 알려줍니다.
- **`Width`**와 **`Height`**를 설정하면 도형의 크기가 결정됩니다; 설정하지 않으면 아주 작은 자리표시자가 됩니다.
- **`Shadow`** 객체를 통해 그림자의 흐림, 거리, 방향, 색상, 투명도, 퍼짐 등을 세밀하게 조정할 수 있습니다. 이것이 *apply shadow to shape*의 핵심입니다.
- 마지막으로 **`AppendChild`**는 도형을 문서의 첫 번째 단락에 삽입합니다. 이는 테이블이나 헤더를 다루지 않고 *add shape to Word*를 가장 간단히 수행하는 방법입니다.

`ShadowDemo.docx`를 열면 회색 사각형이 문서에 편안히 배치되고, 그림자는 오른쪽 아래로 45° 각도로 기울어져 있습니다. 그림자는 단단한 블록이 아니라 흐림 반경으로 가장자리가 부드럽게 처리되고, 투명도로 자연스러운 드롭 섀도우처럼 보입니다.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(위 이미지는 코드 스니펫의 최종 결과를 보여줍니다.)*

## Word 문서에 도형 추가 – 배치 옵션

예제에서는 **첫 번째 단락**을 사용했는데, 이는 화면에 바로 무언가를 표시하기 가장 빠른 방법이기 때문입니다. 실제 상황에서는 다음과 같이 할 수 있습니다:

- 특정 **섹션**이나 **머리글/바닥글**에 도형 삽입
- **표 셀** 안에 배치하여 표 데이터와 정렬
- **텍스트 래핑** 옵션(`WrapType.Square` 등)으로 주변 텍스트가 사각형 주위를 흐르도록 설정

다음은 도형을 새 단락에 사용자 정의 스타일로 넣는 간단한 변형 예시입니다:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

**전문가 팁:** 도형의 속성을 모두 설정한 **후에** 도형을 추가하세요. 그렇지 않으면 `UpdateLayout`을 호출해 시각적 모습을 새로 고쳐야 할 수도 있습니다.

## 도형에 그림자 적용 – 세밀한 조정

그림자는 문서의 미관을 크게 바꿀 수 있습니다. `Shadow` 클래스는 여러 속성을 제공합니다:

| Property      | What It Controls                                   | Typical Values |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | 그림자 가장자리의 부드러움                         | 2.0 – 10.0      |
| `Distance`    | 도형으로부터 그림자가 떨어진 거리                  | 1.0 – 8.0       |
| `Direction`   | 각도(도) (0 = 왼쪽, 90 = 위)                       | 0 – 360         |
| `Color`       | 그림자 색상(`System.Drawing.Color` 중 하나)       | Gray, Black, Custom |
| `Transparency`| 불투명도(0 = 완전 불투명, 1 = 투명)                | 0.0 – 0.5       |
| `Spread`      | 흐림이 적용되기 전 그림자의 확장 정도               | 0.0 – 1.0       |

**섬세하고 전문적인** 느낌을 원한다면 `BlurRadius`를 4‑6 정도, `Transparency`를 0.2 정도로 유지하세요. **극적인 효과**를 원한다면 `Distance`를 6으로 늘리고, `Direction`을 135°로 설정한 뒤 `Transparency`를 0.05 정도로 낮추면 됩니다.

## 도형 투명도 및 그림자 퍼짐 설정

투명도는 그림자에만 국한되지 않습니다. 사각형 자체를 반투명하게 만들 수도 있습니다:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

반투명 채우기에 부드러운 그림자를 결합하면 현대적인 UI 느낌을 얻을 수 있어, 대시보드나 디자인 목업을 보고서에 삽입할 때 유용합니다.

### 주의해야 할 엣지 케이스

1. **구버전 Word**(2007 이전)는 일부 그림자 속성을 지원하지 않습니다. `.doc` 파일을 대상으로 한다면 그림자를 단순화(예: `BlurRadius`를 0으로)하는 것이 좋습니다.
2. **고 DPI 디스플레이**에서는 그림자가 약간 다르게 보일 수 있습니다. 시각적 일관성이 중요하다면 대상 환경에서 테스트하세요.
3. **도형 겹침**—Aspose는 그림자를 추가된 순서대로 렌더링합니다. 원치 않는 가림 현상을 피하려면 뒤쪽부터 앞쪽 순으로 도형을 삽입하세요.

## 결과 저장 및 확인

`Document.Save` 메서드는 파일 확장자를 기준으로 출력 형식을 자동 감지합니다. **`.docx`** 파일이면 Open XML 형식으로 저장되어 대부분의 최신 워드 프로세서가 인식합니다. 동일한 시각 스타일을 유지한 **PDF** 버전이 필요하면 확장자만 바꾸면 됩니다:

```csharp
document.Save("ShadowDemo.pdf");
```

생성된 `ShadowDemo.docx`(또는 `ShadowDemo.pdf`)를 열면 **그림자가 있는 사각형**이 깔끔하게 표시됩니다. 이는 Aspose.Words를 사용해 *create rectangle shape*와 *apply shadow to shape*를 성공적으로 수행했음을 확인하는 단계입니다.

## 자주 묻는 질문

**Q: 다른 도형, 예를 들어 타원을 사용할 수 있나요?**  
A: 물론입니다. `ShapeType.Rectangle`을 `ShapeType.Ellipse`(또는 다른 `ShapeType` 열거형)으로 바꾸면 됩니다. 그림자 속성은 동일하게 유지됩니다.

**Q: 사각형을 클릭 가능하게 만들려면 어떻게 하나요?**  
A: 도형에 하이퍼링크를 할당할 수 있습니다:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: .NET 6 이상에서도 동작하나요?**  
A: 네. Aspose.Words 23.11 이후 버전은 .NET 6, .NET 7, .NET 8을 완전히 지원합니다. 해당 NuGet 패키지를 참조하면 됩니다.

**Q: 브랜드 색상에 맞게 그림자 색을 바꾸려면?**  
A: 원하는 `System.Drawing.Color`를 사용하면 됩니다:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## 마무리

Word 문서에 **사각형 도형을 만들고**, **도형을 Word에 추가**하며, **그림자를 적용**하고, **투명도를 설정**하는 모든 과정을 살펴보았습니다. 완전한 실행 가능한 코드는 페이지 상단에 있으며, 설명을 통해 크기, 색상, 그림자 매개변수를 자유롭게 조정할 수 있는 자신감을 얻으셨을 겁니다.

다음 단계에 도전해 보세요:

- 배지 효과를 위한 여러 도형 레이어링
- 문서 내용에 따라 동적으로 크기 조정(예: 표 열 너비 기반 계산)
- 그림자를 유지한 채 PDF 또는 HTML로 내보내기

궁금한 점이 있으면 댓글을 남겨 주세요. “그림자가 있는 사각형” 테마에 대한 여러분만의 변형도 공유해 주시면 좋겠습니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}