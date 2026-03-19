---
category: general
date: 2026-03-19
description: Aspose.Words에서 경고를 캡처하는 방법, 기본 글꼴 설정을 지정하는 방법, 그리고 Word 문서를 로드할 때 누락된
  글꼴을 감지하는 방법을 배웁니다.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: ko
og_description: Aspose.Words에서 경고를 캡처하고 기본 글꼴 설정을 지정하며 Word 문서를 로드할 때 누락된 글꼴을 감지하는
  방법.
og_title: 경고 캡처 방법 – 기본 글꼴 설정
tags:
- Aspose.Words
- C#
- Document Processing
title: 경고 캡처 방법 – 기본 글꼴 설정
url: /ko/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 경고 캡처 방법 – 기본 글꼴 설정 지정

**경고 캡처 방법**은 Aspose.Words를 사용할 때 흔히 필요한 작업이며, 특히 문서가 대상 머신에 없을 수 있는 특정 글꼴에 의존하는 경우에 중요합니다. DOCX 파일을 열었을 때 레이아웃이 어색하게 보인 적이 있나요? 그 원인은 종종 누락된 글꼴에 대한 경고에 숨겨져 있습니다.  

이 가이드에서는 **경고를 캡처하는 방법**을 **워드 문서 로드**하면서, **기본 글꼴 설정 지정**을 구성하고, 마지막으로 **누락된 글꼴을 감지**하는 전체 흐름을 단계별로 살펴봅니다. 불필요한 내용 없이 완전한 실행 예제와 각 라인에 대한 설명을 제공합니다.

> **팁:** 경고를 일찍 캡처하면 나중에 발생할 수 있는 신비한 레이아웃 오류를 디버깅하는 시간을 절약할 수 있습니다.

---

## 준비 사항

- **Aspose.Words for .NET** (2026년 현재 최신 버전).  
- .NET 개발 환경 (Visual Studio, Rider, 또는 VS Code).  
- 설치되지 않은 글꼴을 참조하는 샘플 DOCX (예: Linux 환경에서 *Comic Sans MS*).

이것만 있으면 됩니다. Aspose.Words 외에 추가 NuGet 패키지는 필요하지 않습니다.

---

## 1단계 – 경고를 캡처해야 하는 이유 이해하기

Aspose.Words가 문서를 파싱할 때 호스트에 없는 글꼴을 만나면 기본적으로 라이브러리는 조용히 대체 글꼴을 사용합니다. 이 과정에서 줄 바꿈, 간격이 바뀌거나 텍스트가 사라질 수 있습니다.  

**WarningCallback**과 **FontSettings** 객체를 함께 사용하면 다음 두 가지를 얻을 수 있습니다:

1. **가시성** – 모든 대체에 대해 `WarningInfo` 항목을 받습니다.  
2. **제어** – 기본 글꼴을 미리 지정해 시각적 놀라움을 최소화합니다.

마치 엔진 내부에서 부품이 교체될 때마다 외치는 “감시자”를 설치하는 것과 같습니다.

---

## 2단계 – 기본 글꼴 설정 지정

두 번째 보조 키워드인 **set default font settings**가 바로 여기서 등장합니다. `FontSettings` 인스턴스를 생성하고, 필요에 따라 대체 글꼴이 들어 있는 폴더를 지정합니다.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **왜?**  
> 대체 글꼴을 지정하지 않으면 Aspose.Words는 스타일에 맞는 첫 번째 시스템 글꼴을 선택하는데, 이는 크게 다를 수 있습니다. 알려진 기본 글꼴을 설정하면 머신 간에 일관된 렌더링을 보장합니다.

---

## 3단계 – 경고 콜백 준비하기

이제 **how to capture warnings**를 구현하기 위해 `WarningInfoCollection`을 로드 옵션에 연결합니다. 이 컬렉션은 로드 과정에서 발생하는 모든 경고를 저장합니다.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection`은 `IWarningCallback`을 구현하므로 Aspose.Words가 자동으로 각 경고를 `warningInfos`에 푸시합니다. 별도의 폴링이 필요 없습니다.

---

## 4단계 – 구성된 옵션으로 워드 문서 로드

두 번째 보조 키워드인 **load word document**가 빛을 발합니다. `FontSettings`와 `WarningCallback`을 `LoadOptions` 인스턴스에 전달합니다.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

문서가 설치되지 않은 글꼴을 참조하면 경고 콜백이 `WarningType.FontSubstitution` 항목을 캡처합니다.

---

## 5단계 – 수집된 경고에서 누락된 글꼴 감지

마지막으로 세 번째 보조 키워드인 **detect missing fonts**를 구현합니다. 수집된 경고를 순회하면서 누락된 글꼴을 찾아냅니다.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

일반적인 출력 예시:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

이 줄은 어떤 글꼴이 누락되었고 어떤 대체 글꼴이 사용되었는지를 정확히 알려줍니다. 이를 로그에 남기거나 사용자에게 표시하거나, 맞춤형 글꼴 설치 루틴을 트리거하는 데 활용할 수 있습니다.

---

## 전체 실행 예제

아래 코드는 콘솔 애플리케이션에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. **경고 캡처**, **기본 글꼴 설정 지정**, **워드 문서 로드**, **누락된 글꼴 감지**를 한 흐름에서 보여줍니다.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**예상 결과:** 지정된 DOCX가 설치되지 않은 글꼴을 참조하면 콘솔에 각 대체에 대한 경고가 출력됩니다. 모든 글꼴이 존재하면 루프는 아무 출력도 생성하지 않습니다.

---

## 흔히 발생하는 실수와 예외 상황

| 상황 | 발생 원인 | 해결 방법 |
|-----------|----------------|------------------|
| **경고가 나타나지 않음**에도 레이아웃이 잘못 보이는 경우 | 문서가 *임베디드* 글꼴을 사용하고 있을 수 있으며, Aspose.Words는 대체 없이 렌더링합니다. | `Document.HasEmbeddedFonts`를 확인하고, 다른 머신에서 필요하다면 임베디드 글꼴을 추출하는 것을 고려하십시오. |
| **다중 경고** for the |  |  |

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}