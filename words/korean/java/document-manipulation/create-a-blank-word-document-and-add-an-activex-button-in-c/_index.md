---
category: general
date: 2026-10-23
description: C#를 사용하여 빈 Word 문서를 만들고 Aspose.Words를 이용해 버튼을 포함한 ActiveX 컨트롤을 삽입하는 방법을
  배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: ko
lastmod: 2026-10-23
og_description: C#를 사용하여 빈 Word 문서를 만들고 Aspose.Words를 이용해 버튼을 포함한 ActiveX 컨트롤을 삽입하는
  방법을 배워보세요.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: 빈 Word 문서를 만들고 C#에서 ActiveX 버튼을 추가하기
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: C#에서 빈 Word 문서를 만들고 ActiveX 버튼을 추가하기
url: /ko/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서를 만들고 C#에서 ActiveX 버튼 추가하기

프로그래밍 방식으로 **빈 Word 문서 만들기**가 필요하다면, 이 가이드가 정확히 어떻게 하는지 보여줍니다. 새로운 문서를 만들고, ActiveX CommandButton을 삽입하고, 파일을 저장하는 완전한 실행 가능한 예제를 볼 수 있습니다—모두 Aspose.Words for .NET을 사용합니다.

**ActiveX 버튼**을 추가하면 매크로 사용 템플릿이나 Windows 전용 솔루션에서 사용할 수 있는 인터랙티브 기능을 삽입할 수 있습니다. 이 튜토리얼을 마치면 모든 ActiveX 컨트롤을 삽입할 수 있게 되지만, 가장 일반적인 시나리오인 **워드 문서 activex 버튼**(양식을 제출하는) 에 초점을 맞춥니다.

## 사전 요구 사항

