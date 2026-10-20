---
category: general
date: 2026-03-25
description: 워드 문서를 로드하고 누락된 글꼴을 감지하기 위해 경고 콜백을 생성합니다. Aspose.Words for .NET에서 글꼴
  설정을 구성하는 방법을 알아보세요.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: ko
og_description: 누락된 글꼴을 감지하면서 Word 문서를 로드하기 위한 경고 콜백을 생성합니다. 이 가이드는 Aspose.Words에서
  글꼴 설정을 구성하는 방법을 보여줍니다.
og_title: 경고 콜백 만들기 – Word 문서 로드 및 누락된 글꼴 감지
tags:
- Aspose.Words
- C#
- Font handling
title: Word 문서 로드 시 경고 콜백 만들기 – 완전 가이드
url: /ko/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 경고 콜백 만들기 – Word 문서 로드 및 누락된 글꼴 감지

Word 문서를 로드할 때 **경고 콜백을 만들** 필요성을 느껴본 적이 있나요? 그리고 왜 일부 글꼴이 사라지는지 궁금했나요? 당신만 그런 것이 아닙니다. 많은 엔터프라이즈 앱에서 누락된 글꼴은 레이아웃 재앙을 일으키며, 적절한 콜백이 없으면 문제를 전혀 인지하지 못할 수도 있습니다.  

좋은 소식은? Aspose.Words for .NET을 사용하면 **Word 문서를 로드**, **누락된 글꼴을 감지**, **글꼴 설정을 구성**을 몇 줄의 깔끔한 코드로 할 수 있습니다. 이 튜토리얼에서는 완전하고 실행 가능한 예제를 단계별로 살펴보고, 각 부분이 왜 중요한지 설명하며, 경고 콜백이 제대로 작동하는지 확인하는 방법을 보여드립니다.

> **학습 목표**  
> * DOCX를 로드하고 글꼴 대체를 보고하며 글꼴 검색 경로를 사용자 지정할 수 있는 전체 C# 프로그램  
> * `FontSettings`, `LoadOptions`, `IWarningCallback` 클래스에 대한 이해  
> * 임베디드 글꼴이나 시스템 전역 글꼴 폴더와 같은 엣지 케이스를 처리하기 위한 팁  

---

## Prerequisites

- .NET 6+ (또는 .NET Framework 4.7.2+)와 C# 컴파일러.  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`).  
- 머신에 설치되지 않은 최소 하나의 글꼴을 사용하는 샘플 Word 파일 (`input.docx`) (예: 최소 Windows 컨테이너에서 *Calibri Light*).  
- C# 콘솔 앱에 대한 기본적인 친숙함.

추가 라이브러리는 필요하지 않으며, 모든 기능은 Aspose.Words 내부에 포함됩니다.

---

## Step 1: Create warning callback to detect missing fonts

이 퍼즐의 **핵심**은 `IWarningCallback`을 구현하는 클래스입니다. Aspose.Words는 경고가 필요할 상황—가장 흔히는 글꼴 대체—을 만나면 이 콜백을 호출합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**왜 중요한가** – 콜백이 없으면 로그를 사후에 일일이 살펴봐야 합니다. 실시간으로 경고를 처리하면 로드를 중단할지, 누락된 글꼴을 대체 글꼴로 교체할지, 혹은 나중에 검토하도록 로그만 남길지 결정할 수 있습니다.

---

## Step 2: Configure FontSettings for custom font handling

문서를 실제로 로드하기 전에 시스템에 없는 글꼴을 찾을 위치를 Aspose.Words에 알려줄 수 있습니다. 바로 `FontSettings`가 그 역할을 합니다.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**왜 중요한가** – 누락된 글꼴이 들어있는 폴더를 지정하면 대체 없이 원본 글꼴을 사용할 수 있습니다. 불가능할 경우 *Arial* 같은 합리적인 기본값을 지정해 문서 가독성을 유지할 수 있습니다.

---

## Step 3: Load Word document with the configured warning callback

이제 모든 것을 연결합니다: `LoadOptions`를 만들고, `FontSettings`와 `FontWarningHandler`를 연결한 뒤 문서를 로드합니다.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**왜 중요한가** – `LoadOptions`는 문서를 어떻게 읽을지 설정하는 유일한 장소입니다. 글꼴 구성과 경고 콜백을 동시에 제공함으로써 누락된 글꼴을 올바른 위치에서 찾고 즉시 보고하도록 보장합니다.

