---
category: general
date: 2026-06-20
description: Aspose.Words를 사용하여 C#에서 글꼴 대체 경고를 활성화하세요. LoadOptions를 구성하고, 경고를 캡처하며,
  누락된 글꼴을 효율적으로 처리하는 방법을 배워보세요.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: ko
og_description: Aspose.Words를 사용하여 C#에서 글꼴 대체 경고를 활성화합니다. 이 가이드는 LoadOptions 설정, WarningInfo
  읽기 및 누락된 글꼴 메시지 표시 방법을 보여줍니다.
og_title: C#에서 글꼴 대체 경고 활성화 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Aspose.Words를 사용한 C#에서 글꼴 대체 경고 활성화
url: /ko/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Aspose.Words를 사용하여 글꼴 대체 경고 활성화

서버에 설치되지 않은 글꼴을 Word 문서가 참조할 때 **글꼴 대체 경고를 활성화**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 누락된 글꼴은 생성된 PDF나 이미지의 레이아웃을 조용히 손상시킬 수 있으며, 이를 조기에 포착하는 유일한 방법은 Aspose.Words가 발생시키는 경고를 듣는 것입니다.

이 튜토리얼에서는 이러한 경고를 켜고, `WarningInfo` 컬렉션에서 꺼내어 콘솔에 의미 있는 메시지를 출력하는 방법을 단계별 예제로 보여드립니다. 끝까지 따라오시면 **Aspose.Words LoadOptions** 설정 방법, **C# 글꼴 대체 경고** 처리 방법, 그리고 문서 처리 파이프라인을 견고하게 유지하는 방법을 알게 됩니다.

또한 몇 가지 엣지 케이스—경고를 억제했을 때 혹은 출력 대신 로그에 기록해야 할 때—에 대해서도 다루고, 최신 Aspose.Words for .NET(버전 24.10 기준)에서 동작하는 완전한 복사‑붙여넣기 가능한 코드 샘플을 제공합니다.

## 필요 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 작동합니다)
- `Aspose.Words`에 대한 NuGet 참조 (`dotnet add package Aspose.Words` 로 설치)
- 설치되지 않은 글꼴을 참조하는 Word 파일 (예: `DocumentWithMissingFont.docx`)
- 적절한 IDE (Visual Studio, Rider, 또는 VS Code)

그게 전부입니다—추가 서비스도, 독점 도구도 필요 없습니다. 준비되셨나요? 바로 시작합니다.

## Step 1: Enable Font Substitution Warnings

먼저 해야 할 일은 Aspose.Words에 누락된 글꼴을 대체할 때 알림을 받겠다고 알려주는 것입니다. 이는 `LoadOptions` 객체의 `FontSettings` 속성을 통해 수행됩니다. 기본적으로 경고는 **비활성화**되어 API가 조용히 동작하도록 되어 있으므로, 직접 스위치를 켜야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **왜 이렇게 동작하나요:** `FontSettings`가 `null`이 아니면, 라이브러리는 문서를 로드하는 동안 발견한 모든 `WarningType.FontSubstitution` 항목을 자동으로 `Document.WarningInfo`에 채워 넣습니다. 이는 글꼴에 대한 “디버그 모드”를 켜는 것과 같습니다.

## Step 2: Load the Document with Configured Options

경고 컬렉션이 활성화되었으니, 방금 준비한 `LoadOptions`를 사용해 문서를 로드합니다. 문서에 누락된 글꼴이 있으면 Aspose.Words가 대체 글꼴을 적용하고 `WarningInfo` 리스트에 경고를 푸시합니다.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **프로 팁:** 여러 파일을 루프에서 처리한다면 동일한 `LoadOptions` 인스턴스를 재사용하세요—한 번 생성하면 반복당 몇 밀리초를 절약할 수 있습니다.

## Step 3: Iterate Over WarningInfo and Display Font Substitution Messages

문서가 로드되면 `WarningInfo` 컬렉션에 로드 중 발생한 모든 경고가 들어 있습니다. 여기서는 `WarningType.FontSubstitution`만 관심이 있으므로 해당 항목만 필터링합니다.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

