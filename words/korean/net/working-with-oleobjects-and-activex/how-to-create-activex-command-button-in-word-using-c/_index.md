---
category: general
date: 2026-09-21
description: Aspose.Words와 C#를 사용하여 Word 문서에 ActiveX 명령 버튼을 만드는 방법을 배워보세요. 단계별 가이드에서는
  삽입, 위치 지정 및 저장을 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: ko
lastmod: 2026-09-21
og_description: C#와 Aspose.Words를 사용하여 Word 문서에 ActiveX 명령 버튼을 생성합니다. 이 완전한 튜토리얼을
  따라 버튼을 프로그래밍 방식으로 삽입, 위치 지정 및 저장하세요.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: C#로 Word에서 ActiveX 명령 버튼 만들기 – 전체 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: C#를 사용하여 Word에서 ActiveX 명령 버튼 만들기
url: /ko/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에서 ActiveX 명령 버튼 만들기

Word 파일 안에 **ActiveX 명령 버튼**을 **생성**해야 할 경우, 이 가이드는 정확한 단계들을 보여줍니다. Aspose.Words for .NET을 사용하면 버튼을 추가하고, 위치를 지정하며, 완전히 C# 코드만으로 구성할 수 있습니다.

ActiveX 버튼을 프로그래밍 방식으로 삽입하면 수동 UI 작업을 없앨 수 있고, 양식, 보고서 또는 인터랙티브 템플릿을 자동으로 생성할 수 있습니다. 이 튜토리얼에서는 **DocumentBuilder**, **InsertForms2OleControl** 메서드 및 관련 속성을 사용하여 완전한 기능의 버튼을 만드는 방법을 배웁니다.

## 준비 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 SDK 이상 (코드는 .NET Framework 4.7+에서도 동작합니다)
* Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`)
* Visual Studio 2022 또는 VS Code와 같은 IDE
* C# 및 Word 문서 개념에 대한 기본 지식

Microsoft Word가 설치될 필요는 없습니다. Aspose.Words는 Microsoft Word와 독립적으로 동작합니다.

## 1단계: C# 프로젝트 설정

새 콘솔 프로젝트를 만들고 Aspose.Words 패키지를 추가합니다.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words` 라이브러리는 문서를 조작하기 위해 사용할 **DocumentBuilder** 클래스를 제공합니다.

## 2단계: 문서와 Builder 초기화

첫 번째 코드 블록은 빈 문서와 `DocumentBuilder` 인스턴스를 생성합니다. 이 객체가 모든 Word‑처리 작업의 진입점이 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**왜 중요한가:** `DocumentBuilder`는 현재 커서 위치를 유지하므로, 이후 삽입 작업은 커서를 둔 정확한 위치에 나타납니다.

## 3단계: ActiveX 명령 버튼 삽입

**InsertForms2OleControl** 메서드는 요청된 유형의 ActiveX 컨트롤을 생성합니다. 여기서는 `CommandButton`을 요청하고 크기를 포인트 단위(200 × 30 pt)로 지정합니다.

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**설명:**  
* `OleControlType.CommandButton`은 Aspose.Words에게 다른 컨트롤이 아니라 버튼을 만들도록 지시합니다.  
* 메서드는 `Forms2OleControl` 객체를 반환하며, 이 객체는 위치와 속성 필드를 제공합니다.

## 4단계: 버튼 위치 지정 및 속성 설정

삽입 후 버튼을 페이지의 원하는 위치로 이동하고 프로그래밍 이름 및 표시 캡션을 지정할 수 있습니다.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**팁:** 좌표계는 페이지의 좌측 상단 모서리에서 시작합니다. `Left`와 `Top`을 조정하여 버튼을 다른 폼 필드와 정렬하세요.

## 5단계: 문서 저장

마지막으로 문서를 디스크에 기록합니다. 파일에는 ActiveX 버튼이 포함되어 있으며, Microsoft Word에서 열면 버튼이 인터랙티브하게 동작합니다.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

`ActiveXCommandButton.docx`를 Word에서 열면 지정된 위치에 **Submit**이라는 레이블이 붙은 버튼이 표시됩니다. Word에서 클릭하면 기본 명령 버튼 동작이 실행됩니다(추후 VBA나 Word 애드인으로 커스터마이징 가능).

## 완전한 실행 예제

모든 코드를 하나로 합치면 복사·붙여넣기만으로 바로 실행할 수 있는 독립 프로그램이 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**예상 출력:** 콘솔에 *“Document created successfully.”*가 표시되고, 폴더에 `ActiveXCommandButton.docx` 파일이 생성됩니다. Word에서 파일을 열면 왼쪽 여백에서 100 pt, 페이지 상단에서 150 pt 떨어진 위치에 클릭 가능한 **Submit** 버튼이 나타납니다.

## 흔히 발생하는 문제와 해결 방법

| 문제 | 발생 원인 | 해결 방법 |
|------|----------|-----------|
| 버튼이 페이지 밖에 표시됨 | `Left`/`Top` 값이 페이지 크기를 초과 | `doc.FirstSection.PageSetup.PageWidth`와 `PageHeight`를 사용해 안전한 좌표 계산 |
| Word에서 버튼이 보이지 않음 | ActiveX 컨트롤을 제거하는 형식(예: `.txt`)으로 저장 | 항상 `.docx` 또는 `.doc` 형식으로 저장 |
| 런타임 오류 `ArgumentOutOfRangeException` | 너비 또는 높이가 0 이하로 설정 | `InsertForms2OleControl`에 전달하는 크기 인수가 양수인지 확인 |

## 솔루션 확장하기

`Enabled`, `Visible` 같은 추가 속성을 설정하거나 VBA 매크로를 연결해 버튼을 더욱 커스터마이징할 수 있습니다. **Forms2OleControl** 클래스는 체크 박스(`OleControlType.CheckBox`)나 콤보 박스(`OleControlType.ComboBox`)와 같은 다른 ActiveX 컨트롤도 삽입할 수 있게 해줍니다.

여러 개의 버튼을 루프에서 생성해야 한다면 삽입 로직을 헬퍼 메서드로 캡슐화하세요:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## 결론

이제 C#와 Aspose.Words를 사용해 Word 문서에 **ActiveX 명령 버튼**을 **생성**하는 방법을 알게 되었습니다. 프로젝트 설정, `InsertForms2OleControl`로 버튼 삽입, 위치 지정, 최종 파일 저장까지 전체 과정을 다루었습니다. 이를 기반으로 복잡한 양식을 자동화하고, 인터랙티브 컨트롤을 삽입하며, Word 문서를 더 큰 .NET 솔루션에 통합할 수 있습니다.

다음 단계로 **Aspose.Words ActiveX** 폼 필드, **C# DocumentBuilder** 고급 스타일링, 체크 박스와 드롭‑다운 리스트용 **Word에서 ActiveX 컨트롤** 프로그래밍 추가 등을 탐색해 보세요. 다양한 좌표와 크기를 실험해 자신의 레이아웃 요구에 맞게 조정해 보시기 바랍니다. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 배운 기술을 확장하는 데 도움이 되는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하므로, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있습니다.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}