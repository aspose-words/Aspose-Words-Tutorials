---
category: general
date: 2026-10-20
description: C#를 사용하여 Word 문서에 자리 표시자 텍스트를 설정합니다. Aspose.Words for .NET을 사용해 컨트롤을
  추가하고 자리 표시자를 빠르게 설정하는 방법을 배우세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: ko
lastmod: 2026-10-20
og_description: C#를 사용하여 Word 문서에 자리 표시자 텍스트를 설정합니다. 이 튜토리얼에서는 컨트롤을 추가하고, 자리 표시자를
  설정하며, Word 파일을 프로그래밍 방식으로 생성하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: C#로 Word 문서에 자리 표시자 텍스트 설정 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: C#를 사용하여 Word 문서에 자리표시자 텍스트 설정
url: /ko/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word 문서에 자리 표시자 텍스트 설정하기

C#로 Word 파일을 생성하면서 **자리 표시자 텍스트를 설정**해야 한다면, 이 가이드가 정확히 어떻게 하는지 보여줍니다. 콘텐츠 컨트롤을 추가하고, 자리 표시자를 정의하며, 문서를 저장하는 간결하고 끝‑까지의 솔루션을 Aspose.Words for .NET와 함께 확인할 수 있습니다.

많은 개발자들이 Word 문서에 **컨트롤을 추가하는 방법**이나 Word를 직접 열지 않고 **자리 표시자를 설정하는 방법**을 궁금해합니다. 이 튜토리얼은 이러한 질문에 답하고, 사용자 입력을 받을 준비가 된 **Word C# 생성** 방법을 깔끔하게 보여줍니다.

## 이 튜토리얼을 통해 달성할 내용

이 튜토리얼을 마치면 다음을 수행할 수 있습니다:

* 프로그래밍 방식으로 빈 Word 문서를 생성합니다.
* 콘텐츠 컨트롤의 기술적 명칭인 plain‑text Structured Document Tag (SDT)를 삽입합니다.
* SDT에 의미 있는 제목과 자리 표시자 텍스트를 할당합니다.
* 생성된 `.docx` 파일을 디스크에 저장합니다.

Aspose.Words 라이브러리와 .NET 6(이상) 개발 환경 외에 추가 도구가 필요하지 않습니다.

## 사전 요구 사항

