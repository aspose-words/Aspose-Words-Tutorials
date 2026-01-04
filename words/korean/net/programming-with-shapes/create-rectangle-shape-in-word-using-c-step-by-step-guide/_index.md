---
category: general
date: 2026-01-03
description: C#를 사용하여 Word에 사각형 도형을 만들고 그림자를 추가합니다. Word에 도형을 삽입하고, 도형에 그림자를 적용하며,
  프로그래밍으로 Word 문서를 생성하는 방법을 배웁니다.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: ko
og_description: C#를 사용하여 Word에서 사각형 도형을 만들고 도형에 그림자를 추가합니다. 이 가이드를 따라 Word에 도형을 삽입하고,
  그림자를 설정하며, 프로그래밍 방식으로 문서를 생성하세요.
og_title: C#를 사용하여 Word에서 사각형 도형 만들기 – 완전 튜토리얼
tags:
- C#
- Word Automation
- Aspose.Words
title: C#를 사용하여 Word에서 사각형 도형 만들기 – 단계별 가이드
url: /ko/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에서 사각형 모양 만들기 – 완전 튜토리얼

Word 문서에서 **create rectangle shape**가 필요했지만 어디서 시작해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다—많은 개발자들이 **add shadow to shape**를 적용해 세련된 모습을 만들고자 할 때 같은 문제에 부딪힙니다. 이 튜토리얼에서는 **insert shape in Word**하는 정확한 단계와 미묘한 그림자를 적용하는 방법, 그리고 최종적으로 **c# generate word document** 파일을 생성하여 사용자에게 제공하는 과정을 안내합니다.

우리는 프로젝트 설정부터 그림자 속성 조정까지 모든 과정을 다루고, 실행 가능한 코드 샘플로 마무리합니다. 불필요한 내용은 없으며, 바로 적용 가능한 실용적인 내용만 제공합니다.

## 배워게 될 내용

- C#에서 Aspose.Words(또는 Open XML)를 사용하여 **create rectangle shape**하는 방법  
- 깊이를 위해 **add shadow to shape**에 필요한 정확한 속성  
- `DocumentBuilder`를 사용하여 모양을 배치하는 위치  
- 파일을 저장하여 Microsoft Word에서 올바르게 열리는 방법  
- 실제 시나리오를 위한 팁, 함정 및 변형  

### Prerequisites

- .NET 6.0 이상 (코드는 .NET Core 및 .NET Framework에서도 동작합니다)  
- Word 파일을 조작할 수 있는 NuGet 패키지 – 우리는 API가 간결한 **Aspose.Words for .NET**를 사용할 것입니다. Open XML SDK를 선호한다면 개념은 동일하지만 클래스만 다릅니다.  
- Visual Studio, VS Code 또는 원하는 C# IDE  

> **Pro tip:** 예산이 제한된 경우 Aspose에서 제공하는 무료 체험판을 활용하면 학습에 충분합니다. 테스트할 때는 라이선스 라인을 주석 처리하면 됩니다.

## Step 1: Install the Word‑Processing Library

먼저 라이브러리를 프로젝트에 추가합니다. 솔루션 폴더에서 터미널을 열고 다음 명령을 실행하세요:

```bash
dotnet add package Aspose.Words
```

Open XML SDK를 사용하는 경우 명령은 `dotnet add package DocumentFormat.OpenXml`이 됩니다. 이 가이드의 나머지 부분은 Aspose.Words를 기준으로 설명하지만, API 호출을 교체하는 것은 간단합니다.

## Step 2: Create a New Blank Document

