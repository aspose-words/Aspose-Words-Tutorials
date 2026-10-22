---
category: general
date: 2026-09-30
description: Aspose.Words를 사용하여 C#에서 빈 문서를 만들고 사각형 도형, 타원 및 여러 도형을 그룹화합니다. 도형 삽입 방법과
  그룹 생성 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: ko
lastmod: 2026-09-30
og_description: C#에서 빈 문서를 만들고 Aspose.Words를 사용하여 도형을 삽입하고 여러 도형을 그룹화하는 방법을 배워보세요.
  단계별 튜토리얼을 따라하세요.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: C#에서 빈 문서를 만들고 도형을 그룹화하기 – Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: C#에서 Aspose.Words를 사용하여 빈 문서를 만들고 도형을 추가하는 방법
url: /ko/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 C#에서 빈 문서를 만들고 도형을 추가하는 방법

빈 **문서**를 **생성**하고 그래픽을 채워야 할 때, 이 가이드는 정확한 절차를 보여줍니다. **사각형 도형 삽입**, 다른 그리기 객체 추가, 그리고 **여러 도형을 그룹화**하여 하나의 단위처럼 동작하도록 하는 방법을 확인할 수 있습니다.

도형 작업은 계약서, 증명서, 맞춤형 보고서를 생성할 때 흔히 요구되는 기능입니다. 이 튜토리얼에서는 Aspose.Words API for .NET을 사용해 문서 초기화부터 최종 파일 저장까지 전체 워크플로우를 배웁니다.

## 사전 요구 사항

시작하기 전에 다음이 설치되어 있는지 확인하세요.

* .NET 6.0 (또는 이후 버전) SDK  
* 유효한 Aspose.Words for .NET 라이선스 (무료 체험판도 이 예제에 사용 가능)  
* Visual Studio 2022 또는 Visual Studio Code와 같은 IDE  

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## 빈 문서를 만들고 도형을 다루는 방법

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내 Word 파일을 나타내며, 콘텐츠 삽입을 위한 주요 도구인 `DocumentBuilder`에 접근할 수 있게 해줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**왜 중요한가:** 빈 문서는 깨끗한 캔버스를 제공합니다. `DocumentBuilder`는 현재 삽입 위치를 유지하므로, 추가하는 모든 도형이 자동으로 적절한 페이지에 배치됩니다.

## 사각형 도형 및 기타 도형 삽입

다음으로 사각형과 타원을 추가합니다. 두 호출 모두 동일한 `InsertShape` 메서드를 사용하며, 이는 Aspose.Words에서 **도형 삽입** 방법으로 권장됩니다.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*`InsertShape` 메서드는 현재 커서 위치에 도형을 자동으로 배치합니다.* 정확한 위치가 필요하면 삽입 후 `Shape.Left`와 `Shape.Top`을 조정하면 됩니다.

## 여러 도형을 하나의 객체로 그룹화

이제 사각형과 타원을 하나의 논리적 엔터티로 결합합니다. 그룹화는 여러 도형을 함께 이동하거나 크기 조정하고 싶을 때 유용합니다.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**작동 방식:** `InsertGroupShape`는 다른 `Shape`와 동일하게 동작하는 컨테이너를 생성합니다. `AppendChild`를 호출하면 기존 도형을 컨테이너 안으로 이동시키며, 상대 좌표가 자동으로 업데이트됩니다.

### 실용적인 팁

두 개 이상의 도형을 **프로그래밍 방식으로 그룹화**해야 할 경우, 추가 `Shape` 인스턴스마다 `AppendChild`를 반복하면 됩니다. 그룹에는 그림, 텍스트 상자, 혹은 다른 그룹까지 포함한任意의 수의 그리기 객체를 넣을 수 있습니다.

## 전체 예제 – 도형 삽입 및 문서 저장 방법

아래는 지금까지 설명한 모든 단계를 보여주는 완전한 실행 가능한 프로그램입니다. 코드를 실행하면 사각형, 타원, 그리고 그룹화된 도형을 포함한 `ShapesDemo.docx` 파일이 생성됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**예상 출력:** Microsoft Word에서 `ShapesDemo.docx`를 열면 파란 사각형, 초록 타원, 그리고 회색 테두리(그룹을 나타냄)가 한 페이지에 표시됩니다. 그룹을 이동하면 두 도형이 함께 움직이며 **여러 도형을 그룹화** 작업이 성공했음을 확인할 수 있습니다.

## 일반적인 질문 및 엣지 케이스 처리

| Question | Answer |
|----------|--------|
| *특정 페이지에 도형을 배치하려면 어떻게 해야 하나요?* | 도형을 삽입하기 전에 `builder.MoveToDocumentEnd();`를 호출하거나, 특정 섹션을 목표로 하려면 `builder.MoveToSection(sectionIndex);`를 사용합니다. |
| *그룹화된 도형 안에 텍스트를 추가할 수 있나요?* | 가능합니다. `ShapeType.TextBox` 타입의 `Shape`를 생성하고 텍스트를 설정한 뒤, `AppendChild`를 통해 `GroupShape`에 추가합니다. |
| *도형 크기 단위는 포인트인가요, 픽셀인가요?* | Aspose.Words는 **포인트**(1 pt = 1/72 인치)를 사용합니다. 이는 프린터와 디스플레이 간에 일관된 크기를 보장합니다. |
| *그룹의 회전 각도를 어떻게 변경하나요?* | `groupShape.RotationAngle = 45;`와 같이 설정하면 됩니다(단위:도). 모든 자식 도형이 그룹의 원점을 기준으로 회전합니다. |

## 결론

이제 Aspose.Words for .NET을 사용해 **빈 문서 생성**, **사각형 도형 삽입**, **타원과 같은 도형 삽입**, 그리고 **여러 도형을 하나의 객체로 그룹화**하는 방법을 알게 되었습니다. 전체 코드 예제는 권장 접근 방식을 보여주며, 위 팁을 통해 텍스트 상자 추가나 그룹 회전과 같은 복잡한 시나리오에도 적용할 수 있습니다.

더 탐구하고 싶나요? 그룹에 그림 도형을 추가해 보거나, 다양한 채우기 색상을 실험해 보세요. 혹은 각 페이지마다 자체 그룹화된 다이어그램을 포함하는 다중 페이지 보고서를 생성해 보세요. 동일한 원칙을 적용하면 어떤 문서 자동화 프로젝트에도 이 패턴을 확장할 수 있습니다.


## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}