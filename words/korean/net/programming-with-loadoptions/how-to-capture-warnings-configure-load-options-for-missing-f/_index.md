---
category: general
date: 2026-03-30
description: DOCX 파일을 로드할 때 경고를 캡처하는 방법 – 누락된 글꼴을 감지하고, 글꼴 설정을 구성하며, C#에서 로드 옵션을 설정하는
  방법을 배웁니다.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: ko
og_description: DOCX 파일을 로드할 때 경고를 포착하는 방법 – 누락된 글꼴을 감지하고 C#에서 글꼴 설정을 구성하는 단계별 가이드.
og_title: 경고 캡처 방법 – 누락된 글꼴에 대한 로드 옵션 구성
tags:
- Aspose.Words
- C#
- Font management
title: 경고를 포착하는 방법 – 누락된 폰트에 대한 로드 옵션 구성
url: /ko/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 경고 캡처 방법 – 누락된 글꼴에 대한 로드 옵션 구성

문서가 설치되지 않은 글꼴을 사용하려고 할 때 나타나는 **경고 캡처 방법**에 대해 궁금해 본 적 있나요? 이는 워드‑프로세싱 라이브러리를 사용하는 많은 개발자들을 곤란하게 하는 상황이며, 특히 PDF 내보내기 파이프라인이 중단되기 전에 **누락된 글꼴을 감지**해야 할 때 그렇습니다.  

이 튜토리얼에서는 **글꼴 설정을 구성하고**, **로드 옵션을 설정**하며, 모든 대체 경고를 콘솔에 출력하는 실용적이고 바로 실행 가능한 솔루션을 보여드립니다. 마지막까지 읽으면 **누락된 글꼴을 처리**하는 정확한 방법을 알게 되어 애플리케이션을 견고하게 유지하고 사용자를 만족시킬 수 있습니다.

## 배울 내용

- 라이브러리가 글꼴 문제를 조용히 교체하지 않고 보고하도록 **로드 옵션을 설정**하는 방법
- 경고 캡처를 위한 **글꼴 설정 구성** 정확한 단계
- 프로그래밍 방식으로 **누락된 글꼴을 감지**하고 적절히 대응하는 방법
- 최신 Aspose.Words for .NET(v24.10 기준)에서 동작하는 완전한 복사‑붙여넣기 C# 예제
- 솔루션을 확장하여 경고를 로그에 기록하거나, 사용자 정의 글꼴로 폴백하거나, 중요한 글꼴이 없을 때 처리를 중단하는 팁

> **전제 조건:** Aspose.Words for .NET NuGet 패키지가 설치되어 있어야 합니다(`Install-Package Aspose.Words`). 다른 외부 종속성은 필요하지 않습니다.

---

## 단계 1: 네임스페이스 가져오기 및 프로젝트 준비

먼저 필수 `using` 지시문을 추가합니다. 이는 단순한 보일러플레이트가 아니라 `LoadOptions`, `FontSettings`, `Document`가 어디에 있는지 컴파일러에 알려주는 역할을 합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **프로 팁:** .NET 6+을 사용한다면 *global using* 문을 활성화하여 파일마다 이 라인들을 반복할 필요가 없습니다.

---

## 단계 2: 로드 옵션 설정 및 글꼴 대체 경고 활성화

**경고 캡처 방법**의 핵심은 `LoadOptions` 객체에 있습니다. 새 `FontSettings` 인스턴스를 만들고 `SubstitutionWarning` 이벤트 핸들러를 연결하면, 요청된 글꼴을 찾을 수 없을 때마다 라이브러리가 알림을 발생시킵니다.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**왜 중요한가:** 이벤트 구독을 하지 않으면 Aspose.Words는 조용히 기본 글꼴로 폴백하고, 어떤 글리프가 교체됐는지 전혀 알 수 없습니다. `SubstitutionWarning`을 청취하면 전체 감사 로그를 확보할 수 있어 규제‑엄격 환경에서 필수적입니다.

---

## 단계 3: 구성된 옵션으로 문서 로드

이제 경고가 연결되었으니, 앞서 준비한 `loadOptions`를 사용해 DOCX(또는 지원되는 다른 형식)를 로드합니다. `Document` 생성자는 즉시 글꼴 검사 로직을 트리거합니다.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

