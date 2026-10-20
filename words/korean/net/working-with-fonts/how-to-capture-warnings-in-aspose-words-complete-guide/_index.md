---
category: general
date: 2026-03-13
description: Aspose.Words로 문서를 로드할 때 경고를 캡처하는 방법과 누락된 글꼴을 처리하고 사용자 지정 글꼴 설정을 적용하는
  팁. 전체 C# 솔루션을 배워보세요.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: ko
og_description: Aspose.Words로 Word 파일을 로드할 때 경고를 포착하는 방법, 그리고 누락된 글꼴을 처리하고 사용자 지정
  글꼴 설정을 적용하는 실용적인 방법.
og_title: Aspose.Words에서 경고 캡처하는 방법 – 완전 가이드
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words에서 경고를 캡처하는 방법 – 완전 가이드
url: /ko/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 경고 캡처하는 방법 – 완전 가이드

Aspose.Words가 문서를 로드할 때 나타나는 **경고를 캡처하는 방법**이 궁금하셨나요? 실제 프로젝트에서는 글꼴 대체 알림, 사용 중단된 기능 메모, 심지어 보안 관련 메시지도 자주 보게 됩니다. 이를 무시하는 것은 앞유리가 깨진 채로 운전하는 것과 같습니다—목적지는 도달할 수 있어도 언제 문제가 발생할지 전혀 알 수 없습니다.

좋은 소식은 Aspose.Words가 이러한 메시지를 가로챌 수 있는 깔끔한 콜백 기반 방식을 제공한다는 점입니다. 이번 튜토리얼에서는 **전체 C# 예제**를 통해 경고를 캡처할 뿐만 아니라 **누락된 글꼴을 처리**하고 **사용자 지정 글꼴 설정을 적용**하는 방법을 보여드립니다. 이를 통해 문서가 기대한 대로 정확히 렌더링됩니다.

---

## What You’ll Learn

- `LoadOptions`에 사용자 지정 `FontSettings` 객체를 연결하는 방법을 설정합니다.  
- `FontSubstitution` 이벤트를 필터링하는 경고 콜백을 등록합니다.  
- 경고 세부 정보를 콘솔(또는 원하는 로거)으로 출력합니다.  
- 다양한 플랫폼에서 누락된 글꼴을 우아하게 처리하도록 솔루션을 확장합니다.  

이 가이드를 끝까지 따라오면 .NET 프로젝트에 바로 삽입할 수 있는 실행 가능한 스니펫과 흔히 발생하는 함정을 피하는 실용적인 팁을 얻을 수 있습니다.

---

## Prerequisites

| 요구 사항 | 중요 이유 |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 이상) | 사용되는 API(`LoadOptions`, `IWarningCallback`)가 여기 포함됩니다. |
| **.NET 6+** (또는 .NET Framework 4.7.2 이상) | 최신 언어 기능을 활용해 코드를 간결하게 유지합니다. |
| **샘플 DOCX** (`input.docx` 파일) – 알려진 폴더에 위치 | 로드하면서 경고를 발생시킬 대상이 필요합니다. |
| **콘솔 또는 로깅 프레임워크** (선택) | 캡처된 경고를 실제로 확인하기 위해 필요합니다. |

Aspose.Words 자체 외에 추가 NuGet 패키지는 필요하지 않습니다.

---

## Step 1: Set Up Custom Font Settings  

문서를 로드하기 전에 Aspose.Words에 글꼴을 찾을 위치를 알려줄 수 있습니다. 이것이 **사용자 지정 글꼴 설정**을 적용하는 단계입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**왜 중요한가:**  
DOCX 파일이 머신에 설치되지 않은 글꼴을 참조하면 Aspose.Words는 기본적으로 조용히 대체 글꼴을 사용합니다 *단*, 필요한 글꼴이 들어 있는 폴더를 지정해 두면 상황이 달라집니다. 사용자 지정 폴더를 설정하면 “글꼴 대체” 경고가 발생할 가능성을 처음부터 크게 줄일 수 있습니다.

> **Pro tip:** Linux 환경에서는 `fonts-dejavu-core` 패키지나 문서에서 사용하는 TrueType 컬렉션을 추가로 설치해야 할 수 있습니다.

