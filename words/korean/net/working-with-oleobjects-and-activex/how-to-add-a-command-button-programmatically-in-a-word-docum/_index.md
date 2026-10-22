---
category: general
date: 2026-10-13
description: Aspose.Words를 사용하여 프로그래밍 방식으로 명령 버튼을 추가하는 방법을 배웁니다. 이 가이드는 전체 C# 코드를
  사용하여 Word 문서 버튼을 만드는 방법도 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: ko
lastmod: 2026-10-13
og_description: Aspose.Words를 사용하여 Word 문서에 명령 버튼을 프로그래밍 방식으로 추가합니다. C#로 Word 문서 버튼을
  만드는 전체 튜토리얼을 따라 보세요.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Word 문서에 명령 버튼을 프로그래밍 방식으로 추가하기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word 문서에 명령 버튼을 프로그래밍 방식으로 추가하는 방법
url: /ko/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 명령 버튼을 프로그래밍 방식으로 추가하는 방법  

프로그래밍 방식으로 **명령 버튼을 추가**해야 하는 경우, Aspose.Words는 OLE 폼 컨트롤을 .docx 파일에 직접 삽입할 수 있는 깔끔한 API를 제공합니다. 이 튜토리얼에서는 Microsoft Word에서 문서를 열었을 때 일반 폼 버튼처럼 동작하는 **Word 문서 버튼을 생성**하는 데 필요한 모든 단계를 안내합니다.  

개발 환경 설정, 버튼 삽입, 속성 구성 및 결과 확인 방법을 배우게 됩니다. 외부 유틸리티는 필요 없으며 .NET 프로젝트와 Aspose.Words for .NET 라이브러리만 있으면 됩니다.  

## 전제 조건  

시작하기 전에 다음이 준비되어 있는지 확인하십시오:  

* .NET 6.0 SDK 또는 그 이후 버전이 설치되어 있어야 합니다.  
* 최근 버전의 Aspose.Words for .NET (예제는 23.12를 사용하지만 22.x 이상이면 모두 동작합니다).  
* Visual Studio 2022 또는 Visual Studio Code와 같은 IDE.  

Aspose.Words는 플랫폼에 독립적이므로 코드는 Windows, macOS 및 Linux에서 실행됩니다.  

## 단계 1: 프로젝트 설정 및 Aspose.Words 참조  

1. 새 콘솔 프로젝트를 생성합니다:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Aspose.Words NuGet 패키지를 추가합니다:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. **Program.cs** 파일을 열고 다음 단계에 표시된 스캐폴드 내용으로 교체합니다.  

이와 같이 프로젝트를 설정하면 컴파일러가 폼 컨트롤에 필요한 `Aspose.Words` 및 `Aspose.Words.Drawing.Forms` 네임스페이스를 찾을 수 있게 됩니다.  

## 단계 2: 빈 문서와 DocumentBuilder 초기화  

`Document` 클래스는 전체 Word 파일을 나타내며, `DocumentBuilder`는 콘텐츠를 추가하기 위한 유창한 API를 제공합니다.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*이 단계가 중요한 이유* – `DocumentBuilder`가 없으면 페이지에 버튼을 정확히 배치할 수 없습니다. 빌더는 현재 커서 위치를 그대로 유지하므로 이후에 여러 컨트롤을 쉽게 삽입할 수 있습니다.  

## 단계 3: 명령 버튼 OLE 컨트롤 삽입  

Aspose.Words는 명령 버튼을 `ControlType.CommandButton` 유형의 OLE 컨트롤로 취급합니다. 위치와 크기는 포인트 단위(1 포인트 = 1/72 인치)로 측정되는 `RectangleF` 로 정의합니다.  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**핵심 포인트**  

- 사각형의 원점 (X, Y)은 페이지 왼쪽 위 모서리를 기준으로 합니다.  
- `Width` 또는 `Height`를 변경하면 버튼의 시각적 크기가 바뀝니다.  
- `InsertForms2OleControl`은 추가로 구성할 수 있는 `Forms2OleControl` 객체를 반환합니다.  

## 단계 4: 버튼의 이름 및 캡션 구성  

**name**은 Word 매크로 엔진이 컨트롤을 식별하는 데 사용되며, **caption**은 사용자가 보는 텍스트입니다.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

