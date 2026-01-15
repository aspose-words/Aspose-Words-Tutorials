---
category: general
date: 2026-01-14
description: Aspose.Words를 사용하여 Word 문서를 로드할 때 글꼴 대체 경고를 기록하십시오. 누락된 글꼴을 감지하고 C#에서
  누락된 글꼴을 캡처하는 방법을 배우세요.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: ko
og_description: Aspose.Words를 사용하여 Word 문서를 로드할 때 글꼴 대체 경고를 기록합니다. 누락된 글꼴을 감지하고 C#에서
  누락된 글꼴을 캡처하는 방법을 알아보세요.
og_title: 글꼴 대체 경고 로그 – 완전한 Aspose.Words 가이드
tags:
- Aspose.Words
- C#
- Document Processing
title: 글꼴 대체 경고 로그 – 완전한 Aspose.Words 가이드
url: /ko/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 대체 경고 기록 – 완전한 Aspose.Words 가이드

Aspose.Words 로 Word 문서를 로드한 후에도 문서가 정확히 동일하게 보이도록 보장하려면 글꼴 대체 경고를 기록하는 것이 필수적입니다. **누락된 글꼴을 감지하는 방법**이나 **누락된 글꼴을 캡처하는 방법**에 대해 궁금했다면, 여기가 바로 그곳입니다.  

이 튜토리얼에서는 실제 시나리오를 단계별로 살펴보고, 전체 C# 코드를 보여드리며 각 라인이 왜 중요한지 설명합니다. 끝까지 읽으면 모든 글꼴 대체 이벤트를 기록하고 대응할 수 있게 되어, 미스테리 경고가 남지 않게 됩니다.

![글꼴 대체 경고 기록 예시](/images/font-warnings.png "콘솔 출력에 표시된 글꼴 대체 경고 스크린샷")

## 배울 내용

- `LoadOptions`를 구성하여 Aspose.Words가 글꼴 대체에 대한 형식화된 경고를 발생시키는 방법.  
- 문서 로드 중 **누락된 글꼴을 감지**하는 정확한 단계.  
- **누락된 글꼴을 캡처**하고 이를 자체 로그 또는 모니터링 시스템에 기록하는 깔끔한 방법.  
- 엣지 케이스 처리(예: 문서에 서버에 설치되지 않은 글꼴이 포함된 경우).  

### 사전 요구 사항

- .NET 6.0 이상(.NET Framework 4.6+에서도 코드가 작동합니다).  
- 유효한 Aspose.Words for .NET 라이선스(또는 무료 체험).  
- C# 및 콘솔 애플리케이션에 대한 기본 지식.  

위 조건을 이미 갖추었다면, 바로 시작해봅시다.

## 단계 1 – 형식화된 경고를 발생하도록 LoadOptions 설정

해결책의 핵심은 `LoadOptions.FontSubstitutionWarning`에 있습니다. 이를 `RaiseTypedWarnings`로 전환하면 Aspose.Words에 요청한 정확한 글꼴을 찾지 못할 때마다 **매번** 이벤트를 발생하도록 지시합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **왜 중요한가:**  
> 기본 동작은 누락된 글꼴을 가장 근접한 글꼴로 조용히 교체하는데, 이는 예기치 못한 레이아웃 오류를 초래할 수 있습니다. 형식화된 경고를 발생시키면 전체 상황을 파악할 수 있습니다.

## 단계 2 – 경고 이벤트 구독

이제 `loadOptions.FontSubstitutionWarning`에 연결합니다. 람다식은 누락된 글꼴과 대신 사용된 글꼴을 정확히 알려주는 `e` 객체를 받습니다.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **프로 팁:** 웹 서버에서 실행한다면 `Console.WriteLine`을 구조화된 로거(Serilog, NLog 등)로 교체하여 나중에 데이터를 조회할 수 있게 하세요.

## 단계 3 – 구성된 옵션으로 문서 로드

경고 메커니즘이 설정되었으니, 평소와 같이 문서를 로드하면 됩니다. 누락된 글꼴마다 이벤트가 자동으로 발생합니다.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### 예상 콘솔 출력

`input.docx`에 설치되지 않은 *MyFancyFont* 글꼴이 참조되어 있으면, 다음과 같은 출력이 나타납니다:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

