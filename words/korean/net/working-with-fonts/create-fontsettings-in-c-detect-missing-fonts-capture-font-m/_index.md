---
category: general
date: 2026-03-01
description: C#에서 FontSettings를 생성하여 누락된 글꼴을 감지하고, 글꼴 메시지를 캡처하며, Aspose.Words로 누락된
  글꼴을 처리합니다. 개발자를 위한 단계별 가이드.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: ko
og_description: Aspose.Words를 사용하여 C#에서 FontSettings를 생성하고, 누락된 글꼴을 감지하고, 글꼴 메시지를
  캡처하며, 누락된 글꼴을 처리하는 방법을 알려드립니다. 코드와 함께하는 완전한 튜토리얼.
og_title: C#에서 FontSettings 만들기 – 누락된 폰트 감지 및 폰트 메시지 캡처
tags:
- Aspose.Words
- C#
- Font Management
title: C#에서 FontSettings 만들기 – 누락된 폰트 감지 및 폰트 메시지 캡처
url: /ko/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 FontSettings 만들기 – 누락된 폰트 감지 및 폰트 메시지 캡처

Ever needed to **create FontSettings** in a .NET project but weren’t sure how to spot fonts that aren’t installed on the target machine? You’re not alone. In many real‑world apps—think automated report generators or document converters—missing fonts can silently break layout, and you won’t know until the PDF looks wonky.  

What if you could **detect missing fonts**, **capture font messages**, and **handle missing fonts** before they ruin your output? The good news is that Aspose.Words makes this a piece of cake. In this tutorial we’ll walk through the entire process, from setting up the `FontSettings` object to wiring a warning callback that tells you exactly which glyphs were substituted.

> **TL;DR:** 끝까지 진행하면 모든 폰트 대체를 기록하는 실행 준비가 된 C# 콘솔 앱을 얻게 되며, 교체 폰트를 삽입할지 사용자에게 알릴지를 결정할 수 있습니다.

---

## 전제 조건

- .NET 6 SDK (또는 최신 .NET 버전)  
- Visual Studio 2022 또는 C# 확장이 포함된 VS Code  
- Aspose.Words for .NET 라이선스 (무료 체험판으로도 이 데모 가능)  
- 설치되지 않은 폰트를 참조하는 샘플 DOCX (예: Linux 환경의 *Comic Sans MS*)

`Aspose.Words` 외에 특별한 NuGet 패키지는 필요하지 않습니다.

---

## Step 1 – Aspose.Words 설치 및 프로젝트 설정

우선, 새 콘솔 프로젝트를 만들고 Aspose.Words 라이브러리를 추가합니다.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** 이미 솔루션이 있다면 NuGet 패키지 관리자 UI를 통해 패키지를 추가하세요—버전 관리를 더 쉽게 해줍니다.

---

## Step 2 – FontSettings 만들기 (주요 키워드가 여기 나타납니다)

**create FontSettings** 단계는 모든 폰트 관련 워크플로우의 핵심입니다. `FontSettings`는 Aspose.Words에 폰트를 찾을 위치, 시스템 폴더 사용 여부, 누락 시 대체 방법을 알려줍니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

왜 중요한가요? 올바르게 구성된 `FontSettings`가 없으면 엔진은 누락된 글리프를 기본 시스템 폰트로 조용히 대체하고, 경고를 전혀 보지 못합니다.

---

## Step 3 – LoadOptions에 FontSettings 연결

`LoadOptions`를 사용하면 `FontSettings`를 문서 로더에 전달할 수 있습니다. 이는 엔진이 `Document` 생성 단계에서 **detect missing fonts**를 할 수 있게 해 주는 다리 역할을 합니다.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

이제 `loadOptions`로 DOCX를 로드할 때마다 Aspose.Words는 앞서 설정한 `FontSettings`를 참조합니다.

---

## Step 4 – **Capture Font Messages**를 위한 경고 콜백 연결

