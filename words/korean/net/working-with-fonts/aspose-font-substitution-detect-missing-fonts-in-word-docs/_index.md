---
category: general
date: 2026-05-04
description: Aspose 글꼴 대체 기능을 사용하여 Word 문서를 로드할 때 누락된 글꼴을 감지하고 누락된 글꼴 세부 정보를 검색하는
  단계별 가이드.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: ko
og_description: 'Aspose 글꼴 대체 마스터: Word 문서를 로드할 때 누락된 글꼴을 감지하고 전체 C# 코드로 누락된 글꼴 정보를
  가져옵니다.'
og_title: Aspose 글꼴 대체 – Word 문서에서 누락된 글꼴 감지
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose 글꼴 대체: Word 문서에서 누락된 글꼴 감지'
url: /ko/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Word 문서에서 누락된 글꼴 감지

다른 컴퓨터에서 Word 문서가 왜 잘못 표시되는지 궁금해 본 적 있나요? 대부분 원인은 누락된 글꼴이며, **Aspose font substitution**은 시각적 재앙이 되기 전에 이러한 문제를 찾아낼 수 있는 도구입니다. 이 튜토리얼에서는 **Word 문서를 로드하는 순간 누락된 글꼴을 감지**하고, **누락된 글꼴** 세부 정보를 **검색**하여 수정하거나 교체하는 방법을 단계별로 안내합니다.

경고 콜백 설정부터 누락된 글꼴의 정리된 목록을 가져오는 것까지 모두 다룹니다. 끝까지 진행하면 어떤 글꼴이 제외되었는지 정확히 알려주는 실행 준비가 된 C# 코드 스니펫을 얻을 수 있으며, 이것이 문서 충실도에 왜 중요한지 이해하게 됩니다.

---

## Prerequisites – 시작하기 전에 필요한 것들

- **Aspose.Words for .NET** (v23.12 또는 이후 버전 권장).  
- .NET 개발 환경 (Visual Studio, Rider, 또는 `dotnet` CLI).  
- 의도적으로 설치되지 않은 글꼴을 사용하는 샘플 DOCX—예: `DocumentWithMissingFont.docx`.  
- 기본 C# 지식—특별한 것이 아니라 콘솔 앱을 실행할 수 있는 능력.

위 항목 중 익숙하지 않은 것이 있다면, 잠시 멈추고 NuGet 패키지를 설치하세요:

```bash
dotnet add package Aspose.Words
```

그게 전부입니다. 추가 글꼴도 없고 외부 서비스도 필요 없습니다.

---

## Step 1: Word 문서 로드 (및 글꼴 검사 트리거)

가장 먼저 해야 할 일은 **Word 문서를 로드**하는 것입니다. Aspose.Words는 파일을 파싱하고, 참조된 글꼴을 찾을 수 없으면 *FontSubstitution* 경고를 큐에 넣습니다. 아래는 로드를 수행하는 코드입니다:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **왜 중요한가:** 문서를 일찍 로드하면 Aspose가 텍스트, 스타일 및 임베디드 객체의 모든 실행을 스캔할 기회를 얻습니다. 시스템이나 사용자 지정 글꼴 폴더에서 글꼴을 찾지 못하면 이후에 경고가 발생합니다.

---

## Step 2: 대체 이벤트를 캡처하기 위한 경고 콜백 연결

Aspose.Words는 누락된 글꼴과 같은 문제를 알려주는 콜백 메커니즘을 사용합니다. `IWarningCallback` 구현을 `doc.WarningCallback`에 할당하면 발생하는 각 경고를 가로챌 수 있습니다.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **프로 팁:** 복합 패턴으로 래핑하여 여러 콜백(예: 로깅, UI 업데이트)을 연결할 수 있지만, 이 튜토리얼에서는 단일 콜백이 명확합니다.

---

## Step 3: Font Substitution 경고 콜백 구현

이제 실제 작업을 수행하는 클래스를 정의합니다. 콜백은 `WarningInfo` 객체를 받고, `WarningType.FontSubstitution`을 필터링한 뒤 나중에 사용할 설명을 저장합니다.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **무슨 일인가:** Aspose가 누락된 글꼴을 만나면 “Font substitution: 'Comic Sans MS'를 찾을 수 없어 대신 'Arial'을 사용했습니다.”와 같은 경고를 생성합니다. 우리의 콜백은 해당 라인을 출력하고 저장합니다.

---

## Step 4: 문서 처리 (선택) 및 누락된 글꼴 수집

