---
category: general
date: 2026-03-25
description: C#에서 PDF 문서를 만들고, 사각형 도형을 추가하고, 채우기 색상을 설정하며, 도형 크기를 조정하고, 투명도를 설정하는
  방법을 몇 단계만에 배워보세요.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: ko
og_description: C#에서 PDF 문서를 생성하고 사각형을 추가한 뒤, 채우기 색상, 크기 및 투명도를 설정하여 깔끔한 PDF 출력을 확인하세요.
og_title: 사각형 모양을 사용한 PDF 문서 만들기 – C# 튜토리얼
tags:
- C#
- PDF
- Aspose.Words
title: 직사각형 도형으로 PDF 문서 만들기 – 전체 C# 가이드
url: /ko/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 사각형 모양이 포함된 PDF 문서 만들기 – 전체 C# 가이드

PDF 문서를 만들 때 사용자 정의 스타일의 도형을 포함해야 하는데 어디서 시작해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다. 보고서 생성기나 마케팅 전단지를 만들 때 프로그래밍으로 사각형을 그리며, 채우기 색상을 설정하고, 크기를 조정하고, 투명도를 조절할 수 있으면 PDF가 훨씬 더 전문적으로 보입니다.

이 튜토리얼에서는 **PDF 문서를 만들고**, **사각형 도형을 추가하고**, **채우기 색상을 설정하고**, **도형 크기를 정의하고**, **도형 투명도를 설정**하여 은은한 외부 그림자를 만드는 완전한 실행 가능한 C# 예제를 단계별로 살펴보겠습니다. 마지막에는 결과를 확인할 수 있는 단일 PDF 파일(`shadow.pdf`)이 생성됩니다.

> **Pro tip:** 동일한 방법을 다른 도형 유형(타원, 선 등)에도 적용할 수 있습니다—필요한 도형으로 `ShapeType.RECTANGLE`을 교체하면 됩니다.

## 필요 사항

| 전제 조건 | 왜 중요한가 |
|--------------|----------------|
| **.NET 6+** (or .NET Framework 4.6+) | Aspose.Words 라이브러리는 최신 런타임을 대상으로 합니다. |
| **Aspose.Words for .NET** NuGet package | `Document`, `Shape`, `ShadowEffect` 및 관련 클래스를 제공합니다. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | 샘플을 디버깅하고 실행하는 작업을 손쉽게 해줍니다. |
| **Basic C# knowledge** | 깊이 파고들지 않아도 구문을 이해할 수 있습니다. |

다음 명령줄을 사용하여 라이브러리를 설치할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

이것으로 끝입니다—추가 DLL이나 네이티브 종속성이 없습니다. 패키지가 설치되면 아래 코드를 컴파일하고 실행할 수 있습니다.

## 단계별 구현

아래에서는 프로세스를 다섯 개의 논리적 단계로 나눕니다. 각 단계는 명확한 제목(AI 모델이 인덱싱할 수 있도록)과 직접 복사‑붙여넣기 할 수 있는 짧은 코드 블록을 포함합니다.

### ## 1. PDF 문서를 만들고 캔버스를 준비하기

우리가 가장 먼저 하는 일은 `Document` 객체를 인스턴스화하는 것입니다. 이것을 최종적으로 PDF 파일이 될 빈 캔버스로 생각하면 됩니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Why?** `Document`는 모든 섹션, 단락 및 도형을 보유합니다. 깨끗한 객체로 시작하면 이전 실행에서 남은 숨겨진 아티팩트가 없음을 보장합니다.

### ## 2. 사각형 도형 추가 – 채우기 색상 설정 및 도형 크기 정의

이제 사각형을 만들고 밝은 노란색 채우기를 적용한 뒤 크기를 정의합니다. 이는 **사각형 도형 추가**, **채우기 색상 설정**, **도형 크기 설정**을 모두 포함합니다.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Note:** 너비/높이는 포인트 단위로 측정됩니다(1 포인트 = 1/72 인치). 레이아웃에 맞게 이 값을 조정하세요.

