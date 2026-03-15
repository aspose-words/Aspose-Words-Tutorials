---
category: general
date: 2026-03-14
description: Aspose.Words로 누락된 글꼴을 빠르게 처리하세요. 글꼴 대체 경고를 캡처하고 LoadOptions를 구성하며 렌더링
  문제를 방지하는 방법을 알아보세요.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: ko
og_description: Aspose.Words에서 누락된 글꼴을 경고 수집기를 사용해 처리합니다. 이 튜토리얼은 글꼴 대체를 감지하고 기록하는
  방법을 단계별로 보여줍니다.
og_title: Aspose.Words에서 누락된 글꼴 처리 – 완전한 C# 가이드
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Aspose.Words에서 누락된 글꼴 처리 – 완전 C# 가이드
url: /ko/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

Also keep code placeholders unchanged.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 누락된 글꼴 처리 – 완전한 C# 가이드

Word 문서를 로드할 때 **누락된 글꼴을 처리**해야 했고, PDF나 이미지 출력이 왜 이상하게 보이는지 궁금했던 적이 있나요? 당신만 그런 것이 아닙니다. 누락된 글꼴 파일은 조용히 문제를 일으켜 완벽하게 디자인된 보고서를 뒤죽박죽으로 만들 수 있습니다.  

좋은 소식은? Aspose.Words는 이러한 글꼴 대체 이벤트를 포착하고, 로그에 기록하며, 원한다면 대체 글꼴로 교체할 수 있는 깔끔한 방법을 제공합니다. 이 튜토리얼에서는 경고 수집기를 설정하고 `LoadOptions`에 연결한 뒤, 누락된 글꼴이 있을 수 있는 문서를 로드하는 완전한 실행 예제를 단계별로 살펴보겠습니다.

이 가이드를 끝까지 읽으면 다음을 할 수 있게 됩니다:

* 문서 로드 중 발생하는 모든 글꼴 대체를 감지합니다.  
* 누락된 각 글꼴에 대해 친절한 콘솔 메시지를 출력하거나 로거로 라우팅합니다.  
* 필요에 따라 글꼴을 교체하도록 솔루션을 확장합니다.  

**Prerequisites** – 필요 사항:

* .NET 6.0 이상 (코드는 .NET Core 및 .NET Framework에서도 동작합니다).  
* Aspose.Words for .NET NuGet 패키지 (현재 버전 23.11).  
* 의도적으로 설치되지 않은 글꼴을 참조하는 Word 파일 – 여기서는 `doc-with-missing-font.docx`라고 부르겠습니다.  

이미 C#에 익숙하고 프로젝트가 설정돼 있다면 바로 코드로 넘어가도 됩니다. 그렇지 않다면 계속 읽어 주세요; 먼저 작은 설정 단계들을 다루겠습니다.

---

## 누락된 글꼴 처리가 중요한 이유

Aspose.Words가 문서를 로드할 때, 머신에 설치된 글꼴과 각 글리프를 매칭하려고 시도합니다. 정확한 글꼴을 찾지 못하면 가장 근접한 글꼴을 조용히 대체합니다. 이 대체는 줄 높이, 커닝을 변경하고 심지어 문자가 사라지게 만들 수도 있습니다. `WarningType.FontSubstitution` 이벤트를 캡처하면 **무엇이** 교체됐고 **왜** 교체됐는지 투명하게 확인할 수 있어 다음에 필수적입니다:

* 브랜드 일관성 유지 (기업 글꼴이 설계대로 정확히 표시되어야 함).  
* PDF 변환 문제 디버깅 – 종종 원인은 누락된 글꼴입니다.  
* 자동화된 문서 파이프라인 구축 시, 문제 파일을 수동 검토용으로 표시해야 할 때.

“왜”가 명확해졌으니, 이제 **어떻게** 진행할지 살펴보겠습니다.

---

## Step 1 – 경고 수집기 설정

첫 번째로 필요한 것은 Aspose.Words 경고를 청취할 수 있는 객체입니다. `DocumentWarnings`는 `IWarningCallback`을 구현하여 라이브러리가 경고를 발생시킬 때마다 반응할 수 있게 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**What’s happening?**  
* `DocumentWarnings`는 콜백 인터페이스를 감싸는 얇은 래퍼입니다.  
* 람다식은 `e.WarningType`을 확인해 관련 없는 경고(예: 사용 중단된 기능)를 무시합니다.  
* `e.WarningInfo`에 누락된 글꼴 이름이 들어 있으며, 이를 콘솔에 출력합니다.  

*Pro tip*: 프로덕션에서는 `Console.WriteLine`을 구조화된 로거(Serilog, NLog)로 교체하세요—타임스탬프와 로그 레벨을 자동으로 얻을 수 있습니다.

---

## Step 2 – LoadOptions에 수집기 연결

