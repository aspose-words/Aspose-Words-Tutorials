---
category: general
date: 2025-12-29
description: Aspose.Words C#를 사용하여 Word 문서에 사각형 도형을 만들고, 도형 투명도 설정, 그림자 색상 지정 방법을
  배우며, Word 문서를 손쉽게 저장하세요.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: ko
og_description: Aspose.Words C#를 사용하여 Word 문서에 사각형 모양을 만듭니다. 이 가이드는 모양 투명도 설정, 그림자
  색상 설정 및 Word 문서 저장 방법을 보여줍니다.
og_title: Word에서 사각형 도형 만들기 – 완전한 Aspose.Words 튜토리얼
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words를 사용하여 Word에서 사각형 도형 만들기 – 단계별 가이드
url: /ko/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 사각형 도형 만들기 – 완전한 Aspose.Words 튜토리얼

Word 문서에 **사각형 도형**을 만들어야 하는데 어디서 시작해야 할지 막막하셨나요? 보고서나 청구서를 자동화할 때 많은 개발자들이 겪는 문제입니다. 이 가이드에서는 Aspose.Words for .NET을 사용해 사각형 도형을 만들고, 도형 투명도를 설정하고, 그림자 색상을 지정한 뒤 **Word 문서 저장**까지의 정확한 단계를 차근차근 설명합니다.

문서 객체 생성부터 최종 `.docx` 파일 저장까지 모두 다루므로, 끝까지 읽으시면 **프로그래밍으로 Word 문서 만들기**를 추측 없이 구현할 수 있습니다. 외부 참고 자료 없이 프로젝트에 복사·붙여넣기만 하면 되는 자체 포함 솔루션입니다.

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 동작)
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)
- C# 기본 문법에 대한 약간의 이해
- 원하는 IDE (Visual Studio, Rider, VS Code 등)

> **Pro tip:** Aspose.Words 무료 체험판을 사용하면 출력 파일에 워터마크가 삽입됩니다. 실제 서비스에서는 유효한 라이선스가 필요합니다.

## 1단계: Document와 Builder 초기화

먼저 빈 Word 문서를 만들고, 내용을 삽입할 수 있는 `DocumentBuilder`를 생성합니다. Builder는 페이지에 그리는 가상의 펜이라고 생각하면 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **왜 중요한가:** `DocumentBuilder` 없이 저수준 노드 트리를 직접 조작해야 하므로 오류가 발생하기 쉽고 코드 가독성이 떨어집니다.

## 2단계: 사각형 도형 만들기

이제 **사각형 도형**을 실제로 **생성**합니다. `InsertShape` 메서드는 `ShapeType` 열거형, 너비, 높이(포인트)를 인수로 받습니다. 반환된 `Shape` 객체를 통해 이후 시각 속성을 조정할 수 있습니다.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

이 시점에서 사각형은 현재 단락에 고정된 검은색 실선 박스입니다. 필요에 따라 이동·크기 조정·회전이 가능합니다.

![create rectangle shape with shadow](/images/rectangle-shadow.png "Word 문서에 회색 그림자가 있는 사각형 도형을 표시")

*이미지 대체 텍스트: Word 문서에 그림자가 있는 사각형 도형 만들기*

## 3단계: 도형 투명도 설정

투명도는 도형 채우기의 “비투명” 정도를 의미합니다. Aspose.Words는 `0.0`(불투명)부터 `1.0`(완전 투명)까지의 값을 갖는 `Transparency` 속성을 제공합니다. 여기서는 **도형 투명도**를 40 %로 설정해 배경 텍스트가 읽히도록 합니다.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **예외 상황:** 그림자는 보이게 하고 도형 자체는 완전히 보이지 않게 하려면 `Transparency`를 `1.0`으로 설정하고 외곽선 두께를 0이 아닌 값으로 지정합니다.

## 4단계: 그림자 구성

