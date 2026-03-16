---
category: general
date: 2026-03-16
description: Aspose.Words에서 FontSettings를 사용하여 누락된 글꼴을 우아하게 처리하는 방법을 배우세요—전체 코드, 이벤트
  처리 및 모범 사례 팁.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: ko
og_description: Aspose.Words에서 FontSettings를 사용하여 누락된 글꼴을 처리하는 방법—전체 C# 예제와 실용적인 팁을
  포함한 단계별 가이드.
og_title: Aspose.Words에서 누락된 글꼴을 처리하기 위한 FontSettings 사용 방법
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose.Words에서 누락된 글꼴을 처리하기 위한 FontSettings 사용 방법
url: /ko/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 누락된 글꼴을 처리하기 위해 FontSettings 사용 방법

서버에 설치되지 않은 글꼴을 Word 문서가 참조할 때 **FontSettings를 어떻게 사용하는지** 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 누락된 글꼴은 보기 흉한 대체 글꼴을 사용하게 하거나 예외를 발생시킬 수 있으며, 대부분의 개발자는 문제가 프로덕션에 나타날 때까지 무시합니다.  

이 튜토리얼에서는 Aspose.Words에서 **누락된 글꼴을 처리하기 위해 FontSettings를 사용하는 방법**을 정확히 보여주고, 자세한 경고를 캡처하며, 문서 렌더링을 예측 가능하게 유지하는 방법을 설명합니다. 끝까지 진행하면 바로 실행 가능한 C# 샘플을 얻고, 각 라인이 왜 중요한지 이해하며, 대규모 프로젝트에 적용하는 방법을 알게 됩니다.

## 이 가이드에서 다루는 내용

- **FontSettings** 설정 및 `SubstitutionWarning` 이벤트 구독하기.  
- `LoadOptions`에 설정을 연결하여 문서를 로드할 때 적용되도록 하기.  
- 의도적으로 글꼴이 없는 테스트 문서를 실행하고 콘솔 출력을 확인하기.  
- 로깅, 자동 대체 비활성화, 여러 누락 글꼴 처리와 같은 엣지 케이스 팁 제공.  

외부 문서는 필요 없습니다—여기서 모든 것을 확인할 수 있습니다.

## 사전 요구 사항

- .NET 6+ (또는 .NET Framework 4.6.2+).  
- Aspose.Words for .NET 23.9 이상 (우리가 사용하는 API는 최신 버전에서도 안정적입니다).  
- 설치되지 않은 글꼴을 참조하는 간단한 `.docx` 파일 (예: Linux 컨테이너에서 *Comic Sans MS*).  

이것만 있으면 됩니다—Aspose.Words 외에 추가 NuGet 패키지는 필요하지 않습니다.

## 누락된 글꼴 처리가 중요한 이유

문서가 런타임에서 찾을 수 없는 글꼴을 참조하면 Aspose.Words는 자동으로 가장 근접한 글꼴을 대체합니다. 이 대체는 대부분 허용되지만, 경우에 따라 **누락된 글꼴을 로그**해야 할 수도 있고(규정 준수 목적) **대체 자체를 방지**해야 할 수도 있습니다(예: 브랜드 전용 PDF). `FontSettings.SubstitutionWarning`에 연결하면 전체 가시성과 제어권을 얻을 수 있습니다.

## 단계 1: FontSettings 생성 및 Substitution‑Warning 이벤트 구독

먼저 `FontSettings` 인스턴스를 생성합니다. 이 객체는 라이브러리의 모든 글꼴 관련 구성을 보관합니다. 핵심은 `SubstitutionWarning` 이벤트를 연결하는 것으로, Aspose.Words가 요청된 글꼴을 찾지 못할 때마다 **매번** 발생합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**왜 중요한가:**  
- **가시성:** 누락된 글꼴을 즉시 알 수 있습니다.  
- **감사 가능성:** 콘솔(또는 로거)을 파일로 리다이렉트하여 규정 준수 보고에 활용할 수 있습니다.  
- **제어:** 이후에 대체 글꼴을 사용자 정의 글꼴로 교체할 수 있습니다.

> **Pro tip:** 로깅 프레임워크(Serilog, NLog 등)를 사용한다면 `Console.WriteLine` 호출을 `logger.Information(...)` 으로 교체하세요.

## 단계 2: FontSettings를 LoadOptions에 연결

`LoadOptions`는 파일을 로드하는 동안 Aspose.Words가 어떻게 동작할지를 지정하는 매개체입니다. `FontSettings` 객체를 할당하면 경고 핸들러가 **콘텐츠가 파싱되기 전에** 활성화됩니다.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**왜 중요한가:**  
- `LoadOptions` 없이 문서를 로드하면 기본 글꼴 처리가 적용되어 경고를 놓치게 됩니다.  
- 같은 객체에서 비밀번호 보호 등 다른 로드 옵션도 함께 조정할 수 있습니다.

