---
category: general
date: 2026-02-24
description: Aspose.Words를 사용하여 Word 문서에서 글꼴을 감지하는 방법. 콜백을 설정하고 전체 코드 예제로 Word 문서를
  로드하는 방법을 배워보세요.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: ko
og_description: 경고 콜백을 사용하여 Word 문서에서 폰트를 감지하는 방법. 이 가이드는 콜백을 설정하고 Aspose.Words로 Word
  문서를 로드하는 방법을 보여줍니다.
og_title: Word 문서에서 글꼴 감지 방법 – 단계별 C# 튜토리얼
tags:
- C#
- Aspose.Words
- Document Processing
title: Word 문서에서 글꼴을 감지하는 방법 – 완전한 C# 가이드
url: /ko/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 글꼴 감지 방법 – 완전한 C# 가이드

Word 파일을 로드할 때 누락된 **글꼴을 감지하는 방법**이 궁금했나요? 편집기에서는 문서가 정상으로 보이지만, 생성한 PDF에서 몇몇 서체가 뒤에서 교체되는 경우를 겪어보셨을지도 모릅니다. 이는 글꼴 대체의 전형적인 증상이며, 이를 조기에 포착하면 레이아웃 문제가 발생하는 것을 방지할 수 있습니다.

이 튜토리얼에서는 실용적인 솔루션을 단계별로 살펴보겠습니다: **Aspose.Words**를 사용해 `.docx`를 로드하고, 경고 콜백을 연결하며, 모든 글꼴 대체를 보고하는 **콜백 설정 방법**을 다룹니다. 최종적으로 **프로그램matically 글꼴을 감지하는 방법**을 알게 될 뿐만 아니라, **콜백을 올바르게 설정하는 방법**과 **워드 문서를 안전하게 로드하는 방법**도 이해하게 됩니다—모두 하나의 실행 가능한 C# 예제에서.

> **얻을 수 있는 것**
> * 복사‑붙여넣기 바로 사용할 수 있는 완전한 코드 샘플  
> * 각 라인에 대한 단계별 설명  
> * 여러 누락된 글꼴이나 사용자 정의 글꼴 폴더와 같은 엣지 케이스 처리 팁  
> * 모든 것이 정상 작동하는지 확인할 수 있는 예상 콘솔 출력  

---

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Core에서도 동작합니다)  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)  
- 의도적으로 설치되지 않은 글꼴을 참조하는 Word 파일 (예: `MissingFont.docx`)  
- Visual Studio, Rider 또는 원하는 편집기  

다른 라이브러리는 필요하지 않으며, 나머지는 모두 표준 .NET 런타임에 포함됩니다.

## Word 문서에서 글꼴을 감지하는 방법

### 단계 1: Load Options 생성 및 Warning Callback 연결

먼저 Aspose.Words에 파일을 로드하는 동안 발생하는 모든 문제에 대해 알림을 받겠다고 알려줍니다. 여기서 **콜백 설정 방법**이 등장합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**왜 중요한가:**  
`LoadOptions`는 로드 프로세스를 사용자 정의할 수 있는 관문입니다. `FontWarningCollector` 인스턴스를 `WarningCallback`에 할당하면, Aspose.Words는 누락된 글꼴을 대체 폰트로 교체할 때마다 우리의 `Warning` 메서드를 호출합니다. 이는 머신에 존재하지 않는 **글꼴을 감지하는 방법**의 핵심입니다.

### 단계 2: LoadOptions 인스턴스 준비

이제 `LoadOptions`를 인스턴스화하고 콜백을 연결합니다.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**팁:** Aspose가 대체 글꼴을 찾는 *위치*를 제어해야 한다면 여기서 `loadOptions.FontSettings`를 설정할 수 있습니다. 서버에 개인 글꼴 폴더가 있을 때 유용합니다.

### 단계 3: 워드 문서 로드

옵션이 준비되면 이제 **워드 문서를 로드**합니다. 이때 Aspose가 DOCX를 파싱하고, 누락된 글꼴이 있으면 콜백이 실행됩니다.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**내부에서 무슨 일이 일어나나요?**  
Aspose.Words는 DOCX의 XML 파트를 읽고 각 `<w:font>` 참조를 해석한 뒤 시스템 글꼴 컬렉션을 확인합니다. 참조를 만족시킬 수 없을 때마다 첫 번째 일치하는 대체 글꼴을 사용하고 `FontSubstitution` 경고를 발생시킵니다.

