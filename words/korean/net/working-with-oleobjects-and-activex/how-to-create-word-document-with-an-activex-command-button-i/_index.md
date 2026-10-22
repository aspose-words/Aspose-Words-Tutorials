---
category: general
date: 2026-09-05
description: Aspose.Words C#를 사용하여 Word 문서를 만들고 ActiveX 명령 버튼을 삽입하고 버튼 크기를 설정하며 인터랙티브
  버튼 기능을 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: ko
lastmod: 2026-09-05
og_description: C#에서 Word 문서를 생성하고 ActiveX 명령 버튼을 삽입합니다. 이 튜토리얼에서는 버튼 크기를 설정하고 인터랙티브한
  버튼 기능을 추가하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: C#에서 ActiveX 명령 버튼을 사용하여 Word 문서 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: C#에서 ActiveX 명령 버튼이 포함된 Word 문서 만드는 방법
url: /ko/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 ActiveX 명령 버튼으로 Word 문서 만들기

프로그래밍 방식으로 **Word 문서**를 만들고 클릭 가능한 UI 요소를 삽입해야 한다면, 이 가이드는 정확한 방법을 보여줍니다. Aspose.Words for .NET을 사용하면 **Word 문서**를 **생성하고**, **명령 버튼을 추가**하며, 외관을 제어할 수 있습니다—Microsoft Word를 열 필요 없이.

**ActiveX** 컨트롤을 삽입하는 방법, **버튼 크기 설정** 방법, 그리고 버튼을 인터랙티브 UI 구성 요소처럼 동작하게 만드는 방법을 배웁니다. COM이나 VBA에 대한 사전 경험은 필요 없으며, .NET 개발 환경과 Aspose.Words 라이브러리만 있으면 됩니다.

## 달성 목표

* **C#로 처음부터 Word 문서**를 생성합니다.
* **ActiveX 명령 버튼**을 삽입합니다 (클래식 “Click Me” 컨트롤).
* **버튼 크기**와 위치를 정확히 설정합니다.
* 선택적으로 간단한 **인터랙티브 버튼** 로직을 추가합니다 (예: 매크로 자리표시자).
* 파일을 `.docx` 형식으로 저장하여 Microsoft Word 또는 호환 뷰어에서 열 수 있습니다.

### 전제 조건

