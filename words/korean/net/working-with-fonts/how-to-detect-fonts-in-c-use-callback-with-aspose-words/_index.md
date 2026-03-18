---
category: general
date: 2026-03-17
description: Aspose.Words와 경고 콜백을 사용하여 C#에서 글꼴을 감지하는 방법. 문서를 로드하는 동안 누락된 글꼴 대체를 캡처하기
  위해 콜백을 사용하는 방법을 배웁니다.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: ko
og_description: C#에서 Aspose.Words를 사용하여 글꼴을 감지하는 방법. 이 가이드는 문서를 로드하는 동안 누락된 글꼴 경고를
  캡처하기 위해 콜백을 사용하는 방법을 보여줍니다.
og_title: C#에서 글꼴 감지 방법 – Aspose.Words와 콜백 사용
tags:
- Aspose.Words
- C#
- Document Processing
title: C#에서 글꼴 감지 방법 – Aspose.Words와 콜백 사용
url: /ko/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

**. **how to use callback** again.

Proceed.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 폰트를 감지하는 방법 – Aspose.Words와 콜백 사용

프로그래밍으로 Word 문서에서 **폰트 감지 방법**이 필요했으며, 변환 후 일부 문자가 이상하게 보이는 이유가 궁금했나요? 당신만 그런 것이 아닙니다. 인보이스 생성기, 보고서 내보내기 도구, 배치 처리 파이프라인 등 많은 실제 프로젝트에서 누락된 폰트가 조용히 레이아웃 오류를 일으켜 디버깅이 어렵습니다.  

좋은 소식은? Aspose.Words는 경고 콜백을 통해 이러한 문제를 명확히 드러낼 수 있는 방법을 제공합니다. 이 튜토리얼에서는 **콜백 사용 방법**을 확인하여 문서를 로드하는 동안 Aspose가 수행하는 모든 폰트 대체를 캡처하고, 누락된 폰트에 대한 명확한 보고서를 출력하는 바로 실행 가능한 예제를 얻을 수 있습니다.

다룰 내용:

* 최소 사전 요구 사항(.NET 프로젝트와 Aspose.Words NuGet 패키지).  
* `IWarningCallback`을 구현하여 `WarningType.FontSubstitution`을 감지하는 방법.  
* 콜백을 `LoadOptions`에 연결하고 문서를 로드하는 방법.  
* 출력 예시와 실무에 적용할 수 있는 몇 가지 팁.

끝까지 읽으면 DOCX, DOC, RTF 파일에서 자동으로 **폰트를 감지**하고 누락된 폰트 정보를 기반으로 로깅, 사용자 알림 또는 대체 폰트 적용 등을 수행할 수 있게 됩니다.

---

