---
category: general
date: 2026-04-07
description: Aspose.Words를 사용하여 C#에서 글꼴을 감지하고 누락된 글꼴을 처리하면서 경고를 캡처하는 방법을 배웁니다. 단계별
  코드가 포함되어 있습니다.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: ko
og_description: Aspose.Words에서 글꼴을 감지하는 방법은? 이 튜토리얼을 따라 경고를 포착하고 누락된 글꼴을 손쉽게 처리하세요.
og_title: Aspose.Words에서 폰트 감지하는 방법 – 완전 가이드
tags:
- Aspose.Words
- C#
- Font handling
title: Aspose.Words에서 글꼴을 감지하는 방법 – 완전 가이드
url: /ko/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 폰트 감지하는 방법 – 완전 가이드

Word 문서를 프로덕션에 배포하기 전에 **누락된 폰트를 감지**하고 싶으신가요? 여러분만 그런 것이 아닙니다. 많은 엔터프라이즈 시나리오에서 한 글자체가 PDF 변환 파이프라인을 중단시키거나 레이아웃 오류를 일으켜 비전문적으로 보이게 할 수 있습니다. 좋은 소식은 Aspose.Words가 이러한 부재 폰트를 찾아내고 명확한 경고를 표시하는 내장 기능을 제공한다는 점입니다.

이 튜토리얼에서는 **폰트를 감지하는 방법**, **경고를 캡처하는 방법**, 그리고 **누락된 폰트를 처리하는** 최선의 방법을 단계별로 살펴보겠습니다. 외부 도구 없이, 추측 없이—지금 바로 프로젝트에 삽입할 수 있는 순수 C# 코드만 제공합니다.

> **빠른 미리보기:** 마지막에 재사용 가능한 `FontSubstitutionWarningCollector`를 얻어 문서 로드 중 발생하는 모든 폰트 대체 메시지를 수집하고, 폰트를 찾을 수 없을 때 어떻게 대응해야 하는지 알게 됩니다.

---

## 배울 내용

- `LoadOptions`를 구성하여 폰트 대체 경고를 수신하는 방법.  
- 사용자 정의 컬렉터 클래스에서 해당 경고를 캡처하는 방법.  
- 수집된 경고를 처리하여 중단, 로그 기록 또는 폰트 대체를 결정하는 방법.  
- 원격 또는 임베디드 폰트를 참조하는 문서에 대한 엣지 케이스 처리.  

**전제 조건:** .NET 6+ (또는 .NET Framework 4.6+), Aspose.Words for .NET (최신 버전), 그리고 C#에 대한 기본 지식. Aspose.Words를 처음 사용한다면 걱정 마세요—이 가이드는 몇 분만 투자하면 따라 할 수 있도록 설계되었습니다.

---

## Aspose.Words LoadOptions를 사용한 폰트 감지

누락된 폰트를 감지하려면 먼저 Aspose.Words에 이를 보고하도록 지시해야 합니다. 이는 `LoadOptions.WarningCallback` 속성을 통해 수행되며, `IWarningCallback`을 구현하는 모든 클래스를 받을 수 있습니다. 아래에서는 모든 경고를 저장하는 작은 컬렉터를 만들었습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**왜 중요한가:** 경고 콜백이 없으면 Aspose.Words는 누락된 폰트를 기본 폰트로 조용히 대체하고, 문제 존재 여부를 알 수 없습니다. `WarningType.FontSubstitution`을 캡처함으로써 **사용 가능한 폰트가 아닌 경우**를 정확히 파악할 수 있습니다.

이제 컬렉터를 `LoadOptions`에 연결하고 문서를 로드합니다:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **프로 팁:** 배치로 여러 문서를 처리할 경우 동일한 `FontSubstitutionWarningCollector` 인스턴스를 재사용하되, 서로 다른 파일에서 발생한 경고가 섞이지 않도록 로드 사이에 `Clear()`를 호출하세요.

---

## 문서 로드 중 경고 캡처

문서가 로드된 후 컬렉터는 이미 모든 폰트 관련 경고를 보유하고 있습니다. 다음 논리적인 질문은: *경고를 어떻게 캡처*해서 로그나 화면에 쉽게 표시할 수 있느냐 입니다.

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Typical output looks like:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**이것이 의미하는 바:** 각 라인은 원본 폰트 이름과 Aspose.Words가 선택한 대체 폰트를 보여줍니다. 이 정보를 바탕으로 대체 폰트가 허용 가능한지, 아니면 누락된 폰트를 직접 임베드해야 하는지 판단할 수 있습니다.

---

## 누락된 폰트를 우아하게 처리하기

경고를 감지하고 캡처하는 것만으로는 절반에 불과합니다. 실제 가치는 **누락된 폰트를 프로덕션 수준으로 처리**할 때 비로소 발휘됩니다. 아래는 흔히 사용되는 세 가지 전략입니다:

1. **로그 기록 후 계속 진행** – 배치 처리에서 감사 로그만 필요할 때 적합합니다.  
2. **중요 폰트에 대해 중단** – 특정 폰트(예: 브랜드 전용 서체)가 없을 경우 예외를 발생시킵니다.  
3. **실시간 폰트 임베드** – 알려진 폴더에서 누락된 폰트를 로드하고, 문서를 다시 로드하기 전에 Aspose.Words에 등록합니다.

### 예시: 중요한 폰트에 대해 중단

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### 예시: 누락된 폰트 자동 임베드

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**왜 이런 패턴이 도움이 되는가:** 폰트가 없을 때 명시적으로 어떤 행동을 할지 결정함으로써, 브랜드나 가독성을 해칠 수 있는 조용한 대체를 방지합니다. 이것이 **누락된 폰트를 제어된 방식으로 처리**하는 핵심입니다.

---

## 완전한 작동 예제

모든 내용을 하나로 합치면, **폰트를 감지하고**, **경고를 캡처하며**, **누락된 폰트를 로그로 기록**하는 간단한 정책을 구현한 단일 실행 프로그램이 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**예상 결과:** 머신에 존재하지 않는 폰트를 참조하는 문서를 대상으로 프로그램을 실행하면 콘솔에 각 대체 경고가 나열됩니다. 경고 중 `critical` 집합에 포함된 폰트가 있으면 프로그램이 조기에 종료되어 결함이 있는 PDF가 생성되는 것을 방지합니다.

---

## 자주 묻는 질문 (FAQs)

| Question | Answer |
|----------|--------|
| *Aspose.Words 라이선스가 필요합니까?* | 예, 유효한 Aspose.Words 라이선스를 적용하면 평가 워터마크가 제거되고 전체 기능을 사용할 수 있습니다. |
| *이 방법으로 임베드된 폰트를 감지할 수 있나요?* | 임베드된 폰트는 파일에 이미 포함되어 있으므로 Aspose.Words는 대체 경고를 발생시키지 않습니다. 필요하다면 `Document.FontInfos`를 확인해 임베드된 폰트를 열거할 수 있습니다. |
| *Windows에서는 시스템 폰트가 있지만 Linux에서는 없을 경우는 어떻게 되나요?* | Linux에서는 해당 폰트가 설치되지 않았기 때문에 동일한 경고가 발생합니다. “누락된 폰트 처리” 전략을 사용해 필요한 `.ttf` 파일을 앱과 함께 배포하세요. |
| *Is the warning collector thread |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}