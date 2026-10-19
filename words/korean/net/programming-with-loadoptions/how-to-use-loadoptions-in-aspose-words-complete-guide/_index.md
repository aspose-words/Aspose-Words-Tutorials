---
category: general
date: 2026-01-10
description: Aspose.Words에서 누락된 글꼴을 처리하기 위해 LoadOptions를 사용하는 방법을 배웁니다. 단계별 코드, 팁
  및 견고한 문서 로드를 위한 모범 사례.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: ko
og_description: Aspose.Words에서 누락된 글꼴을 처리하기 위해 LoadOptions를 사용하는 방법. 설명과 실용적인 팁이 포함된
  전체 실행 가능한 예제를 확인하세요.
og_title: Aspose.Words에서 LoadOptions 사용 방법 – 완전 가이드
tags:
- Aspose.Words
- C#
- .NET
title: Aspose.Words에서 LoadOptions 사용 방법 – 완전 가이드
url: /ko/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 LoadOptions 사용 방법 – 완전 가이드

Word 문서를 로드할 때 폰트가 누락될 수 있다는 상황을 **어떻게 처리해야 할지** 궁금하셨나요? 이런 고민은 혼자만 하는 것이 아닙니다. 실제 프로젝트에서는 문서가 여러 컴퓨터를 오가며, 대상 시스템에 작성자가 사용한 정확한 글꼴이 없을 때가 많습니다. 그 결과? 레이아웃이 깨지거나 중요한 문자가 보이지 않거나, 브랜드 이미지와 맞지 않는 폰트 대체가 발생합니다.  

다행히 Aspose.Words는 `LoadOptions` 객체와 경고 콜백을 제공하여 *누락된 폰트를 깔끔하게 처리*할 수 있게 해줍니다. 이 튜토리얼에서는 **LoadOptions를 사용하여** 폰트 대체 경고를 캡처하고, 로그에 기록하며, 처리 파이프라인을 견고하게 유지하는 방법을 단계별로 배웁니다.

다룰 내용:

* 경고 콜백 클래스 설정  
* 해당 콜백을 포함한 `LoadOptions` 구성  
* 누락된 폰트를 추적하면서 문서 로드  
* 문제 해결 팁 및 확장 방법  

외부 문서는 필요 없습니다—여기서 바로 시작하세요.

---

## 준비물

시작하기 전에 다음을 준비하세요:

* **Aspose.Words for .NET** (2026년 현재 최신 버전) – NuGet을 통해 설치  
* .NET 개발 환경 (Visual Studio, Rider, 혹은 VS Code)  
* 설치되지 않은 폰트를 참조하는 샘플 DOCX 파일 (`input.docx`라고 부릅니다)  

그 외에 추가 라이브러리는 필요하지 않습니다.

---

## 1단계 – 폰트 대체를 캡처할 경고 콜백 정의

첫 번째 퍼즐 조각은 `IWarningCallback`을 구현하는 클래스입니다. Aspose.Words는 주목할 만한 상황이 발생할 때마다(예: 누락된 폰트) `Warning` 메서드를 호출합니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**이것이 중요한 이유:**  
`WarningType.FontSubstitution`만 필터링하면 관련 없는 경고(예: 사용 중단된 기능)로 인한 잡음이 사라집니다. 콜백을 통해 파일에 로그를 남기거나 예외를 발생시키거나, 프로그램matically 대체 폰트를 삽입하는 등 완전한 제어가 가능합니다.

---

## 2단계 – 콜백을 포함한 LoadOptions 구성

핸들러를 만들었으니 이제 Aspose.Words에 이를 사용하도록 알려야 합니다. 바로 **LoadOptions를 실제로 사용하는 방법**입니다.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**팁:** `LoadOptions`에는 `Password`, `LoadFormat`, `Encoding` 등 다양한 옵션이 있습니다. 필요에 따라 체인처럼 연결할 수 있지만, 누락된 폰트를 다룰 때는 `WarningCallback`이 핵심입니다.

---

## 3단계 – 구성된 옵션으로 문서 로드

`LoadOptions`가 준비되었으면 문서를 로드하는 과정은 매우 간단합니다. Aspose.Words는 찾을 수 없는 폰트가 있을 때 자동으로 콜백을 호출합니다.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**예상 출력:**  

`input.docx`에 설치되지 않은 *“GothicBold”* 폰트가 사용된 경우 다음과 같은 경고가 표시됩니다:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

경고 라인은 **누락된 폰트를 만나자마자** 정확히 출력되어 즉시 피드백을 제공합니다.

---

## 4단계 – (선택) 문서 추가 처리

보통 파일을 로드한 뒤에 더 많은 작업을 수행합니다. 아래는 경고 설정과 자연스럽게 연동되는 몇 가지 일반적인 후처리 예시입니다.

### 4.1 문서를 PDF로 저장

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 알려진 대체 폰트로 누락된 폰트 교체

특정 대체 폰트(예: *“Calibri”*)를 사용하고 싶다면 저장하기 전에 `FontSettings`를 조정합니다:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 모든 경고를 파일에 기록

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

