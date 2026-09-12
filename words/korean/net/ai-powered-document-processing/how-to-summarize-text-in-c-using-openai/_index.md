---
category: general
date: 2026-09-11
description: API 키를 읽고 OpenAI를 호출하여 C#에서 텍스트를 요약하고 Word 문서의 간결한 요약을 생성하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: ko
lastmod: 2026-09-11
og_description: C#에서 텍스트를 요약하는 방법은? 이 튜토리얼에서는 API 키를 읽고, OpenAI를 호출하며, Word 문서의 요약을
  만드는 방법을 보여줍니다.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: OpenAI와 함께 C#에서 텍스트 요약하기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: OpenAI를 사용하여 C#에서 텍스트 요약하는 방법
url: /ko/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 OpenAI를 사용하여 텍스트 요약하기

만약 .docx 파일에서 **텍스트 요약 방법**이 필요하다면, 이 가이드는 완전하고 바로 실행 가능한 솔루션을 보여줍니다. 환경 변수에서 API 키를 읽는 방법, C#에서 OpenAI(또는 Google)를 호출하는 방법, 그리고 Word 문서의 간결한 요약을 만드는 방법을 배웁니다.

Word 문서를 요약하는 것은 보고서 생성, 이메일 요약, 또는 지식베이스 추출 등에서 일반적인 요구사항입니다. 이 튜토리얼을 마치면 제공하는 모든 `.docx` 파일에 대해 다섯 문장 요약을 출력하는 명령줄 프로그램을 갖게 됩니다.

## 사전 요구사항

- .NET 6.0 SDK 또는 그 이후 버전 ([dotnet.microsoft.com](https://dotnet.microsoft.com/download)에서 다운로드)
- 환경 변수 `OPENAI_API_KEY`에 저장된 유효한 OpenAI API 키 (**API 키 읽기**를 확인할 수 있습니다)
- `.docx` 파일을 읽기 위한 `DocumentFormat.OpenXml` NuGet 패키지
- `OpenAI` NuGet 패키지 (또는 Google 제공자를 선호한다면 `Google.AI`)

## 1단계: 프로젝트 설정 및 종속성 설치

새 콘솔 프로젝트를 만들고 필요한 패키지를 추가합니다:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** 나중에 종속성을 추가할 경우 관련 패키지를 `<ItemGroup>` 아래에 그룹화하여 `csproj`를 깔끔하게 유지하세요.

## 2단계: API 키를 안전하게 읽기

시크릿을 하드코딩하는 것은 안전하지 않습니다. 이 튜토리얼은 환경 변수에서 **API 키 읽기**를 수행하는 올바른 방법을 보여줍니다.

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## 3단계: 요약하려는 Word 문서 로드하기

아래 코드는 OpenXML 구조에서 일반 텍스트를 추출하여 **Word 문서 요약 방법**을 보여줍니다.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## 4단계: 재사용 가능한 요약 클래스 만들기

이 클래스는 **OpenAI 호출 방법**(또는 Google) 을 캡슐화하고 **요약 생성 방법** 로직을 구현합니다. 또한 단일 enum 값으로 제공자를 전환할 수 있게 합니다.

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### 이 구조가 중요한 이유

- **관심사 분리:** 문서 로드, API 키 읽기, AI 서비스 호출이 각각의 메서드로 분리됩니다. 이는 코드를 테스트하고 확장하기 쉽게 만듭니다.
- **제공자 유연성:** enum을 사용하면 호출 코드를 수정하지 않고 OpenAI와 Google 사이를 전환할 수 있어, **OpenAI 호출 방법** 및 **요약 생성 방법**에 재사용 가능한 답을 제공합니다.
- **오류 처리:** API 키가 없을 경우 명확한 예외를 발생시켜 무음 실패를 방지합니다.

## 5단계: `Program.cs`에 모든 것을 통합하기

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### 예상 출력

샘플 문서로 프로그램을 실행하면:

```bash
dotnet run -- "sample/input.docx"
```

다음과 같은 결과가 나올 수 있습니다:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## 6단계: 일반적인 변형 및 엣지 케이스

| 상황 | 권장 조정 |
|-----------|------------------------|
| **Large documents** ( > 10 KB ) | 텍스트를 청크로 나누어 각 청크를 요약한 뒤 결과를 결합합니다. |
| **Non‑English content** | 프롬프트에 언어 힌트를 전달합니다. 예: “다음 프랑스어 텍스트 요약 …”. |
| **Google provider** | `SummarizeWithOpenAIAsync` 호출을 해당 Google API 클라이언트로 교체하고, 동일한 enum 인터페이스를 유지합니다. |
| **Custom summary length** | `SummarizeAsync` 호출 시 `maxSentences` 인자를 변경합니다. |
| **Missing API key** | `GetOpenAIApiKey` 메서드는 이미 명확한 예외를 발생시키므로, 더 친절한 메시지를 원한다면 `Main`에서 잡아 처리합니다. |

## 프로덕션 사용을 위한 팁

1. **API 키 캐시** – 매 호출마다 환경에서 읽는 비용은 무시할 수 있지만, 한 프로세스에서 요약기를 여러 번 호출한다면 static readonly 필드에 저장할 수 있습니다.
2. **요청 속도 제한** – OpenAI는 요청 제한을 적용합니다; `429 Too Many Requests`가 발생하면 지수 백오프를 구현하세요.
3. **입력 정제** – 외부 AI 서비스에 텍스트를 보내기 전에 개인 식별 정보를 제거합니다.
4. **추출 로직 단위 테스트** – `WordprocessingDocument`를 모킹하여 다양한 문서 구조에서 `ExtractTextFromDocx`가 올바르게 동작하는지 검증합니다.

## 결론

이제 C#에서 API 키를 안전하게 읽고, OpenAI를 호출하며, Word 문서의 간결한 요약을 생성하는 **텍스트 요약 방법**을 알게 되었습니다. 동일한 패턴을 사용하면 다른 제공자와 함께 **OpenAI 호출 방법**을 사용하고, 다양한 콘텐츠 유형에 대한 **요약 생성 방법** 로직을 구현하며, 환경에서 **API 키 읽기** 값을 안전하게 사용할 수 있습니다. 더 긴 문서, 다른 제공자, 혹은 맞춤 프롬프트를 실험하여 요약을 특정 도메인에 맞게 조정해 보세요.

---

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 동작 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [C#에서 Aspose.Words API를 사용한 Word 문서 요약 – 완전한 AI 기반 가이드](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Word에서 PDF 만들기 – 완전한 C# 가이드](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word 문서 - 내용 제거 방법](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}