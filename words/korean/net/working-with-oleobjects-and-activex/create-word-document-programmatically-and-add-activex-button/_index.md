---
category: general
date: 2026-08-10
description: Aspose.Words를 사용해 프로그래밍 방식으로 워드 문서를 만든 다음, ActiveX 컨트롤 워드 버튼을 추가합니다.
  몇 분 안에 ActiveX 명령 버튼을 삽입하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: ko
lastmod: 2026-08-10
og_description: Aspose.Words를 사용해 프로그래밍으로 워드 문서를 만들고, ActiveX 컨트롤 워드 버튼을 추가합니다. ActiveX
  명령 버튼을 빠르게 삽입하는 방법을 배워보세요.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: 프로그램으로 워드 문서 만들기 – C#에서 ActiveX 버튼 추가
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: 워드 문서를 프로그래밍 방식으로 생성하고 ActiveX 버튼을 추가
url: /ko/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 프로그래밍 방식으로 Word 문서 만들기 및 ActiveX 버튼 추가

If you need to **프로그래밍 방식으로 Word 문서 생성**, this guide walks you through the entire process with Aspose.Words for .NET. You’ll also learn how to **ActiveX 컨트롤 Word 요소 추가** and **ActiveX 커맨드 버튼 삽입** objects in a single, self‑contained example.

코드에서 Word 파일을 생성하면 Microsoft Word를 수동으로 여는 단계를 없앨 수 있어 보고서, 청구서 또는 데이터 기반 계약서를 자동으로 만들 수 있습니다. 이 튜토리얼을 마치면 인터랙티브한 ActiveX CommandButton이 포함된 `.docx` 파일을 생성하는 C# 콘솔 앱을 바로 실행할 수 있게 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 SDK 이상 (코드는 .NET Framework 4.6+에서도 작동합니다)
* Visual Studio 2022 또는 .NET 개발을 지원하는 IDE
* 유효한 Aspose.Words for .NET 라이선스 (테스트용 무료 평가 키 사용 가능)
* C# 문법 및 COM/ActiveX 컨트롤 개념에 대한 기본 지식

> **Pro tip:** Word가 설치되지 않은 사용자에게 생성된 문서를 배포하려는 경우, ActiveX 컨트롤 런타임 파일을 `.docx`와 함께 포함하거나 매크로 사용 가능한 템플릿을 제공하세요.

## Create word document programmatically – initial setup

먼저 프로젝트에 Aspose.Words NuGet 패키지를 추가합니다:

```bash
dotnet add package Aspose.Words
```

그 다음, 아직 프로젝트가 없으면 새 콘솔 프로젝트를 생성합니다:

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

생성된 `Program.cs` 파일을 열고, 아래 전체 솔루션으로 내용을 교체합니다.

## Step 1: Import namespaces and configure the license

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Why this matters*: Importing `Aspose.Words.Drawing` gives you access to `Forms2OleControl`, the class that represents an ActiveX control inside a Word document. Setting a license early prevents runtime warnings in production.

*왜 중요한가*: `Aspose.Words.Drawing`을 가져오면 Word 문서 안의 ActiveX 컨트롤을 나타내는 `Forms2OleControl` 클래스를 사용할 수 있습니다. 라이선스를 미리 설정하면 프로덕션 환경에서 런타임 경고가 발생하지 않습니다.

## Step 2: Create a blank document and a DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` object is the in‑memory representation of a `.docx` file. `DocumentBuilder` works like a cursor that you move around the document to insert elements.

`Document` 객체는 `.docx` 파일의 메모리 내 표현이며, `DocumentBuilder`는 문서 안을 이동하면서 요소를 삽입하는 커서와 같습니다.

## Step 3: Insert an ActiveX CommandButton control

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` creates an OLE object that Word treats as an ActiveX control. The coordinate system uses points (1 point = 1/72 inch), which matches Word’s layout engine.

`InsertForms2OleControl`은 Word가 ActiveX 컨트롤로 인식하는 OLE 객체를 생성합니다. 좌표계는 포인트 단위(1 point = 1/72 인치)를 사용하므로 Word 레이아웃 엔진과 일치합니다.

## Step 4: Set the button’s caption and optional properties

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Setting the `Caption` property is the most common way to label the button. If you need the button to execute a VBA macro, assign the macro name to `OnAction`. This tutorial focuses on the visual part; macro integration is covered in the “Next steps” section.

`Caption` 속성을 설정하면 버튼에 라벨을 지정할 수 있습니다. 버튼이 VBA 매크로를 실행하도록 하려면 매크로 이름을 `OnAction`에 할당하면 됩니다. 이 튜토리얼은 시각적 부분에 초점을 맞추며, 매크로 통합은 “다음 단계” 섹션에서 다룹니다.

## Step 5: Save the document

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

When you run the program, you’ll see a console message confirming that `ActiveX_CommandButton.docx` has been written to disk.

프로그램을 실행하면 `ActiveX_CommandButton.docx` 파일이 디스크에 저장되었다는 콘솔 메시지가 표시됩니다.

### Full source code (copy‑paste ready)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Running the snippet produces a Word file that contains a clickable **ActiveX command button**. Open the file in Microsoft Word, switch to **Design Mode** (Developer tab → Design Mode), and you’ll see the button rendered exactly where you placed it.

코드를 실행하면 클릭 가능한 **ActiveX 커맨드 버튼**이 포함된 Word 파일이 생성됩니다. Microsoft Word에서 파일을 열고 **디자인 모드**(개발자 탭 → 디자인 모드)로 전환하면 버튼이 배치한 위치에 정확히 표시됩니다.

## Step 6: Verify the result

1. Open `ActiveX_CommandButton.docx` in Microsoft Word.
2. Enable the **Developer** tab if it isn’t visible (`File → Options → Customize Ribbon → check Developer`).
3. Click **Design Mode**. The button should appear with the label “Submit”.
4. If you added an `OnAction` macro, click the button while Design Mode is off to trigger the macro.

If the button does not show, ensure that Word’s security settings allow ActiveX controls (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I insert other ActiveX types?** | Yes. `Forms2OleControlType` enum includes `CheckBox`, `OptionButton`, `ComboBox`, etc. Replace `CommandButton` with the desired enum value |

## What Should You Learn Next?

다음 튜토리얼에서는 이 가이드에서 다룬 기술을 기반으로 하여 관련 주제를 심도 있게 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 제공하므로 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words를 사용하여 헤더와 푸터가 있는 Word 문서 만들기](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words를 사용하여 Word 문서에 인라인 이미지 삽입](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}