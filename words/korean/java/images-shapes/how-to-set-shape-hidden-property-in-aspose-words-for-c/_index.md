---
category: general
date: 2026-08-20
description: Aspose.Words for C#에서 도형의 숨김 속성을 설정하는 방법을 배웁니다. 이 가이드는 이미지를 삽입하고 도형을
  숨겨 UI나 인쇄 출력에 절대 표시되지 않도록 하는 방법을 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: ko
lastmod: 2026-08-20
og_description: C#를 사용하여 Aspose.Words에서 도형의 숨김 속성을 설정합니다. 이미지를 삽입하고 도형을 숨겨 UI나 인쇄
  출력에 절대 표시되지 않도록 합니다.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Aspose.Words에서 도형 숨김 속성 설정 – 완전 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Aspose.Words for C#에서 도형 숨김 속성을 설정하는 방법
url: /ko/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C#에서 shape hidden 속성 설정 방법

Word 문서에서 **shape hidden 속성**을 설정해야 하는 경우, 이 튜토리얼에서는 Aspose.Words for .NET을 사용한 정확한 단계들을 보여줍니다. 템플릿 엔진을 구축하거나, 보고서를 생성하거나, 보이지 않아야 하는 로고를 삽입하는 경우에도, 이미지를 삽입하고 shape를 숨겨 UI나 인쇄 출력에 절대 나타나지 않도록 하는 방법을 배울 수 있습니다.

이 가이드에서는 **insert image into document**도 다루며, shape를 숨기는 것이 인쇄에 왜 중요한지 설명하고, 완전하고 실행 가능한 코드를 단계별로 안내합니다. 외부 참조는 필요 없으며, 복사·붙여넣기만 하면 바로 실행할 수 있습니다.

## 사전 요구 사항

* .NET 6.0 이상 (최신 Aspose.Words 버전은 .NET 6+을 대상으로 함)
* 유효한 Aspose.Words for .NET 라이선스 (또는 무료 평가 모드 사용)
* Visual Studio 2022 또는 선호하는 C# IDE
* `logo.png`와 같은 이미지 파일을 코드에서 참조할 수 있는 폴더에 배치

## 단계 1: 새 Document 및 DocumentBuilder 만들기

`DocumentBuilder` 클래스는 프로그래밍 방식으로 Word 콘텐츠를 구축하기 위한 진입점입니다. 이를 통해 단락, 표, 이미지와 같은 shape를 삽입할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*왜 이 단계인가?*  
`Document`를 생성하면 .docx 파일의 메모리 내 표현을 얻을 수 있고, `DocumentBuilder`는 객체를 삽입하는 fluent API를 제공합니다. 이 객체들이 없으면 문서에 shape를 배치할 수 없습니다.

## 단계 2: 이미지를 shape로 삽입하기

Aspose.Words는 모든 그림을 `Shape`으로 취급합니다. `InsertImage` 메서드는 해당 `Shape` 인스턴스를 반환하며, 이후에 조작할 수 있습니다.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*왜 이 단계인가?*  
`InsertImage`를 사용하면 그림을 텍스트 흐름에 추가할 뿐만 아니라 구성할 수 있는 참조(`picture`)를 얻습니다. 이는 다음에 설정할 **C# shape hidden property**에 필수적입니다.

## 단계 3: shape hidden 속성 설정

`Hidden` 속성은 shape가 UI 및 인쇄에 참여하는지를 제어합니다. 이를 `true`로 설정하면 Word UI에서 shape가 보이지 않으며 인쇄되지 않음이 보장됩니다.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*왜 이 단계인가?*  
shape가 hidden으로 표시되면 Word는 이를 주석처럼 처리합니다—문서 구조에는 존재하지만 렌더링되지 않습니다. 이것이 **set shape hidden property**의 핵심입니다.

## 단계 4: 문서 저장

