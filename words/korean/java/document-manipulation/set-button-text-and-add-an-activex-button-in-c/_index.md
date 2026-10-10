---
category: general
date: 2026-10-10
description: Aspose.Words를 사용하여 C#에서 버튼 텍스트를 설정하고 ActiveX 버튼을 추가합니다. 버튼 삽입, 버튼 컨트롤
  생성 및 Word 문서에서 캡션을 사용자 지정하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: ko
lastmod: 2026-10-10
og_description: C#와 Aspose.Words를 사용하여 버튼 텍스트를 설정하고 ActiveX 버튼을 추가합니다. 버튼을 삽입하고, 버튼
  컨트롤을 생성하며, 캡션을 사용자 정의하는 단계별 가이드를 따라보세요.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: C#에서 버튼 텍스트 설정 및 ActiveX 버튼 추가 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: C#에서 버튼 텍스트 설정 및 ActiveX 버튼 추가
url: /ko/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 버튼 텍스트 설정 및 ActiveX 버튼 추가

Word 문서 안의 ActiveX 버튼에 **set button text**를 설정해야 한다면, 이 가이드는 정확한 방법을 보여줍니다. 튜토리얼이 끝날 때쯤이면 **insert button**을 수행하고, **button control**을 생성하며, 몇 줄의 C# 코드만으로 캡션을 사용자 정의할 수 있게 됩니다.

Word에서 인터랙티브한 양식을 만들고 싶을 때 ActiveX 컨트롤을 사용하는 경우가 많습니다—계약 템플릿, 설문조사, 내부 도구 등을 만들 때 말이죠. 예제는 Aspose.Words for .NET을 사용합니다. 이 라이브러리는 Microsoft Office 없이도 Word 파일을 조작할 수 있게 해줍니다.

## 사전 요구 사항

