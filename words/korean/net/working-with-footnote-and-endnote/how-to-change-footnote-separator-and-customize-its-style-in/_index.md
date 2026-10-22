---
category: general
date: 2026-10-13
description: Aspose.Words를 사용하여 Word 문서에서 각주 구분자를 변경하는 방법. 프로그래밍으로 Word 문서의 글꼴 색상을
  변경하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: ko
lastmod: 2026-10-13
og_description: Aspose.Words를 사용하여 Word 문서에서 각주 구분자를 변경하는 방법. 이 튜토리얼에서는 C#를 사용하여 Word
  문서의 글꼴 색상을 변경하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Word 문서에서 각주 구분 기호 변경 방법 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Word 문서에서 각주 구분자를 변경하고 스타일을 사용자 정의하는 방법
url: /ko/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 각주 구분선 변경 및 스타일 사용자 지정 방법

Word 문서에서 **각주 구분선을 변경하는 방법**이 필요하다면, 이 가이드는 완전하고 바로 실행할 수 있는 솔루션을 제공합니다. Aspose.Words for .NET을 사용하면 **Word 문서에서 글꼴 색상 변경**과 같은 요소(각주 및 미주 구분선)를 변경하여 최종 파일을 브랜드나 스타일 가이드에 맞출 수 있습니다.

문서 작성자들은 종종 이렇게 묻습니다: *기본 각주 구분선이 왜 단조롭게 보이고, 어떻게 하면 눈에 띄게 만들 수 있을까요?* 답은 구분선 단락 객체에 직접 접근하여 글꼴 속성을 조정하고 결과를 저장하는 것입니다. 이 튜토리얼은 .docx 파일을 로드하는 단계부터 스타일이 적용된 출력을 저장하는 단계까지 모든 과정을 안내합니다.

다음과 같은 내용을 배웁니다:

* 이미 각주와 미주가 포함된 Word 파일을 로드합니다.  
* 각주 및 미주 구분선 단락을 찾습니다.  
* 각 구분선의 글꼴 색상을 변경합니다(각주는 빨간색, 미주는 파란색).  
* 기존 내용을 잃지 않고 수정된 문서를 저장합니다.

Aspose.Words 라이브러리와 .NET 개발 환경 외에 별도의 외부 도구는 필요하지 않습니다.

## 사전 요구 사항

* .NET 6.0 SDK 이상(코드는 .NET Framework 4.7+에서도 작동합니다).  
* Visual Studio 2022, Rider 또는 원하는 C# 편집기.  
* Aspose.Words for .NET NuGet 패키지(`Aspose.Words`).  
* 하나 이상의 각주와 미주가 포함된 샘플 Word 파일(`Footnotes.docx`).

> **Pro tip:** 샘플 파일이 없으면 새 Word 문서를 만들고, 각주(`References → Insert Footnote`)와 미주(`References → Insert Endnote`)를 삽입하세요. 코드를 통해 참조할 수 있는 폴더에 `Footnotes.docx`로 저장합니다.

## Aspose.Words를 사용하여 각주 구분선 변경 방법

작업의 핵심은 Aspose.Words가 *separator* 노드로 노출하는 특수 단락을 가져오는 것입니다. 이러한 노드는 `Paragraph` 유형이며 다른 단락과 마찬가지로 서식 지정이 가능합니다.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### 각 라인이 중요한 이유

* **문서 로드** (`new Document`)는 Aspose.Words가 조작할 수 있는 메모리 내 표현을 제공합니다.  
* `ParagraphNodeType.FootnoteSeparator`와 함께 **`GetChild`**를 사용하면 Word가 각주와 본문을 구분하는 선을 그리기 위해 사용하는 숨겨진 단락을 반환합니다. 동일한 메서드는 미주 구분선에도 적용됩니다.  
* **`Font.Color` 변경**은 Word가 구분선을 단일 “‑” 문자로 된 단락으로 렌더링하기 때문에 라인의 모양에 직접 영향을 줍니다. 색상을 `Color.Red`(또는任意 `System.Drawing.Color`)로 설정하면 시각적 스타일이 업데이트됩니다.  
* **저장**은 변경 사항을 모든 워드 프로세서가 열 수 있는 .docx 파일에 기록합니다.

### 예상 출력

Microsoft Word에서 `FootnoteSeparatorsStyled.docx`를 열면:

* 각주 구분선이 **빨간색**으로 표시됩니다.  
* 미주 구분선이 **파란색**으로 표시됩니다.  
* 원래의 모든 각주 및 미주 내용은 그대로 유지됩니다.

## C#를 사용하여 Word 문서에서 글꼴 색상 변경

