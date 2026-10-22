---
category: general
date: 2026-08-04
description: Aspose.Words를 사용하여 빈 워드 문서를 만들고 명령 버튼을 삽입합니다. C#에서 버튼 크기를 설정하고 클릭 가능한
  버튼을 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: ko
lastmod: 2026-08-04
og_description: Aspose.Words를 사용하여 빈 워드 문서를 만들고 명령 버튼을 삽입합니다. 이 가이드는 버튼 크기를 설정하고,
  클릭 가능한 버튼을 추가하며, 파일을 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: 빈 워드 문서를 만들고 명령 버튼을 추가하기 – 전체 C# 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 명령 버튼으로 빈 워드 문서 만들기 – 단계별 가이드
url: /ko/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 명령 버튼이 포함된 빈 워드 문서 만들기 – 단계별 가이드

If you need to **create blank word document** that contains an interactive button, this tutorial shows you exactly how to do it with Aspose.Words for .NET. You’ll learn to **insert command button**, adjust its appearance, and make it clickable—all in a few lines of C#.

이 튜토리얼에서는 대화형 버튼이 포함된 **빈 워드 문서 만들기**가 필요하다면, Aspose.Words for .NET을 사용하여 정확히 어떻게 수행하는지 보여드립니다. **명령 버튼 삽입**, 외관 조정, 클릭 가능하게 만들기 등을 C# 몇 줄로 배울 수 있습니다.

The guide covers everything from project setup to saving the final file, so you can copy‑paste the complete solution into your own application. Along the way we’ll also explain how to **add clickable button**, **set button size**, and **create command button** programmatically.

이 가이드는 프로젝트 설정부터 최종 파일 저장까지 모든 과정을 다루며, 전체 솔루션을 복사‑붙여넣기하여 자신의 애플리케이션에 적용할 수 있습니다. 진행하면서 **클릭 가능한 버튼 추가**, **버튼 크기 설정**, **명령 버튼 만들기**를 프로그래밍 방식으로 설명합니다.

## 사전 요구 사항

* .NET 6.0 SDK 이상이 설치되어 있어야 합니다.
* Visual Studio 2022(또는 .NET을 지원하는 IDE).
* Aspose.Words for .NET NuGet 패키지(`Aspose.Words` 버전 23.12 이상).
* C# 및 객체 지향 프로그래밍에 대한 기본적인 이해.

Aspose.Words는 Microsoft Word와 완전히 독립적으로 동작하므로 추가 Office Interop 어셈블리는 필요하지 않습니다.

## 1단계: .NET 프로젝트 설정

Create a console application that will host the Word automation code.

콘솔 애플리케이션을 생성하여 워드 자동화 코드를 실행합니다.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

This command creates a new folder `WordButtonDemo` with a ready‑to‑run `Program.cs` and adds the Aspose.Words library.

이 명령은 `WordButtonDemo`라는 새 폴더를 만들고 실행 준비가 된 `Program.cs`를 생성하며 Aspose.Words 라이브러리를 추가합니다.

## 2단계: 빈 워드 문서 만들기

The first operation is to **create blank word document**. Aspose.Words provides a `Document` class that represents an empty Word file out of the box.

첫 번째 작업은 **빈 워드 문서 만들기**입니다. Aspose.Words는 기본적으로 빈 Word 파일을 나타내는 `Document` 클래스를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Creating a blank document gives you a clean canvas on which you can add paragraphs, tables, or, in this case, an OLE command button.

빈 문서를 생성하면 단락, 표 또는 이 경우와 같이 OLE 명령 버튼을 추가할 수 있는 깨끗한 캔버스를 얻게 됩니다.

## 3단계: DocumentBuilder 초기화

`DocumentBuilder`는 문서에 내용을 삽입할 수 있게 해 주는 도우미입니다. 방금 만든 문서에 연결해야 합니다.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder maintains the current cursor position, so any subsequent insertion happens exactly where you want it.

빌더는 현재 커서 위치를 유지하므로 이후 삽입은 원하는 정확한 위치에 이루어집니다.

## 4단계: 명령 버튼 삽입

Now we **insert command button** (an OLE `Forms2OleControl`) into the document. The method `InsertForms2OleControl` requires three arguments:

이제 문서에 **명령 버튼 삽입**(OLE `Forms2OleControl`)을 수행합니다. `InsertForms2OleControl` 메서드는 세 개의 인수를 필요로 합니다:

1. OLE 컨트롤의 ProgID – 표준 버튼의 경우 `"CommandButton"`.
2. `Rectangle` 객체로 **버튼 크기 설정** 및 위치를 정의합니다.
3. 버튼에 표시되는 캡션.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

When the document is opened in Word, the button behaves like any native form control—you can click it, and Word will fire the associated macro (if one exists). This satisfies the **add clickable button** requirement.

문서를 Word에서 열면 버튼은 기본 폼 컨트롤처럼 동작합니다—클릭할 수 있으며, 해당 매크로가 있으면 Word가 실행합니다. 이는 **클릭 가능한 버튼 추가** 요구사항을 충족합니다.

### 왜 Forms2OleControl을 사용하나요?

`Forms2OleControl`은 OLE 객체를 DOCX 파일에 직접 삽입하여 Word Interop 어셈블리 없이도 컨트롤 속성을 보존합니다. 이는 Word 버전 전반에 걸쳐 작동하는 **명령 버튼 만들기**에 가장 신뢰할 수 있는 방법입니다.

