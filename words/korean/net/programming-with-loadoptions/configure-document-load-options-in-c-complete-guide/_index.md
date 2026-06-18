---
category: general
date: 2026-06-05
description: C#에서 문서 로드 옵션을 구성하여 글꼴 대체 경고를 처리하고 경고 콜백을 사용해 로드 동작을 사용자 지정합니다.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: ko
og_description: C#에서 문서 로드 옵션을 구성하여 글꼴 대체 경고를 관리하고 경고 콜백으로 문서 로드를 세밀하게 조정합니다.
og_title: C#에서 문서 로드 옵션 구성 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: C#에서 문서 로드 옵션 구성 – 완전 가이드
url: /ko/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 문서 로드 옵션 구성 – 완전 가이드

기본 로딩 동작이 만족스럽지 않아 C#에서 **문서 로드 옵션을 구성**해야 했던 적이 있나요? 예상치 못한 글꼴 대체가 나타나거나 파일 가져오기 중에 발생하는 모든 경고를 기록하고 싶을 수도 있습니다. 이 튜토리얼에서는 옵션을 설정할 뿐만 아니라 글꼴 대체 경고에 대한 **경고 콜백**을 보여주는 실용적인 엔드‑투‑엔드 솔루션을 단계별로 살펴보겠습니다.

우리는 콜백을 생성하는 작은 코드 스니펫부터 사용자 정의 설정으로 문서를 실제로 여는 순간까지 모든 것을 다룰 것입니다. 끝까지 진행하면 인보이스, 법률 계약서, 간단한 보고서 등 어떤 Aspose.Words 프로젝트에도 적용할 수 있는 재사용 가능한 패턴을 얻게 됩니다.

## 배울 내용

- `LoadOptions` 로 **문서 로드 옵션을 구성**하는 방법.
- `FontSubstitution` 알림을 포착하는 **경고 콜백** 구현 방법.
- 왜 **글꼴 대체 경고**를 초기에 처리하는 것이 레이아웃 문제를 방지할 수 있는지.
- 누락된 글꼴에 대한 엣지 케이스 처리 및 우아한 폴백 방법.
- 오늘 바로 실행할 수 있는 완전한 복사‑붙여넣기 가능한 코드 샘플.

### 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 작동합니다).
- Aspose.Words for .NET 설치 (`dotnet add package Aspose.Words`).
- C# 구문에 대한 기본적인 이해.

준비가 되셨다면, 시작해봅시다.

## 문서 로드 옵션 구성 – 단계별

아래는 네 개의 명확한 단계로 나눈 전체 워크플로우입니다. 각 단계는 설명 뒤에 Visual Studio에 바로 붙여넣을 수 있는 간결한 코드 블록이 따라옵니다.

### 단계 1: 글꼴 대체를 위한 경고 콜백 구현

먼저—**경고 콜백**이란 무엇일까요? Aspose.Words에서 이것은 라이브러리가 누락된 글꼴과 같이 플래그를 달아야 할 상황을 마주할 때마다 호출되는 대리자(delegate)입니다. `WarningType.FontSubstitution` 을 포착함으로써 엔진이 교체한 정확한 글꼴을 기록할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**왜 중요한가:** 콜백이 없으면 라이브러리는 누락된 글꼴을 조용히 교체하여 최종 PDF나 DOCX에서 텍스트가 깨질 수 있습니다. 경고를 표면에 드러내면 가시성을 확보하고, 누락된 글꼴을 포함시킬지, 폴백으로 전환할지, 사용자에게 알릴지를 결정할 수 있습니다.

> **Pro tip:** 모든 경고를 캡처해야 한다면 `if` 검사를 제거하세요. 모든 이벤트에 대해 `warningInfo.Description` 을 로그에 남기면 됩니다.

### 단계 2: 콜백과 함께 LoadOptions 설정

이제 콜백이 준비되었으니 실제로 사용하도록 **문서 로드 옵션을 구성**해야 합니다. `LoadOptions` 는 `Document` 생성자 호출 중 Aspose.Words 가 어떻게 동작할지를 알려주는 가벼운 컨테이너입니다.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**왜 중요한가:** `WarningCallback` 을 할당하면 로드 단계에서 발생하는 모든 경고가 우리 대리자를 통해 전달됩니다. 여기서 `LoadFormat` (정확한 파일 형식을 알고 있을 때)이나 암호화된 문서를 위한 `Password` 등 다른 `LoadOptions` 속성도 조정할 수 있습니다.