* .NET 6.0 또는 그 이후 버전 (코드는 .NET Framework 4.7+에서도 작동합니다)
* Visual Studio 2022 (또는 any C# IDE)
* **Aspose.Words for .NET** NuGet 패키지  
  ```bash
  dotnet add package Aspose.Words
  ```
* C# 구문에 대한 기본적인 이해

> **팁:** Aspose.Words는 상용 라이브러리이지만, 테스트용 무료 임시 라이선스를 제공합니다. 평가 워터마크를 피하려면 라이선스를 미리 설치하세요.

## 단계 1: Aspose.Words로 빈 Word 문서 만들기

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이는 메모리 내의 빈 `.docx` 파일을 나타냅니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document`는 섹션, 페이지, 내용이 전혀 없는 상태로 시작합니다. 이는 **빈 Word 문서 만들기**와 같은, 처음부터 보고서를 생성하는 시나리오에 필요한 깨끗한 상태입니다.

## 단계 2: 문서를 편집하기 위해 DocumentBuilder 얻기

`DocumentBuilder`는 텍스트, 이미지 및 컨트롤을 추가하기 위한 편리한 API를 제공합니다. 우리는 이를 사용해 ActiveX 컨트롤의 위치를 지정할 것입니다.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

빌더는 자동으로 기본 섹션과 첫 페이지를 추가하므로, 바로 객체 삽입을 시작할 수 있습니다.

## 단계 3: 문서에 ActiveX 컨트롤 삽입하는 방법

Aspose.Words는 OLE/ActiveX 객체를 삽입하기 위해 `InsertForms2OleControl`을 제공합니다. 이 메서드는 컨트롤 유형, 너비 및 높이(포인트 단위)를 필요로 합니다. 아래에서는 **CommandButton**을 삽입합니다—레거시 Word 템플릿에서 볼 수 있는 전통적인 폼 버튼입니다.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **왜 작동하나요:** `Forms2OleControlType.COMMANDBUTTON`은 Word에게 ActiveX를 지원하는 Windows 환경에서 문서를 열 때 클릭 이벤트에 반응할 수 있는 버튼을 만들도록 지시합니다.

## 단계 4: ActiveX 컨트롤 만들기 – 속성 설정

이제 버튼에 프로그래밍용 이름과 표시되는 캡션을 부여합니다. 이는 개발자들이 종종 간과하는 **ActiveX 컨트롤 만들기**의 부분입니다.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name`은 VBA 매크로(`ActiveDocument.InlineShapes("btnSubmit")`)에서 참조할 식별자입니다.
* `Caption`은 버튼 자체에 표시되는 레이블입니다.

## 단계 5: ActiveX 버튼이 포함된 Word 문서 저장

마지막으로, 문서를 디스크에 기록합니다. 파일 확장자는 `.docx`이어야 하며(나중에 매크로를 추가하려면 `.docm` 사용) 예제는 자리 표시자 폴더에 저장합니다—자신의 경로로 교체하세요.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Windows 전용 Microsoft Word에서 결과 파일을 열면, VBA 코드에 연결할 수 있는 기능적인 **워드 문서 activex 버튼**이 표시됩니다.

## 전체 작동 예제

아래는 새 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**프로그램을 실행했을 때 예상되는 출력**

```
Document saved to C:\Temp\ActiveXButton.docx
```

생성된 `ActiveXButton.docx`를 Word에서 열면, 첫 페이지 상단에 **Submit**이라는 레이블이 붙은 버튼이 표시됩니다.

## 엣지 케이스 및 일반적인 함정

| Situation | What to watch for | Recommendation |
|-----------|-------------------|----------------|
| macOS 또는 Linux에서 실행 | ActiveX는 Windows 전용 기술이므로 버튼이 자리 표시자로 표시됩니다. | 튜토리얼은 Windows 대상 템플릿에만 사용하세요. |
| Word Online에서 문서 열기 | 브라우저 보기에서는 ActiveX 컨트롤을 지원하지 않습니다. | 대체 UI를 제공하거나 사용자가 데스크톱 클라이언트에서 파일을 열도록 안내하세요. |
| 매크로 사용 파일이 필요함 | `.docx` 파일은 VBA 코드를 저장할 수 없습니다. | `.docm`으로 저장(`document.Save("MyFile.docm", SaveFormat.Docm)`)하고 매크로를 별도로 추가하세요. |
| 컨트롤 크기 불일치 | 너비/높이 값은 포인트 단위(1 pt ≈ 1/72 in)입니다. | 원하는 시각적 크기를 얻기 위해 숫자 값을 조정하세요. |

## 자주 묻는 질문

**버튼이 아닌 다른 ActiveX 컨트롤을 삽입하려면?**  
동일한 `InsertForms2OleControl` 메서드를 사용하되 `COMBOBOX` 또는 `LISTBOX`와 같은 다른 `Forms2OleControlType` 열거값을 전달합니다.

**버튼의 글꼴이나 색상을 변경할 수 있나요?**  
ActiveX 버튼의 외관은 호스트 애플리케이션(Word)과 기본 Windows 테마에 의해 결정됩니다. 문서를 연 후 VBA를 통해 `ForeColor` 및 `BackColor`와 같은 속성을 수정할 수 있습니다.

**C#에서 직접 클릭 핸들러를 추가할 방법이 있나요?**  
없습니다. 클릭 이벤트는 VBA나 Word 추가 기능에서 처리해야 합니다. 버튼은 .NET 애플리케이션이 아니라 Word 프로세스 내에서 실행되기 때문입니다.

## 결론

이제 Aspose.Words for .NET을 사용해 프로그래밍 방식으로 **빈 Word 문서 만들기**와 **ActiveX 버튼** 삽입 방법을 알게 되었습니다. 다룬 단계는 다음과 같습니다:

1. `Document` 인스턴스화하기.
2. `DocumentBuilder`를 사용해 파일 작업하기.
3. `InsertForms2OleControl`을 호출해 **ActiveX 삽입 방법** 컨트롤을 추가하기.
4. 컨트롤의 속성을 구성하기 (**ActiveX 컨트롤 만들기**).
5. 파일을 저장하여 VBA 통합이 가능한 **워드 문서 activex 버튼**을 만들기.

여기서부터는 다른 컨트롤 유형을 추가하거나 VBA 매크로를 연결하거나 버튼을 정적 이미지로 유지한 채 문서를 PDF로 변환하는 등 다양한 실험을 할 수 있습니다. 다양한 크기, 캡션, 이름을 시도해 보세요.

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 작동 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼 추가하는 방법](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [ActiveX 버튼이 포함된 Word 문서 만들기 – C# 가이드](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}