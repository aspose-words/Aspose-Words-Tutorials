---
category: general
date: 2026-09-14
description: C#를 사용하여 Word 문서에 ActiveX 컨트롤을 만들기. ActiveX 삽입 방법, 인터랙티브 버튼 추가, 그리고 .docx
  파일을 프로그래밍 방식으로 생성하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: ko
lastmod: 2026-09-14
og_description: C#를 사용하여 Word 문서에 ActiveX 컨트롤을 생성합니다. 이 완전한 예제를 따라 ActiveX를 삽입하고,
  인터랙티브 버튼을 추가하며, 파일을 저장하세요.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: C#를 사용하여 Word에서 ActiveX 컨트롤 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: C#를 사용하여 Word 문서에 ActiveX 컨트롤 만들기
url: /ko/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 C#으로 ActiveX 컨트롤 만들기

Microsoft Word 파일 안에 **ActiveX 컨트롤**을 **생성**해야 하는 경우, 이 가이드는 완전하고 바로 실행할 수 있는 솔루션을 보여줍니다. ActiveX CommandButton을 삽입하고, 속성을 설정하며, 순수 C# 코드만으로 결과 `.docx` 파일을 저장하는 방법을 정확히 확인할 수 있습니다.

Word 문서에 대화형 버튼을 추가하는 것은 최종 사용자가 문서 UI에서 직접 매크로나 사용자 정의 로직을 트리거하도록 해야 할 때 흔히 요구되는 기능입니다. 아래 예제는 타사 도구에 의존하지 않고 **ActiveX 삽입 방법**을 보여주며, **Word 문서 생성 방법**도 프로그래밍 방식으로 다룹니다.

이 튜토리얼을 마치면 **코드로 버튼 만들기**, 캡션 커스터마이징, 그리고 ActiveX 컨트롤을 보존하는 휴대용 Word 파일을 만들 수 있게 됩니다.

## 전제 조건

- .NET 6.0 이상 (Aspose.Words for .NET 라이브러리는 .NET Core 및 .NET Framework와 함께 작동합니다)
- `Aspose.Words` NuGet 패키지에 대한 참조  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# 및 객체 지향 프로그래밍에 대한 기본 지식

## 단계 1: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 프로젝트를 만들고(또는 기존 C# 애플리케이션에 코드를 통합) 필요한 네임스페이스를 가져와 컴파일러가 Word 처리 클래스를 찾을 수 있도록 합니다.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **왜 이 단계가 중요한가** – `Aspose.Words` API는 `Document`, `DocumentBuilder`, `Forms2OleControl` 클래스를 제공하여 객체 수준에서 Word 파일을 조작할 수 있게 합니다. 이러한 참조가 없으면 나머지 코드는 컴파일되지 않습니다.

## 단계 2: 새 Word 문서 및 DocumentBuilder 만들기

`Document` 객체는 전체 `.docx` 패키지를 나타내고, `DocumentBuilder`는 콘텐츠 삽입을 위한 유창한 API를 제공합니다.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **설명** – 새로운 `Document`를 인스턴스화하면 깨끗한 캔버스를 얻게 됩니다. Builder의 커서는 첫 번째 섹션의 시작에 위치하며, 다음 삽입을 준비합니다.

## 단계 3: ActiveX CommandButton 삽입

`InsertForms2OleControl`을 사용하여 특정 위치에 ActiveX 컨트롤을 배치합니다. 이 메서드는 컨트롤 유형과 X/Y 좌표 및 크기(포인트 단위)를 정의하는 `RectangleF`를 필요로 합니다.

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **왜 이것이 작동하는가** – `OleControlType.CommandButton`은 API에 표준 Windows CommandButton을 만들도록 지시합니다. 사각형은 페이지의 왼쪽 상단 모서를 기준으로 버튼을 배치하여, 필요한 정확한 위치에 **대화형 버튼을 추가**할 수 있게 합니다.

## 단계 4: 버튼 속성 구성

이제 버튼의 표시 텍스트(`Caption`)와 내부 이름(`Name`)을 설정합니다. 이 속성들은 사용자가 보는 내용이며, 이후 VBA 코드에서 참조할 수 있는 요소입니다.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **실용적인 팁** – `Name`은 문서 내에서 고유해야 합니다; 그렇지 않으면 VBA 매크로가 잘못된 컨트롤을 참조할 수 있습니다.

