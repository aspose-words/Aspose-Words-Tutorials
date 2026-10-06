---
category: general
date: 2026-02-26
description: Aspose.Words를 사용하여 C#에서 누락된 글꼴을 처리합니다. 글꼴 대체 경고를 포착하고 IWarningCallback을
  구현하여 문서가 올바르게 표시되도록 유지하는 방법을 배웁니다.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: ko
og_description: C#에서 누락된 글꼴을 빠르게 처리하세요. 이 가이드는 Aspose.Words를 사용하여 글꼴 대체 경고를 캡처하고,
  IWarningCallback을 구현하며, 결과를 확인하는 방법을 보여줍니다.
og_title: C#에서 누락된 글꼴 처리 – 단계별 Aspose.Words 튜토리얼
tags:
- Aspose.Words
- C#
- Document Processing
title: C#에서 Aspose.Words로 누락된 글꼴 처리 – 완전 가이드
url: /ko/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Aspose.Words로 누락된 글꼴 처리하기 – 완전 가이드

Word 문서를 C#에서 로드할 때 **누락된 글꼴을 처리**해야 했던 적이 있나요? 출력 결과가 이상하게 보이는 이유가 궁금했나요? 당신만 그런 것이 아닙니다. 소스 파일이 머신에 설치되지 않은 글꼴을 참조하면 Aspose.Words는 조용히 다른 글꼴로 대체하고, 이 때문에 레이아웃이나 브랜드 이미지가 깨질 수 있습니다.  

좋은 소식은? **경고 콜백**을 연결하면 모든 글꼴 대체 이벤트를 포착하고, 로그에 기록하며, 대체 글꼴을 제공할지 여부를 결정할 수 있습니다. 이 튜토리얼에서는 프로젝트 설정부터 콘솔 출력 확인까지 전체 과정을 단계별로 안내하므로, 다시는 보이지 않는 글꼴에 놀라지 않을 것입니다.

> **얻을 수 있는 것**: 누락된 각 글꼴을 보고하고, 경고가 발생하는 이유를 설명하며, 사용자 정의 로직을 위한 핸들러 확장 방법을 보여주는 실행 가능한 C# 콘솔 앱.