Aspose.Words는 다양한 상황에 대해 경고를 발생시키며, 그 중 폰트 대체가 흔한 경우입니다. `IWarningCallback` 구현을 제공하면 실시간으로 **capture font messages**를 할 수 있습니다.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### 경고 처리기 클래스

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description` 필드에는 *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*와 같은 사람이 읽을 수 있는 메시지가 들어 있습니다. 이는 **handle missing fonts**를 우아하게 처리하기 위해 필요한 정확한 출력입니다.

---

## Step 5 – 문서를 로드하고 콜백이 작업을 수행하도록 하기

모든 연결이 완료되면 문서 로드는 간단합니다. 소스 파일이 시스템에 없는 폰트를 참조하면 경고 처리기가 작동합니다.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

프로그램을 실행하면 다음과 같은 콘솔 출력이 표시됩니다:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

이 출력은 워크플로우의 **capture font messages** 부분입니다. 핸들러를 확장하여 파일에 로그를 남기거나, 텔레메트리를 전송하거나, 중요한 폰트가 누락된 경우 변환을 중단하도록 할 수 있습니다.

---

## Step 6 – 전체 작업 예제 (모든 조각 결합)

아래는 완전한 복사‑붙여넣기 가능한 프로그램입니다. `Program.cs`에 붙여넣고 파일 경로를 조정한 뒤 `dotnet run`을 실행하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### 예상 출력

*Comic Sans MS*가 없는 머신에서 프로그램을 실행하면 다음과 같은 출력이 표시됩니다:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

또한 대체된 폰트를 사용한 `Result.pdf`가 생성되어 변환이 절대 중단되지 않도록 합니다.

---

## 일반 질문 및 엣지 케이스

| Question | Answer |
|----------|--------|
| **변환이 대체 대신 실패하도록 하고 싶다면 어떻게 해야 하나요?** | `FontSubstitutionWarningHandler` 내부에서 `info.Description`에 중요한 폰트 이름이 포함되어 있으면 예외를 발생시킵니다. |
| **대체 폰트를 자동으로 삽입할 수 있나요?** | 예. 누락된 폰트를 감지한 후, 알려진 경로에서 대체 `FontInfo`를 로드하고 `fontSettings.SetFontsFolder`를 통해 `fontSettings`에 추가할 수 있습니다. |
| **Linux/macOS에서도 작동하나요?** | 물론입니다. `FontSettings`는 크로스‑플랫폼이며, 대체 폴더에 적절한 `.ttf` 또는 `.otf` 파일이 포함되어 있는지 확인하면 됩니다. |
| **경고 콜백이 스레드‑안전한가요?** | 콜백은 문서를 로드하는 동일한 스레드에서 실행되므로 콘솔 로깅에 추가 동기화가 필요하지 않습니다. 다중 스레드 상황에서는 공유 자원을 보호하세요. |
| **경고를 파일에 로그하려면 어떻게 해야 하나요?** | `Console.WriteLine`을 `File.AppendAllText("font_warnings.log", ...)` 로 교체하거나 원하는 로깅 프레임워크(Serilog, NLog)를 사용하세요. |

---

## 프로덕션 수준 폰트 처리를 위한 팁

1. **Cache Font Lookups** – 여러 문서를 로드할 때 동일한 `FontSettings` 인스턴스를 재사용하면 파일 시스템 스캔을 반복하지 않아도 됩니다.  
2. **Whitelist Critical Fonts** – 브랜드에 특정 폰트가 필요하면 초기 단계에서 존재 여부를 확인하고 명확한 오류 메시지와 함께 중단합니다.  
3. **Use `SetFontFolder` Recursively** – `recursive: true`로 설정하면 하위 폴더까지 스캔되므로 전체 폰트 컬렉션을 제공할 때 유용합니다.  
4. **Combine with `FontSubstitutionSettings`** – 대체 규칙을 세밀하게 조정할 수 있습니다(예: 동일한 패밀리 이름을 가진 폰트를 우선 선택).  

---

## 결론

우리는 이제 **created FontSettings**를 수행하고, `LoadOptions`를 구성해 **detect missing fonts**를 설정했으며, **captures font messages** 콜백을 연결하고, **handle missing fonts**를 깔끔하고 프로덕션 수준으로 구현하는 방법을 보여주었습니다. 전체 흐름은 C# 몇십 줄 안에 들어가지만, 처리하는 모든 DOCX의 폰트 상황을 완전히 파악할 수 있게 해 줍니다.

다음과 같은 항목을 탐색해 볼 수 있습니다:

- **Embedding fallback fonts**를 출력 PDF에 직접 삽입 (`PdfSaveOptions.FontEmbeddingMode`).  
- 기업 브랜드 규칙에 따라 **Programmatically substituting fonts**.  
- 인증되지 않은 폰트를 사용하는 문서를 자동으로 표시하도록 **Integrating with a CI pipeline**.

한 번 실행해 보고, 필요에 맞게 경고 처리기를 조정하여 문서 파이프라인을 안심하고 운영하세요—보이지 않는 폰트 교체로 인한 신비한 레이아웃 오류가 더 이상 발생하지 않습니다.

코딩 즐겁게! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}