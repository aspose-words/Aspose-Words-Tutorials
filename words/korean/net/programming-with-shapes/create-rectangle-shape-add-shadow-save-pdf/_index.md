---
category: general
date: 2026-02-24
description: C#에서 Aspose.Words를 사용해 사각형 모양을 만든 뒤, 모양에 그림자를 추가하고 문서를 PDF로 저장합니다. 몇
  분 안에 그림자 추가 방법과 PDF 저장 방법을 배워보세요.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: ko
og_description: Aspose.Words를 사용해 C#에서 사각형 모양을 만든 뒤 그림자를 추가하고 문서를 PDF로 저장하는 완전한 단계별
  가이드.
og_title: 사각형 만들기, 그림자 추가 및 PDF 저장
tags:
- Aspose.Words
- C#
- PDF generation
title: 사각형 모양 만들기, 그림자 추가 및 PDF 저장
url: /ko/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 사각형 모양 만들기, 그림자 추가 및 PDF 저장

Word 문서에서 **사각형 모양 만들기**가 필요했지만 멋진 드롭 섀도우와 PDF 출력도 원하셨나요? 당신만 그런 것이 아닙니다. 많은 보고서나 청구서 생성 프로젝트에서 시각적 마감—예를 들어 은은한 그림자—이 “그냥 또 하나의 파일”과 “전문가 수준 문서” 사이의 차이를 만들곤 합니다.  

이 튜토리얼에서는 바로 그 과정을 단계별로 살펴보겠습니다: **Aspose.Words for .NET**을 사용해 사각형 모양을 만들고, 그림자를 추가한 뒤, **문서를 PDF로 저장**합니다. 끝까지 따라오시면 그림자가 있는 사각형이 포함된 PDF를 생성하는 C# 콘솔 앱을 바로 실행할 수 있게 되고, 그림자 조정이나 내보내기 옵션 변경 방법도 이해하게 됩니다.

## 필요 사항

- .NET 6 SDK (또는 최신 .NET 버전) – API는 .NET Framework 4.x에서도 동일하게 작동합니다.  
- Aspose.Words for .NET NuGet 패키지 (`Aspose.Words`) – `dotnet add package Aspose.Words` 명령으로 설치합니다.  
- 코드 편집기 – Visual Studio, VS Code, Rider 중 하나면 충분합니다.  

이 예제에는 별도의 라이선스 단계가 필요하지 않으며, 무료 평가 모드만으로도 PDF 출력을 확인할 수 있습니다.

## 단계 1: 프로젝트 설정 및 네임스페이스 가져오기

먼저 콘솔 프로젝트를 만들고 필요한 클래스를 가져옵니다.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*왜 중요한가:* `Document`와 `DocumentBuilder`는 캔버스를 제공하고, `Shape`와 `ShadowFormat`은 사각형을 그리며 스타일을 지정합니다. 미리 가져오면 이후 코드가 깔끔해집니다.

## 단계 2: **사각형 모양 만들기** 원하는 크기로

이제 빈 문서를 만들고 사각형을 삽입합니다. `InsertShape` 메서드가 바로 스타일을 적용할 수 있는 `Shape` 객체를 반환한다는 점에 주목하세요.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*설명*: 크기는 포인트 단위(1 pt = 1/72 in)로 표시됩니다. 레이아웃에 맞게 숫자를 조정하세요. 그림자를 돋보이게 하기 위해 사각형에 연한 파란색 채우기를 적용했습니다.

## 단계 3: **그림자 추가** – 효과 미세 조정

그림자는 단순히 “켜기/끄기”가 아닙니다. 색상, 블러, 거리, 방향, 투명도까지 제어할 수 있습니다. 대부분의 보고서에 잘 맞는 실용적인 설정을 아래에 제시합니다.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*값을 바꾸고 싶을 때:*  
- **BlurRadius** – 꿈같은 효과를 원하면 늘리고, 선명한 가장자리를 원하면 줄이세요.  
- **Direction** – 0°는 오른쪽, 90°는 아래, 180°는 왼쪽 등을 의미합니다. 페이지 레이아웃에 맞게 회전하세요.  
- **Transparency** – `0`이면 완전 불투명, `0.5`이면 반투명 등으로 설정합니다.

### 그림자 추가 방법 – 대체 접근법

