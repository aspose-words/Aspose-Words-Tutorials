---
category: general
date: 2026-02-18
description: Aspose.Words를 사용하여 C#에서 글꼴 경고를 캡처하고 누락된 글꼴을 감지하는 방법을 배워보세요. 단계별 가이드를
  따라 누락된 글꼴을 효율적으로 처리하세요.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: ko
og_description: C#에서 폰트 경고를 캡처하고, 누락된 폰트를 감지·처리·목록화하는 방법을 전체 코드 예제와 함께 배워보세요.
og_title: C#에서 폰트 경고 캡처하기 – 완전 가이드
tags:
- Aspose.Words
- C#
- Font Management
title: C#에서 폰트 경고 캡처 – 완전 프로그래밍 가이드
url: /ko/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 폰트 경고 캡처 – 완전 프로그래밍 가이드

서버에 설치되지 않은 폰트를 문서가 참조할 때 **폰트 경고를 캡처**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 엔터프라이즈 앱에서 누락된 폰트가 레이아웃 오류를 일으키며, 이를 발견할 수 있는 유일한 신뢰할 만한 방법은 라이브러리가 발생시키는 경고를 청취하는 것입니다.  

이 튜토리얼에서는 **폰트 경고를 캡처**할 뿐만 아니라 **누락된 폰트를 감지**, **누락된 폰트를 처리**, 그리고 **누락된 폰트를 나열**하는 즉시 실행 가능한 솔루션을 보여드립니다. 이를 통해 대체, 임베드 또는 사용자에게 알릴지를 결정할 수 있습니다. 외부 문서는 필요 없으며, 복사·붙여넣기만 하면 바로 실행됩니다.

## 배울 내용

- `LoadOptions`를 구성하여 폰트 대체 경고를 활성화하는 방법.  
- DOCX를 로드하고 모든 경고를 추출하는 데 필요한 정확한 코드.  
- 각 단계가 중요한 이유와 성능 고려 사항.  
- 혼합 스크립트 폰트나 사용자 정의 폰트 폴더가 있는 문서와 같은 엣지 케이스 처리.  

**전제 조건**: .NET 6+ (또는 .NET Framework 4.6+), **Aspose.Words** NuGet 패키지에 대한 참조, 그리고 C#에 대한 기본 이해. Aspose.Words를 처음 사용하더라도 걱정하지 마세요—이 가이드는 모든 세부 사항을 단계별로 안내합니다.

![Diagram showing capture font warnings flow](image.png){alt="폰트 경고 캡처 흐름도"}

## 폰트 경고 캡처 – 왜 중요한가

Aspose.Words가 문서를 로드할 때, 사용 불가능한 폰트를 조용히 대체 폰트로 교체합니다. 이 대체 폰트는 로드 작업을 유지하지만, 시각적인 결과는 완전히 어긋날 수 있습니다. **SubstitutionWarningLevel.All** 플래그를 켜면 라이브러리는 누락된 각 폰트에 대해 `WarningInfo` 항목을 추가하여, 문서가 렌더링되거나 저장되기 전에 **누락된 폰트를 감지**할 수 있게 합니다.

> **Pro tip:** 배치 작업에서 수백 개의 파일을 처리한다면, 이러한 경고를 중앙 저장소에 로깅하면 나중에 수시간에 달하는 수동 QA 작업을 절감할 수 있습니다.

## 단계 1: 프로젝트 설정

1. 좋아하는 IDE(Visual Studio, Rider, VS Code)를 엽니다.  
2. 새 콘솔 프로젝트를 생성합니다:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Aspose.Words 패키지를 추가합니다:

```bash
dotnet add package Aspose.Words
```

그게 전부—추가 DLL이나 COM 인터옵이 필요 없습니다. 라이브러리는 **누락된 폰트를 처리**하는 데 필요한 모든 것을 포함하고 있습니다.

## 단계 2: 모든 폰트 대체 경고를 캡처하도록 Load Options 준비

엔진이 **폰트 경고를 캡처**하도록 하려면 모든 대체를 기록하도록 알려야 합니다. 다음 스니펫은 `LoadOptions` 인스턴스를 만들고, 경고 레벨을 활성화하며, (선택적으로) 사용자 정의 폰트가 들어 있는 폴더를 엔진에 지정합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**왜 이것이 중요한가:**  
- `SubstitutionWarningLevel.All`은 **모든** 누락된 폰트 이벤트가 기록되도록 보장하며, 첫 번째 이벤트만 기록되지 않습니다.  
- 이 플래그가 없으면 Aspose.Words가 폰트를 조용히 교체하고 문제 존재 여부를 알 수 없습니다.

## 단계 3: 구성된 옵션으로 문서 로드

이제 실제로 파일을 엽니다. `DocumentWithMissingFonts.docx`를 테스트 문서의 경로로 바꾸세요.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

파일에 머신(또는 선택한 폴더)에 없는 폰트가 참조되어 있으면 `document.WarningInfoCollection`이 채워집니다.

## 단계 4: 폰트 대체 경고 찾기 및 표시

튜토리얼의 핵심입니다: `WarningInfoCollection`을 순회하여 **누락된 폰트를 나열**합니다. `WarningType.FontSubstitution`으로 필터링하고 친절한 메시지를 출력합니다.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

문서에 설치된 폰트만 사용된 경우 “✅ No missing fonts detected” 라인이 표시됩니다.

## 단계 5: 고급 – 프로그래밍 방식으로 **누락된 폰트 처리** 방법

단순히 목록을 출력하는 것만으로도 진단 도구에는 충분할 수 있지만, 많은 프로덕션 시스템에서는 **누락된 폰트를 자동으로 처리**해야 합니다. 아래는 두 가지 일반적인 전략입니다:

### 5.1 Known Fallback으로 대체

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Custom Font를 즉시 임베드

기업 폰트 파일(`MyBrand.ttf`)이 있다면, 누락된 폰트가 감지될 때 이를 임베드할 수 있습니다:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note:** 폰트를 임베드하면 출력 파일 크기가 증가할 수 있으므로, 품질과 대역폭 사이의 트레이드오프를 고려하십시오.

## 일반적인 함정 및 회피 방법

| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| 문서는 잘못 보이지만 경고가 나타나지 않음 | `SubstitutionWarningLevel`가 `All`로 설정되지 않음 | 단계 2에서 플래그가 정확히 설정되었는지 확인하십시오 |
| 경고에 동일한 폰트가 여러 번 표시됨 | 문서에 해당 폰트가 여러 스타일로 포함됨 | 고유한 목록만 필요하면 중복을 제거하십시오: `fontWarnings.Select(w => w.Description).Distinct()` |
| 대용량 DOCX 파일에서 애플리케이션이 충돌함 | 기본 메모리 설정으로 로드함 | `LoadOptions.LoadFormat`을 사용하거나 파일을 스트리밍하여 메모리 압력을 줄이십시오 |

## 전체 작업 예제 (복사·붙여넣기 준비 완료)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

`dotnet run`으로 프로그램을 실행하십시오. 누락된 폰트 목록이 콘솔에 출력되어 **폰트 경고를 성공적으로 캡처**했음을 확인할 수 있습니다.

## 결론

이제 Aspose.Words를 사용해 C#에서 **폰트 경고를 캡처**, **누락된 폰트를 감지**, **누락된 폰트를 처리**, 그리고 **누락된 폰트를 나열**하는 완전하고 프로덕션 준비된 패턴을 갖추었습니다. 이 접근 방식은 가볍고 몇 줄의 코드만 필요하며, 기존 파이프라인에 언제든지 삽입할 수 있습니다—당신이

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}