위에서 보여준 작업은 보다 광범위한 기능의 특정 사례이며, 프로그래밍 방식으로 **Word 문서에서 글꼴 색상 변경**을 할 수 있습니다. `Paragraph`, `Run` 또는 텍스트를 포함하는任意 `Node`를 얻으면 해당 `Font.Color` 속성을 조정할 수 있습니다.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* 이 스니펫은 모든 단락을 반복하면서 `Heading 1` 스타일을 사용하는지 확인하고 글꼴 색상을 설정합니다.  
* 조건을 변경하여 각주, 표 또는 다른 노드 유형을 대상으로 할 수 있습니다.

## 단계별 분석

### 1. Aspose.Words 설치

프로젝트 폴더에서 터미널을 열고 다음을 실행합니다:

```bash
dotnet add package Aspose.Words
```

이 패키지는 앞서 보여준 코드에 필요한 모든 어셈블리를 포함합니다.

### 2. 입력 파일 준비

`Footnotes.docx`를 알려진 디렉터리(예: `C:\Docs`)에 배치합니다. 파일에 최소 하나의 각주와 하나의 미주가 포함되어 있어 구분선 노드가 존재하도록 합니다.

### 3. C# 프로그램 작성

새 콘솔 프로젝트(`dotnet new console -n FootnoteStyler`)를 만들고 생성된 `Program.cs`를 **각주 구분선 변경** 섹션의 전체 코드 블록으로 교체합니다. 파일 경로를 환경에 맞게 조정하는 것을 잊지 마세요.

### 4. 실행 및 확인

프로그램을 실행합니다:

```bash
dotnet run
```

실행이 완료되면 `FootnoteSeparatorsStyled.docx`를 엽니다. 설명된 대로 빨간색과 파란색 구분선이 표시되어야 합니다.

### 5. 솔루션 확장

* **다른 색상:** 任意 `System.Drawing.Color` 값을 사용할 수 있습니다. 예: 주황색은 `Color.FromArgb(255, 128, 0)`.  
* **맞춤 선 스타일:** 색상을 변경하는 대신 `ParagraphFormat` 속성(`LineSpacing`, `Shading` 등)을 수정하거나 구분자 문자를 교체할 수 있습니다.  
* **다중 문서:** 입력 및 출력 경로를 매개변수로 받는 메서드로 로직을 감싸고, 배치 처리를 위해 루프에서 호출합니다.

## 일반적인 함정 및 회피 방법

| 증상 | 원인 | 해결 방법 |
|------|------|----------|
| `GetChild`가 `null`을 반환 | 원본 문서에 각주/미주 구분선이 없음(예: 각주가 없음). | 최소 하나의 각주 또는 미주를 추가하거나 `Font`에 접근하기 전에 `null`을 확인합니다. |
| 색상 변경이 보이지 않음 | 일부 Word 버전에서는 구분선이 문자 대신 선으로 렌더링됩니다. | `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly`와 `ParagraphFormat.LineSpacing = 1`을 설정하여 보이는 문자를 강제합니다. |
| 런타임 예외 `FileNotFoundException` | 파일 경로가 잘못되었습니다. | 절대 경로를 사용하거나 `Environment.CurrentDirectory`와 `Path.Combine`을 활용합니다. |

## 전체 실행 가능한 예제

아래는 콘솔 앱에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 오류 처리와 각 작업을 설명하는 주석이 포함되어 있습니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

이 프로그램을 실행하면 각주 구분선이 빨간색, 미주 구분선이 파란색인 Word 파일이 생성되어 **각주 구분선 변경 방법** 요구사항을 충족하고 **Word 문서에서 글꼴 색상 변경**을 보여줍니다.

## 결론

이제 Aspose.Words for .NET을 사용하여 Word 문서에서 **각주 구분선 변경 방법**과 **Word 문서에서 글꼴 색상 변경**을 프로그래밍 방식으로 수행하는 방법을 알게 되었습니다. 접근 방법은 다음과 같습니다:

1. 문서를 로드합니다.  
2. 숨겨진 구분선 단락을 가져옵니다.  
3. `Font.Color` 속성을 설정합니다.  
4. 수정된 파일을 저장합니다.

여기서부터는 선 두께 조정, 다른 글꼴 적용, 다수 파일에 대한 자동화 등 보다 고급 스타일링을 탐색할 수 있습니다. 이러한 기술을 마스터하면 C# 코드만으로 Word 문서의 외관을 세밀하게 제어할 수 있습니다.

---


## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 보여준 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Word 문서에서 단락 스타일 구분자 가져오기](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Aspose.Words를 사용하여 머리글 및 바닥글이 있는 Word 문서 만들기](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET을 사용하여 Word 문서 바닥글에 페이지 번호 추가](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}