### 단계 3: 구성된 옵션을 사용해 문서 로드

콜백이 연결되었으니 이제 실제로 **문서를 로드**할 차례입니다. `Document` 생성자는 파일 경로와 방금 준비한 `LoadOptions` 를 받아들입니다.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

소스 파일이 머신에 설치되지 않은 글꼴을 참조하면 콘솔에 다음과 같은 라인이 표시됩니다:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

이 즉각적인 피드백을 통해 누락된 글꼴을 앱과 함께 배포할지, 프로그래밍 방식으로 교체할지를 결정할 수 있습니다.

### 단계 4: 선택 사항 – 로드된 글꼴 검증 (엣지 케이스 처리)

특히 배치 처리 시나리오에서 문서를 완전히 로드하기 전에 *사전 검증*하고 싶을 때가 있습니다. Aspose.Words 는 필요한 글꼴을 열거할 수 있는 `FontSettings` 클래스를 제공합니다.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**사용 시점:** 사내 브랜드 글꼴과 같은 개인 글꼴 저장소를 관리한다면 `FontSettings` 를 해당 폴더에 지정해 엔진이 일반 글꼴로 폴백되지 않고 올바른 서체를 찾도록 할 수 있습니다.

## 전체 작업 예제

아래는 전체 프로그램입니다—복사, 붙여넣기, 실행만 하면 됩니다. 콜백 생성부터 최종 문서 로드까지 모든 과정을 보여줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**예상 출력**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

누락된 글꼴이 없으면 콜백은 조용히 동작합니다—걱정할 필요가 없습니다.

## 일반 질문 및 엣지 케이스

### 경고 콜백이 예외를 발생시키면 어떻게 되나요?

콜백은 문서를 로드하는 동일한 스레드에서 실행됩니다. 대리자 내부에서 예외를 발생시키면 로드가 중단되고 예외가 전파됩니다. 복원력이 필요하면 로직을 `try/catch` 로 감싸세요.

### 모든 경고를 처리하지 않고 억제할 수 있나요?

예—`loadOptions.WarningCallback = null;` 로 설정하거나 아무 작업도 하지 않는 콜백을 제공하면 됩니다. 다만 잠재적인 문제에 대한 가시성을 잃게 됩니다.

### 암호화된 DOCX 파일에서도 작동하나요?

물론입니다. `Document` 를 만들기 전에 `LoadOptions` 에 `Password = "yourPassword"` 를 추가하면 됩니다. 글꼴 문제에 대한 경고 콜백은 여전히 작동합니다.

### `DocumentBuilder` 사용과는 어떻게 다릅니까?

`DocumentBuilder` 는 문서를 로드한 후 *생성*하거나 *수정*할 때 사용합니다. **문서 로드 옵션 구성** 은 *초기* 파싱 단계에 영향을 주며, 여기서 글꼴 대체 결정이 이루어집니다.

## 시각적 개요

![문서 로드 옵션 구성 흐름을 보여주는 다이어그램](https://example.com/images/load-options-flow.png "문서 로드 옵션 구성 흐름을 보여주는 다이어그램")

*이미지는 흐름을 보여줍니다: 콜백 → LoadOptions → Document 생성자 → 경고 처리.*

## 결론

이제 C#에서 **문서 로드 옵션을 구성**하여 글꼴 대체 경고를 포착하고, 사용자 정의 글꼴 폴더를 주입하며, 로드 프로세스를 완전히 제어하는 방법을 알게 되었습니다. 이 패턴을 사용하면 누락된 모든 글꼴이 보고되어 어떤 환경에서도 문서 충실도를 유지할 수 있습니다.

다음 단계는? 콘솔 로그를 보다 견고한 텔레메트리 시스템으로 교체하거나, 이 접근 방식을 `DocumentBuilder` 와 결합해 누락된 글꼴을 기업 기본 글꼴로 자동 교체해 보세요. 또한 `DocumentStructure` 와 같은 다른 `WarningType` 값을 탐색해 더 깊은 인사이트를 얻을 수도 있습니다.

행복한 코딩 되시고, 문서가 언제나 의도한 대로 정확히 렌더링되길 바랍니다!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스는 단계별 설명과 함께 완전한 작업 코드 예제를 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Python에서 향상된 문서 처리를 위한 Aspose.Words Markdown 로드 옵션 마스터](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [HTML, RTF 및 TXT 옵션으로 문서 로드 최적화](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Java용 Aspose.Words에서 문서 옵션 및 설정 사용](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}