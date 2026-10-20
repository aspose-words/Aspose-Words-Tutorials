---
category: general
date: 2026-04-02
description: Aspose.Words를 사용하여 C# 문서에서 글꼴을 감지하는 방법. 글꼴 설정을 구성하고 누락된 글꼴을 효율적으로 처리하는
  방법을 배워보세요.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: ko
og_description: Aspose.Words를 사용하여 C# 문서에서 글꼴을 감지하는 방법. 이 가이드는 글꼴 설정을 구성하고 누락된 글꼴을
  처리하는 방법을 보여줍니다.
og_title: C#에서 폰트를 감지하는 방법 – 완전 가이드
tags:
- C#
- Aspose.Words
- Document Processing
title: C#에서 폰트를 감지하는 방법 – 완전 가이드
url: /ko/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 폰트 감지하기 – 완전 가이드

.NET에서 Word 문서를 로드할 때 누락되었거나 대체된 **폰트를 감지하는 방법**이 궁금하셨나요? 여러분만 그런 것이 아닙니다—문서가 서버에 설치되지 않은 폰트를 참조하면 개발자들은 자주 난관에 봉착합니다. 좋은 소식은 Aspose.Words가 이러한 문제를 깔끔하고 프로그래밍 방식으로 찾아낼 수 있는 방법을 제공한다는 점입니다.

이 튜토리얼에서는 **폰트를 감지하는 방법**을 보여줄 뿐만 아니라 **폰트 설정을 구성**하고 **누락된 폰트를** 우아하게 처리하는 방법을 시연하는 실습 예제를 단계별로 살펴보겠습니다. 마지막까지 하면 모든 폰트 대체 경고를 출력하는 실행 가능한 코드 스니펫을 얻을 수 있으므로 필요에 따라 로그를 남기거나 알림을 보내거나 폰트를 교체할 수 있습니다.

---

## 필요한 준비물

- **Aspose.Words for .NET** (최신 버전이 가장 좋으며, 아래 코드는 .NET 6+을 대상으로 합니다)
- .NET 개발 환경 (Visual Studio, Rider, 또는 VS Code)
- 설치되지 않은 폰트를 참조하는 샘플 `.docx` 파일 (테스트에 유용합니다)

Aspose.Words 외에 추가 NuGet 패키지는 필요 없으며, 이 솔루션은 Windows, Linux, macOS 모두에서 동작합니다.

---

## 단계 1: Aspose.Words 설치 및 참조

먼저, 라이브러리를 프로젝트에 추가합니다. NuGet 명령은 간단합니다:

```bash
dotnet add package Aspose.Words
```

> **팁:** CI 서버를 사용 중이라면 패키지 버전을 고정하여 예상치 못한 깨지는 변경을 방지하세요.

---

## 단계 2: 폰트 설정 구성 (및 로드 옵션 준비)

문서를 열기 전에 Aspose.Words에 대체 폰트를 찾을 위치를 알려줄 수 있습니다. 이것이 **폰트 설정 구성** 단계이며, 엔진이 원하지 않는 폰트를 조용히 교체하는 것을 방지합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

왜 신경 써야 할까요? 문서가 *Comic Sans*를 참조하지만 서버에 *Calibri*만 있다면, Aspose.Words는 *Calibri*로 대체하고 경고를 발생시킵니다. 검색 경로를 구성함으로써 원치 않는 놀라움을 줄일 수 있습니다.

---

## 단계 3: 준비된 옵션으로 문서 로드

이제 실제로 파일을 엽니다. 이전 단계에서 만든 `LoadOptions`를 `Document` 생성자에 직접 전달합니다.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

파일을 찾을 수 없거나 손상된 경우 예외가 발생하므로, 실제 코드에서는 이를 try/catch로 감싸는 것이 좋습니다.

---

## 단계 4: 문서 경고에서 폰트 대체 검사