## 단계 3: 구성된 옵션으로 문서 로드

이제 실제 Word 파일을 읽습니다. 경로는 절대 경로나 상대 경로나 상관없으며, Aspose.Words는 방금 준비한 `LoadOptions`를 그대로 사용합니다.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

문서에 설치되지 않은 글꼴이 포함되어 있으면 `SubstitutionWarning` 이벤트가 발생하고 아래 예시와 유사한 출력이 콘솔에 표시됩니다.

### 예상 콘솔 출력

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

대체 글꼴은 운영 체제의 글꼴 대체 체인에 따라 달라질 수 있지만, **누락된 글꼴 이름**은 항상 보고됩니다.

## 단계 4: 결과 확인 (선택적 렌더링)

대체 후에도 문서가 정상적으로 보이는지 확인하고 싶을 때가 있습니다. 간단히 PDF로 저장하고 결과를 열어보세요.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

대체 자체를 **완전히 방지**하고 싶다면 로드하기 전에 `FontSettings.SubstitutionSettings.TableSubstitution = false` 로 설정하십시오. 그러면 누락된 글꼴에 대해 Aspose.Words가 예외를 발생시키며, 이를 잡아 처리할 수 있습니다.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## 전체 작동 예제

아래는 완전한 실행 가능한 프로그램입니다. 콘솔 애플리케이션에 붙여넣고 파일 경로만 조정한 뒤 **F5** 키를 눌러 실행하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### 기대 결과

- 콘솔에 누락된 각 글꼴과 선택된 대체 글꼴이 출력됩니다.  
- 옵션으로 저장한 PDF는 대체 글꼴을 사용해 레이아웃을 유지한 채 문서를 표시합니다.

## 흔히 묻는 질문 & 엣지 케이스

| Question | Answer |
|----------|--------|
| **여러 글꼴이 동시에 누락되면 어떻게 되나요?** | 이벤트가 누락된 글꼴마다 한 번씩 발생하므로 각각 별도의 로그 라인이 생성됩니다. |
| **대체 글꼴을 사용자 정의 글꼴로 교체할 수 있나요?** | 가능합니다. 이벤트 핸들러 내부에서 `e.SubstitutedFont = new FontInfo("MyCustomFont")` 를 호출하면 됩니다. |
| **임베디드 글꼴이 로드에 실패해도 경고가 발생하나요?** | 네. 외부 글꼴이든 임베디드 글꼴이든 동일한 경고가 발생합니다. |
| **`Document`를 반드시 Dispose 해야 하나요?** | `Document`는 `IDisposable`을 구현합니다. 파일을 여러 개 루프 처리한다면 `using` 블록으로 감싸는 것이 좋습니다. |
| **Linux 컨테이너에서도 동작하나요?** | 시스템 글꼴(`fontconfig` 등)을 찾을 수 있다면 동일한 이벤트 메커니즘이 작동합니다. |

## 모범 사례 & Pro Tips

- **로그 중앙화:** 콘솔과 영구 로그 파일 모두에 기록하는 헬퍼 메서드를 만들세요.  
- **배치 처리:** 수십 개의 문서를 변환할 때는 `FontSettings` 인스턴스를 재사용해 이벤트 구독을 중복하지 않도록 하세요.  
- **성능:** 경고는 거의 무시할 수 있는 오버헤드이지만, 수천 개 파일을 처리한다면 검증이 끝난 뒤 경고를 비활성화하는 것을 고려하세요.  
- **버전 안정성:** `SubstitutionWarning` API는 Aspose.Words 16.0부터 안정화되었으므로 향후 업그레이드에서도 안심하고 사용할 수 있습니다.

## 결론

Aspose.Words에서 **FontSettings**를 사용해 **누락된 글꼴을 우아하게 처리**하는 방법을 단계별로 살펴보았습니다. `FontSettings` 객체를 만들고 `SubstitutionWarning`에 구독한 뒤 `LoadOptions`를 통해 문서를 로드하면 글꼴 문제에 대한 완전한 가시성을 확보하고, 로그, 교체 또는 중단 여부를 자유롭게 결정할 수 있습니다.  

간단한 콘솔 출력부터 맞춤형 대체 로직까지, 이 패턴은 대규모 배치 문서 파이프라인에도 확장 가능해 출력의 일관성과 감사 가능성을 보장합니다.

**다음 단계:**  

- 이벤트 내부에서 `e.SubstitutedFont` 를 지정해 **맞춤형 글꼴 대체**를 탐색해 보세요.  
- **이미지 렌더링**과 결합해 썸네일 생성 파이프라인을 구축해 보세요.  
- 최종 PDF에 대체 글꼴을 직접 포함하려면 **Aspose.PDF** 를 검토해 보세요.

행복한 코딩 되시고, 문서가 다시는 누락된 글꼴 때문에 고통받지 않길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}