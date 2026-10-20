---
category: general
date: 2026-06-17
description: Aspose.Words에서 글꼴 대체를 처리하고 .NET 개발자를 위한 단계별 튜토리얼로 누락된 글꼴을 빠르게 감지하세요.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: ko
og_description: Aspose.Words에서 글꼴 대체를 처리하고, 명확한 코드 예제로 문서에서 누락된 글꼴을 감지하는 방법을 배워보세요.
og_title: Aspose.Words에서 글꼴 대체 처리 – 전체 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Aspose.Words에서 글꼴 대체 처리 – 완전 프로그래밍 가이드
url: /ko/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 글꼴 대체 처리 – 완전한 프로그래밍 가이드

Word 문서가 서버에 설치되지 않은 글꼴을 참조할 때 **글꼴 대체를 어떻게 처리할지** 궁금하셨나요? 여러분만 그런 것이 아닙니다. 인보이스 생성기나 자동 보고서 서비스와 같은 실제 애플리케이션에서는 누락된 글꼴 때문에 레이아웃이 깨지는 경우가 많습니다.  

좋은 소식은 Aspose.Words가 **누락된 글꼴을 감지**하고 원하는 방식으로 대응할 수 있는 내장 경고 시스템을 제공한다는 점입니다. 이 튜토리얼에서는 경고 핸들러를 등록하고, 문서를 로드하며, 알아야 할 정확한 글꼴 대체 이벤트를 추출하는 과정을 단계별로 살펴봅니다. 마지막에는 “**누락된 글꼴을 어떻게 감지할까**?” 라는 질문에 대한 깔끔하고 프로덕션 수준의 코드를 확인할 수 있습니다.

## 이 튜토리얼에서 다루는 내용

* 모든 글꼴 대체에 대해 경고를 발생시키도록 Aspose.Words 설정하기
* 사용자 정의 핸들러에서 경고를 캡처해 로그를 남기거나, 교체하거나, 중단하기
* 캡처한 데이터를 사용해 문서를 저장하거나 렌더링하기 전에 **누락된 글꼴을 감지**하기
* 대체 글꼴이 조용히 선택되는 경우와 같은 엣지 케이스 트러블슈팅 팁
* .NET 콘솔 앱에 바로 넣어 실행할 수 있는 완전한 예제

> **Prerequisites** – 최신 .NET SDK(6.0 이상)와 유효한 Aspose.Words for .NET 라이선스(또는 임시 평가 키), 그리고 의도적으로 설치되지 않은 글꼴을 참조하는 샘플 DOCX가 필요합니다. 다른 서드파티 라이브러리는 필요하지 않습니다.

---

## ## 사용자 정의 경고 핸들러로 글꼴 대체 처리하기

Aspose.Words는 요청된 글꼴을 찾지 못할 때마다 `WarningInfo` 객체를 발생시킵니다. 기본적으로 이러한 경고는 무시되기 때문에 대체가 일어나도 눈치채지 못합니다. **글꼴 대체를 처리**하려면 기본 경고 핸들러를 실제 동작을 수행하는 핸들러로 교체하면 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### 왜 이렇게 동작하는가

* `FontSettings.DefaultWarningHandler`는 전역 정적 속성입니다—한 번 설정하면 현재 AppDomain 내 **모든** Aspose.Words 작업이 해당 대리자를 사용합니다.
* `WarningInfoCollectionHandler`는 `WarningInfo` 객체를 받아오며, 여기에는 `WarningType`과 사람이 읽을 수 있는 `Description`이 포함됩니다. `WarningType.FontSubstitution`으로 필터링하면 관심 있는 이벤트만 확인할 수 있습니다.
* `doc.Save`를 호출하면 라이브러리가 모든 글꼴을 해결하게 되고, 그때 경고가 발생합니다. 저장 없이 문서만 검사하고 싶다면 `doc.UpdatePageLayout()`을 대신 호출하면 됩니다.

**예상 콘솔 출력**(누락된 글꼴이 “Papyrus”인 경우):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

이 한 줄이 라이브러리가 **누락된 글꼴을 감지**하고 대체 글꼴을 선택했음을 증명합니다.

---

## ## 렌더링 전에 누락된 글꼴 감지하기

필요한 글꼴이 없을 경우 프로세스를 완전히 중단하고 싶을 때가 있습니다—예를 들어 브랜드 가이드라인이 정확한 타이포그래피를 요구하는 경우. 경고 핸들러를 확장해 모든 누락된 글꼴 메시지를 리스트에 수집한 뒤, 이를 기반으로 판단할 수 있습니다.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### “누락된 글꼴을 어떻게 감지할까”에 대한 답변

