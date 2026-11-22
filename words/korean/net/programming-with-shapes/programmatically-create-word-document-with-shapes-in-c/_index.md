---
category: general
date: 2026-11-22
description: C#를 사용해 프로그래밍 방식으로 Word 문서를 생성하고 사각형 도형을 삽입하며, 여러 도형을 추가하고, Aspose.Words를
  이용해 도형을 Word에 기록합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: ko
lastmod: 2026-11-22
og_description: C#에서 사각형 모양을 삽입하고 여러 모양을 추가하여 프로그래밍 방식으로 Word 문서를 생성하고, Aspose.Words를
  사용해 모양을 Word에 기록합니다.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: C#에서 프로그래밍으로 도형이 포함된 Word 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: C#를 사용하여 프로그래밍 방식으로 도형이 포함된 Word 문서 만들기
url: /ko/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 도형이 포함된 Word 문서를 프로그래밍 방식으로 만들기

Word 문서에 사용자 정의 그래픽을 **프로그래밍 방식으로 생성**해야 하는 경우, 이 가이드는 Aspose.Words for .NET을 사용하여 수행하는 방법을 보여줍니다. 사각형 도형을 삽입하고, 추가 도형을 추가하고, 이를 그룹화한 뒤, 최종적으로 도형을 Word에 기록하는 전체 과정을 몇 줄의 C# 코드로 배울 수 있습니다.

그래픽이 포함된 Word 파일을 만드는 데 더 이상 수동 편집이나 매크로 스크립트가 필요하지 않습니다. 이 튜토리얼을 마치면 사각형과 타원이 함께 그룹화된 `.docx` 파일을 생성하는 재사용 가능한 메서드를 얻게 되며, 이를 다운스트림 처리나 보고에 활용할 수 있습니다.

## 필요 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 동작)
- Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`)
- Visual Studio 2022와 같은 IDE (C#을 컴파일할 수 있는 편집기면 충분)

> **Pro tip:** 코딩을 시작하기 전에 CLI 명령 `dotnet add package Aspose.Words` 로 패키지를 설치하세요.

## 프로그래밍 방식으로 Word 문서 만들기 – 개요

전체 흐름은 세 가지 논리적 단계로 구성됩니다:

1. **새 `Document`와 `DocumentBuilder` 초기화**.  
2. **여러 도형 삽입** (사각형과 타원) 후 `GroupShape`에 배치.  
3. **`Document`를 `.docx` 파일로 저장**하여 도형을 Word에 기록.

각 단계는 아래에 별도 섹션으로 정리되어 있으니, 코드를 그대로 복사해 프로젝트에 붙여넣기만 하면 됩니다.

![프로그램matically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="그룹화된 도형이 포함된 Word 문서를 프로그래밍 방식으로 만들기"}

## 단계 1: 문서와 빌더 초기화

`Document` 클래스는 전체 Word 파일을 나타내고, `DocumentBuilder`는 콘텐츠를 추가하기 위한 유창한 API를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*이 단계가 중요한 이유:* 먼저 `Document`를 생성하면 깨끗한 캔버스를 확보할 수 있습니다. `DocumentBuilder`는 현재 삽입 위치를 추적하므로, 이후에 도형을 단락 계층에 연결할 때 필수적입니다.

## 단계 2: 그룹 도형 컨테이너 삽입

`GroupShape`를 사용하면 여러 개별 도형을 하나의 단위로 취급할 수 있습니다. 이는 도형을 함께 이동하거나 크기를 조정하고 싶을 때 유용합니다.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*설명:* `InsertGroupShape`는 빈 컨테이너를 삽입하고 자동으로 현재 도형으로 설정합니다. 이후 삽입되는 모든 도형은 이 컨테이너에 추가되며, 그룹을 닫을 때까지 계속됩니다.

## 사각형 도형 삽입

이제 첫 번째 그래픽인 사각형을 추가합니다. 이는 **사각형 도형 삽입** 요구사항을 충족합니다.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

사각형은 그룹의 서식 컨텍스트를 상속받아 `GroupShape` 내부에 표시됩니다. 필요에 따라 선 색, 채우기, 텍스트 등을 나중에 설정할 수 있습니다.

## 여러 도형 삽입

**여러 도형 삽입** 기능을 보여주기 위해 사각형 바로 뒤에 타원을 추가합니다. 그룹을 닫기 전까지 원하는 만큼 도형(예: 삼각형, 별)을 계속 추가할 수 있습니다.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

이 시점에서 그룹에는 두 개의 서로 다른 도형, 즉 사각형과 타원이 포함됩니다. 동일한 부모를 공유하므로 하나의 단위로 이동할 수 있습니다.

## 단계 3: 그룹 도형을 단락 계층에 연결

Word 문서는 단락 트리 구조에 콘텐츠를 저장합니다. 최종 파일에 그룹을 표시하려면 현재 단락에 연결해야 합니다.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*이 단계가 필요한 이유:* 그룹을 단락에 추가하지 않으면 도형은 메모리 상에만 존재하고, 문서를 저장할 때 제외됩니다.

## 단계 4: 문서 저장 – 도형을 Word에 기록

마지막으로 메모리 상의 `Document`를 디스크에 영구 저장합니다. 이는 **도형을 Word에 기록** 목표를 달성합니다.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`GroupShape.docx`를 Microsoft Word에서 열면 코드가 삽입한 대로 사각형과 타원이 함께 그룹화된 것을 확인할 수 있습니다.

### 예상 결과

- 프로젝트 출력 폴더에 **GroupShape.docx** 라는 파일이 생성됩니다.
- Word 파일 내부: 하나의 단락에 그룹화된 사각형(100 pt × 50 pt)과 타원(80 pt × 40 pt)이 포함됩니다. 어느 하나의 도형을 선택하면 전체 그룹이 선택됩니다.

## 일반적인 엣지 케이스 처리

| 상황 | 권장 사항 |
|-----------|----------------|
| **다른 DPI 또는 페이지 크기** | 도형을 삽입하기 전에 `builder.PageSetup.PaperSize`를 명시적으로 설정하여 예상치 못한 스케일링을 방지합니다. |
| **도형을 정확히 위치시켜야 할 경우** | `builder.MoveTo` 로 삽입 지점을 이동한 뒤, `groupShape.Left` 및 `groupShape.Top` 속성을 포인트 단위로 설정합니다. |

## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}