## 5단계: 버튼 사용자 정의 (선택 사항)

You might want to **set button size** more precisely or change additional properties such as the font or background color. Aspose.Words exposes the underlying OLE object, allowing further tweaks.

**버튼 크기 설정**을 보다 정확히 하거나 글꼴, 배경색 등 추가 속성을 변경하고 싶을 수 있습니다. Aspose.Words는 기본 OLE 객체를 노출하여 추가 조정을 가능하게 합니다.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

If you need a different size, simply adjust the `Rectangle` values in Step 4. The coordinates are measured in points (1 pt = 1/72 inch), so `120` corresponds to roughly 1.67 inches wide.

다른 크기가 필요하면 Step 4의 `Rectangle` 값을 조정하면 됩니다. 좌표는 포인트 단위(1 pt = 1/72 인치)이며, `120`은 대략 1.67 인치 너비에 해당합니다.

## 6단계: 문서 저장

Finally, write the document to disk. The resulting file contains a **blank word document** with a fully functional command button.

마지막으로 문서를 디스크에 저장합니다. 결과 파일은 완전한 기능을 갖춘 명령 버튼이 포함된 **빈 워드 문서**를 포함합니다.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

When you open `CommandButtonDemo.docx` in Microsoft Word, you’ll see a button labeled “Click Me”. Clicking the button will display the default macro dialog unless you attach a custom macro.

Microsoft Word에서 `CommandButtonDemo.docx`를 열면 “Click Me”라는 레이블이 붙은 버튼이 표시됩니다. 버튼을 클릭하면 사용자 매크로를 연결하지 않은 경우 기본 매크로 대화 상자가 나타납니다.

## 전체 소스 코드

Below is the full program you can copy into `Program.cs`. It includes all the steps described above and compiles without modifications.

아래는 `Program.cs`에 복사하여 사용할 수 있는 전체 프로그램입니다. 위에서 설명한 모든 단계가 포함되어 있으며 수정 없이 컴파일됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 예상 결과

Running the program produces `CommandButtonDemo.docx`. Opening the file in Word shows:

프로그램을 실행하면 `CommandButtonDemo.docx`가 생성됩니다. Word에서 파일을 열면 다음과 같이 표시됩니다:

* 버튼 레이블이 **Click Me**인 단일 페이지.
* 버튼이 **버튼 크기 설정**(120 × 30 포인트)을 유지합니다.
* 버튼을 클릭하면 Word의 기본 명령 버튼 동작이 실행되어 **클릭 가능한 버튼 추가** 작업이 성공했음을 확인합니다.

## 일반적인 질문 및 예외 상황

| Question | Answer |
|----------|--------|
| **이것을 .doc 파일에서도 사용할 수 있나요?** | 예. `doc.Save("file.doc")`에서 파일 확장자를 변경하면 됩니다. OLE 컨트롤은 레거시 바이너리 형식에도 저장됩니다. |
| **여러 개의 버튼이 필요하면 어떻게 하나요?** | `InsertForms2OleControl`을 반복 호출하고, 각 새 버튼에 대해 `Rectangle`을 조정하여 겹치지 않도록 합니다. |
| **버튼에 매크로를 연결할 수 있나요?** | 버튼 자체에는 매크로 코드가 포함되지 않습니다. VBA 매크로를 문서에 수동으로 또는 `Document` 객체의 `Modules` 컬렉션을 통해 추가해야 합니다. |
| **PDF로 내보낼 때 버튼이 보이나요?** | Aspose.Words를 사용해 DOCX를 PDF로 내보내면 버튼은 정적 이미지로 렌더링되며, 인터랙티브 컨트롤은 아닙니다. |
| **지원되는 Word 버전은 무엇인가요?** | OLE 명령 버튼은 표준 Forms2.0 사양을 따르므로 Word 2007 이후 버전에서 작동합니다. |

## 결론

You now know how to **create blank word document**, **insert command button**, **add clickable button**, and **set button size** using Aspose.Words for .NET. The complete example demonstrates the **create command button** workflow from start to finish, giving you a solid foundation for more advanced Word automation tasks.

이제 Aspose.Words for .NET을 사용하여 **빈 워드 문서 만들기**, **명령 버튼 삽입**, **클릭 가능한 버튼 추가**, **버튼 크기 설정** 방법을 알게 되었습니다. 전체 예제는 **명령 버튼 만들기** 워크플로우를 처음부터 끝까지 보여주며, 보다 고급 워드 자동화 작업을 위한 탄탄한 기반을 제공합니다.

## 다음 단계

* `InsertForms2OleControl`에서 ProgID를 변경하여 다른 OLE 컨트롤(예: `CheckBox`, `ListBox`)을 탐색합니다.
* 버튼을 VBA 매크로와 결합하여 사용자가 클릭할 때 사용자 지정 동작을 수행합니다.
* 버튼을 삽입하기 전에 Aspose.Words의 `DocumentBuilder`를 사용해 표, 이미지, 각주 등 추가 콘텐츠를 추가합니다.
* **버튼 크기 설정** 값을 실험하여 문서 레이아웃 요구사항에 맞춥니다.

코딩을 즐기시고, 인터랙티브 컨트롤이 포함된 풍부한 워드 문서를 만드는 즐거움을 누리세요!

## 다음에 배울 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 워드 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [그림자 사각형 도형이 있는 빈 워드 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words for .NET을 사용하여 워드 문서 만들기](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}