---

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Core와 .NET Framework 모두에서 동작)
- Visual Studio 2022 (또는 선호하는 C# IDE)
- Aspose.Words for .NET **라이선스** (무료 체험판으로 테스트 가능)
- 설치되지 않은 글꼴을 참조하는 Word 문서 (예: Linux 환경에서 *Comic Sans MS*)

위 항목을 갖추었다면 바로 시작합니다.

---

## 1단계: 새 콘솔 프로젝트 생성 및 Aspose.Words 추가

정돈된 작업을 위해 새 콘솔 프로젝트를 시작합니다.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **프로 팁**: 특정 런타임을 타깃으로 하려면 `--framework net6.0` 플래그를 사용하세요.

이 명령은 최신 Aspose.Words NuGet 패키지를 가져오며, 여기에는 `LoadOptions`와 `IWarningCallback` 타입이 포함됩니다.

---

## 2단계: 경고 핸들러 구현 (IWarningCallback)

Aspose.Words는 문서를 로드하는 동안 발생하는 모든 비치명적 문제에 대해 `WarningInfo` 객체를 발생시킵니다. `IWarningCallback`을 구현하면 해당 경고를 어떻게 처리할지 결정할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**왜 중요한가**: 핸들러가 없으면 글꼴 대체 경고가 조용히 무시됩니다. 이를 출력하면 어떤 글꼴이 누락됐고 Aspose.Words가 어떤 글꼴을 사용했는지 즉시 확인할 수 있습니다.

---

## 3단계: LoadOptions에 경고 콜백 설정

이제 핸들러를 문서 로드 과정에 연결합니다. `LoadOptions`를 사용하면 파일이 파싱되기 전에 콜백을 삽입할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **참고**: `YOUR_DIRECTORY`를 실제 테스트 `.docx` 파일이 있는 폴더 경로로 바꾸세요. `LoadOptions` 인스턴스를 `Document` 생성자에 전달하지 않으면 기본적으로 조용히 동작합니다.

---

## 4단계: 애플리케이션 실행 및 출력 확인

컴파일하고 실행합니다:

```bash
dotnet run
```

문서가 머신에 없는 글꼴(예: *Papyrus*)을 참조하고 있다면 다음과 같은 출력이 나타납니다:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

이 한 줄만으로 어떤 글꼴이 누락됐고 Aspose.Words가 어떤 대체 글꼴을 선택했는지 정확히 알 수 있습니다. 이제 누락된 글꼴을 포함시키거나, 원본 문서를 수정하거나, 대체를 그대로 받아들일지 결정하면 됩니다.

---

## 5단계: 고급 – 경고를 나중에 사용할 수 있도록 수집

경고를 즉시 출력하는 대신 저장하고 싶을 때가 있습니다. 아래는 메시지를 리스트에 모으는 간단한 핸들러 수정 예시입니다.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

그리고 `Main` 메서드를 다음과 같이 업데이트합니다:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

이제 로그 파일에 기록하거나 모니터링 서비스로 전송하거나 UI에 표시할 수 있는 재사용 가능한 리스트가 생겼습니다.

---

## 6단계: 흔히 발생하는 문제와 해결 방법

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **경고가 나타나지 않음** | 콜백이 연결되지 않았거나 `LoadOptions` 없이 문서를 로드했음 | `Document` 생성자를 호출하기 **전** `LoadOptions.WarningCallback`을 설정했는지 확인 |
| **메시지에 잘못된 글꼴 이름** | 일부 글꼴이 문서에 포함돼 있을 경우 Aspose.Words는 *원본* 이름을 보고함 | 원본 파일의 글꼴 참조를 확인; 글꼴을 포함시키면 경고가 사라짐 |
| **성능 영향** | 수천 개 문서에 대해 경고를 수집하면 오버헤드가 발생 | 빠른 디버깅 시에는 `Console.WriteLine`만 사용하고, 데이터가 필요할 때만 콜렉터로 전환 |

---

## 시각적 요약

![누락된 글꼴을 처리하는 흐름을 보여주는 경고 콜백 다이어그램](/images/handle-missing-fonts.png "Aspose.Words로 누락된 글꼴을 처리하는 다이어그램")

*다이어그램(대체 텍스트에 주요 키워드 포함)은 문서 로드 중 글꼴 대체 이벤트를 경고 콜백이 어떻게 가로채는지 시각화합니다.*

---

## 결론

이제 C#에서 Aspose.Words를 사용해 **누락된 글꼴을 처리**하는 방법을 알게 되었습니다. `LoadOptions`에 `IWarningCallback`을 연결하면 모든 글꼴 대체 이벤트를 완전히 파악하고, 로그를 남기거나 필요한 조치를 취할 수 있어 생성된 문서가 의도한 디자인을 유지하도록 보장할 수 있습니다.

> **빠른 요약**:  
> 1. 콘솔 앱에 Aspose.Words를 추가합니다.  
> 2. `FontWarningHandler`(또는 콜렉터)를 구현합니다.  
> 3. 문서를 로드할 때 `LoadOptions`에 전달합니다.  
> 4. 콘솔 출력이나 저장된 경고를 확인합니다.  

앞으로는 **누락된 글꼴 포함**(`FontSettings.SubstitutionSettings`)이나 **기업 글꼴 서버에서 자동 다운로드**와 같은 확장 기능을 탐색해 볼 수 있습니다—방금 만든 패턴의 자연스러운 확장입니다.

**Aspose.Words 글꼴 경고**, **C# LoadOptions**, 혹은 **누락된 글꼴이 있는 문서 로드**에 대해 더 궁금한 점이 있으면 댓글을 남겨 주세요. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}