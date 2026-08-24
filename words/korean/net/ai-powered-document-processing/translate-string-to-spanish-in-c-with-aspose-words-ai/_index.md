---
category: general
date: 2026-08-23
description: C#에서 Aspose.Words AI Translator와 Google 제공자를 사용하여 문자열을 스페인어로 번역합니다. 단계별
  가이드를 따라 C#에서 문자열을 빠르게 번역하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: ko
lastmod: 2026-08-23
og_description: Aspose.Words AI를 사용하여 C#에서 문자열을 스페인어로 번역합니다. 이 튜토리얼에서는 Google 제공자를
  설정하고, 문자열을 번역하며, 결과를 표시하는 방법을 보여줍니다.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: C#에서 문자열을 스페인어로 번역하기 – 전체 코드 예제
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: C#와 Aspose.Words AI를 사용하여 문자열을 스페인어로 번역
url: /ko/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Aspose.Words AI를 사용하여 문자열을 스페인어로 번역하기

.NET 애플리케이션에서 **문자열을 스페인어로 번역**해야 할 경우, 이 가이드는 정확히 어떻게 하는지 보여줍니다. Google 서비스를 호출하고 스페인어 텍스트를 출력하는 번역기를 만드는 완전한 실행 예제를 확인할 수 있습니다.

이 튜토리얼은 또한 Aspose.Words AI 라이브러리를 사용한 **C#에서 문자열 번역** 방법을 다루므로, 외부 스크립트 없이 코드베이스에 직접 로컬라이제이션을 통합할 수 있습니다.

## 필요 사항

- .NET 6.0 SDK 이상 (코드는 .NET Core 및 .NET Framework에서도 컴파일됩니다)
- 활성화된 Google Cloud Translation API 키
- NuGet 패키지 `Aspose.Words.AI` (`dotnet add package Aspose.Words.AI` 로 설치)
- Visual Studio 2022와 같은 코드 편집기 또는 IDE

이 전제 조건들은 샘플이 바로 실행될 수 있도록 보장합니다.

## Aspose.Words AI로 문자열을 스페인어로 번역하기

이 섹션에서는 Google 제공자를 사용하도록 구성된 `Translator` 객체를 생성합니다. 제공자는 Google 번역 엔드포인트에 대한 HTTP 요청을 처리합니다.

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**작동 원리:**  
- `Translator`는 HTTP 호출을 추상화하며, 제공한 API 키로 인증을 처리합니다.  
- `TranslationProvider.Google`은 SDK가 요청을 Google Cloud Translation으로 라우팅하도록 지정합니다.  
- `Language.Spanish`는 대상 언어 코드(`es`)를 선택합니다.  
- `Translate` 메서드는 번역된 문자열을 반환하며, 이를 애플리케이션 어디에서든 사용할 수 있습니다.

## Google 번역 제공자 설정하기

1. Google Cloud Console → APIs & Services → Credentials 에서 **API 키**를 얻습니다.  
2. 프로젝트에 **Cloud Translation API**를 활성화합니다.  
3. 키를 안전하게 저장합니다(환경 변수, 비밀 관리자 등). 예제에서는 가독성을 위해 리터럴을 사용했지만, 실제 코드에서는 비밀을 하드코딩하지 않아야 합니다.

## C#에서 문자열 번역 – 단계별 가이드

| 단계 | 작업 | 이유 |
|------|------|------|
| 1 | `TranslationProvider.Google`와 함께 `Translator` 인스턴스화 | SDK를 Google 서비스에 연결 |
| 2 | `Translate(source, Language.Spanish)` 호출 | 원본 텍스트를 전달하고 스페인어 결과를 받음 |
| 3 | `Console.WriteLine`으로 결과 출력 | 번역을 확인하고 사용 방법을 시연 |

프로그램을 실행하면 다음과 같이 출력됩니다:

```
¡Hola mundo!
```

> **참고:** 정확한 출력은 Google 번역 모델에 따라 약간 다를 수 있습니다(예: “Hola mundo” vs. “¡Hola mundo!”). 두 경우 모두 유효한 스페인어 표현입니다.

## 실행 및 출력 확인하기

1. 프로젝트 폴더에서 터미널을 엽니다.  
2. `dotnet run`을 실행합니다.  
3. 콘솔에 스페인어 문구가 표시되는지 확인합니다.

콘솔에 *“401 Unauthorized”*와 같은 오류가 표시되면 API 키가 올바른지, Cloud Translation API가 프로젝트에 활성화되어 있는지 다시 확인하십시오.

## 흔히 발생하는 문제와 모범 사례

- **API 할당량 제한** – Google은 청구 계정당 요청 제한을 적용합니다. 예상치 못한 제한을 피하려면 Cloud Console에서 사용량을 모니터링하세요.  
- **네트워크 지연** – 번역 호출은 원격 HTTP 요청이므로, 자주 번역되는 문자열을 캐시하여 지연을 줄이는 것을 고려하세요.  
- **인코딩 문제** – SDK는 UTF‑8 문자열을 사용합니다. 특수 문자를 보존하려면 소스 파일을 UTF‑8 인코딩으로 저장하세요.  
- **오류 처리** – `Translate` 호출을 try‑catch 블록으로 감싸 `ApiException`을 처리하고 대체 텍스트를 제공하십시오.

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## 예제 확장하기

- **다른 언어로 번역** – `Language.Spanish`를 `Language.French`, `Language.German` 등으로 교체합니다.  
- **배치 번역** – 문자열 리스트를 처리하기 위해 루프 안에서 `Translate`를 호출합니다.  
- **UI와 통합** – ASP.NET Core Razor 페이지, Windows Forms, WPF 애플리케이션 등에서 번역된 문자열을 사용합니다.

## 결론

이제 Aspose.Words AI와 Google Translation 서비스를 이용해 C#에서 **문자열을 스페인어로 번역**하는 방법을 알게 되었습니다. 전체 솔루션은 제공자 설정, 번역 호출, 오류 처리 및 출력 검증을 포함합니다.

다음 단계에서는 추가 언어를 실험하고, 성능을 위해 결과를 캐시하며, 번역기를 더 큰 로컬라이제이션 파이프라인에 통합해 보세요.

--- 

*더 많은 콘텐츠를 로컬라이즈하고 싶으신가요? 대체 클라우드 제공자인 **Azure Cognitive Services와 함께 C#에서 문자열을 번역**하는 다음 튜토리얼을 확인해 보세요.*

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 단계별 설명과 완전한 코드 예제를 제공합니다. 이를 통해 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색할 수 있습니다.

- [문자열 교체](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [문자열 교체](/words/english/net/find-and-replace-text/replace-with-string/)
- [Aspose.Words로 Word 문서 만들기 – 단계별 가이드](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}