---
category: general
date: 2026-10-20
description: Aspose.Words for C#의 새로운 `Hidden` 속성을 사용하여 도형을 숨기거나 표시합니다. 도형 가시성을 전환하는
  방법, 예외 상황을 처리하는 방법 및 결과를 저장하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: ko
lastmod: 2026-10-20
og_description: Aspose.Words for C#를 사용하여 새로운 `Hidden` 속성으로 도형을 숨기거나 표시합니다. 도형 가시성
  전환을 마스터하고 흔히 발생하는 함정을 피하세요.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Aspose.Words(C#)에서 새로운 `Hidden` 속성을 사용하여 도형 숨기기/보이기
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words for C#의 새로운 `Hidden` 속성을 사용하여 도형 숨기기/보이기
url: /ko/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 새 `Hidden` 속성을 사용하여 Aspose.Words for C#에서 도형 숨기기/보이기

Word 문서에서 **새 `Hidden` 속성을 사용하여 도형을 숨기거나 보이게** 해야 할 경우, 이 가이드는 Aspose.Words for .NET을 사용해 정확히 어떻게 수행하는지 보여줍니다. 보고서를 생성하거나 템플릿을 구축하거나 가져온 문서를 정리할 때, 프로그래밍으로 도형 가시성을 제어하면 수동 편집을 피할 수 있습니다.

이 튜토리얼에서는 문서를 로드하고, 도형을 찾아, `Hidden` 속성을 토글하고, 수정된 파일을 저장하는 방법을 배웁니다. 또한 여러 도형을 처리하거나 인라인 그래픽과 플로팅 그래픽을 구분하는 일반적인 변형도 다룹니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요.

* .NET 6.0(또는 그 이상) – Aspose.Words는 .NET Standard 2.0 및 .NET Core를 지원합니다.  
* **Aspose.Words for .NET** 라이선스 사본(무료 평가판으로도 탐색 가능)  
* Visual Studio 2022 또는 Visual Studio Code와 같은 IDE  
* 하나 이상의 도형(예: 그림, SmartArt, 드로잉 캔버스)이 포함된 Word 문서(`input.docx`)

## 1단계: Word 문서 로드

첫 번째 작업은 디스크에 있는 .docx 파일을 나타내는 `Document` 객체를 만드는 것입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*이 단계가 중요한 이유*: `Document`는 Aspose.Words 모든 작업의 진입점입니다. 파일을 메모리로 로드하면 노드 트리 전체에 접근할 수 있으며, 여기에는 도형도 포함됩니다.

## 2단계: 대상 도형 가져오기

가시성을 토글하려면 도형 노드에 대한 참조를 얻어야 합니다. 아래 예제는 문서에서 첫 번째 도형을 가져오지만, 이름, 유형 또는 인덱스로 도형을 찾도록 로직을 조정할 수 있습니다.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*이 단계가 중요한 이유*: `GetChild`에 `true`를 전달하면 깊은 검색이 수행되어 테이블이나 헤더 내부에 중첩된 도형도 찾을 수 있습니다. `null` 검사는 문서에 도형이 없을 때 `NullReferenceException`을 방지합니다.

## 3단계: `Hidden` 속성으로 도형 숨기기

Aspose.Words는 도형이 렌더링되거나 인쇄되는지를 제어하는 `Hidden` 속성을 도입했습니다. `true`로 설정하면 도형이 숨겨지고, `false`로 설정하면 다시 보이게 됩니다.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

이전에 숨겨진 도형을 **보이게** 하려면 `false`를 할당하면 됩니다.

```csharp
// Show the shape again
shape.Hidden = false;
```

*이 단계가 중요한 이유*: `Hidden` 속성은 플로팅 도형과 인라인 도형 모두에 적용되며, Word의 기본 “Hidden” 서식과 통합됩니다. 노드를 문서 트리에서 제거하지 않고 플래그만 바꾸므로 레이아웃과 참조가 유지되어 보다 신뢰할 수 있습니다.

## 4단계: 수정된 문서 저장

가시성을 조정한 후 변경 사항을 새 파일에 기록하거나(원한다면) 원본을 덮어씁니다.

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*이 단계가 중요한 이유*: `Save`는 메모리상의 노드 트리를 .docx 패키지로 직렬화합니다. 숨김 플래그가 저장되므로 Microsoft Word에서 파일을 열면 `Hidden` 설정에 따라 도형이 표시됩니다.

## 전체 실행 가능한 예제

모든 단계를 합치면 복사·컴파일·실행할 수 있는 독립 프로그램이 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

프로그램을 실행했을 때 **예상 출력**:

```
Document saved. Shape hidden = True
```

`ShapeHidden.docx`를 Microsoft Word에서 열면 대상 도형이 없는 문서가 표시됩니다. 저장 전에 `shape.Hidden = false;` 로 설정하면 도형이 다시 나타납니다.

## 여러 도형 처리하기

위 예제는 단일 도형에만 적용됩니다. 실제 문서에는 그래픽이 많이 포함될 수 있습니다. 조건에 맞는 모든 도형을 숨기거나 보이게 하려면 루프를 사용하세요(예: 특정 이름이나 유형).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*팁*: `ShapeType`으로 필터링하면 텍스트 상자나 SmartArt와 같은 장식 요소를 실수로 숨기는 것을 방지할 수 있습니다.

## 엣지 케이스 및 모범 사례

| 상황 | 권장 처리 방법 |
|-----------|----------------------|
| **헤더/푸터 안에 도형이 있는 경우** | 먼저 헤더/푸터 노드를 가져온 뒤 해당 서브‑문서에서 `GetChild(NodeType.Shape, …)`를 호출합니다. |
| **문서에 도형이 전혀 없는 경우** | `GetChild` 후 항상 `null` 여부를 확인하거나 `doc.GetChildNodes(NodeType.Shape, true).Count`를 검증합니다. |
| **다양한 Word 버전에서 숨김 플래그를 유지해야 하는 경우** | `Hidden` 속성은 도형 XML에 `<w:hidden/>` 형태로 저장되며 Word 2007 이후 버전에서 지원됩니다. |
| **대용량 문서에서 성능 최적화** | `doc.GetChildNodes(NodeType.Shape, true)`를 한 번만 호출하고 컬렉션을 재사용하여 `GetChild`를 반복 호출하는 것을 피합니다. |

## 전문가 팁: `Hidden`과 `WrapType` 결합하기

도형을 숨겨도 Word는 해당 공간을 예약합니다. `WrapType = WrapType.None`을 설정하면 자리 표시자 영역이 제거됩니다.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

이렇게 하면 레이아웃이 도형이 전혀 없었던 것처럼 축소되어 깔끔한 보고서를 만들 때 유용합니다.

## 결론

이제 Aspose.Words for C#에서 새로운 `Hidden` 속성을 사용해 **도형을 숨기고 보이게** 하는 방법을 알게 되었습니다. 문서 로드, 도형 찾기, `Hidden` 속성 토글, 변경 사항 저장까지 전체 흐름을 다루었습니다. null 검사, 다중 도형 처리, 래핑 설정 조정 등 모범 사례를 따르면 어떤 Word 자동화 시나리오에서도 도형 가시성을 안정적으로 제어할 수 있습니다.

다음 단계도 살펴보세요:

* **사용자 정의 메타데이터**를 기반으로 여러 도형 숨기기/보이기(“프로그램matically hide shape” 기법 활용)  
* `Hidden`을 조건부 콘텐츠와 결합해 Aspose.Words 필드로 동적 보고서 생성  
* 차트 객체의 `Visible`이나 단락 수준 제어를 위한 `IsDeleted` 등 다른 노드 속성 탐색

코딩을 즐기시고, Aspose.Words가 제공하는 세밀한 도형 가시성 제어를 마음껏 활용하세요!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 배운 기술을 확장하는 데 도움이 되는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}