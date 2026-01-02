---
category: general
date: 2026-01-02
description: Aspose.Words를 사용하여 사각형 모양이 포함된 Word 문서를 만들고, 모양의 채우기 색상을 설정한 뒤 docx 파일로
  저장합니다. 몇 분 안에 그림자 효과가 있는 사각형을 만드는 방법을 배워보세요.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: ko
og_description: 사용자 지정 사각형이 포함된 Word 문서를 만들고, 채우기 색상을 설정하고, 그림자를 추가한 뒤 DOCX로 저장합니다.
  전체 코드와 설명.
og_title: 직사각형 도형이 포함된 워드 문서 만들기 – 단계별 가이드
tags:
- Aspose.Words
- C#
- Document Generation
title: 워드 문서에 사각형 모양과 그림자 만들기 – 완전 가이드
url: /ko/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 사각형 모양과 그림자가 있는 Word 문서 만들기 – 완전 가이드

아무리 멋진 사각형이 포함된 **Word 문서**를 만들고 싶었나요? 로고 자리 표시자, 색상 배너, 혹은 보고서의 시각적 힌트가 필요할 수도 있습니다. 이 튜토리얼에서는 **사각형 모양을 추가**하고, 채우기 색을 지정한 뒤, 은은한 그림자를 적용하고, 마지막으로 **docx 파일을 저장**하는 과정을 Aspose.Words for .NET을 사용해 보여드립니다.

실행 가능한 C# 코드 스니펫, 각 라인에 대한 명확한 설명, 그리고 프로젝트에 재사용할 수 있는 팁을 얻을 수 있습니다. 불필요한 설명은 없으며, 바로 복사‑붙여넣기 가능한 실용적인 솔루션만 제공합니다.

## 필요 사항

- .NET 6 이상 (코드는 .NET Framework에서도 동작합니다)  
- Visual Studio 2022 (또는 선호하는 다른 편집기)  
- **Aspose.Words** NuGet 패키지 (`Install-Package Aspose.Words`)  

이미 준비되었다면, 바로 시작해 보겠습니다.

## Step 1 – 새 문서 초기화 (Word 문서 만들기)

먼저 메모리 상에 **Word 문서**를 **생성**합니다. 빈 캔버스를 열고 그 위에 사각형을 그릴 준비를 하는 셈입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **왜 중요한가:** `Document`는 전체 DOCX 파일을 나타내고, `DocumentBuilder`는 텍스트, 표, 이미지, 도형 등을 직접 노드 트리를 다루지 않고도 삽입할 수 있게 해 주는 편리한 도우미입니다.

## Step 2 – 사각형 모양 삽입 (Add rectangle shape)

이제 문서에 **사각형 모양**을 **추가**합니다. `InsertShape` 메서드는 도형 종류와 크기를 포인트 단위(1포인트 = 1/72인치)로 받습니다.

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **프로 팁:** 다른 기하학 도형(타원, 삼각형 등)이 필요하면 `ShapeType.Rectangle`을 원하는 enum 값으로 바꾸기만 하면 됩니다.

## Step 3 – 그림자 설정 (Set shape fill color & shadow)

그림자는 평면 도형에 입체감을 부여합니다. 여기서는 그림자를 활성화하고 외관을 미세 조정합니다.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **왜 이런 값인가:** 적당한 블러 반경과 5포인트 거리로 그림자가 도형을 압도하지 않게 하며, 45°는 왼쪽 위에서 빛이 오는 일반적인 UI 관례를 모방합니다.

## Step 4 – 문서 저장 (Save docx file)

마지막으로 **docx 파일**을 디스크에 **저장**합니다. 환경에 맞게 경로를 조정하세요.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

`ShadowDemo.docx`를 Word에서 열면 아래 스크린샷과 같이 연한 파란색 사각형에 부드러운 회색 그림자가 표시됩니다.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*이미지 대체 텍스트:* **Create Word Document** – 그림자가 있는 사각형 모양을 보여줍니다.

## 전체 실행 가능한 예제 (How to create rectangle and save)

모든 코드를 합치면 콘솔 앱에 복사해 넣을 수 있는 완전한 프로그램이 됩니다:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### 기대 결과

- 대상 폴더에 **ShadowDemo.docx** 파일이 생성됩니다.  
- Microsoft Word에서 열면 “Shadow Demo” 텍스트 뒤에 연한 파란색 사각형이 표시됩니다.  
- 사각형은 45° 각도에서 부드러운 회색 그림자를 드리워 약간의 3‑D 느낌을 줍니다.

## 흔히 묻는 질문 및 예외 상황

### 다른 크기가 필요하면?

`InsertShape`의 `200, 100` 인자를 원하는 너비와 높이(포인트)로 바꾸면 됩니다. 정사각형을 원한다면 두 값을 동일하게 지정하세요.

### 그림자를 더 강조하고 싶다면?

`BlurRadius`를 늘려 부드러운 가장자리를 만들고, `Distance`를 늘려 오프셋을 크게 하거나, `Transparency`를 낮게(`0.1` 등) 설정해 그림자를 어둡게 할 수 있습니다.

### 사각형에 테두리를 추가하려면?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### 오래된 Aspose.Words 버전에서도 동작하나요?

예. `ShadowFormat` 클래스는 2020년 초반 릴리즈부터 존재합니다. 매우 오래된 버전을 사용 중이라면 모든 속성을 사용하려면 최신 버전으로 업그레이드해야 할 수 있습니다.

## 팁 및 주의사항

- **프로 팁:** 큰 문서는 사용이 끝난 뒤 `doc.Dispose()` 로 반드시 해제하세요. 특히 웹 애플리케이션에서는 네이티브 리소스 해제가 중요합니다.  
- **주의:** 상대 경로를 사용할 경우 권한 문제가 발생해 `UnauthorizedAccessException` 이 발생할 수 있습니다. 절대 경로를 사용하거나 앱 풀에 쓰기 권한을 부여하세요.  
- **기억:** `FillColor` 속성은 `System.Drawing.Color` 를 그대로 받습니다. `Color.FromArgb(255, 173, 216, 230)` 와 같이 원하는 파스텔 색상을 자유롭게 지정하세요.

## 다음 단계

이제 **Word 문서 만들기**, **사각형 모양 추가**, **채우기 색 설정**, **docx 파일 저장** 방법을 알았으니, 다음을 시도해 보세요:

- `RelativeHorizontalPosition` 및 `RelativeVerticalPosition` 으로 여러 도형을 배치하기.  
- `Shape.TextBox` 를 이용해 사각형에 캡션 텍스트 삽입하기.  
- 동일 문서를 PDF 로 내보내기 (`doc.Save("output.pdf")`) 로 배포하기.

보다 고급 그래픽에 관심이 있다면 Aspose.Words 가 지원하는 **WordArt**, **차트**, **인라인 이미지** 를 살펴보세요. 모두 같은 패턴을 따릅니다: 노드 생성 → 속성 설정 → 저장.

---

### TL;DR

- `Document`와 `DocumentBuilder` 로 **Word 문서 만들기**.  
- `InsertShape(ShapeType.Rectangle, …)` 로 **사각형 모양 추가**.  
- 원하는 배경색을 `FillColor` 로 지정.  
- `ShadowFormat` 을 활성화하고 속성을 조정해 세련된 그림자 적용.  
- `document.Save("yourPath.docx")` 로 **docx 파일 저장**.

즐거운 코딩 되세요, 그리고 Word 파일을 좀 더 스타일리시하게 만들어 보세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}