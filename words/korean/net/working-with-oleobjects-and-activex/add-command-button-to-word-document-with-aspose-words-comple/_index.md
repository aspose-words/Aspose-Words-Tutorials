---
category: general
date: 2026-07-29
description: Aspose.Words를 사용하여 워드 문서에 명령 버튼을 추가합니다. 몇 가지 간단한 단계로 ActiveX 컨트롤 속성을
  설정하고 명령 버튼 캡션을 지정하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: ko
lastmod: 2026-07-29
og_description: Aspose.Words를 사용하여 워드 문서에 명령 버튼을 추가합니다. 이 튜토리얼에서는 ActiveX 컨트롤 속성을
  설정하고 명령 버튼 캡션을 빠르게 설정하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Word 문서에 명령 버튼 추가 – Aspose.Words 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Aspose.Words를 사용하여 Word 문서에 명령 버튼 추가 – 완전 가이드
url: /ko/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 명령 버튼 추가 – 완전한 프로그래밍 워크스루

Word 문서에 **명령 버튼을 추가**해야 하는데 어떤 API 호출을 사용해야 할지 몰라 고민한 적 있나요? 혼자가 아닙니다. 많은 개발자들이 DOCX 파일에 인터랙티브 컨트롤을 삽입하려고 할 때 이 장벽에 부딪힙니다. 좋은 소식은 Aspose.Words를 사용하면 이 과정이 놀라울 정도로 간단하다는 점입니다. 이 가이드에서는 CommandButton ActiveX 컨트롤을 생성하고, **ActiveX 컨트롤 속성을 설정**하며, **명령 버튼 캡션을 설정**하는 방법을 깔끔한 C# 코드와 함께 단계별로 살펴보겠습니다. 코드를 복사‑붙여넣기만 하면 바로 사용할 수 있습니다.

이 튜토리얼을 마치면 클릭 가능한 “Submit” 버튼이 포함된 완전한 Word 파일을 얻을 수 있으며, Microsoft Word에서 바로 열 수 있습니다. 외부 VBA 스크립트도 없고, 수동 UI 조작도 필요 없습니다—오직 순수 프로그래밍 방식만 사용합니다.

## 배울 내용

* 빈 Word 문서와 `DocumentBuilder`를 만드는 방법
* Aspose.Words를 사용해 **Word 문서에 명령 버튼을 추가**하는 정확한 메서드 호출
* 크기, 위치, 이름 등 **ActiveX 컨트롤 속성을 설정**하는 방법
* 버튼에 원하는 텍스트가 표시되도록 **명령 버튼 캡션을 설정**하는 올바른 기법
* 다양한 버튼 유형, DPI 스케일링, Word 버전 호환성 등 엣지 케이스 처리 팁

