---
category: general
date: 2025-12-08
description: Aspose.Words를 사용하여 도형에 빠르게 그림자를 추가하세요. Aspose를 이용해 Word 문서를 만드는 방법, 도형에
  그림자를 추가하는 방법, 그리고 C#에서 그림자 투명도를 적용하는 방법을 배워보세요.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: ko
og_description: Aspose.Words를 사용하여 Word 파일의 도형에 그림자를 추가합니다. 이 단계별 가이드는 문서를 만들고, 도형을
  추가하고, 그림자 투명도를 적용하는 방법을 보여줍니다.
og_title: 도형에 그림자 추가 – Aspose.Words C# 튜토리얼
tags:
- Aspose.Words
- C#
- Word Automation
title: Word 문서에서 도형에 그림자 추가 – 완전한 Aspose.Words 가이드
url: /korean/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# 도형에 그림자 추가 – 완전한 Aspose.Words 가이드

Word 파일에 **도형에 그림자 추가**가 필요했지만 어떤 API 호출을 사용해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 처음으로 사각형이나 기타 그리기 요소에 적절한 드롭‑섀도우를 적용하려 할 때, 특히 Aspose.Words for .NET을 사용할 때 벽에 부딪히곤 합니다.

이 튜토리얼에서는 **Aspose를 사용한 Word 문서 만들기**부터 그림자 구성, 흐림 정도, 거리, 각도 조정 및 **그림자 투명도 적용**까지 알아야 할 모든 것을 단계별로 안내합니다. 마지막에는 `.docx` 파일에 부드러운 그림자가 적용된 사각형을 생성하는 실행 가능한 C# 프로그램을 얻을 수 있습니다—Word에서 수동으로 조정할 필요가 없습니다.

---

## 배울 내용

- Visual Studio에서 Aspose.Words 프로젝트 설정 방법.  
- **Aspose를 사용한 Word 문서 만들기** 및 도형 삽입 정확한 단계.  
- **도형에 그림자 추가** 방법과 흐림, 거리, 각도, 투명도에 대한 완전한 제어.  
- 일반적인 문제점(예: 라이선스 누락, 단위 오류) 해결 팁.  
- 오늘 바로 실행할 수 있는 완전한 복사‑붙여넣기 코드 샘플.

> **전제 조건:** .NET 6+ (또는 .NET Framework 4.7.2+), 유효한 Aspose.Words 라이선스(또는 무료 체험판), 그리고 C#에 대한 기본적인 이해.

---

## Step 1 – 프로젝트 설정 및 Aspose.Words 추가

먼저 Visual Studio를 열고 **새 콘솔 앱(.NET Core)**을 만든 뒤 Aspose.Words NuGet 패키지를 추가합니다:

```bash
dotnet add package Aspose.Words
```

> **프로 팁:** 라이선스 파일(`Aspose.Words.lic`)이 있다면 프로젝트 루트에 복사하고 시작 시 로드하세요. 이렇게 하면 무료 평가판 모드에서 나타나는 워터마크를 방지할 수 있습니다.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Step 2 – 새 빈 문서 만들기