* .NET 6.0 SDK 또는 이후 버전이 설치되어 있어야 합니다  
* Visual Studio 2022 (또는 C#를 지원하는 모든 IDE)  
* Aspose.Words for .NET 라이선스 (무료 평가판은 학습용으로 사용할 수 있습니다)  

또한 `Aspose.Words` NuGet 패키지에 대한 참조가 필요합니다:

```bash
dotnet add package Aspose.Words
```

## Word 문서에 버튼 삽입하는 방법

첫 번째 단계는 새로운 `Document`와 `DocumentBuilder`를 만드는 것입니다. Builder는 콘텐츠를 추가하기 위한 진입점이며, 여기에는 ActiveX 컨트롤도 포함됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `Document`는 전체 .docx 파일을 나타내고, `DocumentBuilder`는 `InsertParagraph`와 `InsertFormField`와 같은 고수준 메서드를 제공합니다. 깨끗한 문서에서 시작하면 버튼이 원하는 정확한 위치에 표시됩니다.

## Forms2OleControl로 버튼 컨트롤 생성

이제 실제 버튼 컨트롤을 생성합니다. `Forms2OleControl`은 Aspose.Words가 모든 ActiveX 객체에 사용하는 클래스이며, `COMMANDBUTTON` 유형은 Word에서 클릭 가능한 버튼으로 표시됩니다.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**설명:**  
* `InsertForms2OleControl`는 제공한 정확한 좌표에 컨트롤을 배치합니다.  
* 크기는 포인트 단위로 정의됩니다 (1 포인트 = 1/72 인치). 레이아웃에 맞게 이 값을 조정하세요.

## ActiveX 컨트롤을 추가하고 고유한 이름 지정

각 ActiveX 객체는 나중에 (예: VBA에서 이벤트를 처리할 때) 참조할 수 있도록 고유한 이름을 가져야 합니다.

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**팁:** 이름에 공백이나 특수 문자를 사용하지 마세요; Word는 이름을 내부 폼 모델의 식별자로 취급합니다.

## ActiveX 버튼에 버튼 텍스트(캡션) 설정

여기서 핵심 키워드 **set button text**가 사용됩니다. `Caption` 속성은 사용자가 버튼에서 보는 레이블을 정의합니다.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

문서를 저장하기 전 언제든지 캡션을 변경할 수 있습니다. 나중에 UI를 현지화해야 한다면, 다른 문자열로 `SetCaption`을 다시 호출하면 됩니다.

## 문서 저장 및 결과 확인

마지막으로 문서를 디스크에 기록합니다. Microsoft Word에서 파일을 열면 사용자 지정 캡션이 적용된 버튼이 표시됩니다.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**예상 출력:** Word에서 *ActiveXButton.docx*를 열면 지정된 좌표에 배치된 버튼이 **Click Me**라는 레이블과 함께 표시됩니다. 버튼을 클릭하면 기본 Word 명령 버튼 동작이 트리거됩니다(이를 나중에 VBA로 사용자 정의할 수 있습니다).

![Set button text example](https://example.com/activex-button.png){alt="버튼 텍스트 설정 예시"}

## ActiveX 버튼 추가 및 이벤트 처리 (선택 사항)

버튼이 사용자 정의 동작을 수행하도록 하려면 `Click` 이벤트에 반응하는 VBA 매크로를 추가할 수 있습니다. 매크로를 프로그래밍 방식으로 삽입할 수 있지만, 이는 이 튜토리얼의 범위를 벗어납니다. 중요한 점은 버튼이 이미 존재하고 캡션이 설정되어 있어, 원하는 이벤트 처리에 바로 사용할 수 있다는 것입니다.

## 흔히 발생하는 문제와 해결 방법

| 문제 | 발생 원인 | 해결 방법 |
|-------|----------------|-----|
| 버튼이 정렬되지 않음 | 좌표가 픽셀이 아니라 포인트 단위 | 픽셀 값을 포인트로 변환 (`points = pixels * 72 / DPI`) |
| 저장 후 캡션이 변경되지 않음 | `SetCaption`이 `Save` 이후에 호출됨 | 캡션은 항상 `doc.Save` 호출 **전**에 설정하세요 |
| 오래된 Word 버전에서 컨트롤이 보이지 않음 | 일부 오래된 Word 버전은 전체 ActiveX 지원이 부족함 | 대상 Word 버전에서 테스트하고, 대안으로 `CheckBox` 또는 `DropDownList` 사용을 고려하세요 |
| 출력에 라이선스 경고 | 평가 라이선스가 만료됨 | `License license = new License(); license.SetLicense("Aspose.Words.lic");`와 같이 유효한 Aspose.Words 라이선스를 적용하세요 |

## 전체 실행 가능한 예제

아래는 복사·붙여넣기·실행할 수 있는 전체 프로그램입니다. 필요한 모든 `using` 지시문을 포함하고 있으며, 문서 생성부터 저장까지 전체 워크플로우를 보여줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

`dotnet run`으로 프로그램을 실행하세요. 실행 후 *ActiveXButton.docx*를 열어 버튼 캡션이 **Click Me**인지 확인합니다.

## 배운 내용 요약

* Aspose.Words를 사용하여 ActiveX 버튼에 **set button text**하는 방법을 배웠습니다.  
* **how to insert button**, **create button control**, 그리고 **add activex control**을 Word 문서에 적용하는 정확한 단계를 확인했습니다.  
* 이제 어떤 폼 기반 Word 자동화 프로젝트에도 적용할 수 있는 재사용 가능한 코드 스니펫을 보유하게 되었습니다.

## 다음 단계

* `CHECKBOX` 또는 `LISTBOX`와 같은 다른 `Forms2OleControlType` 값을 탐색하여 보다 풍부한 폼을 구축하세요.  
* 버튼을 VBA 매크로와 결합해 계산이나 데이터 검증을 수행하세요.  
* 문서가 작성된 후 사용자 입력을 읽기 위해 Aspose.Words의 `FormField` API를 사용하세요.

크기, 위치, 캡션을 자유롭게 실험하여 디자인 요구사항에 맞추세요. 문제가 발생하면, Aspose.Words 문서에서 이 튜토리얼에 사용된 모든 클래스에 대한 자세한 참고 자료를 확인할 수 있습니다.

코딩 즐겁게 하세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words로 빈 워드 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Aspose.Words로 워드에서 도형에 그림자 추가 – 단계별](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Aspose.Words for .NET을 사용하여 워드 문서 바닥글에 페이지 번호 추가](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}