만약 **누락된 글꼴을 감지**하는 것만 필요하다면 로드 단계만으로 충분합니다—경고가 자동으로 발생합니다. 그러나 많은 개발자는 일부 작업(예: 저장, 변환) 후에 **누락된 글꼴** 정보를 **검색**해야 합니다. 아래에서는 모든 경고가 발생하도록 PDF 저장이라는 작은 작업을 강제로 수행한 뒤 수집된 메시지를 가져옵니다.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **예상 콘솔 출력** (예시):  
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

각 라인이 원래 글꼴과 Aspose가 선택한 대체 글꼴을 명확히 표시하는 것을 확인하세요. 이것이 **aspose font substitution** 보고의 핵심입니다.

---

## Step 5: 고급 – 대체를 줄이기 위한 사용자 지정 글꼴 소스 사용

때때로 누락된 글꼴이 실제로 존재하지만 기본 시스템 폴더에 없을 수 있습니다. Aspose.Words는 `FontSettings`를 통해 사용자 지정 디렉터리를 지정할 수 있게 해줍니다. 이 단계를 추가하면 대체 경고 수를 크게 줄일 수 있습니다.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **왜 추가하나요?** 여러 머신에 문서를 배포할 경우, 필요한 글꼴을 알려진 폴더에 번들링하면 모든 곳에서 동일한 시각적 모습을 보장합니다. 또한 Aspose가 대체하기 전에 해당 폴더를 확인하므로 **누락된 글꼴 감지** 루틴이 더 정확해집니다.

---

## 완전한 작업 예제

모두 합치면, 아래는 복사‑붙여넣기만 하면 되는 콘솔 프로그램입니다. `Program.cs`로 저장하고 `dotnet run`으로 실행하세요.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**예상 출력:** 소스 DOCX가 없는 글꼴을 참조하면 콘솔에 각 대체 라인과 간결한 요약이 출력됩니다. 모든 글꼴이 존재하면 “No missing fonts were detected.” 메시지가 표시됩니다.

---

## 일반적인 함정 및 회피 방법

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **경고가 나타나지 않음** | 문서가 시스템 글꼴만 사용하거나 이미 누락된 글꼴이 포함된 사용자 지정 폴더를 추가했기 때문입니다. | DOCX가 실제로 사용 불가능한 글꼴을 참조하는지 확인하세요. Word에서 열어 단락을 희귀 글꼴(예: “Papyrus”)로 변경할 수 있습니다. |
| **중복 메시지** | 같은 글꼴이 여러 실행에 사용되어 여러 경고가 발생합니다. | `Distinct()`를 사용해 고유한 집합만 필요하면 목록을 중복 제거하세요. |
| **대형 문서에서 성능 저하** | 각 경고가 UI 스레드에서 처리됩니다. | 로드를 백그라운드 작업으로 실행하거나 후처리를 위해 `Parallel.ForEach`를 사용하세요. |
| **잘못된 대체 글꼴** | Aspose의 기본 대체 글꼴이 브랜드와 일치하지 않을 수 있습니다. | `FontSettings.SubstitutionSettings.DefaultFontName`을 선호하는 대체 글꼴(예: “Calibri”)로 설정하세요. |

---

## 솔루션 확장 – 누락된 글꼴을 JSON으로 내보내기

클라이언트에 누락된 글꼴을 보고해야 하는 웹 서비스를 구축한다면, 목록을 직렬화하는 것은 간단합니다:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

이제 API가 다른 시스템이 사용할 수 있는 깔끔한 JSON 페이로드를 반환할 수 있습니다.

---

## 결론

이 가이드에서는 **Aspose font substitution**을 처음부터 끝까지 시연했습니다: Word 문서 로드, 경고 콜백 연결, 각 *누락된 글꼴 감지* 이벤트 캡처, 그리고 최종적으로 **누락된 글꼴** 정보를 보고 또는 수정용으로 **검색**했습니다. 선택적인 사용자 지정 글꼴 폴더를 추가하면 대체 목록을 줄일 수 있으며, 몇 줄만 더 추가하면 결과를 JSON으로 내보낼 수도 있습니다.

문서의 시각적 무결성은 사용된 글꼴에 달려 있다는 점을 기억하세요. 여기 소개한 기술을 사용하면 예상치 못한 대체에 놀라지 않을 것입니다.  
다음 단계로 나아갈 준비가 되었나요? 이 로직을 더 큰 문서 처리 파이프라인에 통합하거나, 글꼴 임베딩(`doc.FontSettings.EmbeddedFonts`)과 같은 Aspose.Words의 다른 기능을 탐색해 보세요. 가능성은 무한하며, 사용자는 깔끔한 출력에 감사할 것입니다.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}