## 단계 5: 문서 저장

마지막으로 파일을 디스크에 씁니다. ActiveX 컨트롤은 Word 패키지 내부에 저장되므로, 저장된 파일을 Microsoft Word에서 열면 전체 기능을 유지합니다.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **결과** – Word에서 `CommandButton.docx`를 열면 “Click Me” 라는 레이블이 붙은 클릭 가능한 CommandButton이 표시됩니다. 이 컨트롤은 Word UI(`Developer → Design Mode → Properties`)를 통해 매크로에 연결할 수 있습니다.

## 전체 소스 코드

모든 단계를 합치면 복사·붙여넣기·실행이 가능한 단일 독립 프로그램이 됩니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 예상 출력

프로그램을 실행하면 확인 메시지가 출력됩니다:

```
Document saved to C:\Temp\CommandButton.docx
```

생성된 파일을 Microsoft Word에서 열면 지정된 좌표에 **CommandButton**이 배치된 것을 볼 수 있습니다. 디자인 모드에서 버튼을 클릭하면 강조 표시되고, 실행 모드에서는 표준 ActiveX 버튼처럼 동작합니다.

## 일반적인 변형 및 엣지 케이스

| 시나리오 | 조정 |
|----------|------------|
| **Different control type** | `OleControlType.CommandButton`을 `OleControlType.CheckBox`, `OleControlType.OptionButton` 등으로 교체합니다. |
| **Multiple buttons** | `InsertForms2OleControl`을 반복 호출하고, 각 새 버튼에 대해 `RectangleF` 좌표를 업데이트합니다. |
| **Dynamic sizing** | 페이지 크기(`builder.PageSetup.PageWidth`)를 기반으로 사각형 크기를 계산합니다. |
| **Saving to a stream** | 웹 API에서 파일을 반환해야 할 때 `document.Save(stream, SaveFormat.Docx)`를 사용합니다. |
| **Word 97‑2003 format** | `SaveFormat.Doc`으로 저장 형식을 변경하여 ActiveX 컨트롤이 포함된 `.doc` 파일을 생성합니다. |

> **프로 팁:** 생성된 문서를 대상 Word 버전에서 항상 테스트하세요. 오래된 버전은 기본적으로 ActiveX 컨트롤을 비활성화하는 보안 설정을 적용할 수 있습니다.

## 자주 묻는 질문

**Does this work with .NET Core?**  
예. Aspose.Words 라이브러리는 크로스 플랫폼이며 .NET Core 및 .NET 5/6+와 완전히 호환됩니다.

**Can I assign a macro to the button programmatically?**  
API는 VBA 코드를 직접 삽입하지 않습니다. 문서가 생성된 후 Word에서 열고 Developer 탭을 활성화한 뒤, `btnClick`을 참조하는 매크로를 기록하거나 작성하세요.

**What if the button does not appear?**  
Word에서 `Developer` 탭이 활성화되어 있는지, 문서가 **보호된 보기**로 열리지 않았는지 확인하세요. 또한 사각형 좌표가 페이지 여백 내에 있는지도 검증하십시오.

## 결론

이제 C#을 사용해 Word 파일 안에 **ActiveX 컨트롤을 생성**하는 방법을 알게 되었습니다. 튜토리얼에서는 **ActiveX 삽입 방법**, **대화형 버튼 추가**, **새 Word 문서 만들기**, 그리고 **코드로 버튼 만들기**를 다루었으며, 저장 후에도 지속되는 방법을 보여줍니다.

앞으로는 추가 ActiveX 유형을 탐색하고, 버튼을 VBA 매크로에 연결하거나, 더 큰 문서 생성 서비스에 로직을 포함시킬 수 있습니다. 다양한 크기, 위치 및 컨트롤 속성을 실험하여 원하는 사용자 경험에 맞추세요.

---

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접하게 관련된 주제를 다룹니다. 각 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [새 Word 문서 만들기](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word 문서에서 Vba 프로젝트 만들기](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Aspose.Words for .NET에서 Word 문서 만들기 및 스타일 적용](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}