---

## Step 2: Register a Warning Callback  

Aspose.Words는 `IWarningCallback` 인터페이스를 구현합니다. 여기서는 누락되었거나 대체된 글꼴에 대한 경고만 출력하도록 작은 핸들러를 만들겠습니다.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**왜 중요한가:**  
이제 **누락된 글꼴을 처리**하는 상황이 눈에 보이게 됩니다. 어떤 글꼴이 교체되었는지 추측하는 대신 “Font 'Calibri' was substituted with 'Arial'”와 같은 명확한 설명을 얻을 수 있어, PDF 생성이나 인쇄 보고서 레이아웃 문제를 디버깅할 때 큰 도움이 됩니다.

---

## Step 3: Load the Document with the Configured Options  

이제 준비한 `LoadOptions`를 사용해 문서를 메모리로 불러옵니다.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

소스 파일이 `C:\MyFonts`에 없는 글꼴을 사용하고 있다면 다음과 유사한 출력이 나타납니다:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

이 한 줄이 바로 **경고를 캡처하는 방법**의 결과입니다.

---

## Step 4: Full Working Example (Copy‑Paste Ready)

아래는 전체 프로그램 코드이며 바로 컴파일할 수 있습니다. 새 콘솔 프로젝트에 붙여넣고 실행하세요—단, 경로는 실제 머신에 맞게 수정해야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**예상 출력:**  

- 모든 글꼴이 존재하는 경우:  
  `Document processed. Check console for any warning messages.`  

- 글꼴이 누락된 경우:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Step 5: Common Variations & Edge Cases  

| 상황 | 조정 방법 |
|-----------|----------------|
| **Multiple font folders** | 각 추가 위치마다 `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` 를 호출합니다. |
| **Suppress all warnings** | `Warn` 메서드를 구현하되 본문을 비워두거나 `loadOptions.WarningCallback = null;` 로 설정합니다. |
| **Capture other warning types** | `info.WarningType`을 `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` 등과 비교합니다. |
| **Running on Linux/macOS** | 글꼴 폴더에 Linux 호환 `.ttf`/`.otf` 파일이 포함되어 있는지 확인하고, 필요 시 `libfontconfig` 를 설치합니다. |
| **Large documents** | 메모리 압력을 줄이기 위해 (`LoadOptions.LoadFormat = LoadFormat.Docx;`) 문서를 스트리밍 로드하는 방식을 고려합니다. |

이러한 시나리오를 미리 대비하면 개발 머신에서 CI 파이프라인이나 클라우드 VM으로 이동할 때 발생할 수 있는 놀라움을 방지할 수 있습니다.

---

## Step 6: Visual Confirmation (Optional)

시각적인 확인이 필요하다면 캡처된 경고를 작은 HTML 보고서로 내보낼 수 있습니다. 아래 스니펫은 메시지를 `warnings.html` 파일에 기록합니다:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

문서를 로드한 뒤 `handler.WriteReport(@"C:\Docs\warnings.html");` 를 호출하고 브라우저에서 열어보세요. 아래 이미지는 보고서 예시입니다:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt text:* **how to capture warnings** – 콘솔 출력과 HTML 보고서의 스크린샷.

---

## Conclusion  

우리는 **Aspose.Words에서 경고를 캡처하는 방법**을 다루었고, **누락된 글꼴을 처리하는 신뢰할 수 있는 방법**을 보여주었으며, **결정적인 렌더링을 위한 사용자 지정 글꼴 설정** 적용법도 소개했습니다. 전체 예제는 어떤 .NET 솔루션에도 바로 삽입할 수 있으며, 모듈형 `FontWarningHandler`는 로깅이나 텔레메트리 전략에 맞게 확장할 수 있습니다.

다음 단계는 `Console.WriteLine` 호출을 Serilog 같은 구조화 로거로 교체하거나, Application Insights에 경고를 푸시해 실시간 모니터링을 구현해 보는 것입니다. 또한 로드 후 문서 내용을 검사해야 한다면 `DocumentVisitor` 패턴을 탐색해 보세요.

다른 경고 유형이나 글꼴 임베딩 전략에 대한 질문이 있으면 아래 댓글에 남겨 주세요—행복한 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}