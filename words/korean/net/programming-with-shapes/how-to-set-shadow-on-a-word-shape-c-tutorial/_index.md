---
category: general
date: 2026-03-30
description: C#를 사용하여 Word 도형에 그림자를 설정하는 방법을 배웁니다. 이 가이드는 도형 그림자 추가, 도형 투명도 조정 및 사각형
  그림자 추가 방법도 보여줍니다.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: ko
og_description: C#에서 Word 도형에 그림자를 설정하는 방법은? 단계별 가이드를 따라 도형 그림자를 추가하고, 도형 투명도를 조정하며,
  사각형 그림자를 추가하세요.
og_title: Word 도형에 그림자 설정 방법 – C# 튜토리얼
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Word 도형에 그림자 적용 방법 – C# 튜토리얼
url: /ko/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 도형에 그림자 설정하기 – C# 튜토리얼

Ever wondered **그림자 설정 방법** on a shape inside a Word document without fiddling with the UI? You're not the only one. In many reports or marketing decks a subtle drop‑shadow makes a rectangle pop, and doing it programmatically saves hours.

In this guide we’ll walk through a complete, ready‑to‑run example that not only shows **그림자 설정 방법**, but also covers **add shape shadow**, **adjust shape transparency**, and even **add rectangle shadow** for those classic call‑out boxes. By the end you’ll have a Word file (`output.docx`) that looks polished, and you’ll understand why each property matters.

## Prerequisites

- .NET 6+ (또는 .NET Framework 4.7.2)와 C# 컴파일러  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)  
- C# 및 Word 객체 모델에 대한 기본적인 이해  

No additional libraries are required—everything lives inside Aspose.Words.

---

## C#에서 Word 도형에 그림자 설정하기

Below is the complete source file. Save it as `Program.cs` and run it from your IDE or `dotnet run`. The code loads an existing `.docx`, finds the first shape (a rectangle by default), turns on its shadow, tweaks a few visual parameters, and saves the result.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **What you’ll see** – 이제 사각형에 검은색 드롭‑섀도우가 적용되어 30 % 투명하고, 오른쪽과 아래로 각각 5 pt 이동했으며 부드러운 블러가 적용됩니다. Word에서 `output.docx`를 열어 확인하세요.

## 도형 투명도 조정 – 왜 중요한가

Transparency isn’t just an aesthetic knob; it influences readability. A 0.0 value makes the shadow fully opaque, while 1.0 hides it completely. In the snippet above we used `0.3` to achieve a subtle effect that works on both light and dark backgrounds. Feel free to experiment:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Remember, **adjust shape transparency** can also be applied to the shape’s fill color if you need a semi‑transparent rectangle itself.

## 다양한 객체에 도형 그림자 추가하기

The code we used targets a `Shape` object, but the same `ShadowFormat` properties exist on **Image**, **Chart**, and even **TextBox** objects. Here’s a quick pattern you can copy‑paste:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

So whether you’re **add shape shadow** to a logo or a decorative icon, the approach stays identical.

## 모든 도형에 그림자 추가하기 – 예외 상황

1. **Shape without a bounding box** – 일부 Word 도형(예: 자유형 스크리블)은 그림자를 지원하지 않습니다. `ShadowFormat.Visible`를 설정하려고 하면 조용히 실패합니다. 안전하게 처리하려면 `shape.IsShadowSupported`를 확인하세요.  
2. **Older Word versions** – 그림자 속성은 Word 2007 이상 기능에 매핑됩니다. Word 2003을 지원해야 한다면 파일을 열 때 그림자가 무시됩니다.  
3. **Multiple shadows** – 현재 Aspose.Words는 도형당 하나의 그림자만 지원합니다. 이중 레이어 효과가 필요하면 도형을 복제하고, 위치를 오프셋한 뒤 서로 다른 그림자 설정을 적용하세요.

## 사각형 그림자 추가 – 실제 사용 사례

Imagine you’re generating a quarterly report and each section header is a colored rectangle. Adding a **add rectangle shadow** gives the page a “card‑like” look. The steps are identical to the base example; just make sure the shape you target is indeed a rectangle (`shape.ShapeType == ShapeType.Rectangle`). If you need to create the rectangle from scratch, see the snippet below:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Running the full program with this addition will give you a fresh rectangle that already carries the desired **add rectangle shadow** effect.

---

![Word shape with shadow](placeholder-image.png){alt="Word에서 도형에 그림자 설정 방법"}

*그림: 그림자 설정을 적용한 후의 사각형.*

## 빠른 요약 (핵심 포인트 정리)

- **Load** `new Document(path)`로 문서를 로드합니다.  
- **Locate** `doc.GetChild(NodeType.Shape, index, true)`를 사용해 도형을 찾습니다.  
- **Enable** 그림자를 활성화: `shape.ShadowFormat.Visible = true;`.  
- **Set color**를 `System.Drawing.Color`로 지정합니다.  
- **Adjust transparency** (`0.0–1.0`)로 투명도를 조절합니다.  
- **OffsetX / OffsetY**로 그림자를 수평/수직으로 이동합니다(포인트).  
- **BlurRadius**는 가장자리를 부드럽게 합니다—값이 클수록 그림자가 더 흐려집니다.  
- **Save** 파일을 저장하고 Word에서 열어 결과를 확인합니다.

## 다음에 시도해 볼 것?

- **Dynamic colors** – 테마나 사용자 입력에서 그림자 색을 가져옵니다.  
- **Conditional shadows** – 도형의 너비가 임계값을 초과할 때만 그림자를 적용합니다.  
- **Batch processing** – 문서의 모든 도형을 순회하며 **add shape shadow**를 자동으로 적용합니다.  

If you’ve followed along, you now know **how to set shadow**, how to **adjust shape transparency**, and how to **add rectangle shadow** for that professional polish. Feel free to experiment, break things, and then fix them—coding is the best teacher.

---

*코딩을 즐기세요! 이 튜토리얼이 도움이 되었다면 댓글을 남기거나 여러분만의 그림자 팁을 공유해 주세요. 서로 배우면 할수록 우리 Word 문서는 더욱 아름다워집니다.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}