| 요구 사항 | 이유 |
|-------------|--------|
| .NET 6.0 or later | C# 코드 실행을 위한 런타임을 제공합니다. |
| Aspose.Words for .NET (latest version) | `Document`, `DocumentBuilder`, 및 `Forms2OleControl` API를 제공하여 예제에 사용됩니다. |
| Visual Studio 2022 (or any C# IDE) | 샘플을 쉽게 컴파일하고 실행할 수 있게 해줍니다. |
| Basic C# knowledge | 코드 흐름을 이해하는 데 필요합니다. |

> **팁:** Aspose.Words 체험판을 사용하는 경우, 평가 워터마크가 표시되지 않도록 코드를 실행하기 전에 라이선스를 설정하십시오.

## Word 문서 만들기 – 전체 워크플로우

프로세스는 네 가지 논리적 단계로 구성됩니다:

1. **새 문서**를 초기화하고 편집을 위한 `DocumentBuilder`를 생성합니다.  
2. `InsertForms2OleControl`을 사용하여 **ActiveX 명령 버튼**을 삽입합니다.  
3. **버튼 구성** – 캡션, 크기, 위치.  
4. **문서 저장**을 디스크에 수행합니다.

각 단계는 아래 섹션에서 자세히 설명합니다.

![Word document with an ActiveX button](/images/activex-button.png "Screenshot of a Word document that contains an ActiveX command button created with C#")

## ActiveX 명령 버튼 삽입 방법

**ActiveX 삽입 방법**은 `InsertForms2OleControl` 메서드로 시작합니다. 이 메서드는 Word가 ActiveX 객체로 인식하는 COM 기반 컨트롤을 생성합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**왜 작동하는가:** `OleControlType.CommandButton`은 Aspose.Words에 클래식 VB‑스타일 버튼을 만들도록 지시합니다. 크기와 위치는 포인트(1 포인트 = 1/72 인치) 단위로 표현되어 레이아웃을 정밀하게 제어할 수 있습니다.

## 명령 버튼 추가 및 버튼 크기 설정

컨트롤을 삽입한 후 시각적 속성을 조정할 수 있습니다. **명령 버튼 추가** 단계에서는 **버튼 크기 설정**도 다룹니다.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explanation:**  

* `Caption`은 버튼에 표시되는 레이블입니다.  
* `Width`와 `Height`는 초기 삽입 후 **버튼 크기 설정**을 가능하게 하며, 런타임 데이터에 따라 크기가 달라질 때 유용합니다.  
* `Left`와 `Top`은 문서를 다시 만들지 않고 컨트롤의 위치를 재조정합니다.

> **일반적인 실수:** 픽셀 대신 포인트를 사용하지 않으면 버튼이 너무 작거나 크게 표시됩니다. 화면 측정값에서 시작할 경우 항상 픽셀 값을 (`px * 72 / DPI`) 변환하십시오.

## 인터랙티브 버튼 추가 (옵션)

ActiveX 버튼은 클릭 시 매크로를 실행할 수 있지만, C#에서 VBA 코드를 삽입하는 것은 순수 Aspose.Words 워크플로우의 범위를 벗어납니다. 대신 Word가 매크로 이름으로 인식하는 자리표시자 속성을 추가할 수 있습니다.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

사용자가 생성된 `.docx` 파일을 Word에서 열면, 버튼을 클릭했을 때 `MyMacroName` 매크로 실행을 시도합니다. 매크로가 존재하지 않으면 Word가 사용자가 매크로를 만들도록 안내합니다.

**왜 사용할 수 있나요:** 매크로가 필드를 채우는 기업 양식 등에서, C# 코드는 버튼만 배치하면 되고 매크로 로직은 문서의 VBA 프로젝트에 존재합니다.

## 문서 저장 및 결과 확인

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**예상 출력:** Microsoft Word에서 `CommandButton.docx`를 열면 왼쪽 여백에서 100 pts, 위쪽에서 120 pts 떨어진 위치에 **Click Me** 라벨이 붙은 버튼이 표시됩니다. 버튼 크기는 **200 pts × 80 pts**입니다. 버튼을 클릭하면 매크로 자리표시자가 실행됩니다 (존재하는 경우).

## 전체 작업 예제

아래는 모든 내용을 통합한 완전한 실행 가능한 프로그램입니다. 새 콘솔 앱 프로젝트에 복사하고, Aspose.Words NuGet 패키지를 추가한 뒤 실행하십시오.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

프로그램을 실행하고 생성된 파일을 열면, 추가 커스터마이징을 위해 준비된 **인터랙티브 버튼**을 확인할 수 있습니다.

## 자주 묻는 질문

| 질문 | 답변 |
|----------|--------|
| **Does this work with .NET Core?** | 예. Aspose.Words는 .NET Standard를 지원하므로 동일한 코드를 .NET 5/6/7에서도 실행할 수 있습니다. |
| **Can I use other ActiveX controls (e.g., CheckBox)?** | 물론 가능합니다. `OleControlType.CommandButton`을 `OleControlType.CheckBox`, `OleControlType.OptionButton` 등으로 교체하면 됩니다. |
| **What if I need a larger button on a landscape page?** | `Width`, `Height`, `Left`, `Top` 속성을 비례적으로 조정하십시오. 페이지 방향에 관계없이 포인트는 동일하게 유지됩니다. |
| **Is a macro required for the button to be clickable?** | 아니요. 버튼은 UI 요소로서 완전히 동작하며, 매크로는 클릭 시 사용자 정의 동작을 추가할 뿐입니다. |

## 결론

이제 Aspose.Words를 사용하여 **Word 문서**를 **생성하고**, **명령 버튼을 추가**하며, **버튼 크기를 설정**하고, 필요에 따라 버튼을 매크로와 연결하여 **인터랙티브 버튼** 동작을 구현하는 방법을 알게 되었습니다. 이 방법을 통해 양식 생성 자동화, 동적 보고서 생성, 또는 C#에서 직접 Word 기반 UI 프로토타입을 구축할 수 있습니다.

다음에 탐색해 볼 내용:

* **설문 양식을 위한 ActiveX 체크 박스 삽입 방법**  
* `DocumentBuilder`를 사용하여 버튼 주변에 풍부한 텍스트 콘텐츠 추가 방법  
* 버튼 기능을 유지하면서 문서를 보호하는 방법  

다양한 컨트롤 유형, 크기, 매크로 이름을 실험하여 특정 시나리오에 맞게 적용해 보세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}