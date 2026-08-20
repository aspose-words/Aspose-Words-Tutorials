---
category: general
date: 2026-08-20
description: 전체 C# 예제를 통해 ActiveX 컨트롤을 생성하고, 버튼 크기를 설정하며, Word에 버튼을 추가하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: ko
lastmod: 2026-08-20
og_description: C#로 Word 파일에 ActiveX 컨트롤 만들기. 이 튜토리얼에서는 버튼 크기 설정, Word에 버튼 추가, 클릭
  가능한 버튼 만들기를 보여줍니다.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Word에서 ActiveX 컨트롤 만들기 – 단계별 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: C#를 사용하여 Word 문서에 ActiveX 컨트롤을 만드는 방법
url: /ko/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word 문서에 ActiveX 컨트롤 만들기

Microsoft Word 파일 안에 **ActiveX 컨트롤을 만들** 필요가 있다면, 이 가이드는 정확히 어떻게 하는지 보여줍니다. **Word에 버튼을 추가**하고, 버튼의 크기를 설정하며, 컨트롤을 클릭 가능하게 만드는 방법을 짧고 독립적인 C# 프로그램으로 확인할 수 있습니다.

이 튜토리얼에서 여러분은:

* 인터랙티브 Word 문서에서 ActiveX 컨트롤이 왜 유용한지 이해합니다.  
* **버튼 크기 설정**에 필요한 정확한 코드를 배우고 캡션을 지정합니다.  
* 나중에 매크로나 외부 로직에 연결할 수 있는 **클릭 가능한 버튼 만들기** 방법을 확인합니다.  

이 단계는 Aspose.Words .NET 23.12 이상에서 작동하며 .NET 개발 환경만 있으면 됩니다.

> **Prerequisite** – 유효한 Aspose.Words 라이선스(또는 평가 버전)와 Visual Studio 2022 또는 기타 C# IDE가 필요합니다.

---

## Word 문서에 ActiveX 컨트롤 만들기

첫 번째 단계는 빈 `Document`와 `DocumentBuilder`를 인스턴스화하는 것입니다. Builder는 ActiveX 컨트롤과 같은 객체를 삽입하기 위한 고수준 API를 제공합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

다음에 정의된 `InsertActiveXButton` 메서드에는 **버튼 삽입 방법**과 구성 로직이 포함되어 있습니다.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

프로그램을 실행하면 **ActiveXButton.docx**가 생성됩니다. Word에서 파일을 열면 **Submit**이라는 레이블이 붙은 버튼이 표시됩니다. 컨트롤은 완전히 작동하며—클릭하면 표준 `CommandButton_Click` 이벤트가 발생하고, 이를 VBA 매크로에 연결할 수 있습니다.

### 왜 이렇게 동작하나요

* `InsertForms2OleControl`은 Word에 **CommandButton** 유형의 OLE 객체를 삽입하도록 지시합니다. 이는 클래식 ActiveX 버튼 클래스입니다.  
* 너비와 높이 인자는 직접 **버튼 크기 설정**을 수행합니다; Word는 값을 포인트(1 pt ≈ 1/72 in) 단위로 변환합니다.  
* 컨트롤에 `Name = "btnSubmit"`과 같이 이름을 지정하면 VBA(`ActiveDocument.InlineShapes("btnSubmit")`)에서 쉽게 찾을 수 있습니다.  

---

## 버튼 크기와 캡션 설정

다른 외관이 필요하면 `InsertForms2OleControl` 호출의 숫자 인자를 조정하십시오. 메서드 시그니처는 다음과 같습니다:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ActiveX 클래스의 프로그래밍 식별자(`"CommandButton"`은 표준 버튼).  
* **width / height** – 포인트 단위 크기. 예를 들어 가로 2 cm 버튼은 `width = 56.7`(2 cm ≈ 56.7 pt)으로 지정합니다.  

삽입 후 캡션을 수정할 수도 있습니다:

```csharp
commandButton.Caption = "Send Request";
```

캡션을 변경해도 크기는 영향을 받지 않지만, 사용자에게 보여지는 피드백은 바뀝니다.

### Pro tip

정사각형 버튼이 필요하면 두 차원을 동일한 값으로 설정하십시오:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Word에 버튼 추가하고 클릭 가능하게 만들기