### ## 3. 외부 그림자 적용 및 도형 투명도 설정

그림자는 깊이를 더해 주며, 불투명도를 제어하는 것이 **도형 투명도 설정**의 핵심입니다. 아래에서는 30 % 투명도의 회색 외부 그림자를 구성합니다.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Why set transparency?** 30 % 투명도의 그림자는 은은하게 보이며, 사각형이 페이지에서 “평면”처럼 보이는 것을 방지합니다.

### ## 4. 도형을 문서 본문에 삽입하기

이제 사각형을 문서 첫 번째 섹션의 첫 번째 단락에 삽입합니다. 이 단계가 모든 것을 연결합니다.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Edge case:** 새 페이지에 도형이 필요하면, 도형을 추가하기 전에 `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` 를 앞에 삽입하세요.

### ## 5. 문서를 PDF 파일로 저장하기

마지막으로 메모리 내 구조를 실제 PDF 파일로 저장합니다. 파일은 지정한 폴더에 기록됩니다.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

프로그램을 실행하면 `shadow.pdf`라는 파일이 생성됩니다. 이를 열면 4 포인트만큼 오프셋된 부드러운 회색 그림자를 가진 노란색 사각형이 표시됩니다—코드가 설명한 그대로입니다.

> **Expected output:** 사각형이 페이지 왼쪽 상단 근처에 위치하고, 노란색으로 채워지며, 크기가 200 × 100 포인트이고, 반투명 외부 그림자를 가진 단일 페이지 PDF.

## 전체 작업 예제 (복사‑붙여넣기 준비 완료)

아래는 전체 소스 파일이며, 새 콘솔 프로젝트에 바로 넣어 사용할 수 있습니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** `YOUR_DIRECTORY`를 `C:\Temp`와 같은 절대 경로나 `.\output`과 같은 상대 경로로 교체하세요. 프로그램은 해당 폴더가 없을 경우 자동으로 생성합니다.

## 자주 묻는 질문 (FAQ)

**Q: 페이지에서 사각형 위치를 변경할 수 있나요?**  
A: 물론입니다. 도형을 단락에 추가하기 전에 `rectangle.Left`와 `rectangle.Top`(둘 다 포인트 단위)을 설정하면 됩니다.

**Q: 투명 그림자 대신 투명 채우기가 필요하면 어떻게 하나요?**  
A: `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` 를 사용하세요 – 첫 번째 인자는 알파 채널(0‑255)이며, 128은 약 50 % 투명도를 의미합니다.

**Q: 이것이 .NET Core에서도 작동하나요?**  
A: 네. Aspose.Words는 .NET Standard 2.0+를 지원하므로 .NET 6, .NET 7 또는 .NET Framework 4.6+에서도 동일한 코드를 실행할 수 있습니다.

**Q: 여러 도형을 추가하려면 어떻게 해야 하나요?**  
A: 각 도형마다 단계 2‑4를 반복하면 되며, 필요에 따라 다른 단락이나 섹션에 삽입할 수 있습니다.

## 결론

우리는 이제 **PDF 문서를 처음부터 만들고**, **사각형 도형을 추가하고**, **채우기 색상을 설정하고**, **크기를 정의하고**, **도형 투명도를 조정**하여 세련된 그림자 효과를 구현했습니다. 샘플 코드는 독립적이며 1분 이내에 실행되고, 보다 복잡한 PDF 레이아웃에 필요한 핵심 개념을 보여줍니다.

다음 도전을 준비했나요? 사각형을 둥근 모서리 도형으로 교체하거나, 도형 안에 이미지를 삽입하거나, 자동으로 목차를 생성해 보세요. 동일한 API를 사용하면 텍스트, 이미지, 벡터를 겹쳐 배치할 수 있으니 가능성은 무한합니다.

이 가이드가 도움이 되었다면 GitHub에서 별을 달아주시고, 팀원과 공유하거나 여러분만의 변형을 댓글로 남겨 주세요. 즐거운 코딩 되세요! 

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}