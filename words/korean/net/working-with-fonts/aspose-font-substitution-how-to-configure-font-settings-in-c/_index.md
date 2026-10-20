---
category: general
date: 2026-03-27
description: 'Aspose 글꼴 대체를 쉽게: .NET 앱에서 글꼴 설정을 구성하고, 경고를 캡처하며, 누락된 글꼴을 처리하는 방법을 배우세요.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: ko
og_description: 폰트 설정을 구성하고 경고 콜백으로 누락된 폰트를 처리하여 Aspose 폰트 대체를 마스터하세요. 완전한 C# 가이드.
og_title: Aspose 글꼴 대체 – C#에서 글꼴 설정 구성
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose 글꼴 대체 – C#에서 글꼴 설정 구성 방법
url: /ko/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose 글꼴 대체 – 글꼴 설정 구성 완전 가이드

문서가 갑자기 사용자 지정 글꼴을 일반적인 글꼴로 바꾸는 경우를 겪어본 적 있나요? 그것이 **aspose font substitution**이 작업을 수행하는 것으로, 누락된 글꼴을 가장 가까운 매치로 교체합니다. 편리하지만, *정확히* 어떤 글꼴이 교체되었는지 알아야 한다면 라이브러리의 경고 시스템에 접근하고 직접 글꼴 설정을 구성해야 합니다.

이 튜토리얼에서는 실제 시나리오를 따라가 보겠습니다: 누락된 글꼴을 참조하는 DOCX를 로드하고, 대체 이벤트를 캡처하며, 콘솔에 친절한 메시지를 출력합니다. 끝까지 진행하면 **configure font settings**에 익숙해지고, **Aspose.Words warning callback**을 연결하며, 샘플을 어떤 워크플로에도 확장할 수 있게 됩니다.

