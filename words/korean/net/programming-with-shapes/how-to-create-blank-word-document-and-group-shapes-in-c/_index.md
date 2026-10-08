---
category: general
date: 2026-10-07
description: C#에서 빈 Word 문서를 만들고 사각형 도형을 추가하고 이미지 도형을 삽입하며 동적 보고서를 위해 여러 도형을 그룹화하는
  방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: ko
lastmod: 2026-10-07
og_description: Aspose.Words를 사용해 C#에서 빈 Word 문서를 만들고, 사각형 도형 추가, 이미지 도형 삽입, 여러 도형을
  그룹화하여 전문 문서를 만드는 방법을 배우세요.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: C#에서 빈 Word 문서를 만들고 도형을 그룹화하기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#에서 빈 Word 문서를 만들고 도형을 그룹화하는 방법
url: /ko/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 빈 Word 문서를 만들고 도형을 그룹화하는 방법

프로그램matically **빈 Word 문서를 만들** 필요가 있다면, 이 가이드는 정확히 어떻게 하는지 보여줍니다. **사각형 도형 추가**, **이미지 도형 삽입**, 그리고 **여러 도형을 그룹화**하여 나중에 **Word에 이미지 추가** 시 단일 객체처럼 동작하도록 하는 방법을 확인할 수 있습니다.

코드에서 Word 파일을 다루는 것은 위협적으로 느껴질 수 있지만, Aspose.Words가 과정을 간단하게 만들어 줍니다. 이 튜토리얼을 마치면 그룹화된 사각형과 로고가 포함된 깔끔하고 빈 Word 파일을 생성하는 재사용 가능한 C# 스니펫을 얻게 됩니다. 이 결과물을 청구서, 보고서 또는 자동화된 문서 워크플로에 삽입할 수 있습니다.

## 사전 요구 사항

시작하기 전에 다음을 확인하십시오:

* .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 작동합니다).  
* 유효한 Aspose.Words for .NET 라이선스 또는 무료 평가 키.  
* 코드에서 참조할 수 있는 폴더에 배치된 이미지 파일(`logo.png` 등).  
* Visual Studio 2022 또는 C# 호환 IDE.

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Aspose.Words로 빈 Word 문서 만들기

첫 번째 단계는 항상 **빈 Word 문서를 만들** 것입니다. 이 객체가 이후 모든 도형을 호스트합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`는 전체 `.docx` 파일을 나타냅니다. 이 시점에서 파일은 비어 있어 *빈 Word 문서를 만들* 요구 사항을 충족합니다.

## 여러 도형을 그룹화할 컨테이너 만들기

도형을 그룹화하면 함께 이동, 회전 또는 크기 조정이 가능합니다. Aspose.Words는 이를 위해 `GroupShape` 클래스를 제공합니다.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

`Bounds` 사각형은 페이지에서 그룹이 나타나는 위치를 결정합니다. 그룹을 첫 번째 단락에 배치하면 **빈 Word 문서를 만들** 즉시 시각적 컨테이너가 포함됩니다.

## 그룹 안에 사각형 도형 추가하기

일반적인 요구 사항은 배경이나 테두리로 **사각형 도형을 추가**하는 것입니다. 다음 코드는 사각형을 생성하고 앞서 정의한 그룹에 추가합니다.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

사각형이 `GroupShape` 내부에 존재하기 때문에 나중에 추가하는 다른 도형과 함께 이동합니다. 이것이 **여러 도형을 그룹화** 기능의 핵심입니다.

## 그룹 안에 이미지 도형 삽입하기

다음으로 **이미지 도형을 삽입**(로고)하고 사각형 옆에 배치합니다. 이는 **Word에 이미지 추가** 워크플로를 보여줍니다.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

`SetImage` 메서드는 파일을 읽어 Word 문서에 직접 삽입하므로 소스 파일이 이동되어도 이미지가 유지됩니다. 이렇게 하면 **이미지 도형 삽입** 단계가 완료되고 **Word에 이미지 추가** 요구 사항이 최종화됩니다.

## 문서 저장하기

마지막으로 파일을 디스크에 영구 저장합니다. 저장된 파일에는 빈 문서, 그룹화된 사각형, 삽입된 로고가 포함됩니다.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Microsoft Word에서 `GroupShape.docx`를 열면 회색 사각형과 로고가 나란히 배치된 단일 그룹이 표시됩니다. 그룹의 어느 부분을 선택해도 전체 컬렉션을 이동하거나 크기를 조정할 수 있어 도형이 실제로 **여러 도형을 그룹화**했음을 증명합니다.

## 완전한 실행 가능한 예제

아래는 복사·붙여넣기·실행할 수 있는 전체 프로그램입니다. `YOUR_DIRECTORY`를 머신에 존재하는 절대 경로나 상대 경로로 바꾸세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### 예상 출력

* `YOUR_DIRECTORY`에 위치한 `GroupShape.docx` 파일.  
* Word에서 파일을 열면 왼쪽에 회색 사각형, 오른쪽에 `logo.png`가 포함된 단일 시각적 그룹이 표시됩니다.  
* 시각적 그룹의 어느 부분을 선택해도 전체 컬렉션을 이동하거나 크기를 조정할 수 있어 도형이 올바르게 **여러 도형을 그룹화**했음을 확인할 수 있습니다.

## 일반적인 질문 및 엣지 케이스 처리

| Question | Answer |
|---|---|
| **같은 그룹에 두 개 이상의 도형을 추가할 수 있나요?** | 예. 추가 `Shape`마다 `group.AppendChild(yourShape)`를 호출하십시오. 그룹은 원하는 만큼의 그리기 객체를 포함할 수 있습니다. |
| **이미지 파일이 없으면 어떻게 되나요?** | `SetImage`는 `FileNotFoundException`을 발생시킵니다. 호출을 try‑catch 블록으로 감싸고 대체 옵션(예: 자리표시자 도형)을 제공하십시오. |
| **도형에 `WrapType`을 설정해야 하나요?** | 기본적으로 도형은 인라인입니다. 떠 있는 동작이 필요하면 그룹에 추가하기 전에 `picture.WrapType = WrapType.Inline;` 또는 다른 랩 모드를 설정하십시오. |
| **문서 크기가 그룹 경계에 어떻게 영향을 줍니까?** | `Bounds` 사각형은 포인트 단위로 정의됩니다(1 pt ≈ 1/72 인치). 다른 페이지 레이아웃(A4 vs. Letter 등)에 그룹을 배치할 경우 크기를 조정하십시오. |
| **같은 그룹을 다른 문서에서 재사용할 수 있나요?** | 예. `GroupShape cloned = (GroupShape)group.Clone(true);` 로 그룹을 복제한 뒤 다른 `Document`에 삽입하십시오. |

## Pro tips

* **`DocumentBuilder`를 재사용**하여 그룹 전후에 텍스트를 추가하십시오. 현재 커서 위치를 자동으로 인식합니다.  
* 사각형에 눈에 보이는 테두리가 필요하면 `Shape.StrokeColor`를 **설정**하십시오.  
* 로고가 픽셀화되지 않도록 고해상도 PNG를 **사용**하십시오.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접하게 관련된 주제를 다룹니다. 각 리소스에는 단계별 설명과 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [C#으로 Word에서 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words를 사용하여 Word 문서에 인라인 이미지 삽입](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}