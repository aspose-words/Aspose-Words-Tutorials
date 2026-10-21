---
category: general
date: 2026-09-21
description: Aspose.Words를 사용하여 빈 Word 문서를 만든 뒤, 도형 크기와 위치, 색상을 설정하고 한 번의 워크스루로 docx
  파일을 저장합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: ko
lastmod: 2026-09-21
og_description: 빈 Word 문서를 만들고, 도형 크기와 위치, 색상을 설정한 뒤, 몇 분 안에 Aspose.Words로 docx 파일을
  저장합니다.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: 빈 Word 문서를 만들고 색상 도형을 추가 – Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Aspose.Words를 사용해 빈 Word 문서를 만들고 색상 도형 추가하기
url: /ko/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서를 만들고 Aspose.Words로 색상 도형 추가하기

프로그램matically **빈 Word 문서를 만들**어야 할 때, 이 가이드는 Aspose.Words를 사용한 방법을 보여줍니다. **도형 크기 설정**, **도형 위치 설정**, **도형 색상 설정**, 그리고 마지막으로 **docx 파일 저장**을 IDE를 떠나지 않고 수행하는 방법을 배울 수 있습니다.

C#에서 Word 파일을 다루는 것은 종종 저수준 OpenXML 호출을 오가야 하지만, Aspose.Words는 그 복잡성을 추상화합니다. 이 튜토리얼을 마치면 두 개의 색상 사각형으로 구성된 그룹 도형을 포함한 완전한 `.docx` 파일을 만들 수 있게 됩니다—보고서, 증명서, 맞춤 템플릿 등에 이상적입니다.

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 동작)
- Aspose.Words for .NET 23.9 이상 (NuGet으로 설치: `Install-Package Aspose.Words`)
- C# 및 Visual Studio(또는 기타 C# 편집기)에 대한 기본 지식

기존 Word 파일이 필요하지 않으며, 튜토리얼은 **빈 Word 문서 만들기**부터 시작합니다.

## Aspose.Words로 빈 Word 문서 만들기

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내의 빈 Word 파일을 나타냅니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document`는 비어 있는 상태로 시작하므로 **빈 Word 문서를 만들**때 정확히 필요합니다. `builder`는 이후 현재 커서 위치에 도형 그룹을 삽입하는 데 사용됩니다.

## 도형 크기 설정 및 GroupShape 만들기

`GroupShape`는 여러 개별 도형을 담을 수 있는 컨테이너와 같습니다. 먼저 컨테이너 전체 크기를 정의합니다.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

여기서 그룹 자체의 **도형 크기**를 (300 × 200)으로 **설정**합니다. 각 자식 도형에도 동일한 속성 이름(`Width`, `Height`)을 사용해 세밀하게 제어할 수 있습니다.

## 첫 번째 사각형 추가 및 도형 색상 설정

이제 그룹에 사각형을 추가하고 배경 색을 지정합니다.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

`FillColor` 속성은 **도형 색상**을 설정합니다. `System.Drawing.Color`를 사용하면 미리 정의된 색이든 사용자 정의 ARGB 값이든 선택할 수 있습니다.

## 두 번째 사각형 추가, 크기·위치·색상 설정

두 번째 사각형은 **도형 위치**를 그룹에 상대적으로 설정하고 색상을 변경하는 방법을 보여줍니다.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

그룹의 너비가 300 포인트이므로 두 개의 120‑포인트 사각형이 30‑포인트 간격으로 여유 있게 들어갑니다. 다른 레이아웃이 필요하면 `Left`와 `Top`을 조정하세요.

## GroupShape를 문서에 삽입하기

그룹 구성이 완료되면 현재 커서 위치에 배치합니다.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode`는 도형을 문서 본문에 직접 기록하여 앞서 **설정한 도형 위치**를 정확히 유지합니다.

## docx 파일 저장하기

마지막 단계는 문서를 디스크에 저장하는 것입니다. 이는 **docx 파일 저장** 작업을 보여줍니다.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

프로그램을 실행한 뒤 `GroupShape.docx`를 Microsoft Word에서 열면, 두 개의 색상 사각형이 나란히 배치된 그룹 도형이 포함된 빈 페이지를 확인할 수 있습니다.

### 예상 출력

- 단일 페이지 `.docx` 파일
- 페이지에는 왼쪽 및 위쪽 여백으로부터 100 pts 떨어진 위치에 그룹 도형이 존재
- 그룹 안에는 왼쪽에 연한 파란색 사각형, 오른쪽에 연한 코랄 색 사각형이 각각 120 × 80 pts 크기로 배치

## 전체 실행 가능한 예제

아래는 콘솔 애플리케이션에 복사·붙여넣기 할 수 있는 완전한 프로그램입니다. 추가 파일이 필요하지 않습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

이 프로그램을 실행하면 앞서 설명한 문서가 정확히 생성되며, **빈 Word 문서 만들기**, **도형 크기 설정**, **도형 위치 설정**, **도형 색상 설정**, **docx 파일 저장** 네 가지 목표를 모두 달성합니다.

## 일반적인 변형 및 엣지 케이스

| 시나리오 | 변경 내용 | 이유 |
|----------|----------|------|
| **다른 도형 유형** | `ShapeType.Rectangle`을 `ShapeType.Ellipse`, `ShapeType.Triangle` 등으로 교체 | 외부 이미지 없이도 더 복잡한 그래픽을 만들 수 있습니다. |
| **동적 차원** | `Width`와 `Height`를 사용자 입력이나 설정 파일에서 계산 | 여러 문서 템플릿에 재사용 가능한 솔루션이 됩니다. |
| **PDF로 저장** | `document.Save("output.pdf", SaveFormat.Pdf);` 호출 | 수신자가 편집 불가능한 형식을 원할 때 안전한 선택입니다. |
| **도형 내부에 텍스트 추가** | `TextBox` 도형을 만들고 `TextBox.Text` 설정 | 라벨이 있는 배지나 호출 상자를 만들 때 유용합니다. |
| **한 페이지에 여러 그룹** | 서로 다른 `Left`/`Top` 값으로 2‑5 단계를 반복 | 대시보드나 다중 섹션 레이아웃을 구성할 수 있습니다. |

### 전문가 팁

도형을 정확히 정렬해야 할 경우, 그룹을 삽입하기 전에 `ShapeBase.WrapType = WrapType.Inline` 속성을 사용하세요. 이렇게 하면 그룹이 단락처럼 동작해 텍스트가 예기치 않게 흐르는 것을 방지합니다.

## 결론

이제 Aspose.Words를 사용해 **빈 Word 문서를 만들**, **도형 크기 설정**, **도형 위치 설정**, **도형 색상 설정**, 그리고 **docx 파일 저장**하는 방법을 알게 되었습니다. 전체 예제는 어떤 Word 자동화 프로젝트에도 그룹 그래픽을 추가할 수 있는 깔끔하고 재사용 가능한 패턴을 보여줍니다.

다음 단계로 할 수 있는 일:

- 동일 `GroupShape`에 더 많은 도형이나 이미지를 추가(**도형 크기**, **도형 색상** 변형)
- `ShapeBase.Rotation`을 사용해 사각형을 회전시켜 장식 효과 적용
- 동일 문서를 PDF 또는 HTML로 내보내 배포 범위 확대(**docx 파일 저장** 대안)

다양한 색상, 크기, 레이아웃 로직을 실험해 보고, 여러분의 보고서나 템플릿 요구에 맞게 맞춤화해 보세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 단계별 설명과 완전한 코드 예제를 포함하고 있어 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}