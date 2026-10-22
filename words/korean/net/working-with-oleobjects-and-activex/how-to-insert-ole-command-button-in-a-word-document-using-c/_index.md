---
category: general
date: 2026-10-07
description: Aspose.Words C#를 사용하여 Word 문서에 OLE 명령 버튼을 삽입하는 방법을 배웁니다. DocumentBuilder,
  속성 및 파일 저장을 포함한 단계별 가이드.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: ko
lastmod: 2026-10-07
og_description: C#를 사용하여 Word 문서에 OLE 명령 버튼을 삽입합니다. 이 간결한 튜토리얼을 따라 Aspose.Words로 기능적인
  CommandButton을 추가, 구성 및 저장하세요.
og_image_alt: Insert OLE command button example in Word document
og_title: C#를 사용하여 Word에 OLE 명령 버튼 삽입 – 완전한 Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: C#를 사용하여 Word 문서에 OLE 명령 버튼 삽입하는 방법
url: /ko/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word 문서에 OLE 명령 버튼 삽입하기

프로그램matically Word 파일에 **OLE 명령 버튼**을 삽입해야 할 경우, 이 가이드는 Aspose.Words for .NET을 사용하여 정확히 수행하는 방법을 보여줍니다. 양식이 채워진 보고서를 만들거나 사용자 상호 작용이 필요한 템플릿을 자동화하려는 경우, 아래 단계는 완전하고 실행 가능한 솔루션을 제공합니다.

