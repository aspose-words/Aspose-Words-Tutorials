---
category: general
date: 2026-03-27
description: C#로 워드 문서를 만들고 도형을 추가하고 도형에 그림자를 적용하며 그림자 거리를 설정하는 방법을 배웁니다. Aspose.Words
  단계별 가이드.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: ko
og_description: C#로 사각형 모양과 사용자 지정 그림자가 있는 워드 문서를 만들고, 그림자 거리와 스타일을 설정하는 전체 튜토리얼을
  따라보세요.
og_title: C#로 워드 문서 만들기 – 그림자 있는 도형 추가
tags:
- Aspose.Words
- C#
- Document Automation
title: C#로 워드 문서 만들기 – 그림자 있는 도형 추가
url: /ko/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document C# – Add Shape with Shadow

보고서 템플릿에 깔끔한 사각형을 넣고 싶으신가요? 혹은 레이아웃을 돋보이게 할 은은한 드롭‑섀도를 원하시나요? 이 튜토리얼에서는 바로 그 방법—도형을 추가하고, 섀도를 적용하며, Aspose.Words를 사용해 섀도 거리까지 조정하는 과정을 단계별로 안내합니다.

빈 문서에서 사각형을 삽입하고, 사전 설정된 섀도를 적용한 뒤 파일을 저장합니다. 완료되면 .docx 파일을 Word에서 바로 열어 효과를 확인할 수 있습니다. 별도의 외부 도구 없이 순수 C# 코드만으로 구현합니다.

## Prerequisites

- .NET 6 (또는 최신 .NET Framework) 설치
- Visual Studio 2022 또는 C# 확장 기능이 포함된 VS Code
- Aspose.Words for .NET NuGet 패키지 (`Aspose.Words` 버전 23.12 이상)  
  패키지 매니저 콘솔에서 다음 명령으로 추가합니다:

  ```powershell
  Install-Package Aspose.Words
  ```

이것만 있으면 됩니다—추가 DLL이나 COM 인터옵 필요 없음.

## Step 1: Initialize a New Document and Builder – *create word document c#* Basics

먼저 Word 파일을 나타내는 `Document` 객체와 이를 편집할 `DocumentBuilder` 를 생성합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this step matters:** `Document` 클래스는 모든 Word 파트(페이지, 스타일, 이미지)를 담는 컨테이너이며, Builder는 저수준 노드 조작을 추상화한 고수준 API로, XML을 직접 다루지 않고도 **create word document c#** 를 손쉽게 할 수 있게 해줍니다.

## Step 2: Insert a Rectangle Shape – *how to create rectangle*  

이제 페이지에 사각형을 배치합니다. 크기는 포인트 단위(1 pt ≈ 1/72 in)로 지정합니다.

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** 다른 도형이 필요하면 `ShapeType.Rectangle`을 `ShapeType.Ellipse`, `ShapeType.Triangle` 등으로 교체하면 됩니다. 동일한 코드는 **how to add shape** 모든 유형에 적용됩니다.

## Step 3: Apply a Preset Shadow and Fine‑Tune It – *apply shadow to shape*  

Aspose.Words는 여러 사전 설정 섀도 포맷을 제공합니다. 여기서는 `Preset1`을 사용하고 거리, 블러, 투명도, 색상을 커스터마이즈합니다.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Why customize the shadow?** `Distance` 속성은 섀도가 사각형으로부터 떨어진 거리를 제어합니다—3‑D 렌더링에서 “리프트”와 같은 개념입니다. `BlurRadius`를 조정하면 가장자리가 부드러워지고, `Transparency`를 활용하면 미묘하고 전문적인 느낌을 만들 수 있습니다. 이는 **set shadow distance** 요구사항을 충족시키며 **apply shadow to shape** 를 유연하게 구현하는 방법을 보여줍니다.

## Step 4: Save the Document – *create word document c#* Completion

마지막으로 문서를 디스크에 저장합니다. 쓰기 권한이 있는 폴더 경로로 수정하세요.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Microsoft Word에서 결과 파일을 열면, 연한 파란색 사각형에 회색 섀도가 5 pt 만큼 오프셋된 모습을 확인할 수 있습니다. 이는 **create word document c#** 로 스타일이 적용된 도형을 성공적으로 만든 증거입니다.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# 예시: 그림자와 사각형"}

## Optional Variations & Edge Cases

| 시나리오 | 변경 내용 | 중요 이유 |
|----------|----------|-----------|
| **다른 섀도 스타일** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | 추가 코드 없이 더 강렬한 효과 제공 |
| **프리셋 없이 커스텀 섀도** | `Format`을 생략하고 `OffsetX`, `OffsetY`를 직접 설정 | 방향과 깊이를 완전 제어 |
| **여러 도형** | 저장하기 전에 `builder.InsertShape`를 다시 호출 | 아이콘, 로고 등 복잡한 템플릿에 유용 |
| **구버전 Aspose와 호환** | `ShadowEffect` 클래스 사용 (v20.x에서 제공) | 레거시 프로젝트에서도 동작 보장 |
| **PDF로 저장** | `document.Save("ShadowShape.pdf");` | PDF 출력에서도 동일한 섀도 렌더링 |

> **Common question:** *섀도가 Word에서 보이지 않으면 어떻게 하나요?*  
> 최신 버전의 Aspose.Words(≥ 22.9)를 사용하고 있는지 확인하세요. 이전 버전은 섀도 지원이 제한적이었습니다. 또한 Word 2016 이상 최신 버전에서 문서를 열어야 합니다.

## Full Working Example

아래는 복사‑붙여넣기만 하면 바로 실행 가능한 전체 프로그램입니다. 모든 `using` 지시문, 주석, 오류 처리까지 포함돼 있어 원활한 경험을 제공합니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

프로그램을 실행하고 `C:\Temp\ShadowShape.docx` 로 이동하면, 우리가 설정한 정확한 섀도가 적용된 사각형을 확인할 수 있습니다.

## Recap & Next Steps

- 이제 **create word document c#** 로 사각형을 삽입하고 **apply shadow to shape** 와 **set shadow distance** 를 커스터마이즈하는 방법을 알게 되었습니다.  
- 예제는 Aspose.Words를 사용해 OpenXML 복잡성을 추상화하고 Word 버전 간 일관된 렌더링을 보장합니다.  
- 더 나아가고 싶다면 여러 도형을 결합하거나 사각형 안에 텍스트를 넣어보세요. 혹은 동일 문서를 PDF로 내보내어 섀도가 어떻게 변환되는지도 확인해 보세요.

### Related Topics You Might Explore

- 헤더/푸터에 **how to add shape** 로 브랜드 로고 삽입하기  
- **Aspose.Words** 로 차트와 표를 프로그래밍 방식으로 삽입하기  
- 벡터 도형이 아닌 사진에 **shadow effects** 적용하기  
- 인보이스나 인증서와 같은 대량 문서 자동 생성

코드를 자유롭게 실험하고, 깨뜨렸다가 다시 고쳐보세요—가장 빠른 학습 방법입니다. 문제가 생기면 아래 댓글을 남기거나 공식 Aspose.Words 문서를 참고해 깊이 있는 API 정보를 확인하세요.

Happy coding, and enjoy making your Word files look a little more polished!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}