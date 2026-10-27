---
category: general
date: 2026-08-10
description: Aspose.Words를 사용해 C#에서 각주 구분자를 형식화하고 각주와 미주 라인을 사용자 지정하세요. 몇 분 만에 C#
  각주 서식을 배울 수 있습니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: ko
lastmod: 2026-08-10
og_description: Aspose.Words를 사용하여 C#에서 각주 구분자를 포맷합니다. 이 튜토리얼을 따라 각주 및 미주 구분자를 빠르고
  안정적으로 스타일링하세요.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: C#에서 각주 구분자 서식 지정 – 완전한 Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: C#에서 Aspose.Words를 사용해 각주 구분자 서식 지정
url: /ko/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Aspose.Words를 사용하여 각주 구분선 서식 지정

Word 문서에서 **각주 구분선 서식**을 지정해야 하는 경우, 이 가이드는 Aspose.Words for .NET을 사용하여 수행하는 방법을 보여줍니다. 구분선 단락의 정렬과 색상을 변경하는 완전한 실행 예제를 확인하고, 동일한 기술을 종주 구분선에 적용하는 방법도 배울 수 있습니다.

이 튜토리얼은 소스 파일 로드부터 수정된 문서 저장까지 모든 단계를 다루므로, 추가 조사 없이 코드를 복사‑붙여넣기만 하면 자신의 프로젝트에 바로 적용할 수 있습니다.

## 준비 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요.

* .NET 6.0 이상 (.NET Framework 4.6+에서도 동작)
* 유효한 Aspose.Words for .NET 라이선스 (평가용 무료 체험 가능)
* 최소 하나의 각주 또는 종주가 포함된 Word 파일 (예: `Footnotes.docx`)
* Visual Studio 2022 또는 선호하는 C# IDE

이 항목들을 미리 준비하면 **C# 각주 서식** 로직에 집중할 수 있고 환경 설정에 시간을 낭비하지 않아도 됩니다.

## Step 1: 각주 및 종주가 포함된 문서 로드

첫 번째 작업은 소스 파일을 가리키는 `Document` 객체를 생성하는 것입니다. Aspose.Words는 전체 DOCX 패키지를 메모리로 읽어들여 각주와 종주 노드에 완전한 접근 권한을 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*왜 중요한가*: 문서를 로드해야만 어떤 조작도 가능해집니다. 파일 경로가 잘못되면 Aspose.Words가 `FileNotFoundException`을 발생시키므로, 진행하기 전에 경로를 반드시 확인하세요.

## Step 2: 구분선 및 연속 구분선 노드 가져오기

각주와 종주 구분선은 각각 `Footnotes`와 `Endnotes` 컬렉션 내부에 특수 노드로 저장됩니다. 각 컬렉션은 `Separator`와 `ContinuationSeparator` 속성을 제공하며, 이는 `Node` 참조를 반환합니다.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*왜 중요한가*: `Separator` 노드는 본문 텍스트와 각주 블록을 시각적으로 구분하는 선을 나타냅니다. 해당 노드에 대한 참조를 얻으면 단락 서식, 글꼴을 수정하거나 노드를 완전히 교체할 수 있습니다.

## Step 3: 각주 구분선의 시각적 스타일 변경

대부분의 Word 문서에서 구분선은 대시(–)나 별표(*)가 들어간 단일 단락으로 구성됩니다. 아래 코드는 구분선이 `Paragraph`인지 확인하고, 맞다면 가운데 정렬하고 텍스트 색상을 회색으로 바꿉니다.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### 연속 구분선 스타일 지정 (선택 사항)

각주가 여러 페이지에 걸쳐 이어질 때 표시되는 연속 구분선도 동일하게 스타일을 지정할 수 있습니다.

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*왜 중요한가*: 구분선을 정렬하면 가독성이 향상되고, 색상을 변경하면 일반 단락 텍스트와 구분이 명확해집니다. `ParagraphAlignment.Center`를 `Left` 또는 `Right`로 교체하면 문서 디자인 가이드라인에 맞출 수 있습니다.

## Step 4: 수정된 문서 저장

원하는 스타일을 적용한 후, 문서를 디스크에 다시 기록합니다. 원본 파일을 덮어쓰거나 새 버전을 만들 수 있습니다.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

`Footnotes_Styled.docx`를 Microsoft Word에서 열면, 각주 구분선이 코드에서 지정한 대로 가운데 정렬되고 회색으로 표시됩니다.

## 고급 변형

### 종주 구분선 서식 지정

문서에 종주가 포함되어 있다면, 동일한 로직을 `Endnotes` 컬렉션에 적용할 수 있습니다.

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### 구분선에 사용자 정의 문자열 사용

구분선을 별표(`***`) 시리즈로 표시하고 싶을 때는 기존 Run을 새로운 Run으로 교체합니다.

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### 구분선 노드가 없는 문서 처리

드물게 구분선 노드가 삭제된 문서가 있을 수 있습니다(예: 작성자가 직접 삭제). 이 경우 `document.Footnotes.Separator`는 `null`을 반환하므로, 이를 방지하는 코드를 작성해야 합니다.

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## 흔히 발생하는 문제와 해결 방법

| 문제점 | 발생 원인 | 해결 방법 |
|---------|----------------|-----|
| **Separator가 `Paragraph`가 아님** | 일부 Word 템플릿은 구분선으로 `Table`이나 `Shape`을 사용합니다. | 캐스팅하기 전에 `is Paragraph`로 노드 유형을 확인합니다. |
| **`Runs` 컬렉션이 비어 있음** | 구분선이 빈 단락일 수 있습니다. | `Runs[0]`에 접근하기 전에 `Runs.Count > 0`을 확인합니다. |
| **라이선스 미적용** | 라이선스가 없으면 Aspose.Words가 워터마크를 삽입하고 API 사용을 제한할 수 있습니다. | 프로그램 시작 시 `License license = new License(); license.SetLicense("Aspose.Words.lic");`를 호출합니다. |
| **읽기 전용 폴더에 저장** | `Save` 메서드가 `UnauthorizedAccessException`을 발생시킵니다. | 대상 디렉터리에 쓰기 권한이 있는지 확인합니다. |

이러한 문제들을 사전에 해결하면 런타임 예외를 방지하고 **각주 구분선 수정** 작업을 원활하게 진행할 수 있습니다.

## 완전한 실행 예제

아래는 앞서 설명한 모든 단계를 포함한 독립 실행형 콘솔 애플리케이션 예제입니다. 코드를 새 .NET 콘솔 프로젝트에 복사하고 파일 경로만 교체한 뒤 실행하세요.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**예상 결과**  

`Footnotes_Styled.docx`를 열면:

* 각주 구분선이 본문 텍스트 아래 가운데 정렬됩니다.  
* 색상이 연한 회색으로 표시되어 시각적으로 구분됩니다.  
* 문서에 종주가 포함된 경우, 종주 구분선도 동일하게 가운데 정렬되고 회색(또는 슬레이트 색)으로 표시됩니다.

## 다음에 학습할 내용은?

아래 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 추가 API 기능을 마스터하고 다양한 구현 방법을 탐색하는 데 도움이 됩니다.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}