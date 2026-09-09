---
category: general
date: 2026-02-10
description: Aspose.Words에서 기본 글꼴을 구성하고 기본 가져오기 글꼴을 설정하는 동안 글꼴 변경을 모니터링하기 위해 경고 콜백을
  설정합니다. 전체 단계별 솔루션을 확인하세요.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: ko
og_description: 기본 글꼴을 구성하고 기본 가져오기 글꼴을 설정하는 동안 글꼴 변경을 모니터링하기 위해 경고 콜백을 설정합니다. Aspose.Words
  전체 튜토리얼을 따라보세요.
og_title: C#에서 경고 콜백 설정 – 완전 가이드
tags:
- Aspose.Words
- C#
- Document Import
title: C#에서 경고 콜백 설정 – 폰트 처리 완전 가이드
url: /ko/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 경고 콜백 설정 – 폰트 처리 완전 가이드

Word 문서를 로드할 때 **경고 콜백을 설정**하고 동시에 *기본 폰트를 구성*해야 했던 적이 있나요? 당신만 그런 것이 아닙니다. 자동 보고서 생성기나 문서 변환 파이프라인과 같은 실제 프로젝트에서는 누락된 폰트가 레이아웃을 조용히 깨뜨릴 수 있으며, 이러한 문제를 포착하는 유일한 방법은 경고 콜백을 통해 **폰트 변경을 모니터링**하는 것입니다.

이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 **경고 콜백을 설정**, **기본 폰트를 구성**, 그리고 **기본 가져오기 폰트를 설정**하는 실전 예제를 단계별로 살펴봅니다. 끝까지 따라오시면 바로 실행 가능한 코드 스니펫을 얻고, 각 부분이 왜 중요한지 이해하며, 사용자 정의 폰트 폴더나 무음 대체와 같은 엣지 케이스에 어떻게 적용할 수 있는지도 알게 됩니다.

---

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 작동합니다)  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)  
- 사용하려는 대체 폰트가 들어 있는 폴더 (예: `fonts/Arial.ttf`)  
- C# 콘솔 앱에 대한 기본적인 이해  

추가 라이브러리는 필요하지 않습니다.

---

## 단계 1: LoadOptions 생성 및 **기본 폰트 구성**

폰트 처리를 제어하고 싶을 때 가장 먼저 해야 할 일은 `LoadOptions` 인스턴스를 만드는 것입니다. 이 객체는 Aspose.Words에게 가져오기 중 누락된 폰트를 어떻게 처리할지 알려줍니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**이것이 중요한 이유:**  
소스 문서가 서버에 설치되지 않은 폰트를 참조하면 Aspose.Words는 제공한 폴더를 확인합니다. 이것이 **기본 가져오기 폰트 설정**의 핵심이며, 경고가 발생하기 전에도 대체 폰트를 명시적으로 지정하게 됩니다.

---

## 단계 2: **경고 콜백 설정**으로 **폰트 변경 감시**

Aspose.Words는 폰트를 대체해야 할 때마다 `WarningInfoCollection`을 발생시킵니다. 핸들러를 연결하면 각 대체에 대해 로그를 남기거나 대응할 수 있습니다.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**이것이 중요한 이유:**  
단순히 **기본 폰트를 구성**하는 것만으로는 실제로 어떤 폰트가 교체되었는지 감사하기 부족합니다. 콜백을 통해 실시간 로그를 확보하면 **폰트 변경을 모니터링**할 수 있어 CI 파이프라인에서 예상치 못한 대체를 조기에 포착할 수 있습니다.

---

## 단계 3: 준비된 옵션으로 문서 로드

이제 `LoadOptions`가 완전히 준비되었으니 `.docx` 파일을 안전하게 로드할 수 있습니다. 대체가 발생하면 콜백이 자동으로 실행됩니다.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**출력 예시:**  
소스에 존재하지 않는 폰트가 사용된 경우 콘솔에 다음과 같은 내용이 표시됩니다:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

이 출력은 **경고 콜백을 성공적으로 설정**했으며 **기본 가져오기 폰트**가 적용되었음을 확인시켜 줍니다.

---

## 단계 4: (선택 사항) 폰트 대체 동작 세부 조정

