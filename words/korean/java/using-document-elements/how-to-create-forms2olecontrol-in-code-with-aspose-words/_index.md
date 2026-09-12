---
category: general
date: 2026-09-11
description: Aspose.Words DocumentBuilder를 사용하여 코드에서 forms2olecontrol을 만드는 방법을 배웁니다.
  이 단계별 가이드는 ActiveX 명령 버튼 삽입, setOleClassName 사용 및 크기 조정을 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: ko
lastmod: 2026-09-11
og_description: Aspose.Words를 사용하여 코드에서 forms2olecontrol을 생성합니다. 이 가이드를 따라 ActiveX
  명령 버튼을 삽입하고, 클래스 이름을 설정하며, 크기를 조정하세요.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: 코드에서 forms2olecontrol 만들기 – 완전한 Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Aspose.Words를 사용하여 코드에서 forms2olecontrol을 만드는 방법
url: /ko/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 코드에서 forms2olecontrol 만들기

코드에서 **create forms2olecontrol in code**가 필요하다면, 이 가이드는 Aspose.Words .NET API를 사용하여 정확히 수행하는 방법을 보여줍니다. ActiveX 명령 버튼이 필요한 템플릿을 자동화하든, 아니면 프로그래밍 방식으로 Word 문서를 풍부하게 만들고 싶든, 아래 단계에서는 컨트롤 삽입부터 외관 설정까지 모든 과정을 다룹니다.

이 튜토리얼에서는 **Aspose.Words DocumentBuilder**를 사용해 **ActiveX command button**을 삽입하고, **setOleClassName method**로 클래스를 지정하며, **Forms2OleControl size**를 조정하는 방법을 배웁니다. 외부 도구는 필요 없으며, .NET 개발 환경과 Aspose.Words 라이브러리만 있으면 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 이상이 설치되어 있음 (.NET Framework 4.7+에서도 동작)
* 최신 버전의 Aspose.Words for .NET NuGet 패키지
* C# 기본 지식 및 Word 문서에서 ActiveX 컨트롤 개념에 대한 이해

위 항목 중 누락된 것이 있다면 다음 명령으로 NuGet 패키지를 설치하세요:

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* `DocumentBuilder` 인스턴스 생성
* `Forms2OleControl` 삽입 (ActiveX 명령 버튼의 기본 객체)
* `setOleClassName`으로 올바른 클래스 이름 지정
* **Forms2OleControl size** 속성을 사용해 시각적 너비와 높이 설정
* 문서 저장 및 결과 확인

가이드를 끝까지 따라 하면 클릭 가능한 버튼이 포함된 완전한 Word 파일을 얻을 수 있으며, 이를 추가로 커스터마이즈하거나 VBA 매크로에 연결할 수 있습니다.

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialise the DocumentBuilder

`DocumentBuilder` 클래스는 Aspose.Words에서 대부분의 문서 생성 작업의 진입점입니다. 텍스트, 이미지, 표를 추가하는 메서드와 함께, 이 튜토리얼에서 중요한 OLE 컨트롤을 추가할 수 있는 기능을 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`DocumentBuilder`는 문서 내부의 현재 커서 위치를 유지합니다. 초기 단계에서 객체를 생성하면 이후 삽입되는 **ActiveX command button**이 정확히 원하는 위치에 배치됩니다.

### Step 2: Insert the Forms2OleControl

`insertForms2OleControl` 메서드는 `Forms2OleControl` 객체를 반환합니다. 이 객체는 Word가 ActiveX 버튼으로 렌더링할 OLE 컨트롤 자리표시자를 나타냅니다.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Why this matters:**  
이 호출 없이는 컨트롤의 속성을 조작할 수 없습니다. 반환된 `Forms2OleControl`을 통해 **setOleClassName method**, 크기 속성 및 기타 OLE‑전용 설정에 완전하게 접근할 수 있습니다.

### Step 3: Specify the ActiveX class with setOleClassName

Word는 어떤 유형의 ActiveX 컨트롤을 렌더링할지 알아야 합니다. 표준 명령 버튼의 클래스 이름은 `"Forms.CommandButton.1"`입니다.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Why this matters:**  
`setOleClassName` 메서드는 일반 OLE 자리표시자와 구체적인 **ActiveX command button**을 연결하는 다리 역할을 합니다. 잘못된 클래스 이름을 사용하면 빈 객체가 표시되거나 문서를 열 때 런타임 오류가 발생합니다.

### Step 4: Adjust the Forms2OleControl size

너무 작거나 큰 버튼은 비전문적으로 보입니다. `setWidth`와 `setHeight`를 사용해 크기를 제어할 수 있습니다.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Why this matters:**  
이 속성들은 **Forms2OleControl size**를 구성합니다. 버튼이 Word UI에 어떻게 표시되는지를 결정하고, 연결된 매크로가 충분히 클릭 가능한 영역을 확보하도록 합니다.

### Step 5: Save the document and test

컨트롤 구성을 마친 후 원하는 위치에 문서를 저장합니다.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

