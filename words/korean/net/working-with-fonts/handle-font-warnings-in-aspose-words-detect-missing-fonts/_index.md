---
category: general
date: 2026-02-28
description: C#를 사용하여 Aspose.Words에서 글꼴 경고를 처리하고 누락된 글꼴을 감지하는 방법을 배우세요. 전체 코드를 포함한
  단계별 완전 가이드.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: ko
og_description: Aspose.Words에서 글꼴 경고를 처리하고 실행 가능한 C# 예제로 누락된 글꼴을 감지하세요. 단계별로 따라가며
  결과를 확인해 보세요.
og_title: Aspose.Words에서 글꼴 경고 처리하기 – 완전 가이드
tags:
- Aspose.Words
- C#
- Document Loading
title: Aspose.Words에서 글꼴 경고 처리 – 누락된 글꼴 감지
url: /ko/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 폰트 경고 처리 – 누락된 폰트 감지

Word 문서를 로드할 때 **폰트 경고를 처리**해야 했던 적이 있나요? 텍스트가 이상하게 보이는 이유가 궁금했나요? 당신만 그런 것이 아닙니다. 누락된 폰트는 대체 경고를 발생시켜 시각 레이아웃을 조용히 손상시킬 수 있으며, **누락된 폰트를 감지**하지 않으면 무엇이 잘못됐는지 알 수 없습니다.

이 튜토리얼에서는 Aspose.Words의 `IWarningCallback`을 사용하여 **폰트 경고를 처리**하는 실용적인 방법을 보여드립니다. 가이드를 끝까지 따라오면 모든 폰트‑대체 이벤트를 포착하고, 로그에 기록하며, 로드를 중단할지 여부까지 결정할 수 있습니다. 외부 문서는 필요 없으며, 복사‑붙여넣기만 하면 되는 예제 하나만 제공합니다.

## 배울 내용

- 폰트‑대체 알림에만 반응하도록 맞춤 경고 핸들러를 설정합니다.  
- `LoadOptions`에 핸들러를 연결하여 모든 문서 로드가 이를 통과하도록 합니다.  
- 콘솔 출력 결과를 확인하고 각 경고가 의미하는 바를 이해합니다.  

**Prerequisites**

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 동작합니다).  
- NuGet을 통해 설치한 Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- 머신에 설치되지 않은 폰트를 참조하는 Word 파일(예: 커스텀 기업 폰트).  

위 항목 중 누락된 것이 있다면 지금 확보하세요—그렇지 않으면 진행할 수 없습니다.

## Aspose.Words에서 폰트 경고를 처리하는 방법

아래는 전체 실행 가능한 프로그램입니다. `using` 구문부터 `Main` 메서드까지 모두 포함되어 있으니 콘솔 앱에 붙여넣고 **F5**만 누르면 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **예상 콘솔 출력** (문서에 설치되지 않은 폰트가 사용된 경우):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

문서에 **누락된 폰트가 전혀 없**으면 경고 라인이 나타나지 않으며, 따라서 필요할 때만 **누락된 폰트를 감지**한 것이 됩니다.

### 왜 이렇게 작동할까

Aspose.Words는 파일을 파싱하는 동안 발생하는 모든 비‑중요 이슈에 대해 `WarningInfo`를 발생시킵니다. `IWarningCallback`을 구현하면 해당 파이프라인에 훅을 걸 수 있습니다. `WarningType.FontSubstitution` 플래그는 라이브러리가 요청된 폰트를 대체 폰트로 교체해야 했을 때 정확히 알려줍니다. 이는 로드 **중에** 실행되므로 문서 객체 모델에 접근하기 전 가장 신뢰할 수 있는 **폰트 경고 처리** 방법입니다.

## 앱을 중단하지 않고 누락된 폰트 감지하기

때때로 누락된 폰트를 치명적인 오류로 취급하고 싶을 수 있습니다—예를 들어 브랜드 가이드라인에서 어떠한 대체도 허용되지 않을 때. 핸들러를 수정해 로그만 남기는 대신 예외를 발생시키도록 할 수 있습니다:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

이제 `new Document(...)`를 감싼 `try…catch` 블록이 문제를 포착하므로, 중단, 폰트 대체, 사용자에게 알림 등 원하는 동작을 선택할 수 있습니다.

## 보너스: UI 애플리케이션에서 경고 시각화하기

WinForms나 WPF 앱을 만든다면 `Console.WriteLine`을 UI‑친화적인 호출로 교체하세요:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

이렇게 하면 최종 사용자가 즉시 경고를 확인할 수 있고, 모든 플랫폼에서 **폰트 경고를 일관되게 처리**할 수 있습니다.

## Common Pitfalls & Pro Tips

- **Pitfall:** `WarningCallback`을 설정하지 않음. 기본 동작은 폰트 경고를 무시하므로 절대 보이지 않습니다.  
  **Pro tip:** 경고 핸들러만 필요하더라도 `LoadOptions` 인스턴스를 항상 생성하세요. 비용도 적고 명시적입니다.  

- **Pitfall:** 비‑Windows OS에서 잘못된 경로 구분자를 사용함.  
  **Pro tip:** `Path.Combine`을 사용하거나 원시 문자열 리터럴(`@"C:\Docs\MissingFont.docx"`은 Windows에서, Linux에서는 `"/home/user/docs/MissingFont.docx"`)을 활용하세요.  

- **Pitfall:** 임베디드 폰트에 대해 경고가 발생할 것이라 가정함.  
  **Pro tip:** 임베디드 폰트는 존재하는 것으로 간주되므로 대체 경고가 나타나지 않습니다. 실제 *누락된* 폰트로 테스트해 핸들러가 작동하는지 확인하세요.  

- **Pitfall:** 모든 경고 유형을 과도하게 로깅함.  
  **Pro tip:** 예시와 같이 `WarningType.FontSubstitution`으로 필터링하면 콘솔이 깔끔해지고 **누락된 폰트 감지** 시나리오에 집중할 수 있습니다.  

## 전체 작업 예제 요약

주석 없이 깔끔한 코드를 원하는 분들을 위해 전체 프로그램을 다시 한 번 보여드립니다:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

복사‑붙여넣기 후 실행하면 콘솔이 이제 **폰트 경고를 처리**하고 **누락된 폰트를 자동으로 감지**합니다.

## Next Steps

- **Log to a file:** `Console.WriteLine`을 로거(예: NLog)로 교체해 프로덕션 수준 추적을 구현합니다.  
- **Batch processing:** 폴더에 있는 여러 문서를 순회하면서 모든 폰트‑대체 이벤트를 CSV 보고서로 수집합니다.  
- **Automatic font installation:** 경고 핸들러에 연결해 기업 저장소에서 누락된 폰트를 다운로드하고 로드를 계속 진행합니다.  

이러한 확장 기능들은 모두 **폰트 경고를 깔끔하고 재사용 가능한 방식**으로 처리한다는 핵심 아이디어 위에 구축됩니다.

---

*행복한 코딩 되세요! **누락된 폰트를 감지**하려다 이상 현상이 발생하면 아래에 댓글을 남겨 주세요. 기꺼이 문제 해결을 도와드리겠습니다.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}