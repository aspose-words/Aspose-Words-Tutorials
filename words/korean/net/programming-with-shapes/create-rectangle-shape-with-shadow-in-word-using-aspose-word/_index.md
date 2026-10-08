---
category: general
date: 2026-03-06
description: Aspose.Words를 사용하여 Word에서 사각형 도형을 만들고 도형 그림자를 추가합니다. Word에 사각형을 삽입하는
  방법과 C#에서 도형에 그림자를 추가하는 방법을 배워보세요.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: ko
og_description: Aspose.Words를 사용하여 Word에서 사각형 도형을 만들고 도형 그림자를 추가합니다. Word에 사각형을 삽입하고
  도형에 그림자를 추가하는 방법에 대한 단계별 가이드.
og_title: Aspose.Words를 사용하여 Word에서 그림자 있는 사각형 도형 만들기
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.Words를 사용하여 Word에서 그림자 효과가 있는 사각형 도형 만들기
url: /ko/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word에서 그림자와 함께 사각형 도형 만들기

자동화된 문서에 시각적 멋을 더하려고 할 때 **사각형 도형을 만들고** 어떻게 하면 깔끔하게 보일지 몰라 고민한 적 있나요? 대부분의 개발자가 처음에 겪는 문제입니다. 좋은 소식은? Aspose.Words for .NET을 사용하면 **사각형 도형을 만들고** **도형에 그림자를 추가**하는 작업을 몇 줄의 C# 코드만으로 할 수 있다는 것입니다.

이 튜토리얼에서는 **Word에 사각형을 삽입하는 방법**을 단계별로 살펴보고, **도형에 그림자를 추가하는 방법**을 보여줍니다. 최종적으로 `Shadow.docx` 파일을 저장하면 회색 톤의 사각형에 부드러운 그림자가 적용된 모습을 Word에서 확인할 수 있습니다. 별도의 이미지 파일이나 수동 조정 없이 코드만으로 가능합니다.

## 배울 내용

- Aspose.Words를 사용해 **사각형 도형을 만들기** 위한 정확한 C# 구문  
- `Shadow` 객체를 이용해 그림자를 활성화하고 설정하는 방법  
- 각 속성이 의미하는 바(`Transparency`, `Blur`, `Angle` 등)  
- 흔히 발생하는 문제점(단위, 버전 호환성)과 빠른 해결책  
- 오늘 바로 실행할 수 있는 완전한 복사‑붙여넣기 가능한 프로그램

### 사전 요구 사항

- .NET 6+ (또는 .NET Framework 4.7+)  
- Aspose.Words for .NET 23.10 이상(NuGet 패키지 이름은 `Aspose.Words`)  
- C#와 Visual Studio(또는 선호하는 IDE)에 대한 기본 이해  

위 조건을 이미 갖추셨다면 바로 시작해 보세요.

---

## 1단계: 프로젝트 설정 및 네임스페이스 가져오기

먼저 새 콘솔 앱을 만들고(Aspose.Words NuGet 패키지를 추가합니다):

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

이제 `Program.cs`에 필요한 네임스페이스를 추가합니다:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **프로 팁:** .NET 6+을 대상으로 하는 경우 전역 `using` 지시문을 활성화하면 파일마다 이 줄들을 반복할 필요가 없습니다.

---

## 2단계: 빈 Word 문서에 **사각형 도형 만들기**

새 `Document` 객체와 이를 조작할 `DocumentBuilder`를 준비합니다. 도형을 삽입하는 마법은 `InsertShape` 메서드에서 이루어집니다.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

왜 200 × 100 포인트일까요? Word에서 1포인트는 1/72인치이므로, 이 사각형은 대략 2.8 × 1.4 인치 정도가 됩니다—눈에 띄면서도 과하지 않은 크기죠. 레이아웃에 맞게 숫자를 조정할 수 있지만, **포인트** 단위임을 기억하세요, 픽셀이 아니라.

---

## 3단계: **도형 그림자 추가** – 외관 설정

이제 사각형에 은은한 회색 그림자를 입혀 보겠습니다. `Shadow` 객체는 `Shape`에 포함되어 있으며 여러 유용한 속성을 제공합니다.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### 각 속성의 역할

