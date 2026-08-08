---
category: general
date: 2026-08-07
description: C#를 사용하여 Word 문서에 ActiveX 컨트롤을 추가하는 방법을 배웁니다. 버튼에 매크로를 연결하고 클릭 가능한 버튼을
  추가하는 Word 예제가 포함됩니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: ko
lastmod: 2026-08-07
og_description: Aspose.Words를 사용하여 Word 문서에 ActiveX 컨트롤을 추가하는 방법. 이 가이드를 따라 버튼을 삽입하고,
  버튼에 매크로를 연결하며, 클릭 가능한 버튼을 추가하세요.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Word에 ActiveX 컨트롤 추가 방법 – 완전한 C# 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words를 사용하여 Word에 ActiveX 컨트롤을 추가하는 방법 – 단계별 가이드
url: /ko/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word에 ActiveX 컨트롤 추가하는 방법

Microsoft Word 파일에 프로그래밍 방식으로 **ActiveX 컨트롤 추가 방법**이 필요하다면, 이 튜토리얼에서는 Aspose.Words for .NET을 사용한 정확한 단계들을 보여줍니다. 명령 버튼을 삽입하고, 캡션을 설정하며, **버튼에 매크로 연결**을 통해 사용자가 클릭했을 때 컨트롤이 반응하도록 하는 방법을 확인할 수 있습니다. 최종적으로 완전한 기능을 갖춘 매크로 활성화 `.docm` 파일을 얻게 됩니다.

ActiveX 버튼을 추가하는 것은 대출 신청서, 직원 온보딩 양식, 자동 보고서와 같은 인터랙티브 템플릿을 만들 때 흔히 요구되는 작업입니다. 이 가이드는 코드의 모든 줄을 단계별로 살펴보고, 각 단계가 중요한 **이유**를 설명하며, 발생할 수 있는 일반적인 함정들을 다룹니다.

## 사전 요구 사항