---

## Step 4: Verify the output – what should you see?

콘솔에서 프로그램을 실행합니다. `input.docx`가 설치되지 않은 글꼴을 사용하고 `C:\SharedFonts`에도 없으면 다음과 같은 출력이 나타납니다:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

모든 글꼴이 사용 가능하면 경고 라인은 전혀 표시되지 않습니다. 이 즉각적인 피드백 루프는 자동화된 문서 처리 파이프라인에서 브랜드 가이드라인을 깨뜨릴 수 있는 무음 글꼴 교체를 방지하는 데 매우 유용합니다.

---

## Step 5: Common pitfalls and best‑practice tips

| Pitfall | How to avoid it |
|---------|-----------------|
| **Forgot to reference `Aspose.Words.Fonts`** | 파일 상단에 `using Aspose.Words.Fonts;` 를 추가하세요. 그렇지 않으면 컴파일러가 타입을 찾지 못합니다. |
| **Font folder path is wrong** | 경로를 다시 확인하고 하위 폴더가 있다면 `recursive: true` 로 설정하세요. `Path.GetFullPath` 로 디버깅하면 도움이 됩니다. |
| **Multiple warning callbacks** | Aspose.Words는 마지막에 할당된 `WarningCallback`만 사용합니다. 복잡한 로직이 필요하면 단일 핸들러에서 다른 로직을 위임하도록 유지하세요. |
| **Running on a server without UI** | 콘솔 출력은 괜찮지만, 웹 앱에서는 `Console.WriteLine` 대신 파일이나 모니터링 시스템에 로그를 남기는 것이 좋습니다. |
| **Large documents cause performance hit** | 여러 번 로드할 경우 동일한 `FontSettings` 인스턴스를 재사용하세요. 매번 새로 만들면 비용이 많이 듭니다. |

**Pro tip:** 나중에 분석하기 위해 경고를 *수집*해야 한다면, 핸들러 내부에서 `List<string>`에 저장하고 직접 출력하는 대신 해당 리스트를 사용하세요.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

문서 로드 후 `handler.Messages` 를 확인하면 수집된 경고를 볼 수 있습니다.

---

## Step 6: Extending the solution – what if I need to embed a fallback font?

때때로 누락된 글꼴을 출력 PDF에 *임베드*하여 다운스트림 뷰어가 정확한 모양을 표시하도록 하고 싶을 수 있습니다. 문서를 로드한 뒤 다음과 같이 강제로 임베드할 수 있습니다:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

이 스니펫은 동일한 **글꼴 설정 구성** 접근 방식을 로드 단계뿐 아니라 이후 단계에도 확장할 수 있음을 보여줍니다.

---

## Full runnable example

아래는 새 콘솔 앱 프로젝트에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 앞서 논의한 모든 요소가 포함되어 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**예상 출력** (누락된 글꼴이 있는 경우):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

대체가 발생하지 않으면 성공 메시지만 표시됩니다.

---

## Conclusion

우리는 **경고 콜백**을 만들어 Aspose.Words로 **Word 문서를 로드**하면서 **누락된 글꼴을 감지**하고, **글꼴 설정을 구성**해 라이브러리가 글꼴을 찾는 위치와 대체 글꼴을 제어하는 방법을 보여주었습니다. `FontSettings`와 `LoadOptions`를 연결함으로써 글꼴 관련 문제를 완전히 가시화할 수 있게 되었으며, 이제 더 이상 무음 레이아웃 오류에 고민할 필요가 없습니다.

다음 단계는? `FontWarningHandler`를 데이터베이스에 기록하는 로거로 교체하거나, **글꼴 대체 규칙**을 사용해 특정 누락 글꼴을 브랜드 승인 대체 글꼴에 매핑해 보세요. 컨테이너 환경에서 실행한다면 클라우드 스토리지에서 동적으로 글꼴을 로드하는 방법도 탐색해 볼 수 있습니다.

특정 엣지 케이스—예를 들어 OpenType 기능 처리나 암호화된 DOCX 파일 다루기 등에 대한 질문이 있으면 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!  

---

![경고 콜백 생성 다이어그램](https://example.com/images/create-warning-callback.png "경고 콜백 생성 다이어그램")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}