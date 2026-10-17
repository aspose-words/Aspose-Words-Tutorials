---
category: general
date: 2026-04-10
description: C#에서 도형에 그림자를 설정하는 방법 – Aspose.Words를 사용하여 드롭 섀도우 적용, 투명도 변경, 블러 조정 및
  도형 그림자 추가 방법을 배웁니다.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: ko
og_description: C#에서 도형에 그림자를 설정하는 방법 – 이 튜토리얼은 드롭 섀도우 적용, 투명도 변경, 블러 조정, 그리고 명확한
  코드 예제로 도형 그림자를 추가하는 방법을 보여줍니다.
og_title: C#에서 도형에 그림자 설정하는 방법 – 완전 가이드
tags:
- Aspose.Words
- C#
- Document Automation
title: C#에서 도형에 그림자를 설정하는 방법 – 단계별 가이드
url: /ko/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 도형에 그림자 설정하기 – 완전 가이드

Ever wondered **그림자 설정** on a shape when you’re programmatically building a Word document? You’re not alone. Many developers hit a wall when they need a subtle drop shadow for a textbox, a logo, or a call‑out box, and the API docs feel a bit thin.  

In this tutorial we’ll walk through the entire process: from loading a `.docx`, grabbing the first `Shape`, to applying a drop shadow, tweaking its transparency, adjusting the blur radius, and finally positioning it just right. By the end you’ll have a reusable snippet that works with Aspose.Words .NET 2023 or later, and you’ll understand *why* each property matters.

## 필요 사항

- **Aspose.Words for .NET** (NuGet package `Aspose.Words`) – `Document`, `Shape`, and `ShadowFormat` 클래스를 제공하는 라이브러리입니다.  
- **.NET 6+** (or .NET Framework 4.7.2) – any recent runtime will do.  
- A simple Word file (`input.docx`) that already contains at least one shape, such as a textbox.  
- Visual Studio, VS Code, or your favorite IDE.

그게 전부입니다. No extra third‑party tools, no COM interop, just plain C#.

![그림자 설정 예시](image-placeholder.png){:alt="Word 문서에서 도형에 그림자 설정"}

## 그림자 설정 – 개요

The core idea behind **그림자 설정** is to manipulate the `ShadowFormat` object that lives on a `Shape`. Think of `ShadowFormat` as a miniature “style sheet” for the shadow itself: it tells the renderer whether the shadow is visible, what colour it should be, how transparent it is, how blurry, and where it sits relative to the shape.  

Below is the *complete* runnable program. Feel free to copy‑paste it into a console app, hit **F5**, and watch the shadow appear in the saved `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### 왜 이러한 설정이 중요한가

- **Visible** – 이 플래그를 켜지 않으면 다른 모든 속성이 무시됩니다.  
- **Color** – 어두운 회색은 일반 UI 드롭 섀도우를 모방합니다; 원하는 `Color`로 교체할 수 있습니다.  
- **Transparency** – 0.3은 *부드러운* 느낌을 주면서도 도형을 읽기 쉽게 유지합니다.  
- **Size** – 블러를 제어합니다; 값 6이면 보통 전문적인 느낌에 충분합니다.  
- **Distance & Angle** – 두 속성이 함께 *오프셋*을 정의합니다; 45°에서 2 pts는 은은한 대각선 그림자를 만듭니다.

이것이 **그림자 설정**의 핵심입니다. 이제 각 요소를 분리해서 **드롭 섀도우 적용**, **투명도 변경**, **블러 조정**, 그리고 **도형 그림자 추가**를 개별적으로 수행하는 방법을 살펴보겠습니다.

---

## 도형에 드롭 섀도우 적용

When people ask “how do I **apply drop shadow** in C#?”, they often only need the visibility toggle and a colour. The following snippet isolates those two lines:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** 오래된 Word 버전(2003‑2007)을 대상으로 할 경우 표준 색상을 사용하세요. 일부 특이한 ARGB 값은 레거시 렌더러에서 무시될 수 있습니다.

---

## 그림자 투명도 변경 방법

Transparency is expressed as a **float between 0 and 1**. A value of **0** means a completely opaque shadow; **1** makes it invisible. Most designers settle around **0.2‑0.4** for a natural look.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### 엣지 케이스

- **Negative values** – Aspose.Words가 0으로 제한하지만, 입력을 검증하는 것이 좋습니다.  
- **Values > 1** – 1로 제한되어 그림자가 사실상 숨겨집니다.  

If you need to let users pick a percentage, convert it first:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## 그림자 블러(크기) 조정 방법

The **Size** property controls the blur radius. Larger numbers produce a softer, more diffused shadow. It’s measured in points (pt), not pixels.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### 작은 블러와 큰 블러를 언제 사용할까

- **Small blur (2‑4 pt)** – 선명한 가장자리를 원하는 UI 스타일 콜아웃에 적합합니다.  
- **Large blur (8‑12 pt)** – 인쇄 보고서나 도형이 배경에서 멀리 떨어져 있을 때 잘 어울립니다.

## 도형 그림자 추가 – 위치와 방향

The final piece of **add shape shadow** is the offset. Two properties work together:

| 속성 | 의미 |
|----------|---------|
| **Distance** | 그림자가 도형으로부터 떨어진 거리(포인트 단위) |
| **Angle**    | 오프셋 방향(0° = 오른쪽, 90° = 아래, 180° = 왼쪽, 270° = 위) |

Example that creates a subtle bottom‑right shadow:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

You can experiment with angles to simulate light coming from different sources. A common trick is to let the user pick a “light source” from a dropdown and map it to an angle value.

## 전체 작업 예제 (모든 단계 결합)

Below is the same program as earlier, but with **extra comments** that make the logic crystal‑clear. Copy this into `Program.cs` and run it; the output file will contain a textbox with a perfectly tuned shadow.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**예상 결과:** Open `output.docx`. The first textbox will display a dark gray, 30 % transparent shadow that is slightly blurred (size = 6) and offset 2 pt at a 45° angle. The effect is subtle yet noticeable—exactly what most UI designers aim for.

## 자주 묻는 질문 및 주의사항

- **“이미지도 적용할 수 있나요?”**  
  네. 텍스트 상자, 그림, 자동 도형 등 모든 `Shape`은 `ShadowFormat`을 노출합니다. 도형 검색 로직을 해당 인덱스나 이름으로 교체하면 됩니다.

- **“문서에 도형이 여러 개 있으면 어떻게 하나요?”**  
  `doc.GetChildNodes(NodeType.Shape, true)`를 순회하면서 각 도형에 동일한 설정을 적용합니다. `shape.Name`이나 `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}