마지막으로 문서를 디스크에 저장합니다. Aspose.Words가 지원하는 모든 형식(`.docx`, `.pdf`, `.html` 등)을 선택할 수 있습니다.

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*왜 이 단계인가?*  
저장은 메모리 내 변경을 최종 확정합니다. 결과 `.docx`를 Microsoft Word에서 열면 이미지가 보이지 않으며, PDF로 내보내도 shape가 인쇄 출력에 나타나지 않음을 확인할 수 있습니다.

## 전체 실행 가능한 예제

모든 단계를 종합하면, 다음은 컴파일하고 실행할 수 있는 전체 프로그램입니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**예상 결과**

* `HiddenImageDocument.docx`를 Microsoft Word에서 열면 보이는 이미지가 없습니다.
* 문서를 내보내거나 인쇄(또는 PDF를 열어도) 이미지가 표시되지 않습니다.
* hidden shape는 문서 XML에 여전히 존재하며, `.docx`를 zip으로 열어 `word/document.xml`을 확인하면 `<w:pict>` 요소에 `w:hidden="true"`가 있는 것을 확인할 수 있습니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 조치 | 중요한 이유 |
|-----------|------------|----------------|
| **Image file missing** | `InsertImage`를 `try/catch`로 감싸고 `FileNotFoundException`을 처리합니다. | 애플리케이션이 충돌하는 것을 방지하고 명확한 오류를 로그에 기록할 수 있습니다. |
| **Multiple hidden shapes** | 삽입하는 각 `Shape`에 대해 `picture.Hidden = true`를 호출하거나 `doc.GetChildNodes(NodeType.Shape, true)`를 반복합니다. | 원하지 않는 모든 시각 요소가 보이지 않도록 보장합니다. |
| **Need the shape visible only in edit mode** | 편집 후 `picture.Hidden = false`로 설정하고, 저장하기 전에 다시 토글합니다. | UI에서 shape를 작업할 수 있게 하면서 최종 출력은 깔끔하게 유지합니다. |
| **Printing on older Word versions** | Word 2010 이상에서 문서를 확인하십시오; hidden 플래그는 모든 최신 버전에서 지원됩니다. | 사용자 기반 전반에 걸친 호환성을 보장합니다. |
| **Using a different file format (e.g., PDF directly)** | `Hidden` 플래그는 동일하게 작동하며, Aspose.Words는 PDF 변환 시 이를 존중합니다. | **prevent shape from printing**이 모든 내보내기 대상에서 작동함을 확인합니다. |

## 전문가 팁: 프로그래밍 방식으로 hidden 플래그 확인

저장하기 전에 shape가 hidden인지 확인해야 하는 경우, 해당 속성을 검사할 수 있습니다:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

이 간단한 검사는 문서 생성 정책을 준수해야 하는 자동화 파이프라인에서 유용합니다.

## 결론

이제 Aspose.Words for C#에서 **shape hidden 속성**을 설정하는 방법을 알게 되었습니다. 이미지를 삽입하고 `picture.Hidden = true`를 적용한 뒤 문서를 저장하면 shape가 UI에 나타나지 않으며 인쇄 출력에도 절대 표시되지 않습니다. 이 기술은 플레이스홀더, 워터마크 또는 브랜드 요소를 사용자에게 보이지 않게 유지해야 할 때 필수적입니다.

### 다음 단계

* `picture.WrapType`, `picture.Rotation`, `picture.RelativeHorizontalPosition`와 같은 다른 shape 속성을 탐색해 보세요.
* 사용자 입력이나 구성에 따라 **hide shape in Aspose.Words**를 조건부로 적용하는 방법을 배우세요.
* hidden shape를 **insert image into document** 루프와 결합하여 동적이고 보이지 않는 마커를 생성하고 이후 처리(예: 메일 병합 필드)에 활용하세요.

다양한 이미지 형식, 문서 레이아웃 및 내보내기 대상에 대해 자유롭게 실험해 보세요. shape를 숨기면 독자가 실제로 보는 내용과 뒤에서 진행되는 내용을 세밀하게 제어할 수 있습니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words를 사용한 Word에서 사각형 shape 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words for .NET을 사용한 Word 문서에서 그룹 shape 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words를 사용한 Word 문서에 인라인 이미지 삽입](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}