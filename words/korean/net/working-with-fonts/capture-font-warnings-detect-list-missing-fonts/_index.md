---
category: general
date: 2025-12-31
description: Aspose.Words에서 폰트 경고를 캡처하여 누락된 폰트를 감지하고 .NET 애플리케이션에서 누락된 폰트를 나열합니다.
  단계별 C# 솔루션을 배워보세요.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: ko
og_description: Aspose.Words에서 폰트 경고를 캡처하여 누락된 폰트를 감지하고 누락된 폰트를 나열합니다. 코드와 팁이 포함된
  완전한 C# 가이드.
og_title: 폰트 경고 캡처 – 누락된 폰트 감지 및 목록화
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: 폰트 경고 캡처 – 누락된 폰트 감지 및 목록화
url: /ko/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 폰트 경고 캡처 – 누락된 폰트 감지 및 목록화

Word 문서를 로드할 때 **폰트 경고를 캡처**해야 했지만 누락된 폰트 세부 정보를 어떻게 표시해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다. 실제 프로젝트에서는 누락된 폰트가 레이아웃 오류를 일으키고, 적절한 경고가 없으면 보이지 않는 버그를 쫓게 됩니다.  

이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 **누락된 폰트를 감지**하고 **누락된 폰트를 목록화**하는 방법을 보여드립니다. 끝까지 따라오시면 모든 대체 경고를 출력하는 실행 가능한 C# 스니펫을 얻을 수 있어, 로그를 남기거나 알림을 보내거나 폰트를 자동으로 교체할 수 있습니다.

---

## 폰트 경고 캡처가 중요한 이유

Aspose.Words가 서버에 설치되지 않은 폰트를 참조하는 DOCX를 열면 조용히 대체 폰트를 사용합니다. 문서는 정상적으로 보이지만 시각적 정확성이 손상됩니다—예를 들어 기업 로고가 잘못된 서체로 표시되는 상황을 생각해 보세요.  

이러한 경고를 캡처하면 다음을 할 수 있습니다:

* **브랜드 일관성 유지** – 어떤 폰트가 누락되었는지 정확히 알 수 있습니다.
* **자동 복구** – 누락된 폰트를 프로그래밍 방식으로 교체합니다.
* **감사 및 규정 준수** – 법무 또는 디자인 검토를 위한 보고서를 생성합니다.

요컨대, **폰트 경고 캡처**는 조용한 폰트 대체에 대한 첫 번째 방어선입니다.

---

## 누락된 폰트를 감지하기 위한 LoadOptions 설정

경고를 표시하는 핵심은 `LoadOptions.FontSubstitutionWarning` 속성입니다. 기본값은 `None`으로 설정되어 있어 Aspose.Words가 메시지를 무시합니다. 이를 `All`로 전환하면 라이브러리가 모든 대체 이벤트를 기록합니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **팁:** 이미 사용자 지정 폰트 폴더가 있다면 문서를 로드하기 전에 `FontSettings.SetFontsFolder("path")`에 지정하십시오. 이렇게 하면 시스템 디렉터리에 없는 **누락된 폰트**를 감지할 수 있습니다.

---

## 문서를 로드하고 누락된 폰트 목록화

이제 `LoadOptions`가 준비되었으니 Word 파일을 로드합니다. 생성자는 옵션 객체를 받아들이며, 모든 대체는 문서의 `WarningInfoCollection`에 기록됩니다.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

파일이 사용 가능한 폰트를 참조하지 않을 경우, 각 누락된 폰트마다 `WarningInfo` 항목이 생성됩니다. 해당 컬렉션을 반복하면 **누락된 폰트를 목록화**할 수 있습니다.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

일반적인 출력 예시:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

각 행은 누락된 폰트를 정확히 알려주며, **누락된 폰트 목록화** 요구 사항을 충족합니다.

---

## WarningInfoCollection 읽고 해석하기

`WarningInfoCollection`에는 다양한 경고 유형(`DocumentStructure`, `ImageLoading` 등)이 포함될 수 있습니다. 폰트 문제에만 집중하려면 `WarningType.FontSubstitution`으로 필터링합니다.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