때로는 원래 요청과 관계없이 모든 누락 폰트를 하나의 패밀리로 교체하고 싶을 수 있습니다. Aspose.Words는 전역 *대체 폰트*를 설정하는 기능을 제공합니다.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**사용 시점:**  
브랜드에서 제한된 폰트만 허용하는 PDF를 생성해야 할 경우, 소스 문서가 이국적인 폰트를 사용하더라도 일관성을 유지할 수 있습니다.

---

## 단계 5: 문서 저장 또는 추가 처리

로드가 끝난 뒤에는 편집, PDF 변환, 텍스트 추출 등 필요한 모든 처리를 진행할 수 있습니다. 아래 예시는 대체된 폰트를 유지하면서 문서를 PDF로 저장하는 방법을 보여줍니다.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

결과 PDF는 대체가 발생한 모든 위치에 대체 폰트를 표시하므로 **경고 콜백이 정상적으로 작동**했음을 시각적으로 확인할 수 있습니다.

---

## 흔히 발생하는 실수와 전문가 팁

| 문제점 | 발생 원인 | 해결 방법 |
|---------|----------------|-----|
| **콜백이 실행되지 않음** | `LoadOptions.WarningCallback`이 문서를 로드하기 *이전*에 할당되지 않았습니다. | 항상 `new Document(...)`를 호출하기 **이전**에 콜백을 연결하세요. |
| **잘못된 폰트 폴더** | 경로 오타 또는 읽기 권한 부족. | 폴더가 존재하고 애플리케이션에 `Read` 권한이 있는지 확인하세요. 신뢰성을 위해 절대 경로를 사용하세요. |
| **다중 대체, 과도한 출력** | 많은 누락 폰트가 있는 대형 문서. | `WarningType.FontSubstitution`으로 경고를 필터링(예시와 같이)하거나 콘솔 대신 로그 파일에 기록하세요. |
| **대체 폰트가 적용되지 않음** | 대체 폰트가 머신에 설치되지 않았습니다. | `SetFontsFolder`에 전달한 폴더에 `.ttf`/`.otf` 파일을 넣으세요. Aspose.Words가 직접 로드하므로 OS에 설치할 필요가 없습니다. |

**프로 팁:** CI/CD 파이프라인에서 실행할 때는 콘솔 출력을 빌드 아티팩트로 리다이렉트하세요. 이렇게 하면 빌드 중 발생한 모든 폰트 대체에 대한 감사 로그를 확보할 수 있습니다.

---

## 전체 작동 예제 (복사‑붙여넣기 바로 사용)

아래는 새 콘솔 앱 프로젝트에 바로 넣을 수 있는 완전한 프로그램입니다. 모든 단계, `using` 구문, 주석이 포함되어 있습니다.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**예상 콘솔 출력** (예를 들어 `Times New Roman`이 누락된 경우):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

프로그램을 실행하고 `output.pdf`를 열면 필요한 곳마다 대체 폰트가 적용된 문서를 확인할 수 있습니다.

---

## 결론

이제 C#에서 **경고 콜백을 설정**, **기본 폰트를 구성**, **폰트 변경을 모니터링**, 그리고 Aspose.Words를 사용할 때 **기본 가져오기 폰트를 설정**하는 견고하고 생산 환경에 적합한 패턴을 갖추었습니다. 로드 전에 경고 수집기를 연결하고, `FontSettings`를 신뢰할 수 있는 폰트 폴더에 지정하며, 필요에 따라 전역 대체 폰트를 강제함으로써 폰트 대체에 대한 완전한 가시성과 제어를 얻을 수 있습니다—이는 어떤 문서 처리 파이프라인에도 필수적인 요소입니다.

다음 단계에 도전해 보세요:

- 데이터베이스에서 **동적 폰트 로드** (`FontSettings.SetFontsFolder`를 런타임에 사용).  
- **구조화된 로그**(JSON 또는 CSV)로 기록하는 **맞춤형 경고 핸들러** 구현.  
- **병렬 문서 처리** 시 각 스레드가 자체 `LoadOptions`를 사용하도록 하여 교차 간섭 방지.  

코드를 자유롭게 실험하고, 자신의 아키텍처에 맞게 조정한 뒤, 발견한 내용은 댓글에 공유해 주세요. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}