**다중 레이어 그림자**(예: 외곽은 어둡고 내부는 밝은 그림자)가 필요하면 두 번째 shape를 만들고 오프셋을 적용한 뒤 다른 `ShadowFormat`을 설정하면 됩니다. 혹은 “블러 없음” 효과를 원한다면 `BlurRadius = 0`으로 설정하세요.

## 단계 4: **문서 PDF 저장** – 최종 내보내기

사각형과 그림자가 준비되었으면 마지막 단계는 파일을 PDF로 저장하는 것입니다. Aspose.Words가 내부적으로 변환을 처리하므로 원하는 형식으로 `Save`만 호출하면 됩니다.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*팁*: PDF 규격(PDF/A, PDF/X) 제어나 폰트 포함이 필요하면 다음과 같이 오버로드를 사용합니다:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

이것이 **PDF 저장 방법**을 한눈에 정리한 내용입니다.

## 전체 실행 가능한 예제

아래는 `Program.cs`에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. 그대로 컴파일하고 실행하면 됩니다(출력 폴더가 존재하는지 확인하세요).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### 예상 결과

생성된 `ShadowRectangle.pdf`를 열어보세요. 연한 파란색 사각형과 부드러운 회색 그림자가 45° 오른쪽 아래로 오프셋된 단일 페이지가 표시되며 가장자리는 깔끔합니다. PDF는 최신 리더(Adobe Acrobat, Edge, Chrome) 어디서든 열 수 있어야 합니다.

![PDF에서 그림자가 있는 사각형 모양 만들기](/images/shadow-rectangle.png "PDF에서 그림자가 있는 사각형 모양 만들기")

*(이미지 alt 텍스트는 SEO를 위해 주요 키워드를 포함합니다.)*

## 일반적인 질문 및 엣지 케이스 처리

**PDF에서 그림자가 사라지는 경우**  
Aspose.Words 최신 버전(≥23.3)을 사용하고 있는지 확인하세요. 이전 빌드에서는 PDF 변환 시 일부 그림자 속성이 무시되는 버그가 있었습니다.

**브랜드 색상에 맞게 그림자 색을 바꿀 수 있나요?**  
물론입니다—`System.Drawing.Color.Gray`를 원하는 `Color`로 교체하면 됩니다. 예: 반투명 파란색은 `Color.FromArgb(128, 0, 0, 255)`.

**다른 도형(타원, 별 등)에 그림자를 추가하려면?**  
`ShadowFormat`은 모든 `Shape` 객체에 동일하게 적용됩니다. 도형을 만든 뒤 `ShadowFormat`을 가져와 속성을 설정하면 됩니다.

**DPI나 스케일링 문제는요?**  
PDF 렌더링은 shape의 포인트 크기를 그대로 반영합니다. 인쇄용 고해상도가 필요하면 shape 크기를 조정하거나 `PdfSaveOptions.ImageResolution`을 설정하세요.

**PNG 등 다른 포맷으로 내보낼 수 있나요?**  
예—`document.Save("output.png", SaveFormat.Png)`와 같이 호출하면 됩니다. 그림자는 동일하게 렌더링됩니다.

## 전문가 팁 및 모범 사례

- **Builder 재사용**: 여러 shape를 추가한다면 `DocumentBuilder` 인스턴스를 하나만 유지하세요. 새로 만드는 것보다 비용이 적습니다.  
- **배치 저장**: 루프에서 다수의 PDF를 생성할 때는 `PdfSaveOptions` 객체를 재사용해 메모리 할당을 줄이세요.  
- **테스트**: 저장 후 항상 PDF를 열어 그림자가 정상적으로 표시되는지 확인합니다. 일부 PDF 뷰어는 그림자를 약간 다르게 렌더링하므로 Adobe Acrobat을 기준으로 삼는 것이 가장 신뢰됩니다.  
- **성능**: 대용량 문서에서는 `DocumentBuilder.InsertShape`의 자동 페이지 나눔을 비활성화하려면 `builder.PageSetup.DifferentFirstPageHeaderFooter = false`로 설정하세요(필요 없는 경우).

## 결론

우리는 Aspose.Words for .NET을 사용해 **사각형 모양 만들기**, **그림자 추가**, **문서 PDF 저장**을 수행하는 전체 과정을 다루었습니다. 코드가 간결하고 개념이 명확히 설명되었으며, 이제 다른 도형, 그림자 스타일, 내보내기 옵션을 실험할 탄탄한 기반을 갖추게 되었습니다.  

다음 단계? 사각형을 둥근‑  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}