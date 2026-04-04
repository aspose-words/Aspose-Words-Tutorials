---
category: general
date: 2026-04-04
description: Aspose.Words를 사용하여 C#에서 사각형 모양을 만들고, 그림자를 추가하고 그림자에 블러를 적용하며 그림자를 투명하게
  만드는 방법을 단계별로 안내합니다.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: ko
og_description: Aspose.Words를 사용하여 C#에서 사각형 모양을 만들고, 그림자를 추가하고 블러를 적용하며 그림자를 투명하게
  만드는 방법을 간결한 튜토리얼에서 배워보세요.
og_title: C#에서 사각형 모양 만들기 및 그림자 추가 방법
tags:
- Aspose.Words
- C#
- Document Automation
title: C#에서 사각형 모양 만들기 및 그림자 추가 방법
url: /ko/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 사각형 모양 만들기 및 그림자 추가 방법

Word 문서에서 **사각형 모양 만들기**가 필요했지만 미묘한 드롭‑쉐도우를 어떻게 적용해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 보고서나 브랜딩 상황에서 부드럽고 반투명한 그림자가 있는 간단한 사각형은 레이아웃을 손쉽게 세련되게 만들어 줍니다.

이 튜토리얼에서는 Aspose.Words를 사용해 **문서 만들기** 과정을 살펴보고, **그림자 추가 방법**, **그림자에 블러 적용**, 그리고 **그림자 투명화**까지 보여드립니다. 끝까지 따라오시면 몇 분 안에 그림자가 적용된 사각형을 포함한 *.docx* 파일을 생성하는 C# 코드를 바로 실행할 수 있게 됩니다.

## 필요 사항

- .NET 6 이상 (API는 .NET Framework 4.6+에서도 작동합니다)
- Aspose.Words for .NET (무료 체험판을 이 예제에 사용할 수 있습니다)
- 코드 편집기 – Visual Studio, VS Code, Rider 등 원하는 것을 사용하세요
- 기본 C# 지식 – 특별한 것이 아니라 콘솔 앱을 실행할 수 있는 정도면 충분합니다

위 항목들을 갖추셨다면 바로 솔루션으로 들어가겠습니다.

## 단계 1 – 문서 만들기 및 캔버스 초기화 방법

먼저 빈 `Document` 객체가 필요합니다. Aspose.Words가 나중에 Word 파일로 변환할 빈 종이와 같은 역할을 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

왜 템플릿을 로드하지 않고 `Document`를 새로 인스턴스화할까요? 처음부터 시작하면 사각형에 영향을 줄 수 있는 숨겨진 스타일이나 섹션이 없다는 것이 보장됩니다. 또한 파일 크기가 작게 유지돼 여러 문서를 루프에서 생성할 때 좋은 습관이 됩니다.

## 단계 2 – 사각형 모양 만들기 (핵심 키워드)

이제 실제로 **사각형 모양 만들기**를 수행합니다. `Shape` 클래스는 유연합니다; 타입(Rectangle), 크기, 주변 텍스트와의 래핑 방식을 지정하면 됩니다.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

객체 초기화 구문을 사용한 점에 주목하세요 – 간결하면서 나중에 속성을 놓치는 위험을 줄여줍니다. 사각형은 다음 단계에서 추가할 첫 번째 단락 안에 배치됩니다.

## 단계 3 – 그림자 추가 및 모양 커스터마이징 방법

그림자를 추가하는 것은 한 줄로 끝나는 작업이 아닙니다; 조정해야 할 속성이 여러 개 있습니다. 여기서 **그림자에 블러 적용**과 **그림자 투명화**라는 보조 키워드가 등장합니다.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

숫자에 대한 간단한 설명: `BlurRadius`를 5로 설정하면 부드러운 깃털 효과가 적용됩니다; 10으로 늘리면 더 부드러워지고, 2로 줄이면 선명한 가장자리를 얻을 수 있습니다. `Transparency` 값은 0(불투명)부터 1(투명)까지이며, 브랜드 대비 요구사항에 맞게 조정하세요.

### 팁