이제 실제로 **Aspose를 사용한 Word 문서 만들기**를 수행합니다. 이 객체가 도형을 그릴 캔버스 역할을 합니다.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` 클래스는 문단, 섹션 및 물론 그리기 객체 등 모든 작업의 진입점입니다.

---

## Step 3 – 사각형 도형 삽입

문서가 준비되었으니 도형을 추가합니다. 여기서는 간단한 사각형을 선택하지만, 동일한 논리로 원, 선, 사용자 정의 다각형에도 적용할 수 있습니다.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **왜 도형인가?** Aspose.Words에서 `Shape` 객체는 텍스트, 이미지 또는 단순히 장식 요소로 사용할 수 있습니다. 도형에 그림자를 추가하는 것이 사진 프레임을 조작하는 것보다 훨씬 쉽습니다.

---

## Step 4 – 그림자 구성 (Add Shadow to Shape)

이 부분이 튜토리얼의 핵심—**도형에 그림자 추가**와 외관 미세 조정 방법입니다. `ShadowFormat` 속성을 통해 완전한 제어가 가능합니다.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### 각 속성의 역할

| Property | Effect | Typical Values |
|----------|--------|----------------|
| **Visible** | 그림자를 켜거나 끕니다. | `true` / `false` |
| **Blur** | 그림자 가장자리를 부드럽게 합니다. | `0`(선명)부터 `10`(매우 부드러움)까지 |
| **Distance** | 그림자를 도형에서 떨어뜨립니다. | 일반적으로 `1`–`5` 포인트 |
| **Angle** | 오프셋 방향을 제어합니다. | `0`–`360`도 |
| **Transparency** | 그림자를 부분적으로 투명하게 합니다. | `0`(불투명)부터 `1`(투명)까지 |

> **예외 상황:** `Transparency`를 `1`로 설정하면 그림자가 완전히 사라집니다—프로그램matically 토글할 때 유용합니다.

---

## Step 5 – 도형을 문서에 추가

이제 도형을 문서 본문의 첫 번째 문단에 연결합니다. Aspose는 문단이 없을 경우 자동으로 생성합니다.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

문서에 이미 내용이 있다면 `InsertAfter` 또는 `InsertBefore`를 사용해 원하는 노드에 도형을 삽입할 수 있습니다.

---

## Step 6 – 문서 저장

마지막으로 파일을 디스크에 씁니다. 지원되는 형식(`.docx`, `.pdf`, `.odt` 등) 중 원하는 것을 선택할 수 있지만, 이번 튜토리얼에서는 기본 Word 형식으로 저장합니다.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

생성된 `ShadowedShape.docx`를 Microsoft Word에서 열면 45도 각도에 30 % 투명한 부드러운 그림자가 적용된 사각형을 확인할 수 있습니다—우리가 설정한 그대로입니다.

---

## 전체 작업 예제

아래는 **복사‑붙여넣기 바로 사용 가능한** 전체 프로그램입니다. `Program.cs`로 저장하고 `dotnet run`으로 실행하세요.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**예상 출력:** `ShadowedShape.docx`라는 파일이 생성되며, 45° 각도에 약간 투명한 드롭 섀도우가 적용된 사각형 하나가 포함됩니다.

---

## 변형 및 고급 팁

### 그림자 색상 변경

기본적으로 그림자는 도형의 채우기 색을 상속하지만, 사용자 지정 색을 설정할 수 있습니다:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### 서로 다른 그림자를 가진 다중 도형

여러 도형이 필요하면 생성 및 구성 단계를 반복하면 됩니다. 나중에 참조할 계획이라면 각 도형에 고유한 이름을 부여하세요.

### 그림자 보존된 PDF 내보내기

Aspose.Words는 PDF 저장 시 그림자 효과를 유지합니다:

```csharp
doc.Save("ShadowedShape.pdf");
```

### 흔히 발생하는 문제

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| 그림자가 보이지 않음 | `ShadowFormat.Visible`이 `false` 상태 | `true`로 설정 |
| 그림자가 너무 날카로움 | `Blur`가 `0`으로 설정 | `Blur`를 3–6으로 증가 |
| PDF에서 그림자 사라짐 | 오래된 Aspose.Words 버전(< 22.9) 사용 | 최신 라이브러리로 업그레이드 |

---

## 결론

우리는 Aspose.Words를 사용해 **도형에 그림자 추가** 방법을 다루었습니다. 문서 초기화부터 흐림, 거리, 각도, **그림자 투명도 적용**까지 전체 과정을 살펴보았으며, 완전한 예제는 어떤 도형이나 레이아웃에도 적용 가능한 생산 준비된 접근 방식을 보여줍니다.

**Aspose를 사용한 Word 문서 만들기**에 대한 더 복잡한 시나리오(예: 그림자가 있는 표, 동적 데이터 기반 도형 등)가 궁금하시면 아래 댓글을 남기거나 Aspose.Words 이미지 처리 및 문단 서식 관련 튜토리얼을 확인하세요.

코딩을 즐기시고, Word 문서에 한층 더 멋진 시각적 효과를 부여해 보세요! 

--- 

![도형에 그림자 추가 예시](shadowed_shape.png "도형에 그림자 추가 예시")

{{< layout-end >}}

{{< layout-end >}}