예를 들어 파일에 *“Comic Sans MS”*가 지정되어 있고, 머신에 *“Arial”*만 있다면 다음과 같은 메시지를 보게 됩니다:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

이 라인은 앞서 연결한 핸들러 덕분에 콘솔에 바로 출력됩니다.

---

## 단계 4: 캡처된 경고 확인 및 대응

경고를 캡처하는 것만으로는 절반에 불과합니다; 이후에 무엇을 할지 결정해야 합니다. 아래 예시는 경고를 리스트에 저장해 나중에 분석할 수 있는 간단한 패턴을 보여줍니다—파일에 로그를 남기거나 중요한 글꼴이 없을 때 가져오기를 중단하고 싶을 때 유용합니다.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**예외 상황 처리:**  
- **다중 누락 글꼴:** 리스트에는 대체마다 하나씩 항목이 들어가므로 반복하면서 상세 보고서를 만들 수 있습니다.  
- **사용자 정의 폴백 글꼴:** 자체 글꼴 파일이 있다면 로드하기 전에 `FontSettings`에 추가하세요: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. 그러면 경고에 시스템 기본 대신 사용자 정의 폴백이 표시됩니다.  

---

## 단계 5: 전체 작업 예제 (복사‑붙여넣기 준비)

모든 내용을 합치면, 지금 바로 컴파일하고 실행할 수 있는 독립형 콘솔 앱이 아래와 같습니다.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**예상 콘솔 출력**(DOCX에 누락된 글꼴이 참조된 경우):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

만약 “Times New Roman”과 같이 *중요한* 글꼴이 없으면 중단 메시지가 표시됩니다.

---

## 일반적인 질문 및 주의사항

| Question | Answer |
|----------|--------|
| **Do I need to call `SetFontsFolder` to capture warnings?** | No. The warning event works with the default system fonts. Use `SetFontsFolder` only when you want to provide extra fallback fonts. |
| **Will this work on .NET Core / .NET 5+?** | Absolutely. Aspose.Words 24.10 supports all modern .NET runtimes. Just ensure the NuGet package matches your target framework. |
| **What if I want to log warnings to a file instead of console?** | Replace `Console.WriteLine(msg);` with any logging framework call, e.g., `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Can I suppress warnings for specific fonts?** | Yes. Inside the event handler you can filter: `if (e.FontName == "SomeFont") return;`. This gives fine‑grained control. |
| **Is there a way to treat missing fonts as errors?** | Throw an exception manually inside the handler when a condition is met, or set a flag and abort after `Document` construction as shown in the example. |

---

## 결론

이제 **누락된 글꼴이 있는 문서를 로드할 때 발생하는 경고를 캡처하는** 견고하고 프로덕션‑레디 패턴을 갖추었습니다. **누락된 글꼴을 감지하고**, **글꼴 설정을 구성하며**, **로드 옵션을 적절히 설정**함으로써 글꼴 대체 이벤트를 완전히 가시화하고, 로그 기록, 폴백 적용, 혹은 중단 여부를 자유롭게 결정할 수 있습니다.  

다음 단계로 이 로직을 PDF 변환 파이프라인에 통합하고, 사용자 정의 폴백 글꼴을 추가하거나, 경고 리스트를 모니터링 시스템에 전달해 보세요. 이 접근 방식은 작은 유틸리티부터 엔터프라이즈‑급 문서 처리 서비스까지 확장 가능합니다.

---

### 추가 읽을거리 및 다음 단계

- **FontSettings 기능 더 살펴보기** – 사용자 정의 글꼴 임베드, 폴백 순서 제어, 라이선스 고려 사항 등.  
- **PDF 변환과 결합** – 경고를 캡처한 뒤 `doc.Save("output.pdf");`를 호출하고 PDF가 기대한 글꼴을 사용하는지 확인합니다.  
- **테스트 자동화** – 누락된 글꼴이 알려진 문서를 로드하는 단위 테스트를 작성하고, 경고 리스트에 예상 메시지가 포함되는지 검증합니다.  

문제가 발생하거나 개선 아이디어가 있으면 언제든 댓글을 남겨 주세요. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}