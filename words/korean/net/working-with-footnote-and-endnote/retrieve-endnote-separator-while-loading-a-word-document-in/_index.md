---
category: general
date: 2026-09-08
description: Aspose.Words for .NET을 사용하여 Word 문서를 로드할 때, 미주 구분자를 가져오고 각주 구분자를 표시합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: ko
lastmod: 2026-09-08
og_description: Aspose.Words for .NET을 사용하여 Word 문서를 로드할 때, 미주 구분자를 가져오고 각주 구분자를 표시합니다.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: C#에서 Word 문서를 로드할 때 미주 구분 기호 가져오기
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: C#에서 Word 문서를 로드할 때 미주 구분 기호 가져오기
url: /ko/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Word 문서를 로드하면서 엔드노트 구분자 가져오기

Word 파일에서 **엔드노트 구분자**를 가져와야 한다면, 이 가이드는 정확한 방법을 보여줍니다. 또한 Aspose.Words를 사용해 **Word 문서를 로드**하고 콘솔에 **각주 구분자** 텍스트를 표시하는 방법도 배울 수 있습니다. 모두 하나의 실행 가능한 예제로 제공됩니다.

각주와 엔드노트를 다루는 것은 법률, 학술, 출판 애플리케이션에서 흔히 요구되는 기능입니다. 이 튜토리얼은 파일 열기부터 구분자가 없을 경우 처리까지 필요한 모든 내용을 다루므로, 추측 없이 어떤 .NET 프로젝트에도 솔루션을 통합할 수 있습니다.

## 이 튜토리얼에서 다루는 내용

* How to **load Word document** using the Aspose.Words API.  
* How to **retrieve endnote separator** and why the separator matters.  
* How to **display footnote separator** on the console for debugging or logging.  
* Edge‑case handling when a document contains no footnotes or endnotes.  
* A complete, copy‑paste‑ready code sample that runs on .NET 6 or later.

### 전제 조건

