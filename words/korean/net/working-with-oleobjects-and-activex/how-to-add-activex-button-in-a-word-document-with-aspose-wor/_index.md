---
category: general
date: 2026-08-14
description: Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼 추가하기 – 빈 Word 문서를 생성하고 프로그래밍 방식으로
  ActiveX 버튼을 삽입하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: ko
lastmod: 2026-08-14
og_description: Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼을 추가하는 방법. 이 튜토리얼에서는 빈 Word
  문서를 만들고, ActiveX 버튼을 삽입한 다음 결과를 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Word에 ActiveX 버튼 추가 방법 – Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼 추가하는 방법
url: /ko/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼 추가하는 방법

생성된 Word 파일에 **ActiveX** 컨트롤을 **추가하는 방법**이 필요하다면, 이 가이드는 정확한 단계를 보여줍니다. **ActiveX 버튼 삽입**을 프로그래밍 방식으로 수행하는 방법을 배우게 되며, **빈 Word 문서 만들기**부터 Microsoft Word에서 열 수 있는 파일 저장까지 다룹니다.

VBA 코드를 실행하거나 매크로를 트리거하는 버튼을 추가하는 것은 자동 보고서 생성기, 양식 템플릿, 인터랙티브 계약서 등에서 흔히 요구되는 기능입니다. Aspose.Words for .NET을 사용하면 Office를 실행하지 않고도 문서를 만들 수 있어 빠르고 서버 친화적인 프로세스를 유지할 수 있습니다.

## Prerequisites

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 (또는 이후 버전) SDK
* Visual Studio 2022 또는 C#을 지원하는 IDE
* Aspose.Words for .NET NuGet 패키지(`Aspose.Words` 버전 24.9 이상)  
  설치 방법:
  ```bash
  dotnet add package Aspose.Words
  ```
* ActiveX 버튼을 테스트하려면 Windows 환경이 필요합니다. ActiveX 컨트롤은 Microsoft Word의 Windows 버전에서만 작동합니다.

## Step 1: Create an empty Word document

첫 번째 작업은 메모리 내에 **빈 Word 문서 만들기**입니다. Aspose.Words는 이를 위해 `Document` 클래스를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document`는 전체 .docx 파일을 나타냅니다. 현재 문서에는 페이지가 없지만 바로 콘텐츠를 추가할 수 있습니다.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder`는 텍스트, 이미지 및 기타 객체를 문서에 삽입할 수 있게 도와주는 헬퍼입니다. 방금 만든 `Document` 인스턴스에서 작동합니다.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

빌더는 커서 위치를 유지합니다; 이 라인 이후에 삽입되는 모든 내용은 첫 페이지 시작 부분에 나타납니다.

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words는 레거시 폼 컨트롤(ActiveX 포함)을 추가하기 위해 `InsertForms2OleControl` 메서드를 제공합니다. 이 메서드에는 컨트롤 유형과 크기(포인트 단위)가 필요합니다.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

반환된 `Forms2OleControl` 객체를 사용해 컨트롤의 이름 및 캡션과 같은 속성을 구성할 수 있습니다.

## Step 4: Configure the button’s properties

의미 있는 `Name`을 설정하면 나중에 VBA 코드에서 해당 컨트롤을 참조할 수 있습니다. `Caption`은 사용자가 버튼에서 보는 텍스트입니다.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** 이름은 짧고 영숫자로만 구성하세요; Word는 공백이나 특수 문자가 포함된 이름을 거부합니다.

## Step 5: Save the document

마지막으로 문서를 디스크에 저장합니다. 최신 Word 파일은 `.docx` 확장자를 사용하세요; ActiveX 버튼은 `.doc` 파일에서도 동일하게 동작하지만, 새 프로젝트에서는 `.docx`가 권장됩니다.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

`ActiveXButton.docx`를 Microsoft Word에서 열면 클릭 가능한 **Submit** 버튼이 표시됩니다. 매크로를 활성화하면 `btnSubmit_Click`에 VBA 코드를 연결해 사용자가 버튼을 클릭했을 때 실행되도록 할 수 있습니다.

## Full, runnable example

모든 요소를 합치면 복사·붙여넣기·실행이 가능한 독립형 프로그램이 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**예상 출력** – 프로그램 실행 후 콘솔에 저장 위치가 출력되고, 생성된 파일을 Word에서 열면 첫 페이지 상단에 **Submit**이라는 레이블이 붙은 버튼이 표시됩니다.

## Handling common questions and edge cases

### Does the button work in all Word versions?

ActiveX 컨트롤은 Windows용 데스크톱 Word에서 지원됩니다. Word Online, macOS용 Word, 모바일 클라이언트에서는 렌더링되지 않습니다. 크로스 플랫폼 인터랙티브가 필요하면 콘텐츠 컨트롤이나 HTML 기반 솔루션을 고려하세요.

### What if I need a different size or position?

`InsertForms2OleControl`은 현재 빌더 커서 위치에 컨트롤을 배치합니다. 위치를 변경하려면 삽입 전에 `builder.MoveTo`로 커서를 조정하거나, 생성 후 컨트롤의 `Left` 및 `Top` 속성을 수정하세요:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Can I add other ActiveX types?

예. `Forms2OleControlType` 열거형에는 `CheckBox`, `OptionButton`, `ListBox` 등 다양한 타입이 포함됩니다. `CommandButton`을 원하는 열거값으로 교체하고 속성을 적절히 조정하면 됩니다.

### Is a macro required for the button to do something?

버튼 자체는 VBA 코드를 연결하기 전까지 아무 동작도 하지 않습니다. Word에서 **Alt+F11**을 눌러 VBA 편집기를 열고 `btnSubmit_Click`를 찾아 원하는 로직을 작성하세요. VBA 프로젝트를 보존하려면 **SaveFormat.Doc**(레거시 `.doc`) 형식으로 저장해야 하며, `.docx` 파일은 VBA 매크로를 저장할 수 없습니다. 매크로가 필요하면 `.doc` 형식을 사용하세요.

## Conclusion

이제 Aspose.Words를 사용해 Word 파일에 **ActiveX 컨트롤을 추가하는 방법**을 알게 되었습니다. **빈 Word 문서 만들기**, `DocumentBuilder` 초기화, **ActiveX 버튼 삽입**, 속성 구성, 파일 저장 순서를 따라 하면 .NET 코드만으로 인터랙티브 Word 템플릿을 직접 생성할 수 있습니다.

다음 단계로 **ActiveX 버튼 이벤트 처리**, 표나 이미지 삽입을 위한 **create word document aspose**, 매크로가 포함된 문서의 보안 등 관련 주제를 탐색해 보세요. 다양한 컨트롤 타입과 레이아웃 옵션을 실험해 애플리케이션 요구에 맞는 사용자 경험을 설계해 보시기 바랍니다.

Happy coding!


## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있도록 돕습니다.

- [Aspose.Words를 사용하여 머리글 및 바닥글이 있는 Word 문서 만들기](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words를 사용하여 표가 포함된 Word 문서 만들기](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}