왜 필터링하나요? 큰 문서는 손상된 이미지나 지원되지 않는 기능에 대한 경고도 생성할 수 있습니다. 컬렉션을 좁히면 잡음이 사라지고 **폰트 경고 캡처** 출력이 깔끔해집니다.

---

## 전체 작업 예제 – 실제 폰트 경고 캡처

아래는 .NET 콘솔 프로젝트에 바로 넣어 사용할 수 있는 완전하고 독립적인 프로그램입니다. `LoadOptions` 구성부터 누락된 폰트 목록 출력까지 모든 단계를 보여줍니다.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**예상 콘솔 출력**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

문서에 누락된 폰트가 없으면 다음과 같이 표시됩니다:

```
All referenced fonts are available – no warnings captured.
```

---

## 일반적인 엣지 케이스 및 해결 방법

| 상황 | 발생 원인 | 권장 해결책 |
|-----------|----------------|-----------------|
| **문서에 내장된 OpenType 폰트 사용** | Aspose.Words는 내장 폰트를 읽을 수 있지만 파일이 손상되지 않은 경우에만 가능합니다. | 먼저 Word에서 DOCX를 확인하고, 필요하면 폰트를 다시 내장하십시오. |
| **경고가 대량 발생** (예: 200개 이상의 누락된 폰트) | 레거시 시스템에서 대량 가져오기를 할 경우 다양한 폰트 팔레트를 참조하게 됩니다. | 경고를 배치 처리하세요: 데이터베이스에 저장한 뒤 폰트 설치 스크립트를 실행합니다. |
| **WarningInfoCollection이 비어 있음** | 문서에 모든 폰트가 있거나 `FontSubstitutionWarning`이 `None`으로 남아있기 때문입니다. | `LoadOptions` 구성을 다시 확인하고 올바른 파일 경로를 로드했는지 확인하십시오. |
| **네트워크 공유에 사용자 지정 폰트가 위치함** | 네트워크 지연으로 폰트 조회 시 타임아웃이 발생할 수 있습니다. | `FontSettings`에 `SetFontsFolder`를 사용해 폰트를 미리 로드하고 `CacheFontData = true`로 설정하십시오. |

이 팁을 통해 복잡한 환경에서도 **누락된 폰트를 감지**할 수 있습니다.

---

## 이미지 예시

![폰트 경고 캡처 예시](https://example.com/images/capture-font-warnings.png "폰트 경고 캡처 예시")

*스크린샷은 두 개의 누락된 폰트가 보고된 콘솔 실행 화면을 보여줍니다.*

---

## 다음 단계 – 단순 보고를 넘어선 확장

이제 **폰트 경고를 캡처**할 수 있으니 자동 복구를 고려해 보세요:

1. **자동 폰트 대체** – `FontSettings.SubstitutionSettings`를 수정하여 누락된 폰트를 회사 승인 대체 폰트로 교체합니다.
2. **모니터링 시스템에 로깅** – 경고 메시지를 Serilog, ELK, Azure Application Insights 등으로 파이프합니다.
3. **사용자용 보고서** – 디자이너가 설치해야 할 폰트를 검토할 수 있도록 HTML 또는 PDF 요약을 생성합니다.

이 모든 확장은 우리가 다룬 기본 토대, 즉 `LoadOptions` 구성, 문서 로드, `WarningInfoCollection` 읽기에 기반합니다.

---

## 결론

여러분은 이제 Aspose.Words에서 **폰트 경고를 캡처**, **누락된 폰트를 감지**, 그리고 **누락된 폰트를 목록화**하는 방법을 깨끗한 콘솔 친화적 출력과 함께 배웠습니다. 이 접근 방식은 직관적이며 몇 줄의 C# 코드만 필요하고, Aspose.Words 23.x 이상을 지원하는 모든 .NET 버전에서 작동합니다.  

폰트를 의도적으로 제거한 샘플 DOCX로 시도해 보세요—즉시 경고가 표시됩니다. 그 후 누락된 서체를 설치하거나 프로그래밍 방식으로 대체하거나, 나중에 검토를 위해 로그에 남길지 결정하면 됩니다.

행복한 코딩 되시길 바라며, 여러분의 문서가 항상 올바른 폰트로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}