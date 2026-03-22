---
category: general
date: 2026-03-22
description: C#에서 사각형 도형을 만들고 Aspose.Words를 사용해 도형에 그림자를 추가합니다. 그림자 추가 방법, 사각형 만드는
  방법, 그리고 그림자 속성을 설정하는 방법을 배워보세요.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: ko
og_description: C#에서 사각형 도형을 만들고 Aspose.Words를 사용해 도형에 그림자를 추가합니다. 그림자 추가 방법, 사각형
  생성 방법, 그림자 설정 방법을 다루는 단계별 가이드.
og_title: C#에서 그림자와 함께 사각형 모양 만들기 – 전체 가이드
tags:
- Aspose.Words
- C#
- Document Automation
title: Aspose.Words를 사용하여 C#에서 그림자 효과가 있는 사각형 모양 만들기
url: /ko/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 Aspose.Words를 사용하여 그림자 있는 사각형 도형 만들기

워드 문서에 **사각형 도형 만들기**가 필요했지만 미묘한 드롭‑섀도우를 적용하는 방법을 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다—많은 개발자들이 문서 자동화를 처음 접할 때 이 문제에 부딪힙니다. 이 가이드에서는 Aspose.Words를 사용하여 **도형에 그림자 추가하기** 방법을 단계별로 설명하고, “**그림자 추가 방법**”, “**사각형 만들기**”, “**그림자 설정 방법**”에 대한 질문에도 답변합니다.

우선 빈 `Document`를 만들고, 사각형을 그린 뒤 그림자를 켜고, 흐림 정도, 거리, 각도, 색상을 조정한 뒤 파일을 저장합니다. 최종적으로 페이지 위에 떠 있는 회색 사각형이 포함된 사용 준비가 된 `.docx` 파일을 얻게 됩니다. 복잡한 내용 없이, .NET 프로젝트에 그대로 복사‑붙여넣기 할 수 있는 간단한 코드만 제공합니다.

## 사전 요구 사항

* **Aspose.Words for .NET** (2026년 3월 현재 최신 버전). NuGet에서 `Install-Package Aspose.Words` 명령으로 설치할 수 있습니다.
* .NET 개발 환경 – Visual Studio, Rider, 혹은 C# 확장 기능이 설치된 VS Code도 충분합니다.
* 기본 C# 지식 – 특별한 것이 필요 없으며, 콘솔 또는 WinForms 앱을 만들 수 있으면 됩니다.

이것뿐입니다. 추가 라이브러리나 숨겨진 단계는 없습니다. 준비되셨나요? 시작해봅시다.

## 단계 1: 새 빈 문서 초기화