| 속성 | 효과 | 일반적인 값 |
|----------|--------|----------------|
| **Enabled** | 그림자 켜기/끄기 | `true` 또는 `false` |
| **Color** | 그림자의 기본 색상 | 任意 `System.Drawing.Color` |
| **Transparency** | 불투명도(0 = 불투명, 1 = 투명) | 0.0 – 1.0 |
| **Blur** | 가장자리 부드러움 정도 | 0 – 10 (값이 클수록 부드러움) |
| **Distance** | 도형과 그림자 사이 간격 | 0 – 20 포인트 |
| **Angle** | 빛이 오는 방향 | 0 – 360도 |
| **Size** | 도형 대비 그림자 크기 비율 | 0 – 200 % |

> **왜 이런 설정을 할까요?**  
> 그림자를 미세 조정하면 기업 브랜드 가이드라인(예: 전문적인 느낌을 주는 20 % 투명도)과 일치시킬 수 있어 외부 이미지 편집 툴 없이도 원하는 디자인을 구현할 수 있습니다.

---

## 4단계: 문서 저장 및 결과 확인

마지막으로 파일을 디스크에 씁니다. 원하는 폴더 경로로 `YOUR_DIRECTORY`를 교체하면 됩니다.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

`Shadow.docx`를 Microsoft Word에서 열면 회색 사각형에 45° 각도로 부드러운 그림자가 살짝 떨어진 모습을 확인할 수 있습니다. 이 시각적 효과는 도형이 페이지에서 “떠 있는” 느낌을 주어, 깔끔한 보고서나 청구서에 딱 맞습니다.

---

## 전체 작업 예제

아래는 `Program.cs`에 그대로 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. 누락된 부분 없이 바로 컴파일하고 실행할 수 있습니다.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 예상 출력

- **파일:** 프로젝트 실행 폴더에 생성된 `Shadow.docx`  
- **시각적:** 페이지 중앙에 기본 흰색 채우기 사각형이 하나 있고, 오른쪽 아래로 4포인트 이동된 회색 그림자가 약간 흐려져 자연스럽게 보입니다.

---

## 자주 묻는 질문 및 예외 상황

### 1. 다른 단위(예: 센티미터)를 사용하려면?

Aspose.Words는 포인트 단위로 동작하지만, 센티미터를 포인트로 변환하는 간단한 공식이 있습니다:  
`points = centimeters * 28.3465`.

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. 오래된 Aspose.Words 버전에서도 동작하나요?

`Shadow` API는 버전 14.0부터 도입되었습니다. 이전 버전을 사용 중이라면 NuGet을 통해 업그레이드해야 합니다. 도형 생성 코드는 수년간 안정적으로 유지돼 큰 변화가 없습니다.

### 3. 다른 도형(예: 원)에 그림자를 추가할 수 있나요?

물론 가능합니다—모든 `Shape` 객체는 `Shadow` 속성을 가집니다. `ShapeType.Rectangle`을 `ShapeType.Ellipse` 혹은 `ShapeType.Cloud` 등으로 바꾸고 동일한 그림자 설정을 적용하면 됩니다.

### 4. 브랜드 색상(예: 파란색)으로 그림자를 만들고 싶다면?

`Color.Gray`를 원하는 `Color`로 교체하면 됩니다:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

`Transparency` 값을 조정해 색상이 과도하게 강조되지 않도록 하세요.

---

## 🎨 시각 요약

![Word에서 Aspose.Words로 사각형 도형에 그림자 만들기](image-placeholder.png "Word에서 Aspose.Words로 사각형 도형에 그림자 만들기")

*Alt text: Word에서 Aspose.Words로 사각형 도형에 그림자 만들기*

위 스크린샷(플레이스홀더)은 최종 문서를 보여줍니다—사각형과 부드러운 회색 그림자만 표시됩니다.

---

## 결론

이제 **Word 파일에 사각형 도형을 만들고**, **도형에 그림자를 추가**하며, Aspose.Words for .NET을 사용해 모든 시각적 요소를 세밀하게 조정하는 방법을 알게 되었습니다. 우리가 만든 짧은 프로그램은 전체 워크플로우를 포괄합니다—  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}