| 요구 사항 | 이유 |
|-------------|--------|
| .NET 6 SDK 이상 | C# 예제 실행에 필요한 런타임을 제공합니다. |
| Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`) | `Document.Footnotes` 및 `Document.Endnotes`를 제공하는 라이브러리입니다. |
| 하나 이상의 각주 또는 엔드노트를 포함하는 Word 파일 (`Footnotes.docx`) | 구분자를 시연하기 위해 필요합니다. |
| IDE(Visual Studio, Rider, VS Code 등) | 프로그램을 컴파일하고 실행하기 위해 필요합니다. |

> **Pro tip:** 각주가 포함된 문서가 없으면 Microsoft Word에서 빠르게 만들 수 있습니다: Insert → Footnote → 텍스트 입력 → `Footnotes.docx`로 저장.

## Aspose.Words로 Word 문서 로드

첫 번째 단계는 **load word document**를 메모리로 가져오는 것입니다. Aspose.Words는 파일 형식을 읽고 쿼리할 수 있는 객체 모델을 구축합니다.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*왜 중요한가*: 문서를 로드하는 것은 이후 모든 조작의 전제 조건입니다. 파일 경로가 잘못되면 `Document`가 `FileNotFoundException`을 발생시키므로, 실행 전에 경로를 확인하세요.

## 각주 구분자 단락 가져오기

각주 구분자는 본문 텍스트와 각주 목록을 시각적으로 구분하는 단락입니다. 이를 가져오면 서식을 검사하거나 수정할 수 있습니다.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*왜 중요한가*: **Display footnote separator**는 올바른 단락에 접근했는지 확인하는 데 도움이 되며, 특히 사용자 지정 스타일(예: 선이나 특정 글꼴)을 적용해야 할 때 유용합니다.

## 엔드노트 구분자 단락 가져오기

이제 **retrieve endnote separator**를 수행합니다. 과정은 각주 처리와 유사하지만 `Endnotes` 컬렉션을 사용합니다.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*왜 중요한가*: **retrieve endnote separator** 단계는 본문과 엔드노트 목록 사이의 시각적 구분을 조정해야 할 때 필수적이며, 이는 장 끝에 엔드노트가 표시되는 학술 출판에서 흔히 필요합니다.

### 구분자 누락 처리

문서에 구분자가 정의되지 않은 경우 `Footnotes.Separator`와 `Endnotes.Separator`는 모두 `null`을 반환합니다. `GetText()`를 호출하기 전에 항상 `null` 여부를 확인하여 `NullReferenceException`을 방지하세요. 기본 구분자가 필요하면 다음과 같이 만들 수 있습니다:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

이 코드는 최소한의 구분자를 삽입하여 이후 처리에서 존재를 보장합니다.

## 예상 콘솔 출력

샘플을 하나의 각주와 하나의 엔드노트를 포함한 문서에 실행하면 다음과 유사한 결과가 표시됩니다:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

문서에 각주나 엔드노트가 없으면 프로그램은 해당 “not found” 메시지를 출력하여 우아한 오류 처리를 보여줍니다.

## 전체 실행 가능한 예제

아래는 새 C# 콘솔 프로젝트에 복사해 넣을 수 있는 완전한 프로그램입니다. 추가 코드가 필요하지 않습니다.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

파일을 `Program.cs`로 저장하고 Aspose.Words NuGet 패키지를 추가(`dotnet add package Aspose.Words`)한 뒤 `dotnet run`을 실행하세요. 프로그램은 구분자 텍스트를 출력하거나 누락된 경우 알려줍니다.

## 일반적인 변형 및 가정 시나리오

| 시나리오 | 코드 적용 방법 |
|----------|-----------------------|
| **Multiple custom separators** | `doc.Footnotes.Separator`를 사용해 기본 구분자를 교체한 뒤 `doc.Footnotes.Add(separatorParagraph)`로 추가 구분자 단락을 수동으로 추가합니다. |
| **Changing separator style** | 구분자를 가져온 뒤 `ParagraphFormat`을 수정합니다(예: `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Working with .doc files** | 동일한 API를 사용하되 파일 경로가 `.doc`으로 끝나는지 확인합니다. |
| **Processing many documents** | 로드 및 구분자 가져오기 로직을 `foreach` 루프로 감싸고, 필요 시 `doc = new Document(path)`로 재설정하여 단일 `Document` 인스턴스를 재사용합니다. |

## 모범 사례 체크리스트

- ✅ **null**을 항상 확인한 후 구분자 텍스트에 접근하세요.  
- ✅ `GetText()` 결과를 **Trim**하여 숨겨진 줄바꿈 문자를 제거합니다.  
- ✅ 배치로 많은 파일을 처리할 경우 큰 `Document` 객체를 **Dispose**하세요(`using` 사용 또는 `doc.Dispose()` 호출).  
- ✅ 개발 단계에서만 구분자 텍스트를 **Log**하고, 필요하지 않은 경우 프로덕션 로그에 노출하지 마세요.  

## 결론

이제 **retrieve endnote separator**를 수행하면서 **load Word document**를 하고, .NET 콘솔 애플리케이션에서 **display footnote separator**를 출력하는 방법을 알게 되었습니다. 전체 예제는 로드, 쿼리 및 누락된 구분자에 대한 안전한 처리를 보여주어, 모든 각주·엔드노트 조작 작업의 견고한 기반을 제공합니다.

다음 단계로 탐색해 볼 수 있는 내용:

* **각주/엔드노트 서식 맞춤** – 글꼴, 테두리 또는 번호 매기기 스타일을 조정합니다.  
* **각주/엔드노트 내용 추출** – `doc.Footnotes` 또는 `doc.Endnotes` 컬렉션을 순회합니다.  
* **수정된 문서 저장** – `doc.Save("output.docx")`를 사용해 변경 사항을 저장합니다.

다양한 Word 파일, 구분자 스타일, Aspose.Words 기능을 마음껏 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움을 줍니다.

- [Aspose.Words LoadOptions를 사용하여 Word 문서 로드하기](/words/english/net/programming-with-loadoptions/)
- [Word 문서에서 단락 스타일 구분자 가져오기](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Aspose.Words for .NET에서 Word 문서 만들기 및 스타일 적용](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}