* .NET 6 (또는 .NET Core 3.1 / .NET Framework 4.8)이 설치되어 있어야 합니다.
* 유효한 Aspose.Words for .NET 라이선스 또는 임시 평가 키가 필요합니다.
* Visual Studio 2022(또는 C#를 지원하는 기타 IDE).
* 버튼이 트리거할 매크로를 작성하려는 경우, Word 매크로(VBA)에 대한 기본적인 이해가 필요합니다.

> **팁:** 샘플을 실행할 때, 쓰기 권한이 있는 폴더에 출력물을 저장하세요. 그렇지 않으면 `doc.Save`가 예외를 발생시킵니다.

## Aspose.Words를 사용하여 Word 문서에 ActiveX 컨트롤 추가하는 방법

솔루션의 핵심은 새 문서를 만들고, ActiveX **CommandButton** 컨트롤을 삽입한 뒤, 매크로 활성화 문서(`.docm`)로 저장하는 짧은 C# 프로그램입니다. 코드는 완전하며 복사‑붙여넣기 바로 사용할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### 각 라인이 중요한 이유

| 줄 | 목적 |
|------|---------|
| `Document doc = new Document();` | 메모리 내에 새로운 Word 패키지를 인스턴스화합니다. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | ActiveX 컨트롤을 포함한 콘텐츠 삽입을 위한 유창한 API를 제공합니다. |
| `InsertForms2OleControl` | ActiveX 컨트롤을 생성하는 유일한 Aspose.Words 메서드이며, 컨트롤 유형(`CommandButton`)과 그 형태를 지정합니다. |
| `commandButton.Caption = "Click Me";` | 엔드유저가 보는 **클릭 가능한 버튼 텍스트**를 설정합니다. 캡션이 없으면 버튼이 빈 상태로 표시됩니다. |
| `commandButton.OnAction = "MyMacro";` | **버튼에 매크로 연결** – 컨트롤이 클릭될 때 실행할 VBA 매크로를 Word에 알려줍니다. |
| `doc.Save("CommandButton.docm");` | 문서를 매크로 활성화 파일로 저장합니다; 일반 `.docx`는 컨트롤과 매크로를 제거합니다. |

> **Note:** 좌표(왼쪽, 위)는 포인트 단위(1 pt ≈ 1/72 in)로 측정됩니다. 페이지에서 버튼을 원하는 위치에 배치하도록 조정하세요.

## 버튼에 매크로 연결하는 방법

`OnAction` 속성은 버튼을 `MyMacro`라는 VBA 매크로와 연결합니다. 해당 매크로는 Word 파일 안에 직접 만들거나 프로그래밍 방식으로 VBA 코드를 삽입해야 합니다(Aspose.Words는 VBA 코드를 작성하지 않습니다). 다음은 Word의 **Developer → Visual Basic** 편집기를 사용해 추가할 수 있는 최소 매크로입니다:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

사용자가 `CommandButton.docm`을 열고 버튼을 클릭하면 Word가 `MyMacro`를 실행하고 메시지 박스를 표시합니다. 매크로 보안이 **Disable all macros without notification**(알림 없이 모든 매크로 비활성화)으로 설정된 경우 버튼이 비활성화된 채로 나타납니다. 사용자에게 문서에 대한 매크로를 활성화하도록 안내하거나 신뢰할 수 있는 인증서로 매크로에 서명하도록 권장하세요.

### 매크로 연결 시 흔히 발생하는 함정

* **Macro security settings** – 문서가 보안 정책이 엄격한 컴퓨터에서 열릴 경우 매크로가 차단될 수 있습니다. 보안 수준을 낮추는 방법이나 매크로에 서명하는 방법을 안내하세요.
* **Naming conflicts** – 매크로 이름은 문서의 VBA 프로젝트 내에서 고유해야 하며, 그렇지 않으면 Word가 “duplicate procedure name”(중복 절차 이름) 오류를 발생시킵니다.
* **64‑bit vs 32‑bit Word** – ActiveX 컨트롤은 동일하게 작동하지만, VBA 편집기는 Office 버전에 따라 다른 경고 메시지를 표시할 수 있습니다.

## Word 양식에 클릭 가능한 버튼 텍스트 추가하기

`Caption` 속성은 사용자가 버튼에서 보는 텍스트입니다. 이를 더 커스터마이즈할 수 있습니다:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

사용자 입력에 따라 캡션을 동적으로 변경해야 하는 경우, 이후 Word 객체 모델을 통해 컨트롤에 접근할 수 있습니다:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### 경계 상황: 긴 캡션

Word는 버튼 너비를 초과하는 캡션을 잘라냅니다. 클리핑을 방지하려면 `InsertForms2OleControl`의 width 인수를 늘리거나 텍스트를 짧게 하세요. 문자 폭이 다른 언어(예: 독일어, 일본어)로 테스트하는 것이 좋습니다.

## 양식 자동화를 위한 명령 버튼 텍스트 추가하기

시각적 캡션을 넘어, **명령 버튼 텍스트** 개념은 컨트롤의 프로그래밍 이름을 의미합니다. Aspose.Words는 ActiveX 컨트롤에 대한 직접적인 `Name` 속성을 제공하지 않지만, `AltText` 필드를 설정하면 Word가 이를 컨트롤 식별자로 사용합니다:

```csharp
commandButton.AltText = "SubmitButton";
```

VBA에서는 이후 `AltText` 값을 사용해 버튼을 참조할 수 있습니다:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

이 기술은 여러 버튼이 있을 때 프로그래밍적으로 구분해야 할 경우에 유용합니다.

## 전체 작동 예제

아래는 콘솔 애플리케이션으로 컴파일하고 실행할 수 있는 전체 프로그램입니다. 선택적 스타일링, 매크로 연결 및 각 단계를 설명하는 주석 블록이 포함되어 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** Microsoft Word에서 `SubmitForm.docm`을 열면 파란색 테두리의 *Submit Form* 라벨이 붙은 버튼이 표시됩니다. 버튼을 클릭하면 VBA 매크로 `SubmitMacro`가 실행됩니다(문서에 매크로를 추가한 경우). 동일한 `Forms2OleControl` 객체를 사용해 버튼을 이동, 크기 조정 또는 추가 스타일링할 수 있습니다.

## 솔루션 테스트

1. C# 콘솔 앱을 빌드하고 실행합니다.
2. 생성된 `SubmitForm.docm`을 Word에서 엽니다.
3. 프롬프트가 나타나면 매크로를 활성화합니다.
4. *Submit Form* 버튼을 클릭합니다 – `SubmitMacro`에 정의된 메시지 박스가 표시됩니다.

버튼이 표시되지만 동작하지 않으면 매크로 이름이 정확히(`SubmitMacro`) 일치하는지와 매크로 보안이 실행을 차단하고 있지 않은지 다시 확인하세요.

## 자주 묻는 질문

| 질문 | 답변 |
|----------|--------|
| *ActiveX 버튼을 여러 개 추가할 수 있나요?* | 예. 서로 다른 좌표로 `InsertForms2OleControl`을 여러 번 호출하십시오. 서로 다른 `OnAction` 및 `AltText` 값을 사용해 구분할 수 있습니다. |
| *ActiveX 컨트롤이 Word Online에 표시됩니까?* | 아니요. |

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방법을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET에서 Document Builder를 사용하여 콘텐츠 추가하기](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow 튜토리얼 – C#에서 Word Shape에 그림자 추가](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Word 문서에 새 섹션 추가하기 | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}