이 스니펫들은 **LoadOptions를 기본 사용 사례 외에** 활용하는 방법을 보여 주며, 프로덕션 수준 솔루션에 필요한 유연성을 제공합니다.

---

## 흔히 발생하는 실수와 **누락된 폰트**를 우아하게 처리하는 방법

| 실수 | 발생 원인 | 해결 / 완화 방법 |
|------|----------|-------------------|
| **콜백 미연결** | `WarningCallback` 설정을 빼먹음 | 문서를 로드하기 전에 반드시 `LoadOptions` 인스턴스를 만들고 핸들러를 할당하세요. |
| **콜백이 콘솔에만 출력, 저장 안 함** | 웹 서비스에서는 콘솔 출력이 사라짐 | `Console.WriteLine`을 Serilog, NLog 등 로거나 영구 저장소에 기록하도록 교체하세요. |
| **여러 누락 폰트 중 첫 번째만 보고** | 첫 경고에서 예외를 발생시킴 | 콜백은 가볍게 유지하고, 중단이 필요할 때만 예외를 던지세요. |
| **대체 폰트가 눈에 띄게 다름** | 기본 대체가 시각적으로 유사하지 않음 | `FontSettings.SubstitutionSettings.FontSubstitutionRules`를 사용해 선호하는 대체 폰트를 우선순위에 두세요. |
| **대용량 문서에서 성능 저하** | 경고 콜백이 수천 번 호출됨 | 경고를 리스트에 모아 로드 후 일괄 처리하거나, 고유 폰트 이름만 필터링하세요. |

위 상황들을 인지하면 **누락된 폰트**를 예기치 않게 처리하는 일을 방지할 수 있습니다.

---

## 전체 동작 예제 – 모든 파트 합치기

아래는 전체 흐름을 보여 주는 완전 실행 가능한 프로그램입니다. 콘솔 프로젝트에 복사·붙여넣기하고 Aspose.Words NuGet 패키지만 추가하면 바로 동작합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**프로그램 실행 시** 다음을 수행합니다:

1. 폰트 대체 경고를 콘솔에 출력합니다.  
2. 원본 레이아웃을 `output.pdf`로 저장합니다.  
3. 대체 폰트를 *Calibri* 혹은 *Arial*로 강제 적용한 `output-with-fallback.pdf`를 추가 저장합니다.

---

## 자주 묻는 질문 (FAQ)

**Q: DOC, RTF, HTML 파일에도 적용되나요?**  
A: 네. `LoadOptions`는 형식에 구애받지 않으며, 올바른 파일 경로만 전달하면 모든 지원 형식에서 누락 폰트 경고 콜백이 작동합니다.

**Q: 경고를 완전히 숨길 수 있나요?**  
A: 네. 동작이 필요 없으면 `new IWarningCallback { Warning = _ => {} }`와 같은 무동작 콜백을 지정하거나 `LoadOptions.WarningCallback = null`로 설정하면 됩니다. 다만 가시성을 잃으면 중요한 폰트 문제를 놓칠 수 있습니다.

**Q: 누락된 폰트를 임베디드 폰트로 교체하고 싶다면?**  
A: `FontSettings`에 `AddFontSource`를 사용해 대체 폰트 파일을 임베드하고, 대체 규칙과 결합하면 매끄러운 교체가 가능합니다.

**Q: 콜백이 스레드‑안전한가요?**  
A: 대용량 문서를 병렬 로드할 경우 콜백이 여러 스레드에서 호출될 수 있습니다. 로그 파일 등 공유 자원을 사용할 때는 동기화가 필요합니다.

---

## 결론

이번 가이드를 통해 Aspose.Words에서 **LoadOptions를 사용하여 누락된 폰트를** 효과적으로 처리하는 방법을 익혔습니다. `IWarningCallback`을 구현하고 이를 `LoadOptions`에 연결한 뒤 문서를 로드하면 폰트 대체 이벤트를 실시간으로 파악할 수 있습니다. 이후 로그를 남기거나, 대체 폰트를 지정하거나, 임베드 폰트를 삽입하는 등 원하는 방식으로 흐름을 확장하면 됩니다.

핵심 단계 요약:

1. `WarningType.FontSubstitution`에 집중하는 경고 콜백 구현  
2. 콜백을 `LoadOptions`에 연결  
3. 해당 옵션으로 문서 로드  
4. (선택) 추가 폰트 대체 규칙이나 로깅 적용  

필요에 따라 콘솔 로거를 구조화된 로거로 교체하고, 중요한 누락 폰트에 이메일 알림을 추가하거나, 대규모 배치 작업에 통합해 보세요. 이 패턴은 단일 파일부터 수천 개 파일을 처리하는 파이프라인까지 자연스럽게 확장됩니다.

코딩을 즐기시고, 언제나 올바른 글꼴로 문서가 렌더링되길 바랍니다!  

---

![LoadOptions 사용 예시]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}