미묘한 드롭 그림자는 깊이감을 줍니다. **그림자 색상**을 중간 회색으로 지정하고, 흐림 반경과 수평·수직 오프셋을 몇 포인트씩 조정합니다.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **왜 중요한가:** 너무 날카롭거나 어두운 그림자는 인쇄 결함처럼 보일 수 있습니다. `Blur`와 `Transparency` 값을 자연스러울 때까지 조정하세요.

## 5단계: Word 문서 저장

마지막으로 **Word 문서**를 디스크에 **저장**합니다. `Save` 메서드는 파일 확장자를 기준으로 형식을 자동 판단하며, `.docx`는 최신 OpenXML 형식입니다.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

폴더가 존재하지 않으면 Aspose.Words는 `ArgumentException`을 발생시킵니다. 경로가 올바른지 확인하거나 미리 디렉터리를 생성하세요.

## 전체 작업 예제

아래는 모든 단계를 하나로 모은 완전 실행 가능한 프로그램입니다. 새 콘솔 프로젝트에 복사하고 **F5**를 눌러 실행해 보세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 예상 결과

`ShadowRectangle.docx`를 Microsoft Word에서 열면, 40 % 투명도의 연한 회색 사각형에 부드럽게 약간 오프셋된 그림자가 표시됩니다. 도형은 빈 페이지에 위치해 추가 콘텐츠를 삽입할 준비가 되어 있습니다.

## 자주 묻는 질문 및 변형

**다른 도형이 필요하면?**  
`ShapeType.Rectangle`을 다른 열거형 값(`Ellipse`, `Triangle`, `Star` 등)으로 바꾸면 됩니다. 나머지 코드는 동일하게 유지됩니다.

**외곽선상을 바꿀 수 있나요?**  
예 — `rectangleShape.StrokeColor = System.Drawing.Color.Blue;`와 필요 시 `rectangleShape.StrokeWeight = 1.5;`를 설정하세요.

**페이지 특정 위치에 도형을 배치하려면?**  
`rectangleShape.WrapType = WrapType.None;`을 설정한 뒤 `rectangleShape.Left`와 `rectangleShape.Top` 속성을 포인트 단위로 조정합니다.

**사각형 안에 텍스트를 넣을 수 있나요?**  
가능합니다. 도형을 만든 뒤 `rectangleShape.AppendChild(new Paragraph(document))`를 호출하고 `Run`을 추가해 텍스트를 삽입하세요. 풍부한 서식을 원한다면 `rectangleShape.TextBox` 속성을 설정합니다.

## 전문가 팁 및 함정

- **라이선스 먼저 적용:** 라이선스를 적용하지 않으면 Aspose.Words가 첫 페이지에 워터마크를 삽입해 테스트 시 혼란을 줄 수 있습니다.
- **성능 팁:** 루프에서 다수의 문서를 생성할 때는 단일 `Document` 인스턴스를 재사용하고, 저장 후 `document.RemoveAllChildren();`를 호출해 GC 부하를 최소화하세요.
- **그림자 가시성:** 저해상도 화면에서는 미묘한 그림자가 보이지 않을 수 있습니다. 디버깅 시 `Blur` 또는 `OffsetX/Y` 값을 늘렸다가, 실제 배포 시 다시 낮추세요.

## 다음 단계

이제 **사각형 도형 만들기**, **도형 투명도 설정**, **그림자 색상 지정**, **Word 문서 저장** 방법을 알았으니 튜토리얼을 확장해 보세요:

- 여러 도형을 추가하고 그룹화하기
- 보고서 레이아웃을 위해 표 셀 안에 사각형 삽입하기
- `DocumentBuilder.InsertHtml`과 결합해 HTML‑스타일 콘텐츠 오버레이하기
- `Glow`나 `Reflection` 같은 다른 시각 효과를 탐색해 UI‑같은 풍부한 문서 만들기

실험하고, 오류를 만들고, 다시 다듬으세요 — 프로그래밍 기반 문서 생성은 시각 디자인과 코딩이 만나는 놀이터입니다.

---

*코딩 즐겁게! 문제가 발생하면 아래에 댓글을 남겨 주세요. 함께 해결해 드리겠습니다.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}