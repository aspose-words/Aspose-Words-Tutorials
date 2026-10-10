---
category: general
date: 2026-10-10
description: 빈 Word 문서를 만든 다음, Word에 이미지를 삽입하고 이미지 그룹을 추가한 뒤 저장된 파일에서 도형을 숨깁니다. 이
  단계별 가이드를 따라 주세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: ko
lastmod: 2026-10-10
og_description: 빈 Word 문서를 만들고, 이미지를 Word에 삽입하고, 이미지 그룹을 추가한 뒤 도형을 숨깁니다. 이 가이드는 전체
  C# 코드를 보여줍니다.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: 빈 Word 문서를 만들고 이미지 그룹을 추가한 뒤 도형을 숨기기
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: 빈 Word 문서를 만들고 이미지 그룹을 추가한 뒤 도형을 숨기기
url: /ko/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서 만들기, 이미지 그룹 추가, 도형 숨기기

빈 Word 문서를 **create blank word document**하고 나중에 시각 요소를 숨겨야 한다면, 이 튜토리얼이 정확히 어떻게 하는지 보여줍니다. 이미지 삽입, 이미지 그룹 추가, 그리고 도형 숨기기를 하나의 재사용 가능한 C# 루틴으로 배울 수 있습니다.

Aspose.Words for .NET 라이브러리를 사용할 것입니다. 이 라이브러리를 사용하면 Microsoft Word가 설치되지 않은 환경에서도 .docx 파일을 조작할 수 있습니다. 이 가이드를 마치면 숨겨진 이미지 그룹을 포함한 Word 파일을 생성하는 실행 가능한 프로그램을 얻게 되며, 이는 후속 처리나 조건부 표시를 위해 준비됩니다.

## Prerequisites

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 동작합니다)
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)
- 이미지 파일을 읽고 출력 문서를 쓸 수 있는 디스크상의 폴더
- C# 및 Visual Studio(또는 선호하는 IDE)에 대한 기본 지식

## Aspose.Words를 사용해 빈 Word 문서 만들기

첫 번째 단계는 **create blank word document**입니다. Aspose.Words는 메모리 상의 Word 파일을 나타내는 `Document` 클래스를 제공합니다. 인수 없이 인스턴스를 생성하면 내용이 없는 빈 문서를 얻을 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*왜 중요한가:* 빈 문서에서 시작하면 나중에 추가할 도형에 영향을 줄 수 있는 숨겨진 서식이나 남아 있는 섹션이 없으므로 안정적으로 작업할 수 있습니다.

## DocumentBuilder를 사용해 Word에 이미지 삽입

다음으로 **insert image into word**하기 위해 먼저 그림을 담을 그룹 도형을 생성합니다. 그룹 도형을 사용하면 여러 개의 그리기 객체를 하나의 단위로 취급할 수 있어, 나중에 함께 숨기거나 이동할 때 유용합니다.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

`InsertGroupShape` 메서드는 빈 컨테이너를 생성합니다. 크기는 포인트 단위(1 포인트 = 1/72 인치)이며, 삽입하려는 이미지 해상도에 맞게 조정합니다.

## 문서에 이미지 그룹 추가

이제 **add image group**을 수행합니다. 빌더 커서를 새로 만든 그룹 내부로 이동한 뒤 그림을 삽입하면 됩니다. 이후의 모든 삽입은 그룹의 일부가 됩니다.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*팁:* 절대 경로나 올바르게 이스케이프된 상대 경로를 사용하세요. 그렇지 않으면 `InsertImage`가 `FileNotFoundException`을 발생시킵니다.

## Word 문서에서 도형 숨기기

마지막으로 **hide shape word document**를 수행합니다. 그룹의 `Hidden` 속성을 `true`로 설정하면 됩니다. 숨겨진 도형은 Word에서 문서를 열 때 표시되지 않지만 파일 안에 남아 있어 프로그램적으로 나중에 다시 표시할 수 있습니다.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

*GroupHidden.docx*를 Microsoft Word에서 열면 이미지 그룹이 숨겨져 있기 때문에 완전히 빈 페이지가 표시됩니다. 파일에는 여전히 이미지 데이터가 포함되어 있으며, 필요하면 `group.Hidden = false`로 해제하여 다시 표시할 수 있습니다.

## 전체 실행 가능한 예제

아래는 새 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**예상 출력**

- `GroupHidden.docx`라는 파일이 `YOUR_DIRECTORY`에 생성됩니다.
- Word에서 파일을 열면 빈 페이지가 표시됩니다.
- 숨겨진 이미지는 `group.Hidden = false`로 변경하고 다시 저장하면 표시됩니다.

## 일반적인 변형 및 엣지 케이스

| Situation | How to adapt the code |
|-----------|----------------------|
| **Multiple images** | `InsertImage` 호출을 `builder.MoveTo(group)` 뒤에 추가합니다. 모든 이미지는 동일한 그룹 안에 머무르며 숨김 플래그를 공유합니다. |
| **Different image formats** | Aspose.Words는 PNG, JPEG, BMP, GIF, TIFF를 지원합니다. 파일 확장자만 바꾸면 되며 코드 수정은 필요 없습니다. |
| **Conditional visibility** | 사용자 정의 문서 변수(`doc.Variables.Add("ShowImages", "true")`)를 저장하고 런타임에 그 값에 따라 `group.Hidden`을 토글합니다. |
| **Large documents** | 레이아웃 이동을 방지하려면 그룹을 삽입하기 전에 `builder.InsertBreak(BreakType.PageBreak)`를 사용해 특정 페이지에 그룹을 만들세요. |
| **Compatibility with older Word versions** | 레거시 `.doc` 형식이 필요하면 `doc.Save("output.doc", SaveFormat.Doc)`로 저장합니다; 숨겨진 도형은 동일하게 동작합니다. |

**Pro tip:** 모든 자식 요소를 삽입한 **후에** `group.Hidden = true`를 설정하세요. 콘텐츠를 추가하기 전에 플래그를 변경하면 오래된 Word 버전에서 일부 요소가 예상치 못하게 렌더링될 수 있습니다.

## Conclusion

이제 Aspose.Words for .NET을 사용해 **create blank word document**, **insert image into word**, **add image group**, 그리고 **hide shape word document**를 수행하는 방법을 알게 되었습니다. 전체 예제는 문서 초기화부터 숨겨진 이미지 그룹을 포함한 파일 저장까지 모든 단계를 보여줍니다.

다음으로 탐색해 볼 수 있는 내용:

- 동일한 그룹에 텍스트 상자나 차트 추가
- `DocumentBuilder.StartBookmark` / `EndBookmark`를 사용해 숨긴 섹션 표시
- 사용자 입력이나 문서 변수에 따라 프로그래밍적으로 가시성 토글

다양한 도형, 크기, 가시성 규칙을 실험해 보면서 자동화 시나리오에 맞게 적용해 보세요. Happy coding!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}