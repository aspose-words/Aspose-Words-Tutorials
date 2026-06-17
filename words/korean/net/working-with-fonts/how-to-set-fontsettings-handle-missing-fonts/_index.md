---
category: general
date: 2026-05-29
description: Aspose.Words에서 FontSettings를 설정하고 누락된 글꼴을 우아하게 처리하는 방법을 배웁니다. 전체 코드와
  모범 사례가 포함된 단계별 가이드.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: ko
og_description: Aspose.Words에서 FontSettings를 설정하고 누락된 글꼴을 빠르게 처리하는 방법. 완전하고 실행 가능한
  솔루션을 위해 이 가이드를 따라보세요.
og_title: FontSettings 설정 방법 – 누락된 글꼴 처리
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: FontSettings 설정 방법 – 누락된 글꼴 처리
url: /ko/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# FontSettings 설정 방법 – 누락된 폰트 처리

Aspose.Words를 사용할 때 **FontSettings를 설정하는 방법**을 궁금해 본 적이 있나요? 그리고 설치되지 않은 폰트를 참조하는 문서를 만나본 적이 있나요? 특히 최소한의 폰트만 설치된 서버에서 클라이언트가 제공한 파일을 처리할 때 흔히 발생하는 문제입니다. 좋은 소식은? 이러한 빈틈을 포착하고 **누락된 폰트를 처리**하여 앱이 충돌하거나 보기 흉한 PDF가 생성되는 것을 방지할 수 있습니다.

이 튜토리얼에서는 실제 시나리오를 살펴봅니다: Linux 컨테이너에 “DejaVu Sans”만 설치된 상태에서 “Calibri”를 요구하는 DOCX를 로드하는 경우입니다. FontSettings를 구성하고, 대체 경고에 구독하며, 대체 폰트를 제공하여 문서가 작성자가 의도한 대로 렌더링되는 방법을 정확히 보여드립니다. 불필요한 설명은 없습니다—오늘 바로 프로젝트에 넣을 수 있는 코드만 제공합니다.

## 전제 조건

- .NET 6.0 이상 (API는 .NET Framework 4.7+에서도 동일하게 작동합니다)
- Aspose.Words for .NET 23.10 이상 (NuGet 패키지 이름은 `Aspose.Words`입니다)
- 기본 C# 개발 환경 (Visual Studio, Rider, 또는 VS Code)

위 조건을 갖추셨다면, 시작해 봅시다.

## 1단계: FontSettings 생성 및 대체 이벤트 구독

솔루션의 핵심은 `FontSettings` 객체입니다. `FontSubstitutionWarning` 이벤트에 핸들러를 연결하면 Aspose.Words가 누락된 글꼴을 교체해야 할 때마다 실시간 보고를 받을 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Why this matters:**  
When the engine can’t locate *Calibri*, it might fall back to *Arial* silently. By listening to the warning, you keep a transparent audit trail—perfect for debugging or compliance reporting.

> **Pro tip:** If you run this on a CI server, pipe the output to a log file so you can review which fonts were missing after a batch run.

## 2단계: FontSettings를 LoadOptions에 연결

`LoadOptions`는 문서가 어떻게 파싱되는지를 제어하는 관문입니다. 방금 구성한 `FontSettings`를 할당하면 이후에 로드되는 모든 `Document`가 우리의 대체 로직을 따르게 됩니다.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**What’s happening under the hood?**  
During the `Document` constructor Aspose.Words reads the XML of the DOCX, resolves font references, and—if a font isn’t found—triggers the warning we set up earlier. Without this hook, you’d never know a substitution took place.

## 3단계: 문서 로드 및 (선택적으로) 대체 폰트 정의

이제 파일을 메모리로 가져옵니다. 이미 대체 폰트 폴더(예: 앱에 포함된 OpenType 폰트 디렉터리)가 있다면 `FontSettings`에 해당 경로를 알려 주세요. 이 단계는 선택 사항이지만 *누락된 폰트를 처리*하는 가장 깔끔한 방법입니다.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Edge case alert:**  
If the document contains a custom font embedded as a binary stream, Aspose.Words will use it automatically—no substitution needed. The warning only fires for *missing* system fonts.

### 결과 확인

로드 후 PDF 또는 Word로 저장하여 모든 것이 정상적으로 보이는지 확인할 수 있습니다.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

프로그램을 실행하면 콘솔에 다음과 같은 줄이 출력됩니다:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

이 메시지가 보이면 **누락된 폰트를 성공적으로 처리**했으며 어떤 대체가 발생했는지 정확히 알 수 있습니다.

## 4단계: 고급 – 사용자 정의 폰트 대체 규칙 (선택 사항)

때때로 결정적인 매핑이 필요합니다. 예를 들어 *Times New Roman*을 항상 *Liberation Serif*로 교체하고 싶을 때 `FontSettings.SubstitutionTable`을 사용하면 됩니다.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Why bother?**  
Explicit rules give you control over typography, ensuring brand consistency across generated PDFs, especially when you’re producing marketing collateral.

## 흔히 발생하는 실수 및 회피 방법

| 실수 | 증상 | 해결 방법 |
|---------|---------|-----|
| **경고 출력 없음** | 폰트가 정상이라고 생각하지만 문서가 잘못 표시됩니다. | `FontSubstitutionWarning`이 문서를 로드하기 **전**에 연결되어 있는지 확인하십시오. |
| **대체 폰트 폴더가 스캔되지 않음** | 대체가 여전히 시스템 기본값으로 돌아갑니다. | `SetFontsFolder(path, true)`를 호출하고 두 번째 인수 `true`를 사용하여 하위 폴더까지 재귀적으로 검색하도록 합니다. |
| **대량 배치 시 성능 저하** | 1만 개의 문서를 로드하면 속도가 느려집니다. | 단일 `FontSettings` 인스턴스를 캐시하여 로드마다 재사용하고, 매번 새로 만들지 않도록 합니다. |
| **내장 폰트 무시** | 사용자 정의 내장 폰트가 사용될 것으로 기대했지만 대체가 발생합니다. | 원본 DOCX가 실제로 폰트를 내장했는지 확인하십시오 (Word → 파일 → 정보 → 폰트 확인). |

## 전체 작업 예제

아래는 복사‑붙여넣기만 하면 되는 완전한 프로그램 예제입니다. 이벤트 처리부터 최종 PDF 저장까지 모든 과정을 보여줍니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Expected console output** (example):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

프로그램을 실행하고 `Output.pdf`를 열면 텍스트가 대체 폰트로 렌더링된 것을 확인할 수 있습니다—누락된 글리프 사각형도 없고, 충돌도 없습니다.

## 결론

이제 **FontSettings를 설정하는 방법**과 **누락된 폰트를 우아하게 처리**하는 견고하고 프로덕션 수준의 패턴을 갖추었습니다. `FontSubstitutionWarning` 이벤트를 연결하고, 대체 폰트 디렉터리를 지정하며(필요 시) 명시적인 대체 규칙을 정의함으로써 자동화된 문서 파이프라인에서 타이포그래피에 대한 완전한 가시성과 제어권을 얻을 수 있습니다.

다음은? 브랜드 전용 글꼴 컬렉션을 추가하거나 `FontSourceBase` API를 탐색해 데이터베이스 또는 클라우드 스토리지에서 폰트를 로드해 보세요. 동일한 원칙을 적용하면 됩니다—`FontSettings`에 다른 소스를 연결하기만 하면 됩니다.

오른쪽‑왼쪽 스크립트나 이모지 폰트와 같은 특수 경우에 대한 질문이 있나요? 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}