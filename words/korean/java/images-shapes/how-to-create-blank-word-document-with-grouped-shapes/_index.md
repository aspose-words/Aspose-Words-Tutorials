---
category: general
date: 2026-09-08
description: C#를 사용하여 빈 Word 문서를 만들고, 사각형 도형을 삽입하며, 여러 도형을 그룹화하는 방법을 배워보세요. 이 단계별
  가이드를 따라하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: ko
lastmod: 2026-09-08
og_description: C#에서 빈 Word 문서를 만들고 사각형 도형을 삽입한 뒤 여러 도형을 그룹화합니다. 이 튜토리얼은 전체 과정을 단계별로
  안내합니다.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: C#에서 그룹화된 도형이 포함된 빈 Word 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 그룹화된 도형이 있는 빈 Word 문서 만들기
url: /ko/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 그룹화된 도형을 사용하여 빈 Word 문서 만들기

맞춤 그래픽이 포함된 **빈 Word 문서**를 만들어야 한다면, 이 가이드가 정확히 어떻게 하는지 보여줍니다. Aspose.Words for .NET을 사용하여 **사각형 도형 삽입**, **여러 도형 그룹화**, 그리고 **그룹에 도형 추가**하는 방법을 배울 수 있습니다.

빈 문서는 깨끗한 캔버스를 제공하고, 도형을 그룹화하면 하나의 단위로 이동, 크기 조정 또는 회전할 수 있습니다. 이 튜토리얼은 문서 초기화부터 최종 파일 저장까지 모든 단계를 다루므로 코드를 프로젝트에 복사해 바로 결과를 확인할 수 있습니다.

## 필요 사항

시작하기 전에 다음을 준비하세요:

* .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 작동합니다)
* 유효한 Aspose.Words for .NET 라이선스 (무료 평가판을 테스트용으로 사용할 수 있습니다)
* Visual Studio 2022 또는 Visual Studio Code와 같은 IDE
* C# 구문에 대한 기본적인 이해

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## 빈 Word 문서 만들기

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 `DocumentBuilder`로 편집할 수 있는 빈 `.docx` 파일을 나타냅니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 생성자는 메모리 내에 **빈 Word 문서**를 생성합니다. `DocumentBuilder`는 텍스트, 이미지 및 그리기 객체를 삽입하기 위한 유창한 API를 제공합니다.

## 문서에 사각형 도형 삽입

다음으로 사각형 도형을 추가합니다. 이 사각형은 나중에 만들 그룹의 첫 번째 자식이 됩니다.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

`ShapeType.Rectangle`와 함께 `InsertShape`를 호출하면 현재 커서 위치에 **사각형 도형**이 삽입됩니다. 너비와 높이는 포인트 단위로 표현됩니다(1 pt ≈ 1/72 in).

## 여러 도형을 함께 그룹화

`GroupShape`는 컨테이너와 같은 역할을 합니다. 그룹 내부의 모든 자식 도형은 함께 이동하고 변형됩니다. 먼저 그룹을 만든 다음 방금 만든 사각형을 추가합니다.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape` 메서드는 빌더의 커서 위치에 빈 그룹을 배치합니다. 사각형을 추가함으로써 **여러 도형을 그룹화**하게 되며, 사각형은 그룹 내부 노드 컬렉션의 일부가 됩니다.

## 그룹에 도형 추가 및 파일 저장

이제 두 번째 도형인 타원을 추가하여 여러 객체가 동일한 컨테이너를 공유하는 모습을 보여줍니다. 이후 문서를 저장합니다.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`InsertShape` 호출은 반환된 `Shape`를 `GroupShape`에 추가할 때 **그룹에 도형을 추가**합니다. `Document`를 저장하면 Microsoft Word, LibreOffice 또는 호환 뷰어에서 열 수 있는 `.docx` 파일이 생성됩니다.

### 예상 결과

*GroupShapeDemo.docx*를 열면, 밝은 파란색 사각형과 분홍색 타원이 포함된 그룹화된 객체가 있는 빈 페이지가 표시됩니다. 그룹을 선택하면 두 도형이 함께 이동되어 **여러 도형을 그룹화**했음이 확인됩니다.

## GroupShape를 사용하는 이유

* **Atomic transformations** – 그룹을 스케일링, 회전 또는 이동하면 모든 자식이 균일하게 변합니다.
* **Logical organization** – 관련 그래픽을 함께 보관하여 문서 구조를 유지 관리하기 쉽습니다.
* **Performance** – 다수의 독립 도형을 처리하는 것보다 단일 컨테이너를 렌더링하는 것이 종종 더 빠릅니다.

나중에 단일 자식을 수정해야 할 경우 `group.ChildNodes`에서 인덱스 또는 `Name` 속성을 통해 검색할 수 있습니다.

## 일반적인 변형 및 엣지 케이스

| 시나리오                                 | 코드 적용 방법                                                                      |
|------------------------------------------|------------------------------------------------------------------------------------|
| **다른 도형 유형**                        | `ShapeType.Rectangle` 또는 `ShapeType.Ellipse`를 다른 `ShapeType`으로 교체          |
| **도형 내부에 텍스트 추가**               | 도형 삽입 후 `Shape.TextPath.Text = "Hello"` 사용                                   |
| **회전 각도 설정**                       | `group.Rotation = 45;` (도)                                                         |
| **DOCX 대신 PDF로 저장**                  | `doc.Save("GroupShapeDemo.pdf");`                                                   |
| **그룹에 테두리 적용**                    | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`                 |

## 전문가 팁

* **도형에 이름 지정** – `rectangle.Name = "MyRect";`와 같이 이름을 부여하면 나중에 찾기 쉬워집니다.
* **상대 위치 지정 사용** – 그룹을 페이지 여백에 고정하려면 `group.RelativeHorizontalPosition`을 `RelativeHorizontalPosition.Page`로 설정합니다.
* **리소스 해제** – 대규모 애플리케이션에서 작업할 때 `Document`를 `using` 블록으로 감싸서 관리되지 않는 메모리를 즉시 해제합니다.

## 빠른 복사‑붙여넣기를 위한 전체 소스 코드

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

코드를 새 콘솔 프로젝트에 복사하고 `Aspose.Words` NuGet 패키지를 복원한 뒤 실행하세요. 출력 파일은 프로젝트의 `bin/Debug/net6.0`(또는 해당 폴더) 안에 생성됩니다.

## 다음 단계

이제 **빈 Word 문서 만들기**, **사각형 도형 삽입**, **여러 도형 그룹화**를 할 수 있게 되었으니 다음을 탐색해 보세요:

* 그룹 내부에 **텍스트 상자**를 추가하여 라벨이 있는 다이어그램 만들기
* `doc.Save("image.png", SaveFormat.Png)`를 사용해 그룹화된 그래픽을 이미지로 내보내기
* 그룹을 표와 결합해 풍부한 서식 보고서 만들기

다양한 도형 속성, 그룹 계층 구조 및 내보내기 형식을 실험하여 Aspose.Words의 그리기 기능을 최대한 활용하세요.

--- 

*Remember*: grouping shapes is a powerful way to keep your Word documents tidy and your code maintainable. Happy coding!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스에는 완전한 동작 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [C#를 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 도형 삽입](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}