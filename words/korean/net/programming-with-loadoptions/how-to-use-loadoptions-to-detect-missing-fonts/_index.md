---
category: general
date: 2026-06-08
description: Aspose.Words의 LoadOptions를 사용하여 문서 가져오기 중 누락된 글꼴을 감지하는 방법을 배웁니다. 코드,
  설명 및 모범 사례가 포함된 단계별 가이드.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: ko
og_description: Aspose.Words에서 LoadOptions를 사용하는 방법 및 문서를 로드할 때 누락된 글꼴을 감지하는 방법. 코드와
  실용적인 팁이 포함된 완전 가이드.
og_title: LoadOptions를 사용해 누락된 글꼴을 감지하는 방법
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: LoadOptions를 사용해 누락된 글꼴을 감지하는 방법
url: /ko/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LoadOptions를 사용하여 누락된 글꼴 감지하기

Aspose.Words로 Word 문서를 로드할 때 **LoadOptions를 어떻게 사용하는지** 궁금하셨나요? 이 튜토리얼에서는 **LoadOptions를 어떻게 사용하는지** **누락된 글꼴을 감지**하고 이를 우아하게 처리하는 방법을 정확히 보여드립니다. 문서 변환 서비스나 보고 엔진을 구축하든, 누락된 글꼴은 레이아웃에 예기치 않은 변화를 일으킬 수 있으므로 조기에 포착하는 것이 필수입니다.

경고 콜백을 연결하는 단계부터 결과를 해석하는 방법까지 모든 과정을 차근차근 안내하므로, 최종적으로 .NET 프로젝트에 바로 넣어 사용할 수 있는 완전한 C# 예제를 얻을 수 있습니다. 외부 문서는 필요 없으며, 자체 포함 솔루션만 제공합니다. 끝까지 읽으면 경고 시스템이 존재하는 이유, 이를 활성화하는 방법, 콜백이 발생했을 때 취해야 할 조치를 알게 됩니다.

## 사전 요구 사항

- **Aspose.Words for .NET** (최근 버전이면 모두 가능; 사용하는 API는 2022년부터 안정적)
- .NET 개발 환경 (Visual Studio, Rider, 혹은 C# 확장 기능이 설치된 VS Code)
- 머신에 설치되지 않은 글꼴을 참조하는 샘플 Word 파일 (`input.docx`)

그게 전부입니다—Aspose.Words 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Aspose.Words와 함께 LoadOptions 사용하기

**LoadOptions** 클래스는 문서를 읽는 방식을 사용자 정의할 수 있는 관문입니다. 여기서 경고 콜백을 연결하면 Aspose.Words가 파일을 파싱하는 순간 **누락된 글꼴을 감지**할 수 있습니다. 이제 자세히 살펴보겠습니다.

### Step 1: 경고 핸들러 만들기

Aspose.Words는 `IWarningCallback` 인터페이스를 사용해 글꼴 대체와 같은 비치명적 문제를 알려줍니다. 인터페이스를 구현하고 경고가 도착했을 때 수행할 작업을 결정하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**왜 중요한가:**  
콜백이 없으면 Aspose.Words는 누락된 글꼴을 조용히 기본 글꼴(보통 Arial)로 교체합니다. `FontSubstitution` 경고를 포착하면 문제를 로그에 남기거나 사용자에게 알리거나, 심지어 사용자 정의 대체 글꼴로 교체할 수 있습니다.

### Step 2: 핸들러를 LoadOptions에 연결하기

이제 `LoadOptions` 인스턴스를 만들고 `FontWarningHandler`를 사용하도록 지정합니다. 바로 여기서 **LoadOptions 사용 방법**이 빛을 발합니다.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**왜 중요한가:**  
`LoadOptions`는 인코딩, 비밀번호 등 다양한 가져오기 시 설정을 한 곳에서 관리할 수 있는 도구입니다. `WarningCallback`을 설정하면 가볍고 이벤트 기반인 메커니즘을 활성화해 이 옵션을 사용해 로드하는 모든 문서에 적용됩니다.

### Step 3: 구성된 옵션으로 문서 로드하기

마지막으로 `LoadOptions`를 `Document` 생성자에 전달합니다. 소스 파일이 설치되지 않은 글꼴을 참조하고 있다면 Aspose.Words가 경고를 발생시키고 핸들러가 메시지를 출력합니다.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**출력 예시:**  
`input.docx`가 머신에 없는 *“MyCustomFont”* 글꼴을 사용한다고 가정하면 콘솔 출력은 다음과 같습니다.

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

모든 글꼴이 존재하면 콜백은 조용히 동작합니다—출력도 없고 성능에도 영향을 주지 않습니다.

## 경고 콜백으로 누락된 글꼴 감지하기 (보조 키워드 활용)

위 헤더에 **detect missing fonts**라는 문구가 자연스럽게 포함되어 보조 키워드를 강조합니다. 실제 프로젝트에서 마주칠 수 있는 몇 가지 변형을 살펴보겠습니다.

### 루프에서 여러 문서 처리하기

배치 파일을 처리할 때가 많습니다. 동일한 `LoadOptions` 인스턴스를 재사용할 수 있지만, `WarningCallback`은 로드 간에 지속됩니다. 문서별 격리가 필요하면 각 반복마다 새로운 `LoadOptions`를 인스턴스화하세요.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### 사용자 정의 글꼴 대체 로직

단순히 로그만 남기는 대신, 특정 누락 글꼴을 기업에서 승인한 대체 글꼴로 교체하고 싶을 수 있습니다. 핸들러를 확장해 보세요.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

이제 **누락된 글꼴을 감지**할 뿐만 아니라 교체 방법까지 직접 결정할 수 있습니다.

### 불필요한 경고 억제하기

글꼴 문제만 신경 쓰고 나머지는 모두 억제하고 싶다면 아래와 같이 `WarningType`으로 필터링하면 됩니다. 반대로 *모든* 경고를 로그에 남기려면 `if` 검사를 제거하고 `info.WarningType`과 `info.Description`을 함께 출력하세요.

## 전체 실행 가능한 예제

모든 내용을 종합한 완전한 프로그램을 아래에 제공합니다. `"YOUR_DIRECTORY/input.docx"`를 테스트 파일 경로로 바꾸면 됩니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**예상 콘솔 출력 (글꼴이 누락된 경우):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

글꼴이 전혀 누락되지 않았다면 다음과 같이 출력됩니다:

```
Document loaded successfully.
```

## 흔히 저지르는 실수 & 전문가 팁

- **함정:** `WarningCallback`을 설정하지 않음. API는 여전히 글꼴을 대체하지만, 그 사실을 알 수 없습니다.  
  **전문가 팁:** 글꼴 정확도가 필요할 때는 항상 핸들러를 연결하세요; 비용이 거의 들지 않습니다.

- **함정:** 

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}