> **필요한 사항**  
> • .NET 6+ (또는 .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (최신 NuGet)  
> • 누락된 글꼴을 참조하는 DOCX (예: `MissingFont.docx`)  

자, 시작해 보겠습니다.

---

## Step 1: Install Aspose.Words and Prepare the Project

코드를 작성하기 전에 Aspose.Words 패키지가 참조되어 있는지 확인하세요:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** 최신 안정 버전을 사용하세요; 2026년 3월 현재 버전은 23.11.0입니다. 최신 릴리스는 글꼴 매칭 알고리즘을 개선하고 추가 경고 유형을 제공합니다.

새 콘솔 앱을 만들거나 기존 프로젝트에 코드를 추가하고, 일반적인 `using` 지시문을 추가합니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

이 네임스페이스를 통해 `Document`, `LoadOptions` 및 필요한 글꼴 관련 클래스를 사용할 수 있습니다.

---

## Step 2: Configure Font Settings with LoadOptions

**aspose font substitution** 제어의 핵심은 `LoadOptions.FontSettings`에 있습니다. 빈 `FontSettings` 객체를 제공하면 Aspose가 기본 검색 경로를 사용하도록 하면서, 대체 정보를 경고 콜백을 통해 보고하도록 합니다.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

왜 기본값만 사용하지 않을까요? 경고 콜백(다음 단계)을 연결하려면 `FontSettings` 속성이 null이 아니어야 합니다. 이 작은 한 줄이 실제 글꼴 검색 동작을 바꾸지 않으면서도 대체 프로세스에 훅을 제공합니다.

---

## Step 3: Attach a Warning Callback to Capture Substitutions

Aspose.Words는 `IWarningCallback` 인터페이스를 구현합니다. 누락된 글꼴과 같은 중요한 일이 발생하면 `Warning` 메서드를 호출합니다. 우리는 `WarningType.FontSubstitution`을 필터링하고 설명을 콘솔에 출력하는 작은 핸들러를 구현합니다.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

그리고 실제 핸들러는 다음과 같습니다:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **왜 중요한가** – 콜백이 없으면 Aspose가 조용히 글꼴을 교체하고, 어떤 글꼴이 사용됐는지 알 수 없습니다. 콜백을 통해 프로세스가 투명해져서 규정 준수 보고나 레이아웃 디버깅에 필수적입니다.

---

## Step 4: Load the Document Using the Configured Options

이제 준비한 `loadOptions`를 전달하면서 문서를 로드합니다. 소스 파일이 설치되지 않은 글꼴을 참조하면 핸들러가 작동합니다.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

`YOUR_DIRECTORY`를 `MissingFont.docx`가 실제로 위치한 경로로 바꾸세요. 프로그램을 실행하면 다음과 유사한 출력이 표시됩니다:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

이 라인은 누락된 글꼴과 Aspose가 선택한 대체 글꼴을 정확히 알려줍니다.

---

## Step 5: (Optional) Fine‑Tune Font Search Paths

사내 전용 글꼴 폴더가 있다면 시스템 글꼴에 fallback하기 전에 Aspose가 해당 폴더를 검색하도록 지정할 수 있습니다. 이는 **configure font settings**의 고급 활용 예입니다:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

`recursive: true` 옵션을 사용하면 하위 폴더까지 스캔합니다. 이제 라이브러리는 사설 글꼴을 먼저 시도하므로 원치 않는 대체가 발생할 가능성이 줄어듭니다.

---

## Full Working Example

모든 코드를 합치면 다음과 같은 완전한 실행 프로그램이 됩니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**예상 출력** (누락된 글꼴이 발견된 경우):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

모든 글꼴이 존재하면 프로그램은 조용히 실행되며(경고 없음) PDF를 생성합니다.

---

## Common Questions & Edge Cases

### What if I need to *prevent* substitution altogether?

`FontSettings.SubstitutionSettings`를 `null`로 설정하거나 `FontSettings.FontSubstitutionSettings`를 사용해 동작을 제어합니다. 예시:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

이제 Aspose는 조용히 대체하지 않고 예외를 발생시키며, 이를 잡아 처리할 수 있습니다.

### Does this work with other file formats (e.g., .doc, .rtf)?

물론입니다. 동일한 `LoadOptions` 객체를 파일 경로를 받는 모든 `Document` 생성자에 전달할 수 있습니다. 경고 콜백은 글꼴을 사용하는 모든 형식에서 작동합니다.

### Can I capture the *exact* fallback font name?

가능합니다. `info.Description` 문자열에 누락된 글꼴과 교체된 글꼴이 모두 포함됩니다. 프로그래밍적으로 이름이 필요하면 문자열을 파싱하거나 최신 버전에서 제공되는 `FontInfo` 객체를 사용할 수 있습니다.

### How does this behave in a multi‑threaded environment?

`FontSettings`는 **스레드 안전**하지 않습니다. 스레드당 별도의 `LoadOptions`(및 자체 `FontSettings`)를 생성하거나, 접근을 `lock`으로 보호하세요.

---

## Conclusion

우리는 C# 애플리케이션에서 **aspose font substitution**과 **configure font settings**를 마스터하기 위해 필요한 모든 것을 다루었습니다:

1. Aspose.Words를 설치하고 필요한 `using` 문을 추가합니다.  
2. 새 `FontSettings`가 포함된 `LoadOptions` 객체를 생성합니다.  
3. 사용자 정의 `IWarningCallback`을 연결해 대체 이벤트를 표시합니다.  
4. 문서를 로드하고 콜백이 누락된 글꼴을 보고하도록 합니다.  
5. (선택 사항) 검색 경로를 확장하거나 대체 자체를 비활성화합니다.

이 패턴을 사용하면 규정 준수를 위해 누락된 글꼴을 기록하거나 UI에서 사용자에게 알리거나, 배포 전에 대체 글꼴을 자동으로 삽입할 수 있습니다. 다음 단계로 **Aspose.Words 글꼴 대체 정책**을 탐색하거나 워크플로에 통합해 보세요.

행복한 코딩 되시고, 문서가 언제나 올바른 글꼴로 렌더링되길 바랍니다!  

---  

![Aspose.Words가 문서를 로드하고 FontSettings를 호출하며 경고 콜백을 트리거하고 대체 정보를 출력하는 흐름도](image-placeholder.png "aspose 글꼴 대체 워크플로우")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}