---
category: general
date: 2026-09-30
description: C#를 사용하여 Word 문서에 ActiveX 컨트롤을 추가합니다. ActiveX 버튼을 삽입하고, 명령 버튼을 추가하며,
  클릭 가능하게 만드는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: ko
lastmod: 2026-09-30
og_description: C#를 사용하여 Word 문서에 ActiveX 컨트롤을 추가하세요. 이 완전한 가이드를 따라 ActiveX 버튼을 삽입하고,
  명령 버튼을 추가하며, 클릭 가능하게 만들 수 있습니다.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Word 문서에 ActiveX 컨트롤 워드 추가하기 – 단계별 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: C#를 사용하여 Word에 ActiveX 컨트롤을 추가하는 방법
url: /ko/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에 ActiveX 컨트롤 워드를 추가하는 방법

Microsoft Word 파일에 **ActiveX 컨트롤 워드**를 삽입해야 하는 경우, 이 가이드는 정확한 방법을 보여줍니다. 클릭 가능한 버튼을 삽입하고, 문서를 저장하며, 최신 Aspose.Words for .NET과 함께 작동하는 완전한 실행 예제를 확인할 수 있습니다.

ActiveX 컨트롤 워드를 추가하면 인터랙티브 폼, 사용자 정의 대화 상자 또는 기본 Word 컨트롤처럼 동작하는 간단한 UI 요소를 만들 수 있습니다. 사용자 상호 작용이 필요한 계약 템플릿이든, “실행” 버튼이 필요한 보고서이든, 아래 단계가 필요한 모든 것을 다룹니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요.