나중에 VBA 매크로를 추가할 계획이라면, Word 매크로 레코더가 이 속성을 참조하므로 설명적인 이름을 사용하십시오.  

## 단계 5: (선택) 문서 저장 및 결과 확인  

파일을 저장하면 Microsoft Word에서 열어 버튼이 나타나고 작동하는지 확인할 수 있습니다.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Word에서 *CommandButtonDemo.docx*를 열면 왼쪽 여백으로부터 약 1.4인치, 페이지 상단으로부터 약 2.1인치 위치에 **Submit**이라는 레이블이 붙은 버튼이 표시됩니다. 기본적으로 매크로가 연결되어 있지 않기 때문에 클릭해도 아무 동작을 하지 않지만, 시각적 컨트롤은 완전히 작동합니다.  

## 단계 6: 엣지 케이스 및 일반적인 함정  

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **버튼이 기존 텍스트와 겹침** | 사각형이 단락과 교차하여 레이아웃 문제가 발생할 수 있습니다. | `builder.Writeln()`을 호출한 후 버튼을 삽입하여 커서를 새 줄로 이동하거나, `Y` 좌표를 조정합니다. |
| **문서를 열 때 경고가 표시됨** | 일부 Word 버전은 연결된 프로그램이 없는 OLE 컨트롤에 경고 표시를 합니다. | 컨트롤 유형이 `CommandButton`인지 확인하십시오; Word는 이를 표준 폼 요소로 처리하므로 외부 프로그램이 필요하지 않습니다. |
| **헤드리스 환경의 Linux에서 실행** | Word를 실행해 UI를 테스트할 수 없지만 파일은 유효합니다. | `commandButton.Name`, `commandButton.Caption`와 같은 컨트롤 속성을 읽는 단위 테스트를 사용하여 올바르게 설정되었는지 확인합니다. |
| **여러 버튼이 필요함** | 커서를 이동하지 않고 동일한 `DocumentBuilder`를 재사용하면 버튼이 이전 버튼 위에 겹쳐 삽입됩니다. | 각 삽입 전에 `builder.MoveToDocumentEnd()`를 호출하거나 사각형의 `Y` 값을 조정합니다. |

이러한 엣지 케이스를 초기에 해결하면 수십 개의 컨트롤이 포함된 전체 폼으로 확장할 때 시간을 절약할 수 있습니다.  

## 단계 7: 전체 실행 가능한 예제  

아래는 NuGet 복원 외에는 수정 없이 복사·붙여넣기·실행할 수 있는 독립형 프로그램입니다.  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**예상 출력**  

프로그램을 실행하면 다음과 유사한 경로가 출력됩니다:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

생성된 *CommandButtonDemo.docx*를 열면 코드에 정의된 좌표에 배치된 단일 **Submit** 버튼이 표시됩니다. 추가 UI 요소가 나타나지 않아 **프로그래밍 방식으로 명령 버튼 추가** 작업이 성공했음을 확인할 수 있습니다.  

## 결론  

이제 Aspose.Words를 사용하여 Word 문서에 **프로그래밍 방식으로 명령 버튼을 추가**하는 방법과 이후 VBA 매크로나 외부 자동화 도구에 연결할 수 있는 **Word 문서 버튼을 생성**하는 방법을 알게 되었습니다. 이 과정은 문서 초기화, OLE `CommandButton` 컨트롤 삽입, 속성 구성 및 파일 저장으로 구성됩니다.  

다음 단계로 할 수 있는 작업은 다음과 같습니다:  

* 다양한 `ControlType` 값을 사용해 단계 3을 반복함으로써 체크박스, 텍스트 필드 등 더 많은 컨트롤을 추가합니다.  
* 버튼에 VBA 매크로를 연결하여 양식 저장이나 이메일 전송과 같은 작업을 수행합니다.  
* 필드 정의가 담긴 데이터 기반 컬렉션을 순회하여 전체 폼을 동적으로 생성합니다.  

사각형 좌표와 버튼 캡션을 실험하여 UI 디자인에 맞추세요. 즐거운 코딩 되세요!  

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 전체 작동 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 콤보 박스 폼 필드 추가](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 체크 박스 폼 필드 추가](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Aspose.Words로 빈 Word 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}