Aspose.Words는 파싱 중에 경고 목록을 수집합니다. 그 중 `FontSubstitutionWarning`은 어떤 폰트가 교체되었는지 정확히 알려줍니다.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

`Warnings` 컬렉션에는 다른 항목(`DocumentStructureWarning` 등)도 포함될 수 있습니다. `FontSubstitutionWarning`만 필터링하면 우리가 관심 있는 **누락된 폰트 처리** 상황만 보고하게 됩니다.

---

## 단계 5: 전체 합치기 – 완전 실행 가능한 예제

아래는 전체 프로그램입니다. 새 콘솔 앱에 복사‑붙여넣기하고 실행하면 누락된 폰트가 각각 콘솔에 출력되는 것을 확인할 수 있습니다.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**예상 출력** (예시):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

문서가 머신에 존재하는 폰트만 사용할 경우, 대신 “No font substitutions detected” 라인이 표시됩니다.

---

## 엣지 케이스 및 일반 질문

### 문서에 **경고가 전혀** 없으면 어떻게 하나요?

이는 단순히 모든 참조된 폰트를 구성한 검색 폴더에서 찾았다는 의미입니다. 예제의 `anySubstitutions` 플래그가 이 경우를 처리합니다.

### 콘솔 대신 파일에 경고를 **로그**할 수 있나요?

물론 가능합니다. `Console.WriteLine` 호출을 원하는 로거(Serilog, NLog 등)로 교체하면 됩니다. 더 자세한 정보가 필요하면 `WarningInfo` 객체가 `WarningType` 및 `WarningMessage`를 제공합니다.

### 특정 폰트(예: 절대 교체되지 않아야 하는 기업 브랜드 폰트)를 **무시**하려면 어떻게 하나요?

맞춤 대체 규칙을 추가할 수 있습니다:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

이제 Aspose.Words는 *MyBrandFont*을 나열된 대체 폰트로만 교체하며, 여전히 처리할 수 있는 경고를 받게 됩니다.

### 이것이 **Linux** 컨테이너에서도 동작하나요?

네—필요한 `.ttf`/`.otf` 파일이 들어 있는 폴더를 마운트하고 `SetFontsFolder`를 해당 경로로 지정하면 됩니다. Aspose.Words는 OS에 설치된 폰트에 의존하지 않습니다.

---

## 시각적 개요

![폰트 감지 흐름도](detect-fonts.png "문서에서 폰트를 감지하는 단계들을 보여주는 다이어그램")

*이미지 대체 텍스트:* **폰트 감지** 흐름도로, 구성, 로드 및 경고 검사를 설명합니다.

---

## 요약 – 배운 내용

- **Aspose.Words 경고**를 사용하여 누락되었거나 대체된 **폰트를 감지하는 방법**.  
- 사용자 정의 폰트 폴더를 지정하고 기본 대체 폰트를 설정하기 위해 **폰트 설정을 구성하는 방법**.  
- 로그 기록부터 맞춤 대체 규칙까지 **누락된 폰트를 처리하는 전략**.

이 모든 내용은 어떤 .NET 솔루션에도 삽입할 수 있는 간결하고 독립적인 콘솔 앱에 포함됩니다.

---

## 다음 단계 및 관련 주제

- **폰트 임베드**를 통해 출력 문서에 폰트를 직접 포함시켜 향후 대체를 방지 (`SaveOptions`와 `EmbedFullFonts` 사용).  
- **프로그래밍 방식 폰트 교체** – 저장하기 전에 누락된 폰트를 특정 대체 폰트로 교체.  
- **성능 튜닝** – 배치로 다수의 문서를 처리할 때 `FontSettings`를 캐시.

이러한 주제에 관심이 있다면 *configure font settings*와 *handle missing fonts*를 검색해 보세요—Aspose.Words를 활용한 폰트 관리에 대한 심층 자료를 찾을 수 있습니다.

코딩 즐겁게! 특이한 폰트 이슈가 있나요? 댓글을 남겨 주세요, 함께 문제를 해결해 드리겠습니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}