* .NET 6.0 SDK 이상 (코드는 .NET Framework 4.8에서도 작동)
* Visual Studio 2022 (또는 C#를 지원하는 IDE)
* Aspose.Words for .NET 설치 (`dotnet add package Aspose.Words`)
* C#와 Word 문서 구조에 대한 기본 이해

> **Pro tip:** `InsertForms2OleControl` 메서드는 레거시 “Forms 2.0” 컨트롤에만 작동합니다. 이는 Word가 폼 필드에 사용하는 ActiveX 컨트롤입니다. 최신 Office 버전을 대상으로 하더라도 데스크톱 클라이언트에서는 컨트롤이 정상적으로 렌더링됩니다.

## 1단계: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 프로젝트를 만들고 필요한 `using` 문을 추가합니다. 이렇게 하면 컴파일러가 `Document`, `DocumentBuilder`, `OleControlType` 클래스를 찾을 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words` 네임스페이스는 Word 처리용 고수준 API를 제공하고, `Aspose.Words.Drawing`에는 ActiveX 컨트롤 유형을 지정하는 `OleControlType` 열거형이 포함되어 있습니다.

## 2단계: 원본 Word 문서 로드

수정하려는 Word 파일부터 시작해야 합니다. 다음 코드는 지정한 폴더에서 `input.docx`를 로드합니다.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

파일이 존재하지 않으면 Aspose.Words가 `FileNotFoundException`을 발생시킵니다. 오류를 부드럽게 처리하려면 `try/catch` 블록으로 감싸세요.

## 3단계: DocumentBuilder 생성하여 문서 편집

`DocumentBuilder`는 텍스트, 이미지 및 컨트롤을 삽입하는 핵심 도구입니다. 다음 요소가 배치될 위치를 가리키는 커서를 유지합니다.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

기본적으로 빌더의 커서는 첫 번째 섹션의 시작에 위치합니다. 버튼을 다른 위치에 넣고 싶다면 `MoveToDocumentEnd()` 또는 `MoveToParagraph(index)` 같은 메서드로 이동할 수 있습니다.

## 4단계: ActiveX CommandButton 컨트롤 삽입

이제 튜토리얼의 핵심인 **ActiveX 컨트롤 워드**를 클릭 가능한 버튼 형태로 삽입합니다. `InsertForms2OleControl` 메서드는 두 개의 인수를 받습니다—컨트롤 유형과 캡션(또는 이름)입니다.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **왜 `OleControlType.CommandButton`을 사용하나요?**  
  Word에 클래식 Forms 2.0 커맨드 버튼을 만들도록 지시합니다. 캡션을 표시하고 나중에 매크로나 VBA 스크립트에 연결할 수 있습니다.

* **캡션은 무엇을 하나요?**  
  문자열 `"ClickMe"`가 버튼에 표시되는 텍스트가 됩니다. UI에 맞게 원하는 문자열로 바꿀 수 있습니다.

### 특정 위치에 버튼 삽입하기

특정 단락 뒤에 버튼이 필요하면 먼저 빌더를 이동합니다:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## 5단계: 수정된 문서 저장

컨트롤을 삽입한 후 변경 사항을 새 파일(또는 원본 파일 덮어쓰기)로 저장합니다.

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

데스크톱 버전 Word에서 `output.docx`를 열면 **ClickMe**(또는 사용한 캡션에 따라 **Submit**) 라벨이 붙은 버튼이 보입니다. 디자인 모드에서 버튼을 클릭해도 기본 동작은 없으며, 나중에 Word의 “Developer” 탭을 통해 매크로를 할당할 수 있습니다.

## 전체 실행 가능한 예제

아래는 전체 워크플로를 보여주는 독립 실행형 프로그램입니다. 새 콘솔 앱의 `Program.cs`에 복사하고 실행하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### 예상 출력

* 콘솔에 출력 경로와 함께 성공 메시지가 표시됩니다.
* `output.docx`를 열면 빌더가 삽입한 위치에 **ClickMe** 버튼이 나타납니다.
* 버튼은 선택, 크기 조정이 가능하며 Word의 **Developer → Design Mode**에서 매크로를 할당할 수 있습니다.

## 흔히 묻는 질문 및 엣지 케이스 처리

| Question | Answer |
|----------|--------|
| **How to insert an ActiveX button in the header/footer?** | Move the builder to the header/footer with `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` before calling `InsertForms2OleControl`. |
| **What if I need a checkbox instead of a button?** | Use `OleControlType.CheckBox` and provide a caption like `"Agree"`. |
| **Will the button work in Word Online?** | No. Word Online does not support legacy Forms 2.0 ActiveX controls. The button only renders in the desktop client. |
| **Can I set the button’s size programmatically?** | After insertion, retrieve the `Shape` object via `builder.CurrentParagraph.Runs[0].GetShape()` and adjust `Width`/`Height`. |
| **Is there a way to assign a macro from code?** | Aspose.Words does not expose macro editing. You must open the document in Word and attach a macro manually or use the Office Interop API. |

## 프로덕션 사용 시 팁

* **경로를 하드코딩하지 말 것** – `Path.Combine`과 설정 파일을 활용하세요.
* **Document 객체를 Dispose** – 큰 파일을 다룰 경우 `using` 문으로 감싸 메모리를 즉시 해제합니다.
* **출력 검증** – `doc.GetChildNodes(NodeType.Shape, true)`를 순회해 `OleControl` 유형의 Shape가 포함됐는지 프로그램matically 확인합니다.
* **보안 주의** – ActiveX 컨트롤은 클라이언트 머신에서 코드를 실행할 수 있습니다. 신뢰할 수 있는 사용자에게만 배포하고 디지털 서명을 고려하세요.

## 결론

이제 C#를 사용해 Word 문서에 **ActiveX 컨트롤 워드**를 추가하는 방법을 알게 되었습니다. 문서를 로드하고, `DocumentBuilder`를 만든 뒤, `InsertForms2OleControl`로 커맨드 버튼을 삽입하고, 파일을 저장하면 인터랙티브 Word 폼을 자동화할 수 있습니다. 다른 `OleControlType` 값을 실험하고, 헤더나 테이블에 컨트롤을 배치하며, 매크로와 결합해 보다 풍부한 사용자 경험을 만들어 보세요.

---

*다음 단계*: 다른 유형의 **ActiveX** 컨트롤 삽입 방법을 탐색하고, VBA를 통해 **커맨드 버튼** 이벤트 핸들러를 추가하는 방법을 배우며, **ActiveX 버튼 삽입**에 대한 모범 사례를 읽어 크로스‑플랫폼 호환성을 높이세요.


## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 돕습니다.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}