빈 문서를 만들고, `DocumentBuilder`를 사용해 `Forms2OleControl`을 배치하고, 버튼의 캡션과 이름을 설정한 뒤, 최종적으로 `.docx`로 저장하는 방법을 배웁니다. Aspose.Words 라이브러리 외에 별도의 도구는 필요하지 않습니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 이상 (.NET Framework 4.7+에서도 작동)
* 유효한 Aspose.Words for .NET 라이선스 또는 무료 평가 키
* Visual Studio 2022 (또는 선호하는 C# IDE)
* C# 문법 및 Word OLE 개념에 대한 기본 지식

> **Pro tip:** 무료 평가판을 사용하는 경우, 생성된 문서에 작은 워터마크가 포함됩니다. 라이선스 버전은 자동으로 워터마크를 제거합니다.

## Step 1: Install Aspose.Words

NuGet을 통해 Aspose.Words 패키지를 프로젝트에 추가합니다:

```bash
dotnet add package Aspose.Words
```

패키지에는 OLE 컨트롤에 필요한 `Aspose.Words.Drawing` 및 `Aspose.Words.Drawing.Ole` 네임스페이스가 포함됩니다.

## Step 2: Insert OLE command button with DocumentBuilder

튜토리얼의 핵심은 `InsertForms2OleControl` 메서드입니다. 이 메서드는 특정 위치와 크기로 **Forms2 OLE CommandButton**을 생성합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Why this works

* `DocumentBuilder`는 Word 문서를 프로그래밍 방식으로 구축하기 위한 기본 API입니다.  
* `InsertForms2OleControl`은 Aspose.Words에 **Forms2 OLE 컨트롤**을 삽입하도록 지시합니다. 이는 명령 버튼, 체크 박스 등을 지원하는 레거시 Word 양식 기술입니다.  
* `OleControlType.CommandButton` 열거형 값은 삽입되는 컨트롤이 **명령 버튼**임을 지정합니다—즉, **OLE 명령 버튼 삽입**을 원할 때 정확히 필요한 타입입니다.  
* `Rectangle`은 시각적 배치를 결정합니다. 레이아웃에 맞게 X/Y 좌표 또는 너비/높이를 조정하세요.

## Step 3: Save the document

버튼 구성을 마친 후, 문서를 디스크에 저장합니다. Aspose.Words가 지원하는 모든 형식(`.docx`, `.pdf`, `.odt`, …) 중 원하는 것을 선택할 수 있습니다. 이 튜토리얼에서는 Word 문서로 저장합니다.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`CommandButton.docx`를 Microsoft Word에서 열면 **Click Me**라는 레이블이 붙은 클릭 가능한 버튼이 표시됩니다. Word에서 버튼을 누르면 기본 “Run Macro” 대화 상자가 나타나는데, 이는 버튼이 OLE 양식 컨트롤이기 때문이며 필요에 따라 매크로나 VBA 코드를 나중에 연결할 수 있습니다.

## Step 4: Verify the result (expected output)

생성된 파일을 열어 확인합니다:

1. 버튼이 지정한 좌표(대략 페이지 왼쪽 및 위쪽에서 1.4 인치) 에 나타납니다.  
2. 캡션은 **Click Me** 로 표시됩니다.  
3. 이름 속성(`cmdSubmit`)은 Word의 **Developer → Properties** 창에 표시되며, VBA에서 컨트롤을 참조할 때 유용합니다.

![Insert OLE command button example in Word document](insert-ole-button.png)

*Image alt text*: **Word 문서에 OLE 명령 버튼 삽입 예시** (접근성 및 SEO를 위한 주요 키워드 포함).

## Edge Cases & Common Questions

### 1. What if the button does not appear where I expect?

* Word는 픽셀이 아니라 포인트를 사용합니다. 화면 픽셀을 포인트로 변환하려면 `points = pixels * 72 / DPI` 를 사용하세요.  
* 사각형이 페이지 여백과 겹치지 않도록 하세요; 겹치면 Word가 컨트롤을 이동시킬 수 있습니다.

### 2. Can I insert the button into an existing document?

예. `new Document("Existing.docx")` 로 문서를 로드하고 동일한 `DocumentBuilder` 흐름을 사용하면 됩니다. `InsertForms2OleControl`을 호출하기 전에 빌더 커서를 이동(`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` 등)하는 것을 잊지 마세요.

### 3. How do I attach a macro to the button?

Aspose.Words는 VBA 코드를 생성하지 않지만, 문서가 생성된 후 매크로를 삽입할 수 있습니다:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Does this work with .NET Core on Linux?

OLE 컨트롤은 COM에 의존하는 Windows 전용 기능이므로 Linux에서는 버튼이 삽입되지만 인터랙티브 동작 없이 정적 이미지로 표시됩니다. 크로스 플랫폼 인터랙티브 양식을 원한다면 `StructuredDocumentTag`(콘텐츠 컨트롤) 사용을 고려하세요.

### 5. What if I need a different size or multiple buttons?

고유 좌표를 가진 추가 `Rectangle` 객체를 생성하고 `InsertForms2OleControl` 호출을 반복하면 됩니다. 각 버튼마다 별도의 `Caption`과 `Name`을 지정할 수 있습니다.

## Full Working Example

아래는 콘솔 애플리케이션에 복사‑붙여넣기 할 수 있는 전체 프로그램 예시입니다. 필요한 `using` 지시문, 오류 처리 및 주석이 모두 포함되어 있습니다.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

프로그램을 실행하고 생성된 `CommandButton.docx`를 열면 **Click Me** 버튼이 표시되어 추가 커스터마이징이 가능합니다.

## Conclusion

이제 C#와 Aspose.Words를 사용해 Word 문서에 **OLE 명령 버튼**을 삽입하는 방법을 알게 되었습니다. 이번 튜토리얼에서는 다음을 다루었습니다:

* Aspose.Words 패키지 설치  
* `DocumentBuilder.InsertForms2OleControl`와 `OleControlType.CommandButton` 사용  
* 버튼 속성(`Caption`, `Name`) 설정  
* 저장 및 결과 검증  

이후에는 체크 박스, 콤보 박스와 같은 **Aspose.Words OLE 컨트롤**이나 전체 Excel 워크시트 삽입 등 관련 주제를 탐색할 수 있습니다. 더 큰 템플릿에서 **Word OLE 명령 버튼** 자동화를 시도하거나, 크로스‑플랫폼 지원을 위해 최신 **콘텐츠 컨트롤**로 교체하는 것도 좋은 방법입니다.

사각형 값 조정, 다중 버튼 추가, VBA 매크로 연결 등 필요에 맞게 자유롭게 응용하세요. Happy coding!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스에는 완전한 코드 예시와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}