위 코드는 이미 **Word에 버튼을 추가**합니다. 버튼이 동작하도록 하려면 `Click` 이벤트를 처리하는 VBA 매크로를 작성해야 합니다. 아래 최소 매크로를 Word VBA 편집기(`Alt+F11` → Insert → Module)에 붙여넣으세요:

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

컨트롤 이름이 `btnSubmit`이므로 Word는 자동으로 `Click` 이벤트를 `btnSubmit_Click`에 매핑합니다. 이는 외부 라이브러리 없이 **클릭 가능한 버튼 만들기** 기능을 구현하는 표준 방법입니다.

> **Note:** Word의 매크로 보안 설정이 ActiveX 컨트롤을 차단할 수 있습니다. 문서에 대해 “모든 매크로 사용” 또는 “VBA 매크로 사용”이 선택되어 있는지 확인하거나, 프로덕션 사용을 위해 매크로에 디지털 서명을 하세요.

---

## 일반 질문: 버튼 삽입 및 문제 해결

### 1. 저장 후 버튼이 나타나지 않으면 어떻게 해야 하나요?

* `InsertForms2OleControl`을 지원하는 Aspose.Words 버전인지 확인하십시오. 22.5 이전 버전에는 이 기능이 없습니다.  
* 대상 파일 형식이 `.docx` 또는 `.doc`인지 확인하십시오. `.rtf`와 같은 오래된 형식은 ActiveX 객체를 저장할 수 없습니다.

### 2. 특정 북마크에 버튼을 삽입할 수 있나요?

예. `InsertForms2OleControl`을 호출하기 전에 Builder를 해당 북마크로 이동시키면 됩니다:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. 텍스트 길이에 따라 **버튼 크기 설정**을 동적으로 하려면?

`System.Drawing`의 `Graphics.MeasureString` 메서드로 필요한 너비를 계산하고 픽셀을 포인트로 변환(`points = pixels * 72 / DPI`)한 뒤, 계산된 너비를 `InsertForms2OleControl`에 전달합니다.

### 4. 루프에서 여러 버튼을 추가할 방법이 있나요?

물론입니다. 삽입 로직을 `for` 루프로 감싸고 각 반복마다 `Left`와 `Top` 속성을 조정하면 됩니다:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## 예상 출력

프로그램을 실행하고 **ActiveXButton.docx**를 열면:

* 첫 페이지 왼쪽 상단 근처에 **Submit** 버튼 하나가 표시됩니다.  
* 버튼 크기가 제공한 치수(`100 pt × 30 pt`)와 일치합니다.  
* VBA 매크로를 추가한 경우, 버튼을 클릭하면 “You clicked the Submit button!”라는 메시지 상자가 나타납니다.

이제 **ActiveX 컨트롤 만들기**, **버튼 크기 설정**, **Word에 버튼 추가**를 성공적으로 수행했으며, 향후 자동화 작업을 위해 **버튼 삽입 방법**과 **클릭 가능한 버튼 만들기**도 학습했습니다.

---

## 결론

이 튜토리얼을 통해 C#로 Word 문서에 **ActiveX 컨트롤을 만들** 수 있는 방법을 배웠습니다. 단계대로 진행하면 **버튼 크기 설정**, 의미 있는 이름 부여, 그리고 **Word에 버튼 추가**를 통해 VBA 매크로에 연결된 **클릭 가능한 버튼**을 만들 수 있습니다.  

다음과 같은 주제로 확장해 볼 수 있습니다:

* VBA 대신 .NET COM 추가 기능에 버튼을 바인딩하기.  
* `CheckBox` 또는 `ComboBox`와 같은 다른 ActiveX 클래스 사용하기.  
* 여러 컨트롤이 포함된 전체 폼 자동 생성하기.

다양한 크기로 실험해 보세요.

## 다음에 배워야 할 내용은 무엇인가요?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접하게 관련된 주제를 다룹니다. 각 리소스에는 전체 작업 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방법을 탐색하는 데 도움이 됩니다.

- [.NET에서 플로팅 이미지가 포함된 Word 문서 만들기](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Aspose.Words를 사용하여 머리글 및 바닥글이 있는 Word 문서 만들기](/words/english/net/header-footer-formatting/create-header-footer/)
- [Word에서 접근성 PDF 만들기 – 완전 가이드](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}