![How to detect fonts in a Word document using Aspose.Words warning callback](https://example.com/images/detect-fonts.png "how to detect fonts in a Word document")

## 필요 사항

* **.NET 6.0** 이상(예제는 .NET Framework 4.6+에서도 컴파일됩니다).  
* **Aspose.Words for .NET** – NuGet을 통해 설치: `Install-Package Aspose.Words`.  
* 의도적으로 설치되지 않은 폰트를 참조하는 샘플 Word 파일(예: `MissingFont.docx`).  

추가 라이브러리는 필요하지 않으며, 모든 기능은 Aspose 네임스페이스 안에 포함됩니다.

---

## 경고 콜백을 사용한 폰트 감지 방법

### 단계 1: 경고‑콜백 클래스 만들기

콜백은 `IWarningCallback`을 구현합니다. Aspose.Words가 찾을 수 없는 폰트를 만나면 `WarningInfo`와 함께 `WarningType.FontSubstitution`을 발생시킵니다. 우리의 클래스는 콘솔에 친절한 한 줄을 출력합니다.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**왜 중요한가:** `WarningType.FontSubstitution`만 필터링하면 오래된 기능 사용 등 잡음이 되는 경고를 피하고, 머신에 존재하지 않는 **폰트 감지**라는 정확한 문제에 로그를 집중할 수 있습니다.

---

### 단계 2: `LoadOptions`에 콜백 연결하기

`LoadOptions`를 사용하면 문서 파싱 방식을 커스터마이즈할 수 있습니다. 우리의 `FontWarningCollector`를 `WarningCallback` 속성에 할당하면 누락된 폰트를 만나면 Aspose가 콜백을 호출합니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**팁:** 여기서 `LoadOptions.FontSettings`를 설정하면 프로그래밍 방식으로 대체 폰트를 지정할 수 있습니다. 이는 이후에 다룰 고급 시나리오입니다.

---

### 단계 3: 문서를 로드하고 출력 확인하기

이제 실제로 파일을 로드합니다. Aspose가 문서를 파싱하는 즉시 찾을 수 없는 폰트가 있으면 콜백이 트리거됩니다.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**예상 콘솔 출력**(문서가 설치되지 않은 *Comic Sans MS*를 참조한다고 가정):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

문서에 여러 개의 누락된 폰트가 있으면 폰트당 한 줄씩 출력됩니다—필요한 **폰트 감지** 정보를 정확히 제공하죠.

---

## 더 복잡한 시나리오를 위한 콜백 활용법

### 콘솔 대신 파일에 로깅하기

실제 서비스에서는 영구 로그가 필요할 수 있습니다. `Console.WriteLine`을 `StreamWriter`로 교체하세요:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### 나중에 분석을 위해 경고 수집하기

문서 로드 후 누락된 폰트 목록이 필요할 때가 있습니다(예: UI 대화 상자 표시). 경고를 `List<string>`에 저장하고 외부에 노출합니다:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### 프로그래밍 방식으로 대체 폰트 제공하기

회사에서 지정한 폰트를 강제 적용하려면 로드하기 전에 `FontSettings`에 추가하면 됩니다:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

이제 Aspose는 *Arial Unicode MS*로 누락된 폰트를 대체하면서도 콜백을 통해 대체 사실을 보고합니다. 이는 **콜백 사용 방법**을 활용해 감지와 자동 복구를 동시에 수행하는 깔끔한 방법입니다.

---

## 흔히 겪는 문제와 전문가 팁

| 문제점 | 발생 이유 | 해결 방법 |
|--------|-----------|-----------|
| **`Aspose.Words.Warnings`를 참조하지 않음** | `IWarningCallback` 인터페이스가 해당 네임스페이스에 존재합니다. | 파일 상단에 `using Aspose.Words.Warnings;`를 추가합니다. |
| **`LoadOptions` 없이 문서 로드** | 기본 로더가 경고 없이 폰트를 조용히 대체합니다. | 항상 `LoadOptions` 인스턴스를 생성하고 콜백을 할당합니다. |
| **권한이 제한된 서버에서 실행** | 로그 파일 쓰기가 `UnauthorizedAccessException`을 발생시킬 수 있습니다. | 쓰기 가능한 폴더(예: 앱 데이터 디렉터리)를 사용하거나 메모리 컬렉션만 사용합니다. |
| **여러 스레드가 동일 콜렉터 공유** | `FontWarningCollector`는 기본적으로 스레드 안전하지 않습니다. | 스레드당 별도 콜렉터를 만들거나 리스트를 `lock`으로 보호합니다. |
| **임베디드 폰트에 콜백이 호출된다고 가정** | 임베디드 폰트는 문서에 이미 포함되어 있어 경고가 발생하지 않습니다. | 임베디드 폰트 무결성을 확인하려면 `FontSettings`를 통해 `FontInfo`를 검사합니다. |

---

## 전체 작업 예제 (복사‑붙여넣기 가능)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**예상 결과**(파일이 두 개의 누락된 폰트를 참조한다고 가정):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

파일에 설치된 폰트만 사용된 경우 콘솔에 단순히 다음이 출력됩니다:

```
Document loaded successfully.

No missing fonts detected.
```

---

## 마무리

우리는 Aspose.Words에 사용자 정의 경고 콜백을 연결하여 Word 문서에서 **폰트 감지**를 수행하는 방법을 살펴보았습니다. 이 접근 방식은 가볍고, 다음과 같은 것이 필요합니다

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}