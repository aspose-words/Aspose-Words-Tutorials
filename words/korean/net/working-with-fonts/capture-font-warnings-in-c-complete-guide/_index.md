---
category: general
date: 2026-03-06
description: C#에서 Word 문서를 로드할 때 글꼴 경고를 포착합니다. 누락된 글꼴을 감지하고, 문서의 글꼴을 확인하며, 누락된 글꼴을
  효율적으로 처리하는 방법을 배웁니다.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: ko
og_description: C#에서 Word 문서를 로드할 때 폰트 경고를 포착합니다. 이 튜토리얼에서는 누락된 폰트를 감지하고, 문서의 폰트를
  확인하며, 누락된 폰트를 처리하는 방법을 보여줍니다.
og_title: C#에서 폰트 경고 캡처하기 – 완전 가이드
tags:
- Aspose.Words
- C#
- Font Management
title: C#에서 폰트 경고 포착하기 – 완전 가이드
url: /ko/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 폰트 경고 캡처 – 완전 가이드

Word 문서를 처리할 때 **폰트 경고를 캡처**해야 했던 적이 있나요? 폰트 경고를 캡처하는 것은 **누락된 폰트를 감지**하고 최종 출력이 의도한 대로 정확히 표시되도록 보장하는 데 필수적입니다.  

이 튜토리얼에서는 `.docx` 파일을 로드하고, 로드 과정을 모니터링하며, 폰트 대체가 발생하면 이를 보고하는 실용적인 엔드‑투‑엔드 예제를 단계별로 살펴봅니다. 튜토리얼이 끝날 때쯤이면 **워드 문서를 안전하게 로드**하고, **문서 폰트를 확인**하며, **예기치 않은 런타임 오류 없이 누락된 폰트를 처리**하는 방법을 알게 될 것입니다.

## 배워게 될 내용

- Aspose.Words `Document`에 경고 수집기를 연결하는 방법.
- 누락되었거나 대체된 폰트를 나타내는 경고 유형.
- 프로덕션 수준 애플리케이션에서 해당 경고를 기록하거나 대응하는 방법.
- 누락된 폰트를 **우아하게 처리**해야 할 경우 사용자 정의 폰트 소스를 구성하는 팁.

> **Prerequisite:** 유효한 Aspose.Words for .NET 라이선스(또는 무료 체험판)를 보유하고 있으며, .NET 개발 환경(Visual Studio, Rider, 또는 VS Code)이 준비되어 있어야 합니다. 다른 라이브러리는 필요하지 않습니다.

---

## 폰트 경고 캡처 – 단계별

아래는 전체 실행 가능한 코드입니다. 각 섹션은 별도의 단계로 구분되어 있어 복사‑붙여넣기, 실험 및 로직 확장이 가능합니다.

![폰트 경고 캡처 다이어그램](image.png "경고 수집을 보여주는 다이어그램"){: alt="폰트 경고 캡처 다이어그램"}

### 1단계: 워드 문서 로드

먼저, 현재 머신에 설치되지 않은 폰트를 포함할 수 있는 **워드 문서를 로드**해야 합니다. `Document` 생성자가 대부분의 작업을 수행하지만, 필요에 따라 스트림이나 바이트 배열로 교체할 수 있도록 호출을 별도로 유지합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Why this matters:** 경고 핸들러 없이 문서를 로드하면 폰트 대체가 조용히 무시됩니다. 로드 **이전**에 `WarningCallback`을 설정하면 발생하는 모든 `FontSubstitution` 경고를 확인할 수 있습니다.

### 2단계: 경고 수집기 연결

`WarningInfoCollector` 클래스는 `IWarningCallback`의 내장 구현입니다. 각 경고를 리스트에 저장하여 나중에 검사할 수 있습니다.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Pro tip:** **누락된 폰트를** 보다 적극적으로 처리해야 할 경우(예: 로드를 중단하거나 특정 대체 폰트로 교체) `Console.WriteLine`을 사용자 정의 로직으로 교체할 수 있습니다—예외를 발생시키거나, 파일에 로그를 남기거나, 사용자 정의 폰트 소스를 추가하는 식으로.

