---
category: general
date: 2026-10-23
description: Aspose.Words를 사용하여 Word에 타원을 삽입하고 사각형 모양을 추가하는 방법을 배웁니다. 모양으로 커서를 이동하는
  방법과 그룹 모양을 만드는 방법도 포함됩니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: ko
lastmod: 2026-10-23
og_description: Aspose.Words를 사용하여 Word에 타원을 삽입하고 사각형 도형을 추가하는 방법. 커서를 도형으로 이동하고 그룹
  도형을 만드는 단계별 가이드를 따라보세요.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Word 그룹 도형에 타원 및 사각형 도형을 삽입하는 방법
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words를 사용하여 그룹 도형 안에 타원 및 사각형 도형 삽입하는 방법
url: /ko/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 그룹 도형 안에 타원 및 사각형 도형 삽입하는 방법

프로그램matically Word 문서에 **how to insert ellipse**를 삽입하는 방법을 알아야 한다면, 이 가이드는 전체 과정을 보여줍니다. 또한 **how to add rectangle** 도형을 보는 방법, **move cursor to shape**를 배우고, 여러 그리기 개체를 포함하는 **how to create group shape**를 발견하게 됩니다.

Word 자동화는 종종 그리기 개체의 정확한 위치 지정이 필요합니다. 이 튜토리얼이 끝날 때쯤에는 그룹화된 사각형과 타원을 포함하는 `.docx` 파일을 생성할 수 있게 되며, 이는 추가 스타일링이나 내보내기에 준비됩니다. 외부 도구는 Aspose.Words for .NET 라이브러리와 .NET 개발 환경 외에는 필요하지 않습니다.

## 전제 조건

* .NET 6.0 이상이 설치되어 있어야 합니다.
* 프로젝트에 Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`)가 추가되어 있어야 합니다.
* C# 구문 및 Visual Studio(또는 기타 IDE)에 대한 기본 지식.

이 요구 사항은 추가 구성 없이 코드를 컴파일할 수 있도록 보장합니다.

## Word에서 그룹 도형 만들기

그룹 도형은 여러 도형을 단일 단위로 이동, 회전 또는 서식 지정할 수 있게 하는 컨테이너 역할을 합니다. 다음 코드는 특정 크기(300 × 200 포인트)의 그룹을 생성하고, 추가 그리기 작업을 위해 문서를 준비합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Why this step matters*: 그룹 도형은 로컬 좌표계를 정의합니다. 커서를 그룹으로 이동한 후 추가되는 모든 도형은 그룹의 원점을 기준으로 배치되어 레이아웃 계산이 간단해집니다.

## Word에 사각형 도형 추가하기

그룹이 존재하므로, 그 안에 **insert rectangle shape**를 삽입할 수 있습니다. 사각형은 배경이나 다른 콘텐츠를 위한 시각적 자리 표시자로 사용됩니다.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explanation*: `MoveTo(group)`은 빌더에게 현재 삽입 지점이 그룹 도형임을 알려줍니다. 커서를 이동하지 않으면 `InsertShape`는 사각형을 그룹이 아닌 문서 본문에 추가합니다.

## 타원 삽입하기

사각형이 배치된 상태에서 이제 **how to insert ellipse**를 시연할 수 있습니다. 타원은 동일한 그룹 내에서 중앙에 배치되며, 필요에 따라 사각형과 겹칠 수 있습니다.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Why the cursor must be moved*: `InsertShape` 호출마다 현재 커서 위치를 따릅니다. `MoveTo(group)`을 다시 호출하면 타원도 그룹의 자식이 되어 의도된 계층 구조를 유지합니다.

## 추가 객체 삽입 전에 커서를 도형으로 이동하기

나중에 더 많은 도형을 추가해야 한다면, 각 삽입 전에 항상 **move cursor to shape**를 수행하십시오. 이 패턴은 그룹 외부에 실수로 배치되는 것을 방지합니다.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: `MoveTo(group)`을 재사용하는 것은 비용이 적고 코드 가독성을 향상시킵니다. 삽입 컨텍스트가 명시적이기 때문에 향후 유지보수도 쉬워집니다.

## 문서 저장하기

마지막으로, 문서를 디스크에 저장합니다. 예제는 지정한 폴더에 `GroupShape.docx` 파일로 저장합니다.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Microsoft Word에서 저장된 파일을 열면, 사각형과 타원이 포함된 단일 그룹이 올바르게 배치된 것을 볼 수 있습니다.

### 예상 출력

* `GroupShape.docx`라는 `.docx` 파일.
* 문서 내부에 크기 300 × 200 포인트인 그룹화된 그리기 개체.
* 그룹 내부:
  * 그룹 원점에 위치한 사각형 (100 × 50 포인트).
  * 사각형과 겹치는 타원 (80 × 80 포인트).
  * 커서를 이동한 후 추가한 기타 도형들.

## 일반적인 변형 및 엣지 케이스

| 상황 | 권장 접근 방식 |
|-----------|----------------------|
| **다른 단위 크기** | Aspose.Words는 포인트(1 pt = 1/72 in)를 사용합니다. `InsertShape`를 호출하기 전에 센티미터 또는 인치를 포인트로 변환하십시오. |
| **그룹 내부 도형 회전** | 도형을 삽입한 후, 해당 `ShapeBase` 객체를 가져와 `ShapeBase.RotationAngle`을 설정합니다. |
| **도형 내부에 텍스트 추가** | `ShapeBase.AppendChild(new Paragraph(document))`를 사용하고, 원하는 텍스트가 포함된 `Run`을 추가합니다. |
| **DOCX 대신 PDF로 저장** | `document.Save("GroupShape.pdf", SaveFormat.Pdf);`를 호출합니다 – 그룹 계층 구조가 PDF 출력에 보존됩니다. |

이러한 변형은 동일한 **how to insert ellipse** 로직을 다양한 실제 시나리오에 적용할 수 있음을 보여줍니다.

## 전문가 팁

* **Reuse the same `DocumentBuilder` instance** – 메모리 오버헤드를 줄이고 문서 상태를 일관되게 유지합니다.
* **Validate shape dimensions** – 매우 큰 너비나 높이는 오래된 Word 버전에서 렌더링 문제를 일으킬 수 있습니다.
* **Group before styling** – 모든 자식이 추가된 후 그룹에 채우기 색상이나 선 스타일을 적용하면 일관된 외관을 보장합니다.

## 결론

이제 Aspose.Words를 사용하여 Word 문서의 그룹화된 컨테이너 안에 **how to insert ellipse**와 **how to add rectangle** 도형을 삽입하는 방법을 이해했습니다. 각 삽입 전에 일관되게 **move cursor to shape**를 수행하면 깔끔한 계층 구조를 유지하고 실수로 배치되는 것을 방지할 수 있습니다. 전체 예제는 컴파일되고 실행되어 추가 커스터마이징이나 내보내기가 가능한 그룹 도형을 생성합니다.

더 탐구할 준비가 되셨나요? 복잡한 다이어그램을 위해 **how to create group shape**와 이 기술을 결합해 보거나, 풍부한 보고서 생성을 위해 텍스트 상자와 함께 **insert rectangle shape word**를 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words를 사용하여 Word에서 사각형 도형 및 그룹 도형 만들기](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [C#에서 빈 Word 문서를 만들고 숨겨진 타원 도형 추가하기](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [C#에서 그룹 도형 docx를 만들고 인터랙티브 컨트롤 추가하기](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}