> **전제 조건:** Aspose.Words for .NET이 설치된 Visual Studio(또는 기타 C# IDE) (NuGet 패키지 `Aspose.Words`). ActiveX 경험은 필요 없습니다.

---

## 1단계: 프로젝트 설정 및 네임스페이스 가져오기

**Word 문서에 명령 버튼을 추가**하려면 Aspose.Words를 참조하는 C# 프로젝트가 필요합니다. 새 .NET 콘솔 앱을 만든 뒤 NuGet 패키지를 추가하세요:

```bash
dotnet add package Aspose.Words
```

그런 다음 소스 파일에 필요한 네임스페이스를 가져옵니다:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

이 세 개의 `using` 지시문을 통해 `Document`, `DocumentBuilder`, 그리고 ActiveX 삽입을 담당하는 `Forms2OleControl` 클래스를 사용할 수 있습니다.

*팁:* Visual Studio를 사용한다면 클래스 이름을 입력할 때 IDE가 자동으로 `using`을 제안해 줍니다.

---

## 2단계: 빈 문서와 Builder 만들기

새로운 `Document` 객체는 빈 Word 파일을 나타냅니다. `DocumentBuilder`는 텍스트를 삽입하고, 그림을 그리며—특히—ActiveX 컨트롤을 배치할 수 있는 편리한 “펜” 역할을 합니다.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

이 시점에서 문서는 아직 아무것도 없는 캔버스이며, 마치 명령 버튼을 기다리는 깨끗한 종이와 같습니다.

---

## 3단계: CommandButton ActiveX 컨트롤 삽입

이제 **Word 문서에 명령 버튼을 추가**합니다. Aspose.Words는 `InsertForms2OleControl` 메서드를 제공하며, 여기서는 컨트롤 유형과 크기를 지정합니다. `Forms2OleControlType.CommandButton`을 사용하고 가로 150포인트, 세로 30포인트의 크기를 지정합니다.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

이 메서드는 `Forms2OleControl` 인스턴스를 반환하며, 다음 단계에서 **ActiveX 컨트롤 속성을 설정**하는 데 사용됩니다.

---

## 4단계: 컨트롤 구성 – 이름, 캡션, 위치

### 캡션 설정

캡션은 버튼에 표시되는 텍스트입니다. **명령 버튼 캡션을 설정**하려면 `Caption` 속성에 문자열을 할당하면 됩니다:

```csharp
commandButton.Caption = "Submit";
```

`"Submit"`을 원하는 텍스트(예: “Save”, “Export”, “Launch” 등)로 바꾸면 Word에 정확히 그 텍스트가 표시됩니다.

### 컨트롤 이름 지정

컨트롤에 의미 있는 이름을 부여하면 나중에(예: Word 매크로 자동화 시) 참조하기가 쉬워집니다. `Name` 속성을 설정합니다:

```csharp
commandButton.Name = "btnSubmit";
```

### 페이지 내 위치 지정

Word는 레이아웃에 포인트(인치의 1/72)를 사용합니다. `Left`와 `Top` 속성을 조정해 버튼을 원하는 위치에 배치합니다:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

단락에 상대적으로 버튼을 정렬하려면 먼저 Builder 커서를 이동한 뒤 컨트롤을 삽입하면, 좌표가 해당 위치를 기준으로 적용됩니다.

*엣지 케이스:* 고 DPI 모니터에서는 Word에서 시각적인 크기가 약간 다르게 보일 수 있습니다. 장치 간 물리적 크기를 일관되게 유지하려면 목표 DPI(보통 Word는 96 DPI)를 기준으로 포인트를 계산하세요.

---

## 5단계: 문서 저장

버튼 구성이 완료되면 파일 저장은 한 줄로 끝납니다:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

생성된 `CommandButton.docx` 파일에는 완전한 ActiveX 버튼이 들어 있습니다. Microsoft Word에서 열면 삽입한 위치에 “Submit” 버튼이 정확히 표시됩니다.

### 기대 결과

1. Word 문서가 한 페이지로 열립니다.  
2. 지정한 좌표에 **Submit**이라는 레이블이 붙은 사각형 버튼이 나타납니다.  
3. 버튼을 오른쪽 클릭하고 **Properties**를 선택하면 `btnSubmit`이라는 이름과 설정한 기타 속성을 확인할 수 있습니다.

---

## 6단계: 고급 변형 및 흔히 발생하는 문제

### 다른 ActiveX 유형 삽입

`InsertForms2OleControl` 메서드는 명령 버튼에만 국한되지 않습니다. 체크 박스, 옵션 버튼, 혹은 사용자 정의 ActiveX 객체도 삽입할 수 있습니다:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

동일한 **ActiveX 컨트롤 속성을 설정** 패턴을 사용하되, 타입 열거형만 교체하면 됩니다.

### Word 버전 호환성

구버전 Word(2007 이전)는 이진 `.doc` 형식을 사용하며, ActiveX 컨트롤을 저장하는 방식이 다릅니다. Aspose.Words는 `.doc`로 저장할 때 자동으로 컨트롤을 변환하지만, 정확한 위치와 같은 일부 속성은 약간 이동될 수 있습니다. 레거시 형식을 목표로 한다면 해당 Word 버전에서 출력물을 반드시 테스트하세요.

### 보안 설정

보안 매크로 설정이 엄격한 환경에서는 Word가 ActiveX 컨트롤을 비활성화할 수 있습니다. “Security Warning” 대화 상자를 피하려면 다음을 고려하세요:

* 신뢰할 수 있는 인증서로 문서 서명  
* 사용자에게 해당 파일 위치에 대해 ActiveX 콘텐츠를 활성화하도록 안내  
* 보안이 우려되는 경우 매크로 없이 구현 가능한 콘텐츠 컨트롤(예: 일반 컨텐츠 컨트롤) 사용

---

## 7단계: 전체 작업 예제

아래는 지금까지 설명한 모든 단계를 포함한 완전한 실행 가능한 프로그램입니다. `Program.cs`에 복사하고, 필요에 따라 출력 경로를 수정한 뒤 **Run**을 눌러 보세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**코드 설명**

* 새 문서 생성  
* 명령 버튼 삽입, **ActiveX 컨트롤 속성을 설정** 및 **명령 버튼 캡션을 설정**  
* 간단한 설명 문단 추가  
* `CommandButton.docx` 파일로 저장  

프로그램을 실행하고 생성된 파일을 열면 설명 텍스트 아래에 버튼이 배치된 것을 확인할 수 있습니다.

---

## 결론

이번 튜토리얼을 통해 Aspose.Words를 사용해 **Word 문서에 명령 버튼을 추가**, **ActiveX 컨트롤 속성을 설정**, 그리고 **명령 버튼 캡션을 설정**하는 방법을 간결하고 실무에 바로 적용 가능한 C# 코드와 함께 살펴보았습니다. 이 접근 방식은 확장성이 뛰어나며, 컨트롤 유형을 바꾸거나 크기를 조정하고, 데이터 소스를 순회하면서 수십 개의 버튼을 자동으로 삽입하는 등 다양한 시나리오에 적용할 수 있습니다.

다음 단계로 시도해 볼 내용:

* 버튼을 매크로와 연결해 데이터 내보내기 트리거  
* `Picture` 속성을 사용해 버튼 안에 이미지나 커스텀 아이콘 삽입  
* 텍스트 박스, 콤보 박스 등 여러 ActiveX 컨트롤을 조합해 전체 폼 구축  

실험을 통해 Word 자동화에 익숙해지는 것이 가장 좋은 학습 방법입니다. 문제가 발생하면 DPI 계산과 Word 보안 설정을 다시 한 번 점검해 보세요. 즐거운 코딩 되시고, 문서가 더욱 인터랙티브해지길 바랍니다!

## 다음에 배울 내용

다음 튜토리얼들은 이번 가이드에서 다룬 기술을 확장하고, 추가 API 기능을 마스터하며, 프로젝트에 다양한 구현 방식을 적용할 수 있도록 도와줍니다.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}