### 3단계: 출력 확인

콘솔에서 프로그램을 실행하십시오. `input.docx`가 설치되지 않은 폰트를 사용하고 있다면 다음과 같은 줄이 표시됩니다:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

출력이 없으면 문서가 이미 사용 가능한 폰트만 사용했거나 **또는** Aspose.Words가 내장 대체 컬렉션에서 일치하는 폰트를 찾은 것입니다. 어느 경우든 **문서 폰트를 성공적으로 확인**한 것입니다.

---

## 라이선스 없이 누락된 폰트 감지 (무료 체험판)

30일 체험판을 사용 중이더라도 경고 메커니즘은 동일하게 작동합니다. 유일한 차이점은 체험판이 생성된 출력에 워터마크를 추가한다는 점이며, 이는 경고 수집에 **영향을 주지** 않습니다. 따라서 전체 라이선스를 구매하기 전에 안전하게 **누락된 폰트를 감지**할 수 있습니다.

---

## 누락된 폰트 처리 – 고급 옵션

때때로 대체가 발생하지 않도록 자체 폰트 파일(예: 기업 브랜드 폰트)을 제공하고 싶을 수 있습니다. Aspose.Words는 사용자 정의 폰트 폴더를 등록할 수 있게 해줍니다:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

문서를 로드하기 **전**에 위 코드를 배치하면 로더가 초기 파싱 단계에서 해당 폰트를 고려합니다. 이는 기본 시스템 폰트에 의존하지 않고 **누락된 폰트를 처리**하는 가장 신뢰할 수 있는 방법입니다.

---

## 일반적인 함정 및 회피 방법

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **로드 후에 경고 수집기 연결** | 문서가 이미 파싱되었으므로 경고가 기록되지 않습니다. | `new Document(path)` 호출 **전**에 `WarningCallback`을 연결합니다. |
| **일반 경고만 표시** | `WarningType`을 잘못 필터링했습니다. | 폰트 문제에 집중하려면 `WarningType.FontSubstitution`을 사용하십시오. |
| **누락된 폰트가 있음에도 출력이 없음** | Aspose.Words가 내장 대체 폰트(예: Arial)를 찾았습니다. | `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` 로 내장 대체를 비활성화합니다. |
| **대용량 문서 스캔 시 성능 저하** | 모든 경고를 수집하면 비용이 많이 들 수 있습니다. | `FontSubstitution`만 수집하도록 제한하거나, 배치로 경고를 처리합니다. |

---

## 전체 작업 예제 (복사‑붙여넣기 준비 완료)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**예상 콘솔 출력** (누락된 폰트가 두 개라고 가정할 때):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

콘솔에 “Document loaded successfully” 외에 아무 출력도 없으면 **문서 폰트를 확인**했으며 누락된 폰트가 없다는 의미입니다.

---

## 결론

우리는 Aspose.Words를 사용하여 C#에서 **폰트 경고를 캡처**하는 방법을 보여주었으며, 이는 **누락된 폰트를 감지**, **워드 문서를 안전하게 로드**, **문서 폰트를 확인**, 그리고 사용자 정의 폰트 소스를 통해 **누락된 폰트를 처리**하는 신뢰할 수 있는 방법입니다.  

이 패턴을 활용하면 PDF 생성, HTML 변환, 혹은 워드 파일을 단순히 보관하는 등 어떤 자동화 파이프라인에도 폰트 검증을 통합할 수 있습니다.

### 다음 단계는?

- **FontSettings.SubstitutionSettings** API를 탐색하여 자체 대체 규칙을 정의하십시오.
- 경고 수집을 로깅 프레임워크(Serilog, NLog)와 결합하여 프로덕션 모니터링에 활용하십시오.
- 이미지 해상도나 지원되지 않는 기능 등 다른 경고 유형을 캡처하려면 동일한 접근 방식을 사용하십시오.

폰트 처리나 Aspose.Words 전반에 대해 더 궁금한 점이 있나요? 댓글을 남기거나 Aspose 커뮤니티 포럼에 문의하십시오. 즐거운 코딩 되시고, 문서가 언제나 기대한 폰트로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}