각 라인은 **누락된 글꼴 감지** 이벤트에 해당하며, 완전한 감사 로그를 제공합니다.

## 단계 4 – 엣지 케이스 및 고급 시나리오 처리

### 4.1 대체가 발생하지 않을 때

때때로 문서가 이미 설치된 시스템 글꼴만 사용할 때가 있습니다. 이 경우 경고 이벤트가 전혀 발생하지 않으며, 콘솔에 출력이 없게 됩니다. 이는 좋은 신호이며, 환경에 필요한 모든 글꼴이 이미 설치되어 있음을 의미합니다.

### 4.2 나중 분석을 위한 경고 캡처

야간 보고서를 위해 경고를 저장해야 한다면, 리스트에 수집하세요:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

로드 후 `missingFonts`를 JSON으로 직렬화하거나 데이터베이스에 저장하거나 요약을 이메일로 보낼 수 있습니다.

### 4.3 PDF 또는 기타 형식 작업

동일한 `LoadOptions` 접근 방식은 PDF, RTF, 심지어 HTML 파일에 대한 `Load` 호출에서도 작동합니다. 같은 옵션 인스턴스를 전달하면 Aspose.Words가 매치되지 않는 모든 글꼴에 대해 경고를 발생시킵니다.

## 단계 5 – 프로그래밍 방식으로 결과 검증

콘솔을 눈으로 확인하는 대신 자동화된 테스트를 원한다면, 리스트에 예상 항목이 포함되어 있는지 단언하세요:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

이 스니펫은 로그뿐만 아니라 코드에서 **누락된 글꼴을 캡처하는 방법**을 보여줍니다.

## 일반적인 함정 및 회피 방법

| 함정 | 발생 원인 | 해결 방법 |
|------|----------|-----------|
| `RaiseTypedWarnings` 설정을 잊음 | 기본값은 `DoNotRaise`이므로 이벤트가 발생하지 않습니다. | Step 1에서 보여준 대로 `FontSubstitutionWarning`을 명시적으로 설정합니다. |
| 웹 앱에서 `Console.WriteLine` 사용 | IIS/ASP.NET Core에서는 콘솔 출력이 사라집니다. | 지속적인 로거(예: Serilog)로 전환합니다. |
| 상대 경로로 문서 로드 | 런타임 시 작업 디렉터리가 다를 수 있습니다. | 절대 경로를 사용하거나 `Path.Combine(AppContext.BaseDirectory, "input.docx")`를 사용합니다. |
| `SubstitutedFontName` 무시 | 어떤 대체 글꼴이 선택됐는지 알 수 없습니다. | `FontName`과 `SubstitutedFontName`을 모두 기록합니다. |

## 보너스: 글꼴 설치 자동화

배포 환경을 제어할 수 있다면, PowerShell 스크립트를 사용해 누락된 글꼴을 사전 설치할 수 있습니다:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

애플리케이션 시작 전에 이를 실행하면 대부분의 **누락된 글꼴 감지** 경고가 완전히 사라집니다.

## 결론

Aspose.Words 로 Word 문서를 로드할 때 **글꼴 대체 경고를 기록**하는 데 필요한 모든 내용을 다루었습니다. `LoadOptions`를 구성하고, 경고 이벤트를 구독하며, 필요에 따라 결과를 저장하면 .NET 프로젝트에서 **누락된 글꼴을 감지**하고 **누락된 글꼴을 캡처하는 방법**을 확실히 이해할 수 있습니다.

코드를 가져가 로거를 환경에 맞게 조정하면, 조용한 글꼴 교체에 놀라지 않을 것입니다. 다음 단계는 다음과 같습니다:

- 중요한 글꼴이 누락되면 빌드가 실패하도록 CI/CD 파이프라인에 경고 리스트를 통합하기.  
- 여러 문서에 걸쳐 글꼴 사용을 모니터링하도록 접근 방식을 확장하기.  
- 맞춤 대체 글꼴을 제공하기 위해 Aspose.Words의 `FontSettings` API 탐색하기.

질문이나 복잡한 상황이 있나요? 댓글을 남겨 주세요. 함께 문제를 해결해 봅시다. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}