컬러 그림자(예: 기업용 블루)가 필요하다면 `Color.DarkGray`를 `Color.FromArgb(80, 0, 120, 215)`로 교체하면 됩니다. 첫 번째 인자는 알파 채널이며, 미묘함을 위해 낮게 유지하세요.

## 단계 4 – 문서에 도형 삽입

사각형과 그림자가 준비되었으니 이제 이를 문서의 첫 번째 단락에 삽입합니다. 이 단계는 도형이 파일 가장 위에 나타나도록 보장합니다.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

왜 첫 번째 단락일까요? 문서가 완전히 비어 있어도 안전하게 동작하는 기본값입니다. 특정 위치(예: 제목 뒤)에 삽입하려면 해당 노드를 찾아 그곳에 도형을 삽입하면 됩니다.

## 단계 5 – 파일 저장 및 결과 확인

마지막으로 문서를 디스크에 저장합니다. 원하는 경로를 선택하면 되지만, 폴더가 존재하는지 반드시 확인하세요.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Microsoft Word에서 *ShadowRectangle.docx*를 열면 200 × 100 포인트 크기의 사각형에 어두운 회색, 약간 흐릿하고 30 % 투명한 그림자가 오른쪽과 아래쪽으로 각각 3 포인트씩 오프셋된 모습을 확인할 수 있습니다. 효과는 미묘하지만 평평한 레이아웃에 깊이를 더합니다.

![Aspose.Words에서 그림자가 있는 사각형 모양 만들기](https://example.com/placeholder-image.png "Aspose.Words에서 그림자가 있는 사각형 모양 만들기")

*이미지 대체 텍스트:* **Aspose.Words에서 그림자가 있는 사각형 모양 만들기** – 그림은 음영 처리된 사각형이 포함된 최종 문서를 보여줍니다.

## 일반적인 변형 및 엣지 케이스

### 그림자 색상을 동적으로 변경하기

애플리케이션이 테마를 지원한다면 구성 파일에서 그림자 색상을 가져올 수 있습니다:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### 도형을 인라인이 아닌 형태로 만들기

때때로 사각형을 텍스트 위에 떠 있게 하고 싶을 때가 있습니다. `WrapType`을 `WrapType.Square`로 전환하고 `RelativeHorizontalPosition`을 `RelativeHorizontalPosition.Margin`으로 설정하면 더 세밀하게 제어할 수 있습니다.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### 여러 페이지 처리하기

모든 페이지에 사각형이 필요하다면 `doc.Sections`를 순회하면서 각 섹션의 첫 번째 단락에 복제된 도형을 추가합니다. 그림자 설정까지 복제하려면 `rect.Clone(true)`를 호출하는 것을 잊지 마세요.

## 요약 – 달성한 내용

- **Aspose.Words**를 사용해 사각형 모양을 만들었습니다
- 색상, 오프셋, 블러, 투명도를 포함한 **그림자 추가 방법**
- **그림자에 블러 적용** 및 **그림자 투명화**를 시연했습니다
- 즉시 열 수 있는 Word 파일을 저장했습니다

이 모든 작업은 몇 줄의 코드만으로 가능했으며, 복잡한 그래픽 라이브러리가 없어도 정교한 시각적 조정이 가능함을 증명했습니다.

## 다음 단계는?

- `ShapeType`(Ellipse, Cloud 등) 다른 유형을 실험해 보고 그림자가 어떻게 동작하는지 확인하세요.
- 사각형을 텍스트 상자와 결합해 라벨이 있는 콜아웃을 만들 수 있습니다.
- **문서 만들기** 템플릿을 탐색해 보세요. 이미 도형용 플레이스홀더가 포함된 템플릿을 만든 뒤 프로그래밍으로 채울 수 있습니다.

블러 반경, 색상, 투명도를 자유롭게 조정해 디자인 언어에 딱 맞는 그림자를 만들어 보세요. API는 관대하며, 콘솔 앱을 다시 실행하면 변경 사항이 즉시 반영됩니다.

행복한 코딩 되시고, 문서에 언제나 깊이감 있는 터치를 더하시길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}