`ActiveXButton.docx`를 Microsoft Word에서 열면 “CommandButton1”(기본 캡션)이라는 레이블이 붙은 버튼이 표시됩니다. 매크로를 추가하지 않으면 클릭해도 동작하지 않지만, 컨트롤 자체는 완전히 작동합니다.

**Expected output:**  

![Word 문서에 삽입된 ActiveX command button](/images/activeX-button.png "코드로 새로 만든 ActiveX command button이 삽입된 Word 문서의 스크린샷")

*이미지 alt 텍스트는 접근성 및 SEO를 위해 주요 키워드를 포함하고 있습니다.*

---

## Understanding the ActiveX Forms2OleControl class

`Forms2OleControl` 클래스는 Word가 ActiveX 요소에 사용하는 저수준 OLE 인프라를 래핑합니다. `Shape`를 상속하므로 필요에 따라 일반적인 도형 서식(예: 테두리, 회전)도 적용할 수 있습니다.

* **ActiveX command button** – 가장 일반적인 사용 사례이며, Word 개발자 도구를 통해 매크로에 바인딩할 수 있습니다.
* **setOleClassName method** – Word가 로드할 COM 클래스를 결정합니다. 다른 유효한 값으로는 `"Forms.TextBox.1"` 및 `"Forms.ComboBox.1"`이 있습니다.
* **Forms2OleControl size** – `SetWidth`/`SetHeight`를 통해 제어합니다. 이 메서드는 포인트 단위(1 pt = 1/72 in)를 사용합니다.

### When to use Forms2OleControl vs. Content Controls

단순한 데이터 입력(예: 일반 텍스트 필드)만 필요하다면 Word 내장 콘텐츠 컨트롤이 더 가볍습니다. 이벤트 처리나 맞춤 VBA 상호 작용 등 전체 ActiveX 기능이 필요할 때 `Forms2OleControl`을 사용하세요.

---

## Setting additional properties (optional)

핵심 단계만으로도 **create forms2olecontrol in code**가 가능하지만, 버튼의 외관이나 동작을 미세 조정하고 싶을 때가 있습니다.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Why this matters:**  
`SetOleData`를 사용하면 OLE 스트림에 임의의 속성 값을 직접 기록할 수 있습니다. 이는 VBA에 의존하지 않고 **ActiveX command button**을 가장 유연하게 커스터마이즈하는 방법입니다.

---

## Common pitfalls and troubleshooting

| 증상 | 가능한 원인 | 해결 방법 |
|--------|--------------|-----|
| 버튼이 회색 상자로 표시됨 | `setOleClassName`에 잘못된 클래스 이름 전달 | 문자열이 정확히 `"Forms.CommandButton.1"`인지 확인 (대소문자 구분) |
| 크기가 변경되지 않음 | 컨트롤 삽입 전에 Width/Height 설정 | **InsertForms2OleControl** 후에 반드시 `SetWidth`/`SetHeight` 호출 |
| 문서를 열 때 “OLE object not found” 오류 발생 | Aspose.Words 라이선스 누락 (평가 버전은 OLE 제한 가능) | 유효한 라이선스를 적용하거나 전체 OLE 지원이 포함된 무료 체험판 사용 |
| 버튼 캡션이 “CommandButton1” 그대로 | `SetOleData` 미사용 또는 매크로가 속성을 읽지 않음 | VBA 매크로로 `"Caption"` 속성을 읽거나 Word UI를 통해 캡션 설정 |

---

## Full, runnable example

아래는 복사·붙여넣기만 하면 바로 실행할 수 있는 전체 콘솔 애플리케이션 예제입니다. 튜토리얼에서 다룬 모든 내용을 포함하고 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explanation of each section**  

* **Using directives** – `Document`, `DocumentBuilder`, `Forms2OleControl`에 필요한 Aspose.Words 네임스페이스를 가져옵니다.
* **Document creation** – 빈 Word 파일을 생성합니다.
* **InsertForms2OleControl** – 현재 커서 위치에 OLE 컨트롤을 배치합니다.
* **SetOleClassName** – 컨트롤이 **ActiveX command button**임을 Word에 알립니다.
* **SetWidth / SetHeight** – 전문적인 외관을 위해 **Forms2OleControl size**를 조정합니다.
* **SetOleData (optional)** – 캡션과 같은 추가 속성을 기록하는 방법을 보여줍니다.
* **Save** – 최종 `.docx` 파일을 디스크에 저장합니다.

프로그램을 실행(`dotnet run`)하고 `ActiveXButton.docx`를 열면 나중에 매크로에 연결할 수 있는 버튼이 표시됩니다.

---

## Conclusion

이제 Aspose.Words를 사용해 **create forms2olecontrol in code**하는 방법을 알게 되었습니다. `DocumentBuilder` 초기화부터 **ActiveX command button**을 `setOleClassName`으로 지정하고 **Forms2OleControl size**를 제어하는 전체 과정을 익혔으니, 복잡한 Word 문서를 자동화하고 인터랙티브 UI 요소를 삽입하며 모든 로직을 내부에 유지할 수 있습니다.

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 배운 기술을 기반으로 하여 관련 주제를 깊이 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하므로 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}