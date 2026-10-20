---
category: general
date: 2026-08-07
description: Aspose.Words for .NET를 사용하여 각주 구분자를 가져옵니다. 각주 및 미주 구분자를 추출하고, 노드 유형을
  검사하며, C#에서 수정하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: ko
lastmod: 2026-08-07
og_description: Aspose.Words for .NET을 사용하여 각주 구분자를 가져옵니다. 이 가이드는 각주 및 미주 구분자를 추출하고,
  해당 노드 유형을 확인하며, 변경 사항을 저장하는 방법을 보여줍니다.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: C#에서 각주 구분자 가져오기 – 단계별 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: C#에서 각주 구분자 가져오기 – 완전한 Aspose.Words 가이드
url: /ko/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 각주 구분자 가져오기 – 전체 Aspose.Words 가이드

Word 문서에서 **retrieve footnote separator**를 가져와야 한다면, 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 정확히 수행하는 방법을 보여줍니다. 문서 처리 서비스를 구축하거나 각주 서식을 정리하고자 할 때, 각주와 미주 구분자를 모두 추출하는 전체 실행 가능한 예제를 확인할 수 있습니다.

이 가이드에서는 `.docx` 파일을 로드하고, `FootnoteSeparator`와 `EndnoteSeparator` 속성을 호출하며, 반환된 `Node` 객체를 검사하고, 필요에 따라 구분자 라인을 교체하는 방법을 배웁니다. 외부 문서는 필요하지 않으며, 아래에 필요한 모든 내용이 포함되어 있습니다.

## Prerequisites

* .NET 6.0 이상 (코드는 .NET Framework 4.7.2에서도 작동합니다)
* Aspose.Words for .NET NuGet 패키지 (버전 24.9 이상)
* 각주 및/또는 미주가 포함된 Word 문서 (예: `Footnotes.docx`)

Aspose.Words 패키지는 다음 CLI 명령으로 추가할 수 있습니다:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Step 1: Set up the project and import namespaces

새 콘솔 프로젝트를 만들거나 기존 프로젝트에 코드를 추가합니다. 필요한 `using` 지시문은 아래에 나와 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

이 네임스페이스들을 통해 **retrieve footnote separator** 작업에 필요한 `Document` 클래스, `Node` 계층 구조, `NodeType` 열거형에 접근할 수 있습니다.

## Step 2: Load the document that contains footnotes and endnotes

Aspose.Words 워크플로우에서 가장 먼저 수행하는 작업은 소스 파일을 로드하는 것입니다. 자리표시자 경로를 실제 `.docx` 파일 위치로 교체하십시오.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

파일을 로드하면 내부 노드 트리가 준비되며, 이는 구분자 노드가 해당 트리 안에 존재하기 때문에 **retrieve footnote separator**에 필수적입니다.

## Step 3: Retrieve the footnote separator node

이제 `Document` 객체의 `FootnoteSeparator` 속성을 사용하여 **retrieve footnote separator**를 할 수 있습니다. 이 노드는 각주를 본문 텍스트와 구분하는 라인을 나타냅니다.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

표준 구분자 라인의 경우 `NodeType`은 `Paragraph`가 됩니다. 노드 유형을 알면 구분자를 수정하거나 완전히 교체해야 하는지 판단하는 데 도움이 됩니다.

## Step 4: Retrieve the endnote separator node

마찬가지로 `EndnoteSeparator` 속성을 사용하여 **retrieve endnote separator**를 할 수 있습니다. 이 노드는 미주를 본문 내용과 구분합니다.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

대부분의 문서에서 두 구분자 노드는 동일한 `NodeType`(`Paragraph`)을 공유하지만, 각각 독립적으로 사용자 정의할 수 있습니다.

## Step 5: Inspect or modify the separator content (optional)

구분자의 시각적 모습을 변경해야 하는 경우—예를 들어 대시 라인을 얇은 규칙선으로 교체—`Paragraph` 노드를 직접 편집할 수 있습니다. 아래 예시는 기본 구분자 텍스트를 사용자 정의 문자열로 교체하는 방법을 보여줍니다.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

노드를 수정한 후에는 문서를 저장하여 Word에서 변경 사항이 반영되는지 확인할 수 있습니다.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Expected console output

원본 `Footnotes.docx` 파일로 프로그램을 실행하면 다음과 유사한 출력이 표시됩니다:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

`Footnotes_Updated.docx`를 Microsoft Word에서 열면 각주와 미주 구분자가 삽입한 사용자 정의 텍스트로 표시됩니다.

## Common questions and edge cases

**What if the document has no footnotes?**  
`FootnoteSeparator` 속성은 Word가 항상 구분자 자리표시자를 포함하기 때문에 `Paragraph` 노드를 반환합니다. 노드가 비어 있으므로 안전하게 내용을 추가하거나 그대로 둘 수 있습니다.

**Can I retrieve the separator for a specific section?**  
각주와 미주 구분자는 문서 전체에 적용되며 섹션별로 구분되지 않습니다. 섹션 수준 제어가 필요하면 전역 구분자 노드 대신 `Section.FootnoteOptions`와 `Section.EndnoteOptions`를 사용해야 합니다.

**Does this work with .NET Core?**  
예. Aspose.Words for .NET은 크로스‑플랫폼이며, 동일한 코드를 Windows, Linux, macOS에서 .NET 6 이상으로 실행할 수 있습니다.

**What node type should I expect?**  
`FootnoteSeparator`와 `EndnoteSeparator` 모두 `Paragraph` 노드(`NodeType.Paragraph`)를 반환합니다. 다른 유형이 반환되면 문서가 손상되었을 수 있으므로 파일을 다시 로드하거나 검증해야 합니다.

## Full source code for quick copy‑paste

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

코드를 `Program.cs` 파일에 복사하고 파일 경로를 조정한 뒤 `dotnet run`을 실행하십시오. 이 프로그램은 **retrieve footnote separator** 워크플로우 전체를 보여주며, 문서 로드부터 변경 내용 저장까지를 포함합니다.

## Conclusion

이제 Aspose.Words for .NET을 사용하여 **retrieve footnote separator**와 **endnote separator retrieval**을 수행하고, `document node type`을 검사하며, 필요에 따라 내용을 교체하는 방법을 알게 되었습니다. 이 기술을 활용하면 각주 서식을 자동화하고, 사용자 정의 구분자 라인을 생성하거나, 모든 C# 애플리케이션에서 문서 구조를 검증할 수 있습니다.

다음으로는 개별 각주 텍스트를 추출하는 **C# footnote extraction**이나 `FootnoteOptions`를 사용해 **modify footnote reference marks**를 배우는 등 관련 주제를 탐색해 볼 수 있습니다. 두 개념 모두 여기서 다룬 노드‑트리 기본에 직접 기반합니다.

행복한 코딩 되시고, 프로젝트 브랜드에 맞게 다양한 구분자 스타일을 실험해 보세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하도록 돕습니다.

- [각주 및 미주와 함께하는 워드 처리](/words/english/net/working-with-footnote-and-endnote/)
- [Aspose.Words for .NET에서 Document Builder를 사용한 콘텐츠 추가](/words/english/net/add-content-using-document-builder/)
- [각주와 미주 작업하기](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}