* .NET 6 SDK 이상이 설치되어 있어야 합니다.  
* Visual Studio 2022(또는 .NET을 지원하는 기타 IDE).  
* Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`).  

> **Pro tip:** 테스트용이라면 Aspose.Words의 무료 평가판을 사용하세요; 워터마크가 추가되지만 라이선스 버전과 동일하게 작동합니다.

## 단계 1: 프로젝트 설정 및 네임스페이스 가져오기

새 콘솔 프로젝트를 만들고 필요한 `using` 지시문을 추가합니다. 이렇게 하면 핵심 Aspose.Words 클래스와 마크업 네임스페이스를 사용할 수 있게 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Why this step matters:* `Aspose.Words.Markup`을 가져오면 `StructuredDocumentTag`, `SdtType`, `MarkupLevel`에 접근할 수 있으며—이는 **add control**와 **set placeholder**에 필요한 객체들입니다.

## 단계 2: 빈 문서와 DocumentBuilder 만들기

`Document`는 전체 Word 파일을 나타내며, `DocumentBuilder`는 요소를 삽입하기 위한 편리한 커서를 제공합니다.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters:* 깨끗한 문서에서 시작하면 설정한 자리 표시자가 기존 내용에 방해받지 않고 정확히 원하는 위치에 나타납니다.

## 단계 3: 콘텐츠 컨트롤(Structured Document Tag) 만들기

여기서는 plain‑text SDT를 생성하고, 제목을 부여한 뒤, 컨트롤이 비어 있을 때 사용자가 보게 될 자리 표시자 텍스트를 설정합니다.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Why this step matters:* `Title` 속성을 사용하면 나중에 컨트롤을 참조할 수 있습니다(예: 데이터 바인딩). `PlaceholderName`은 바로 **set placeholder text**로, 최종 사용자를 안내합니다.

## 단계 4: 현재 커서 위치에 컨트롤 삽입

`DocumentBuilder`를 사용하여, 현재 빌더가 위치한 곳에 SDT를 문서에 삽입합니다.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Why this step matters:* 노드를 삽입하면 컨트롤이 문서의 DOM에 연결됩니다. 여러 자리 표시자를 추가해야 할 경우, 빌더의 커서를 이동하고 이 단계를 반복하면 됩니다.

## 단계 5: 문서 저장

마지막으로, 문서를 디스크에 저장합니다. `YOUR_DIRECTORY`를 실제 경로로 교체하세요.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`SDT.docx`를 Microsoft Word에서 열면 **Enter name here**라는 회색 음영의 인라인 텍스트 상자를 볼 수 있습니다. 상자를 클릭하면 자리 표시자가 사라지고 사용자가 고객 이름을 입력할 수 있습니다.

### 예상 출력

| 파일 위치 | 내용 미리보기 |
|---------------|-----------------|
| `C:\Temp\SDT.docx` | plain‑text 콘텐츠 컨트롤 *CustomerName* 안에 인라인 자리 표시자 **Enter name here** |

## 엣지 케이스 및 변형

| 상황 | 권장 조정 |
|-----------|------------------------|
| **Multiple placeholders** | 다른 `Title` 및 `PlaceholderName` 값을 가진 추가 `StructuredDocumentTag` 객체를 생성한 뒤, 필요한 위치에 각각 삽입합니다. |
| **Rich‑text placeholder** | `PlainText` 대신 `SdtType.RichText`를 사용하여 자리 표시자 내부에 서식을 허용합니다. |
| **Block‑level control** | `MarkupLevel.Inline`을 `MarkupLevel.Block`으로 변경하면 컨트롤이 전체 문단처럼 동작합니다. |
| **Placeholder not visible** | Word에서 문서 보기 설정이 콘텐츠 컨트롤을 숨기도록 설정되지 않았는지 확인하세요(`File → Options → Advanced → Show content controls`). |
| **Saving to a stream** | 디스크에 쓰는 대신 HTTP로 파일을 전송해야 할 경우 `doc.Save(stream, SaveFormat.Docx)`를 호출합니다. |

## 전체 실행 가능한 예제

아래는 복사·붙여넣기 후 실행할 수 있는 전체 프로그램입니다. 위의 모든 단계를 하나의 `Main` 메서드에 포함하고 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

프로그램을 실행하고 생성된 파일을 열면 사용자 입력을 받을 준비가 된 자리 표시자 텍스트가 표시됩니다.

## 자주 묻는 질문

**Q: Does this work with .NET Core?**  
A: Yes. Aspose.Words for .NET은 .NET Core, .NET 5, .NET 6+와 호환됩니다. 동일한 코드를 그대로 실행할 수 있습니다.

**Q: Can I set a default value in addition to the placeholder?**  
A: SDT를 만든 후 `sdt.SetText("Default value")`를 사용하세요. 값이 설정되면 자리 표시자는 사라집니다.

**Q: What if I need to retrieve the entered value later?**  
A: 문서를 로드하고 `Title`(`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`)을 통해 SDT를 찾은 뒤 `sdt.GetText()`를 읽습니다.

## 결론

C#를 사용하여 Word 문서에 **set placeholder text**하는 방법을 이제 알게 되었습니다. plain‑text `StructuredDocumentTag`를 만들고, 제목과 자리 표시자를 할당한 뒤, `DocumentBuilder`로 삽입하고 파일을 저장하면 **add control** 및 **generate Word C#** 파일을 프로그래밍 방식으로 만들 수 있습니다.

다음과 같은 주제를 탐색해 볼 수 있습니다:

* rich‑text 또는 드롭다운 리스트 컨트롤 추가 (`SdtType.RichText`, `SdtType.DropDownList`).  
* 데이터베이스에서 여러 자리 표시자 채우기.  
* 생성된 `.docx`를 Aspose.Words로 PDF 변환.

애플리케이션 요구에 맞게 다양한 컨트롤 유형과 자리 표시자 스타일을 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words에서 자리 표시자 텍스트 설정 – 완전한 C# 가이드](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [프로그래밍 방식으로 Word 문서 만들기 – 콘텐츠 컨트롤 및 자리 표시자 추가](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Aspose로 콘텐츠 컨트롤 추가 및 Word 문서 생성 – 완전 가이드](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}