위 코드를 누락된 “Papyrus” 글꼴을 참조하는 문서에 적용하면 다음과 같은 출력이 나올 수 있습니다:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

이것이 여러분이 찾던 **글꼴 대체 메시지**이며, 명확하고 실행 가능하며 로그에 기록하거나 알림 시스템에 보낼 준비가 된 형태입니다.

## Full Working Example

아래는 모든 내용을 하나로 묶은 독립 실행형 콘솔 프로그램입니다. 새 `.csproj`에 복사‑붙여넣기하고 **Run**을 눌러 실행하세요.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Expected Output

문서가 설치되지 않은 글꼴을 참조하고 있다면 다음과 비슷한 결과를 보게 됩니다:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

모든 글꼴이 머신에 존재한다면 프로그램은 단순히 다음을 출력합니다:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Common Pitfalls & Pro Tips

| 문제 | 발생 원인 | 해결/예방 방법 |
|-------|----------------|--------------------|
| **경고 사라짐** | `FontSettings`를 지우거나 `LoadOptions`에 포함하지 않았습니다. | 속성을 수정하지 않더라도 항상 `FontSettings`를 인스턴스화하세요. |
| **경고가 너무 많음** | 문서에 다양한 특수 글꼴이 많이 사용됩니다. | 대체를 줄이기 위해 `SetFontsFolder`를 사용해 `FontSettings`에 사용자 정의 글꼴 폴더를 추가하는 것을 고려하세요. |
| **루프에서 성능 저하** | 각 반복마다 `LoadOptions`를 새로 만들면 오버헤드가 발생합니다. | 모든 문서에 대해 단일 `LoadOptions` 인스턴스를 재사용하세요. |
| **콘솔 출력 없음** | `Console.WriteLine`이 무시되는 GUI 앱에서 실행 중. | 경고를 로거(`ILogger`)에 전달하거나 파일에 기록하세요. |

### Handling Warnings in a Real‑World Service

웹 API에서는 콘솔에 쓰는 것이 바람직하지 않을 수 있습니다. 대신 경고를 구조화된 로그로 전달하세요:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

이렇게 하면 **문서 경고 처리**를 유지하면서 서비스도 깔끔하게 유지할 수 있습니다.

## Extending the Example

- `if` 필터를 제거하여 다른 경고 유형(예: `WarningType.UnknownFileFormat`)을 캡처합니다.
- 전체 경고를 JSON으로 저장하여 다운스트림 분석에 활용합니다.
- `FontSettings.SubstitutionSettings.DefaultFontName`을 설정하여 특정 대체 글꼴을 강제합니다.

이 모든 작업은 **글꼴 대체 경고 활성화**를 마스터한 뒤 자연스럽게 확장할 수 있는 내용입니다.

## Conclusion

우리는 C#에서 Aspose.Words를 사용해 **글꼴 대체 경고를 활성화**하는 방법을, `LoadOptions` 설정부터 `WarningInfo` 반복 및 친절한 메시지 출력까지 단계별로 보여드렸습니다. 위 절차를 따르면 누락된 글꼴로 인한 레이아웃 변형을 사전에 방지할 수 있어 문서 처리 파이프라인을 안전하게 보호할 수 있습니다.

다음 단계로는 사용자 정의 글꼴 폴더를 추가하고, 경고를 파일에 기록하거나 모니터링 대시보드로 전송해 보세요. 동일한 패턴은 PDF 변환, 이미지 렌더링, 메일 머지 등 **문서 경고 처리**가 필요한 모든 시나리오에 적용됩니다.

**C# 글꼴 대체 경고**에 대한 질문이 있거나 clever한 해결 방법을 공유하고 싶다면 아래에 댓글을 남겨 주세요—행복한 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 한 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words에서 글꼴 대체 경고 활성화 – 완전 가이드](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Aspose.Words에서 글꼴 감지 방법 – 경고 및 설정 처리](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Java에서 Aspose.Words로 글꼴 대체 경고 캡처 – 완전 가이드](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}