**사각형 도형 만들기**를 위해 먼저 Word 파일을 나타내는 컨테이너, 즉 `Document` 객체가 필요합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document` 클래스는 Aspose.Words가 수행하는 모든 작업의 진입점입니다. 빈 캔버스와 같으며, 이 없이는 도형, 표, 텍스트 등을 추가할 수 없습니다.

## 단계 2: 그림자를 적용할 사각형 만들기

이제 `Rectangle` 유형의 `Shape`을 인스턴스화하여 **사각형 만들기**를 수행합니다. 또한 크기를 포인트 단위로 설정합니다(1 포인트 ≈ 1/72 인치).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

왜 200 × 100 포인트를 선택했을까요? 데모용으로 적당한 크기로, 그림자를 명확히 볼 수 있을 만큼 크지만 페이지를 압도할 정도로 크지는 않습니다. 레이아웃에 맞게 자유롭게 숫자를 조정하세요.

## 단계 3: 그림자 효과 활성화 및 외관 설정

이것이 튜토리얼의 핵심입니다: **그림자 추가 방법**과 **그림자 설정 방법** 속성. Aspose.Words는 모든 도형에 `Shadow` 객체를 제공하여 효과를 켜고 시각적 매개변수를 조정할 수 있게 합니다.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** – 가장자리를 부드럽게 합니다. 값이 클수록 그림자가 더 퍼진 듯 보입니다.
* **Distance** – 그림자를 사각형으로부터 더 멀리 떨어뜨립니다.
* **Angle** – 빛이 오는 방향을 결정합니다; 45°는 대각선으로 자연스러운 모습을 제공합니다.
* **Color** – `System.Drawing.Color` 중 원하는 색을 선택할 수 있습니다. 회색은 안전한 기본값이며, `Color.Black`으로 강하게, `Color.LightGray`로 부드럽게 지정할 수 있습니다.

팁: `Enabled = false` 로 설정하면 다른 모든 그림자 설정이 무시되므로, 해당 플래그를 항상 확인하세요.

## 단계 4: 도형을 문서 본문에 삽입하기

사각형과 그림자 설정이 완료되면 이를 문서에 배치해야 합니다. 가장 간단한 방법은 첫 번째 섹션의 첫 번째 단락에 추가하는 것입니다.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

문서에 이미 텍스트가 있다면 특정 `Paragraph` 혹은 `Table` 셀을 찾아 그곳에 도형을 삽입할 수 있습니다. `AppendChild` 메서드는 다재다능하여 모든 `Node` 유형에 적용됩니다.

## 단계 5: 문서 저장 및 결과 확인

마지막으로 파일을 디스크에 씁니다. 경로는 원하는 위치로 바꾸세요; 폴더가 존재하지 않으면 예외가 발생합니다.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

생성된 `ShadowedRectangle.docx`를 Microsoft Word(또는 LibreOffice)에서 열면 오른쪽 아래로 흐르는 선명한 대각선 그림자가 있는 회색 사각형을 볼 수 있습니다. 그림자가 너무 옅게 보이면 `BlurRadius` 또는 `Distance` 값을 늘리고 코드를 다시 실행해 보세요—실험은 재미의 일부입니다.

![그림자 예시가 포함된 사각형 도형 만들기](rectangle-shadow.png){alt="그림자 예시가 포함된 사각형 도형 만들기"}

### 예상 출력

* 한 페이지로 구성된 Word 문서.
* 페이지 좌측 상단에 위치한 200 × 100 포인트 회색 사각형.
* 45° 각도에서 8픽셀 오프셋, 5픽셀 흐림 효과가 적용된 은은한 회색 그림자.

## 도형에 그림자 추가 – 심층 탐구

‘그림자를 애니메이션화하거나 사용자 입력에 따라 변하게 할 수 있을까?’ 라고 궁금할 수 있습니다. Aspose.Words 자체는 애니메이션을 지원하지 않지만, 저장하기 전에 프로그래밍적으로 그림자 속성을 조정하여 같은 문서의 다양한 버전을 만들 수 있습니다. 예를 들어 색상 컬렉션을 순회하는 경우:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

이 작은 코드 조각은 **그림자 설정 방법**을 동적으로 보여줍니다—테마 보고서를 생성할 때 유용합니다.

## 사각형 만들기 – 대체 도형

둥근 모서리 사각형이 필요하면 `ShapeType`만 바꾸면 됩니다:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

또는 정사각형을 만들려면 `Width`와 `Height`를 동일하게 설정합니다. 동일한 그림자 속성이 적용되므로 선택한 어떤 도형에도 **그림자 추가 방법**이 이미 적용됩니다.

## 흔히 발생하는 문제와 해결 방법

| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| 그림자가 나타나지 않음 | `Shadow.Enabled`가 `false`로 남아 있음 | `rectangleShape.Shadow.Enabled = true;` 로 설정 |
| 그림자가 너무 날카로움 | `BlurRadius`가 0으로 설정됨 | `BlurRadius`를 최소 3 이상으로 증가 |
| 저장 시 `FileNotFoundException` 발생 | 대상 폴더가 존재하지 않음 | 먼저 폴더를 만들거나 올바른 경로를 사용 |
| 도형이 보이지 않음 | Width/Height가 0으로 설정됨 | 두 차원 모두 0보다 크게 설정 |

이러한 문제를 미리 확인하면 흔히 겪는 “왜 도형이 보이지 않을까?” 상황을 피할 수 있습니다.

## 요약 – 우리가 이룬 것

* Aspose.Words를 사용하여 새 Word 문서에 **사각형 도형 만들기**.  
* `Shadow.Enabled` 플래그를 전환하고 흐림, 거리, 각도, 색상을 조정하여 **도형에 그림자 추가하기**.  
* **그림자 추가 방법**, **사각형 만들기**, **그림자 설정 방법**을 깔끔하고 재사용 가능한 코드 스니펫으로 시연.  
* 어떤 C# 프로젝트에도 붙여넣을 수 있는 완전한 실행 예제 제공.

## 다음 단계는?

기본을 숙달했으니 다음을 살펴보세요:

* **이미지에 그림자 추가** – 동일한 `Shadow` API가 `ShapeType.Image`에도 적용됩니다.
* **여러 도형 결합** – Word에서 직접 플로우차트나 인포그래픽을 만들 수 있습니다.
* **PDF로 내보내기** – 그림자를 추가한 후 `document.Save("output.pdf")`를 호출하여 인쇄 가능한 버전을 생성합니다.

다양한 색상, 각도, 심지어 그라디언트 채우기를 실험해 보세요. API가 충분히 유연해 Word를 직접 열지 않고도 전문가 수준의 문서를 만들 수 있습니다.

코딩 즐겁게! 문제가 발생하면 아래에 댓글을 남기거나 Aspose.Words 포럼을 확인하세요—커뮤니티가 빠르게 도와줍니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}