`LoadOptions`는 Aspose.Words로 여는 모든 문서의 관문 역할을 합니다. `fontWarnings` 인스턴스를 `WarningCallback` 속성에 할당하면 로드 과정 동안 수집기가 활성화됩니다.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Why use LoadOptions?**  
경고 외에도 `LoadOptions`를 사용하면 비밀번호 처리, 인코딩, 사용자 정의 리소스 로딩 등을 제어할 수 있습니다. 여기서는 경고 측면에 집중했지만, 동일한 패턴이 다른 콜백에도 적용됩니다.

---

## Step 3 – 구성된 옵션으로 문서 로드

이제 드디어 문서를 메모리로 가져옵니다. 글꼴이 누락된 경우, 수집기가 트리거되고 각 대체마다 콘솔 라인이 표시됩니다.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

예를 들어 *Calibri Light*를 참조하지만 테스트 머신에 *Calibri*만 설치돼 있는 문서를 실행하면 다음과 유사한 출력이 나타납니다:

```
Font 'Calibri Light' was substituted.
```

이것이 전체 감지 루프입니다—단순하지만 강력합니다.

---

## Step 4 – (Optional) 누락된 글꼴을 알려진 대체 글꼴로 교체

때때로 문제를 로그만 남기고 싶지는 않습니다; 렌더링 결과가 일관되도록 대체 글꼴을 강제하고 싶을 때가 있습니다. Aspose.Words는 누락된 글꼴을 교체 글꼴에 매핑하는 사용자 정의 `FontSettings` 객체를 제공한다.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Explanation**  
* 와일드카드 `"*"`는 Aspose.Words에게 *모든* 누락된 글꼴을 동일하게 처리하도록 지시합니다.  
* 필요에 따라 개별 글꼴을 별도로 매핑할 수도 있어 세밀한 제어가 가능합니다.  
* `document.FontSettings`를 설정한 뒤에는 이후의 모든 렌더링(PDF, 이미지, HTML)에서 해당 대체가 적용됩니다.

---

## 전체 작동 예제

아래는 콘솔 앱에 복사·붙여넣기 할 수 있는 완전한 프로그램입니다. 필요한 `using` 문, 오류 처리, 그리고 가독성을 위한 주석이 모두 포함돼 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Expected output** (누락된 글꼴이 감지될 때):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

소스 문서에 이미 모든 필수 글꼴이 포함돼 있다면 경고 라인은 나타나지 않으며, 별다른 문제가 없습니다.

---

## 흔히 묻는 질문 & 예외 상황

| Question | Answer |
|----------|--------|
| **글꼴을 교체하지 않고 로그만 남기고 싶다면 어떻게 하나요?** | `FontSettings` 블록을 완전히 생략하면 됩니다; 경고 수집기만으로 충분합니다. |
| **경고를 파일로 리다이렉트할 수 있나요?** | 예—`Console.WriteLine`을 `File.AppendAllText("font-warnings.log", …)`로 교체하면 됩니다. |
| **DOC, DOCX, ODT 모두에서 작동하나요?** | 물론입니다. `LoadOptions`는 Aspose.Words가 지원하는 모든 포맷에 적용됩니다. |
| **문서에 임베드된 사용자 정의 글꼴은 어떻게 되나요?** | 임베드된 글꼴은 대체 메커니즘을 우회하고 그대로 사용됩니다. |
| **성능에 영향을 미치나요?** | 오버헤드는 최소 수준입니다—누락된 글꼴당 콜백이 한 번 호출될 뿐입니다. 대량 배치 처리 시에는 이벤트당 기록 대신 경고를 모아두는 방식을 고려하세요. |

---

## 결론

우리는 `DocumentWarnings` 수집기를 `LoadOptions`에 연결하고, 필요에 따라 대체 글꼴을 지정한 뒤 결과를 저장함으로써 Aspose.Words에서 **누락된 글꼴을 처리하는 방법**을 보여주었습니다. 이 패턴을 사용하면 글꼴 대체 이벤트를 완전히 가시화할 수 있어 PDF, 이미지, HTML 변환 시 시각적 일관성을 유지하는 데 큰 도움이 됩니다.

다음 단계로 고려해볼 내용:

* 경고 수집기를 중앙 집중식 로깅 프레임워크와 통합합니다.  
* 누락된 글꼴이 있는 문서를 배치 처리할 수 있도록 UI 대시보드를 구축합니다.  
* 이 접근 방식을 Aspose.PDF와 결합해 생성된 PDF가 실제로 대체 글꼴을 사용했는지 검증합니다.  

자유롭게 실험해 보세요—예를 들어 `"Arial"`을 `"Tahoma"`로 바꾸거나 다른 문서 세트를 로드해 보는 식으로. 핵심 아이디어는 동일합니다: 경고를 포착하고, 필요한 조치를 취해 문서가 의도한 대로 정확히 표시되도록 유지합니다.

Happy coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}