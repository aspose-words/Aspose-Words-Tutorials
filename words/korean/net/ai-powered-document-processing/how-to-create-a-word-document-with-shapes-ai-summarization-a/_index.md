---
category: general
date: 2026-11-25
description: Aspose.Words를 사용하여 Word 문서를 만들고, 사각형 도형을 추가하고, AI로 문서를 요약하고, AI를 이용해
  텍스트를 번역한 뒤 DOCX 형식으로 저장하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: ko
lastmod: 2026-11-25
og_description: Word 문서를 생성하고, 사각형 도형을 추가한 뒤, AI로 문서를 요약하고, AI를 사용해 텍스트를 번역하며, DOCX
  형식으로 저장하는 모든 과정을 하나의 C# 튜토리얼에서 수행합니다.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: C#에서 도형, AI 요약 및 번역이 포함된 Word 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: C#에서 도형, AI 요약 및 번역이 포함된 Word 문서 만드는 방법
url: /ko/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 도형, AI 요약 및 번역이 포함된 Word 문서 만들기

프로그램matically **Word 문서**를 **생성**해야 할 때, 이 가이드는 정확한 방법을 보여줍니다. Aspose.Words for .NET을 사용하여 **사각형 도형 추가**, AI 서비스를 호출해 **문서 요약**, **AI를 이용한 텍스트 번역**, 그리고 최종적으로 **DOCX 형식으로 저장**하는 방법을 배웁니다.

많은 개발자가 문서 자동화와 최신 AI 기능을 연결하는 데 어려움을 겪습니다. 이 튜토리얼을 마치면, 시각적 도형, AI‑생성 요약, 다국어 콘텐츠가 포함된 완전한 *.docx* 파일을 생성하는 **단일 C# 프로젝트**를 손에 넣게 됩니다.

## Prerequisites

시작하기 전에 다음이 설치되어 있는지 확인하세요:

- .NET 6.0 SDK 이상  
- Visual Studio 2022 (또는 기타 C# IDE)  
- Aspose.Words for .NET 라이선스(또는 무료 평가 키)  
- AI 요약 및 번역 호출을 위한 인터넷 연결  

`Aspose.Words`와 `Aspose.Words.AI` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Step 1: Set up the project and add required packages

새 콘솔 프로젝트를 만들고 Aspose.Words 라이브러리를 가져옵니다.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** 평가 모드를 사용할 경우, 워터마크를 방지하려면 `Main` 초기에 `Aspose.Words.License.SetLicense("Aspose.Words.lic");` 를 호출하세요.

## Step 2: Initialize the document – the core of **create word document**

첫 번째 실행 가능한 코드는 새로운 **Word 문서** 객체를 생성합니다. 이 객체는 이후 모든 작업의 캔버스가 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder`는 텍스트, 도형, 컨트롤을 저수준 노드 트리를 직접 다루지 않고도 삽입할 수 있게 해줍니다.

## Step 3: **Add rectangle shape** to the document

사각형 도형은 시각적 자리표시자, 레이블 배경, 혹은 간단한 그래픽으로 사용할 수 있습니다. 먼저 `GroupShape`를 만들고 그 안에 `Rectangle`을 삽입합니다.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

사각형은 너비 100포인트, 높이 50포인트입니다. `GroupShape` 내부에 존재하기 때문에 나중에 텍스트 박스 등 다른 요소를 추가해도 레이아웃 충돌을 걱정할 필요가 없습니다.

## Step 4: Insert a plain‑text StructuredDocumentTag (SDT)

`StructuredDocumentTag` 객체는 나중에 데이터 소스와 바인딩할 수 있는 콘텐츠 컨트롤에 유용합니다.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true` 플래그는 해당 태그를 **반복** 컨트롤로 표시하며, 템플릿에 적합합니다.

## Step 5: Add an ActiveX CommandButton control (optional UI)

생성된 문서를 ActiveX를 지원하는 환경에서 사용할 경우, 버튼을 삽입할 수 있습니다.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

이 단계는 선택 사항이며, 대상 사용자가 Windows 환경에서 문서를 전혀 사용하지 않을 경우 제거해도 됩니다.

## Step 6: **Summarize document with AI**

Aspose.Words.AI는 대형 언어 모델 서비스를 편리하게 래핑해 줍니다. 여기서는 OpenAI 백엔드를 사용해 `DocumentSummarizer.Summarize`를 호출합니다.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

이 메서드는 현재 노드 트리를 분석하고 가장 관련성 높은 문장을 추출해 간결한 단락을 반환합니다. 바로 **summarize document with AI** 기능의 핵심입니다.

## Step 7: **Translate text using AI**

다음 예제에서는 영어 문자열을 프랑스어로 번역하는 방법을 보여줍니다. `Translator.Translate` 메서드는 내부적으로 Google AI 모델을 호출합니다.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

`Language.French`를 지원되는 다른 언어 열거형 값으로 교체하면, 실행 시 다국어 문서 생성을 손쉽게 구현할 수 있습니다.

## Step 8: **Save document as DOCX**

마지막으로 편집된 문서를 디스크에 저장합니다. `.docx` 확장자를 지정하면 `Save` 메서드가 자동으로 *.docx* 파일을 생성합니다.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

`Result.docx` 파일에는 이제 다음이 포함됩니다:

- 그룹 도형 안의 사각형 도형  
- 일반 텍스트 콘텐츠 컨트롤 (SDT)  
- ActiveX CommandButton (Step 5를 유지한 경우)  
- AI‑생성 요약 단락  
- “Hello world”의 프랑스어 번역  

Microsoft Word에서 파일을 열어 각 요소를 확인할 수 있습니다.

## Complete source code

아래는 전체 실행 가능한 프로그램입니다. `Program.cs`에 복사하고 `dotnet run`을 실행하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Expected output

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

`Result.docx`를 열면 상단에 사각형 도형, SDT 자리표시자, 버튼, 요약 단락, 그리고 프랑스어 번역 텍스트가 삽입된 것을 볼 수 있습니다.

## Conclusion

이제 **Word 문서 생성**, **사각형 도형 추가**, **AI로 문서 요약**, **AI로 텍스트 번역**, 그리고 **DOCX로 저장**을 몇 줄의 C# 코드만으로 구현하는 방법을 알게 되었습니다. 이 패턴은 확장성이 뛰어나며, 하드코딩된 문자열을 동적 데이터로 교체하고, 더 많은 도형이나 차트를 추가하거나, `SummarizerOptions` 혹은 `Translator` 매개변수를 조정해 AI 공급자를 교체할 수 있습니다.

### What’s next?

- **add rectangle shape** 변형 탐색: 채우기 색상, 선 스타일 변경 또는 도형 내부에 텍스트 추가  
- 더 큰 문서에 **summarize document with AI** 적용해 자동으로 요약문 생성  
- **translate text using AI**를 확장해 전체 단락이나 표를 일괄 번역, 다국어 보고서 작성  
- Aspose.Words 차트 API와 결합해 AI‑생성 인사이트와 함께 데이터 시각화 삽입  

실험해 보고 결과를 댓글이나 GitHub에 공유하세요. 즐거운 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}