* `missingFonts` 리스트는 각 대체 이벤트를 기록하는 장부 역할을 합니다.
* `UpdatePageLayout` 이후 리스트를 검사해 계속 진행할지, 로그를 남길지, 예외를 발생시킬지 결정합니다.
* 이 패턴은 PDF, HTML, 이미지 등 어떤 출력 형식에도 적용됩니다—경고 시스템이 포맷에 구애받지 않기 때문입니다.

---

## ## 고급 팁: 특정 대체 글꼴로 누락된 글꼴 교체하기

기업 전용 글꼴을 반드시 사용해야 하는 경우, Aspose.Words에 누락된 모든 글꼴을 자동으로 지정한 대체 글꼴로 교체하도록 지시할 수 있습니다. 이는 문서를 수동으로 후처리하지 않아도 **여전히** 보기 좋은 상태로 유지하고 싶을 때 유용합니다.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

위 코드를 **문서 로드 전에** 삽입하세요. 이제 원래 이름이 무엇이든 누락된 글꼴은 “Calibri”(또는 Calibri가 없을 경우 “Arial”)로 교체됩니다. 경고는 여전히 발생하지만, 문서는 여러분이 제어하는 글꼴로 렌더링됩니다.

---

## ## 흔히 겪는 실수와 회피 방법

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **첫 호출 이후 경고가 사라짐** | 정적 `DefaultWarningHandler`가 앱의 다른 부분에서 다시 덮어쓰기됨 | 애플리케이션 시작 시 **한 번** 설정하거나, 핸들러를 저장해 두었다가 필요 시 재할당 |
| **첫 번째 누락 글꼴만 보고됨** | 일부 API가 경고를 배치 처리함; 큐를 비우려면 `UpdatePageLayout` 또는 `Save` 호출 필요 | 레이아웃 업데이트를 강제하거나, 생성하려는 형식으로 저장 |
| **중단 후에도 대체가 계속 발생** | 경고 핸들러가 이미 대체가 일어난 뒤에 실행됨 | 핸들러에서 **로그**를 남긴 뒤 예외를 throw해 이후 처리를 중단 |
| **Linux 컨테이너에서 누락된 글꼴** | Linux는 Windows 글꼴 카탈로그가 없어 대체가 많이 발생 | 컨테이너에 필요한 글꼴을 마운트하거나 `FontSettings.SetFontsFolder`로 사용자 정의 폰트 디렉터리 지정 |

---

## ## Web API 시나리오에서 글꼴 대체 감지하기

ASP.NET Core를 통해 문서를 제공한다면 콘솔 출력 대신 경고를 수집해 HTTP 응답에 포함시키는 것이 좋습니다.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

이제 API가 **누락된 글꼴을 감지**하고 PDF가 생성되기 전에 명확한 JSON 페이로드를 반환합니다. 이는 프로덕션 급 서비스에서 “how to detect missing fonts”를 구현한 실용적인 예시입니다.

---

## ## 구현 테스트 방법

1. **테스트 DOCX 만들기** – 머신에 설치되지 않은 글꼴(예: 최소 Docker 이미지에 없는 “Comic Sans MS”)을 참조하도록 설정합니다.  
2. 콘솔 앱 또는 API 엔드포인트 실행.  
3. 콘솔(또는 HTTP 응답)에 대체 경고가 표시되는지 확인.  
4. 선택적으로 생성된 PDF를 열어 글꼴 속성을 확인—Aspose.Words가 설정한 대체 글꼴을 사용하고 있어야 합니다.

경고는 표시되지만 PDF에 예상치 못한 글꼴이 사용된다면 `SubstitutionSettings` 순서를 다시 점검하세요; 첫 번째 매치가 우선 적용됩니다.

---

## ## 결론

이번 가이드에서는 Aspose.Words에서 **글꼴 대체를 처리**하는 모든 방법을 다루었습니다. 경고 핸들러 등록부터 **누락된 글꼴을 감지**하고 기업 전용 글꼴로 교체하는 방법까지. 내장 경고 시스템을 활용하면 “**누락된 글꼴을 어떻게 감지할까**?”라는 질문에 대한 완전한 답을 얻을 수 있습니다.

다음 단계는 **동적 글꼴 로딩**(`FontSettings.SetFontsFolder`)을 결합해 사용자 업로드 글꼴을 즉시 지원하거나, 경고 핸들러를 Serilog 같은 중앙 로깅 서비스에 연결하는 것입니다. 글꼴 처리를 정교하게 계측할수록 문서 파이프라인의 신뢰성은 높아집니다.

복잡한 글꼴 대체 상황에 직면했나요? 아래 댓글에 남겨 주세요. 함께 해결해 봅시다. Happy coding!

## 다음에 배울 내용은?

다음 튜토리얼들은 이번 가이드에서 다룬 기술을 확장하고, 추가 API 기능을 마스터하며, 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}