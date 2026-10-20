---
category: general
date: 2026-10-20
description: Aspose.Words를 사용하여 프로그래밍 방식으로 Word 문서를 만들고 명령 버튼을 추가합니다. ActiveX 컨트롤을
  삽입하고 버튼 캡션을 설정하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: ko
lastmod: 2026-10-20
og_description: 프로그래밍으로 Word 문서를 생성하고 ActiveX 명령 버튼을 삽입합니다. 이 튜토리얼에서는 Aspose.Words를
  사용하여 컨트롤을 삽입하고 캡션을 설정하는 방법을 설명합니다.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: 프로그램으로 Word 문서 만들기 – ActiveX 버튼 추가
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: ActiveX 버튼으로 프로그래밍 방식으로 Word 문서 만들기
url: /ko/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX 버튼이 있는 Word 문서를 프로그래밍 방식으로 만들기

Aspose.Words를 사용해 프로그래밍 방식으로 Word 문서를 만든 다음, 사용자가 클릭할 수 있는 명령 버튼을 추가합니다. 이 가이드는 ActiveX 컨트롤을 삽입하고, 속성을 구성하며, 결과를 **.docx** 파일로 저장하는 과정을 단계별로 안내합니다.

전체 실행 가능한 예제를 확인하고 콘솔 애플리케이션에 복사해 사용할 수 있습니다. 튜토리얼을 마치면 완전한 기능을 갖춘 명령 버튼이 포함된 Word 파일을 생성할 수 있으며, **add command button**, **add activex control**, **insert activex button**, **set button caption**을 C# 코드에서 벗어나지 않고 수행하는 방법을 이해하게 됩니다.

## Prerequisites

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 SDK 이상  
* Visual Studio 2022 (또는 C#을 지원하는 IDE)  
* Aspose.Words for .NET 라이선스 파일 (무료 체험판도 이 예제에 사용 가능)  
* C# 및 .NET 프로젝트 시스템에 대한 기본 지식  

**Aspose.Words** 외에 추가 NuGet 패키지는 필요하지 않습니다. ActiveX 지원이 라이브러리에 내장되어 있기 때문입니다.

## Step 1: Set up the project and add Aspose.Words

1. 터미널이나 Visual Studio를 열고 새 콘솔 프로젝트를 생성합니다:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Aspose.Words 패키지를 추가합니다:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (선택) 라이선스 파일이 있는 경우 프로젝트 루트에 배치하고 `Program.cs` 시작 부분에 다음 코드를 추가하여 평가 워터마크를 제거합니다:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Step 2: Create Word document programmatically – initialize the document

첫 번째 작업은 **create Word document programmatically**입니다. `Document` 객체와 문서 내용을 편집할 수 있는 `DocumentBuilder`를 인스턴스화하여 수행합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document`는 전체 파일을 나타내고, `DocumentBuilder`는 문서 내 어느 위치든 커서를 이동시킬 수 있게 합니다. 이 분리는 API를 깔끔하게 유지하고, 나중에 **add activex control**을 수동으로 저수준 구조를 관리하지 않고도 추가할 수 있게 해줍니다.

## Step 3: Add command button – inserting an ActiveX control

이제 `OleControlType.CommandButton` 유형의 ActiveX 컨트롤을 삽입하여 **add command button**을 수행합니다. `InsertForms2OleControl` 메서드는 컨트롤 유형, 위치(`Point`), 크기(`Size`)를 필요로 합니다.

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

위 호출은 **insert activex button**을 지정한 정확한 좌표에 문서에 삽입합니다. 좌표는 포인트 단위이며(1 pt ≈ 1/72 in) 특정 단락에 버튼이 필요하면 먼저 빌더의 커서를 이동시킵니다:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Step 4: Set button caption – customizing the command button text

라벨이 없는 버튼은 혼란을 초래하므로 **set button caption**을 의미 있는 텍스트로 설정합니다. `Caption` 속성은 버튼에 표시되는 텍스트를 정의하고, `Name`은 컨트롤에 프로그래밍 식별자를 부여합니다.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

나중에 문서를 매크로 사용 형식(`.docm`)으로 내보내는 경우 `OnClick` 값이 VBA 매크로 이름과 일치해야 합니다. 일반 `.docx`에서는 해당 속성이 저장되지만 실행되지 않으며, 대부분의 자동화 시나리오에 적합합니다.

## Step 5: Save the document containing the ActiveX button

컨트롤 구성을 마친 후 **save the document**를 수행합니다. 쓰기 권한이 있는 디렉터리를 선택하고 호환성을 최대로 유지하려면 `.docx` 확장자를 사용합니다.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

생성된 파일을 Microsoft Word에서 열면 지정한 좌표에 **Submit**이라는 레이블이 붙은 버튼이 표시됩니다. 데스크톱 클라이언트에서 버튼을 클릭하면 `SubmitForm` 매크로가 존재할 경우 실행을 시도합니다.

## Step 6: Verify the result and troubleshoot common issues

1. Microsoft Word에서 `ActiveXCommandButton.docx`를 엽니다.  
2. **Design Mode**(Developer 탭 → **Design Mode**)로 전환하여 버튼 테두리를 확인합니다.  
3. 버튼이 보이지 않으면 **Developer** 탭이 활성화되어 있는지, 사용 중인 Word 버전이 ActiveX 컨트롤을 지원하는지 확인합니다.  
4. 매크로 사용 형식(`.docm`) 파일의 경우 `OnClick`에 지정된 매크로 이름이 VBA 루틴과 일치하는지 확인하세요. 일치하지 않으면 Word가 보안 경고를 표시합니다.

### Pro tip

ActiveX 컨트롤은 Windows 전용입니다. 크로스 플랫폼 인터랙티브가 필요하면 ActiveX 버튼 대신 **Content Controls**(`RichTextContentControl`) 사용을 고려하세요.

## Full source code

아래는 완전한 실행 가능한 프로그램 전체 코드입니다. `Program.cs`에 복사하고 `dotnet run`을 실행하십시오.



## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 연관 주제를 다룹니다. 각 리소스는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [ActiveX 버튼이 포함된 Word 문서 만들기 – C# 가이드](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Aspose.Words를 사용한 Word 문서에 명령 버튼 추가 – 완전 가이드](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Aspose.Words로 Word 문서 버튼 만들기 – 전체 코드 예제](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}