라이브러리가 준비되었으니, 깨끗한 `Document` 객체를 시작점으로 **create rectangle shape**를 할 수 있습니다. 이것을 새로운 캔버스로 생각하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder`는 저수준 노드 트리를 직접 다루지 않고도 콘텐츠를 삽입할 수 있는 고수준 인터페이스를 제공합니다.

## Step 3: Insert the Rectangle Shape

빌더를 이용해 **insert shape in Word**를 수행합니다. `InsertShape` 메서드는 모양 유형과 크기(너비, 높이)를 포인트 단위로 받습니다.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

이 시점에서 사각형이 문서에 나타나지만 다소 평면적으로 보입니다. 다음 단계에서 이를 개선합니다.

## Step 4: Add Shadow to the Shape

그림자는 모양에 깊이감을 부여합니다. `Shadow` 객체를 사용하면 블러, 거리, 각도, 색상 및 투명도를 세밀하게 조정할 수 있습니다. 아래는 대부분의 보고서에 잘 맞는 전체 설정 예시입니다.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**왜 이러한 값을 사용했을까요?**  
- `BlurRadius`가 `5.0`이면 가장자리가 부드럽게 유지되면서 흐릿해 보이지 않습니다.  
- `Distance`가 `4.0`이면 그림자가 충분히 눈에 띄게 오프셋됩니다.  
- `Angle` `45`는 왼쪽 위에서 자연광이 비추는 효과를 모방하며, 일반적인 UI 관행입니다.  
- `Transparency` `0.3`은 그림자가 모양의 채우기를 압도하지 않도록 합니다.

더 극적인 효과가 필요하면 `BlurRadius`를 늘리고 `Transparency`를 낮추세요. 거의 보이지 않을 정도의 미세한 상승 효과를 원한다면 그 값을 반대로 설정하면 됩니다.

## Step 5: Save the Document

마지막으로 파일을 디스크에 기록합니다. `Save` 메서드는 파일 확장자를 기반으로 형식을 자동 감지하므로 `.docx`를 사용하면 최신 Word 형식으로 저장됩니다.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Microsoft Word에서 `ShadowRectangle.docx`를 열면 부드러운 그림자가 적용된 선명한 사각형을 확인할 수 있습니다—즉, “**how to add shape**”에 대한 전문적인 마무리를 원했던 바로 그 결과입니다.

![Create rectangle shape with shadow in Word](placeholder-image.png "Create rectangle shape with shadow in Word")

*Image alt text: Word에서 그림자와 함께 사각형 모양 만들기*

## Full Working Example

전체 코드를 한 번에 확인해 보세요. 아래 코드를 콘솔 앱에 복사‑붙여넣기하고 **F5**를 눌러 실행하면 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Expected Result

- 생성된 `ShadowRectangle.docx`에는 커서가 위치한 곳을 중심으로 **one rectangle shape**가 포함됩니다.  
- 사각형은 45° 각도로 오프셋된 **soft, 30 % transparent black shadow**을 표시합니다.  
- 다른 내용은 추가되지 않아 파일이 가볍고, 큰 보고서에 쉽게 삽입할 수 있습니다.

## Common Questions & Edge Cases

### What if I need a different shape?

`ShapeType.Rectangle`를 원하는 다른 `ShapeType` 열거값(예: `Ellipse`, `Triangle`)으로 교체하면 됩니다. 그림자 API는 동일하게 동작하므로 설정을 재사용할 수 있습니다.

### How do I change the fill color?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Can I add the shape to a specific paragraph?

예. `InsertShape`를 호출하기 전에 `builder.MoveToParagraph(index)`를 사용해 `DocumentBuilder`를 목표 단락으로 이동하면 모양이 정확히 원하는 위치에 삽입됩니다.

### What about older Word formats (.doc)?

확장자를 다음과 같이 변경하면 됩니다:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

그림자 기능은 Word 2003 이후 버전에서 지원되므로 여전히 효과를 확인할 수 있습니다.

### Using Open XML SDK instead of Aspose?

절차는 동일합니다: `WordprocessingDocument`를 생성하고 `Drawing` 요소를 추가한 뒤 `<a:shadow>` 속성을 설정합니다. XML이 더 길어지지만 크기, 블러, 거리, 각도와 같은 개념은 동일합니다.

## Tips to Avoid Pitfalls

- **Don’t forget the license**를 사용 중인 유료 Aspose 버전에 적용하세요. 그렇지 않으면 워터마크가 표시됩니다.  
- **Units are points**, 픽셀이 아니라 포인트 단위입니다. 일반 화면 픽셀은 약 0.75 pt이므로 크기를 적절히 조정하세요.  
- **Shadow properties are ignored**는 모양의 `WrapType`이 `Inline`으로 설정된 경우 무시됩니다. 그림자 렌더링을 적용하려면 `WrapType = WrapType.Square`와 같이 플로팅 형태로 설정하세요.  
- **Saving to a network share**는 적절한 권한이 필요할 수 있으니, 경로를 먼저 테스트해 보세요.

## Conclusion

이제 C#를 사용해 Word 문서에 **create rectangle shape**를 삽입하고, **add shadow to shape**를 적용하며, **c# generate word document** 파일을 즉시 사용할 수 있게 만드는 방법을 알게 되었습니다. 핵심 단계—라이브러리 설치, `Document` 인스턴스 생성, 모양 삽입, 그림자 설정, 저장—은 기억하기 쉽고 다른 모양, 색상 또는 동적 데이터에도 손쉽게 적용할 수 있습니다.

다음 단계는 무엇일까요? 여러 모양을 겹쳐 보거나 이미지를 삽입하고, 표와 차트가 포함된 전체 보고서를 생성해 보세요. 데이터 값에 따라 그림자 강도를 조정하는 조건부 서식을 탐색하면 문서를 기능적일 뿐만 아니라 시각적으로도 매력적으로 만들 수 있습니다.

자유롭게 실험해 보고, 문제가 발생하면 아래에 댓글을 남겨 주세요. 즐거운 코딩 되시고, 여러분의 Word 문서에 언제나 완벽한 드롭 섀도우가 적용되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}