### 단계 4: 출력 확인

프로그램을 실행하고 콘솔을 확인하세요. 누락된 글꼴마다 다음과 같은 라인이 표시됩니다:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

문서에 누락된 글꼴이 없으면 콘솔에 아무 출력도 나타나지 않으며, 이는 **글꼴을 감지하는 방법**이 결과를 찾지 못했음을 의미합니다.

### 단계 5: 전체 작동 예제 (콘솔 앱)

아래는 새로운 콘솔 프로젝트에 바로 넣을 수 있는 독립형 `Program.cs`입니다. 여기에는 논의한 모든 요소와 디버깅 시 콘솔 창을 열어두는 작은 헬퍼가 포함되어 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**예상 콘솔 출력** (예시):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

`MissingFont.docx`를 설치된 글꼴만 사용하는 파일로 교체하면 “Press any key…” 라인만 표시됩니다—감지 로직이 의도대로 작동함을 확인할 수 있습니다.

## 일반적인 질문 및 엣지 케이스

### 모든 경고를 캡처해야 한다면, 글꼴 대체만이 아니라?

`if (info.Type == WarningType.FontSubstitution)` 조건을 제거하면 됩니다. `WarningInfo` 객체에는 다른 시나리오(예: `DocumentStructure`, `ImageLoading`)에 사용할 수 있는 `Type` 열거형이 포함되어 있습니다.

### 콘솔 대신 파일에 경고를 기록할 수 있나요?

물론 가능합니다. `Console.WriteLine`을 원하는 로깅 프레임워크 호출(`Serilog`, `NLog` 등)로 교체하면 됩니다. 콜백은 문서를 로드하는 동일한 스레드에서 실행되므로 로거가 스레드‑안전한지 확인하세요.

### 웹 애플리케이션에서는 어떻게 동작하나요?

ASP.NET Core에서는 일반적으로 싱글톤 `IWarningCallback` 구현을 주입하고 `LoadOptions`를 통해 전달합니다. 응답 스트림에 직접 쓰는 것을 피하고, 데이터베이스나 메모리 컬렉션에 로그를 남긴 뒤 API 엔드포인트를 통해 노출하도록 하세요.

### 시스템 폴더가 아닌 곳에 저장된 사용자 정의 글꼴은 어떻게 하나요?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

이제 Aspose.Words는 OS 글꼴로 대체하기 전에 `C:\MyCustomFonts`를 먼저 검색하므로, 표시되는 대체 경고 수가 줄어듭니다.

## 시각적 요약

![Aspose.Words에서 글꼴 경고 콜백 감지](/images/font-warning-callback.png "경고 콜백을 사용하여 글꼴을 감지하는 방법")

*스크린샷은 누락된 글꼴이 대체될 때 콘솔 출력이 어떻게 표시되는지 보여줍니다. alt 텍스트에는 SEO를 위한 주요 키워드가 포함되어 있습니다.*

## 결론

이제 Aspose.Words로 로드하는 모든 Word 파일에서 **글꼴을 감지하는 방법**에 대한 견고하고 프로덕션 준비된 패턴을 갖추게 되었습니다. **콜백 설정 방법**을 통해 누락되거나 대체된 서체에 대한 실시간 인사이트를 얻을 수 있으며, 코드를 깔끔하고 유지 보수 가능하게 **워드 문서를 로드하는 방법**을 올바르게 배웠습니다.

다음 단계는? 콜백을 확장해 경고를 리스트에 수집하고 UI나 자동 보고서에 표시해 보세요. 또한 `FontSettings.SubstitutionSettings`를 탐색해 *어떤* 글꼴이 대체 폰트로 선택되는지 제어할 수도 있습니다.

자유롭게 실험해 보세요—문서를 교체하거나, 더 많은 누락된 글꼴을 추가하거나, 로직을 더 큰 문서 처리 파이프라인에 통합해 보세요. 문제가 발생하면 아래에 댓글을 남기거나 GitHub에서 저에게 연락하세요.

코딩을 즐기세요, 그리고 여러분의 문서가 언제나 기대한 글꼴로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}