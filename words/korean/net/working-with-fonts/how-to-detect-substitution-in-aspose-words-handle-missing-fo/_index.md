---
category: general
date: 2026-04-24
description: C#를 사용하여 Aspose.Words에서 누락된 글꼴의 대체를 감지하는 방법. 이 가이드는 FontSettings 경고를
  통해 누락된 글꼴을 안정적으로 처리하는 방법을 보여줍니다.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: ko
og_description: C#를 사용하여 Aspose.Words에서 누락된 글꼴의 대체를 감지하는 방법. FontSettings 경고를 활용해
  누락된 글꼴을 처리하는 방법을 배워보세요.
og_title: Aspose.Words에서 대체 감지 방법 – 완전 가이드
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Aspose.Words에서 대체를 감지하는 방법 – 누락된 글꼴 처리
url: /ko/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 대체 감지 방법 – 누락된 글꼴 처리

서버에 설치되지 않은 글꼴을 문서가 사용하려 할 때 **대체 감지 방법**을 궁금해 본 적이 있나요? 자동 파이프라인에서 PDF나 Word 파일을 생성할 때 흔히 겪는 문제입니다. 좋은 소식은 Aspose.Words가 이러한 상황을 정확히 포착할 수 있는 내장 훅을 제공하며, **누락된 글꼴 처리**를 우아하게 **처리**할 수도 있다는 점입니다.

이 튜토리얼에서는 `FontSettings.Warning` 이벤트를 통해 **대체 감지 방법**을 보여주는 실제 예제를 단계별로 살펴보고, **누락된 글꼴 처리** 방법을 설명합니다. 마지막까지 읽으면 바로 실행 가능한 코드 조각과 각 라인의 의미에 대한 명확한 이해, 그리고 일반적인 함정을 피하기 위한 몇 가지 팁을 얻을 수 있습니다.

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework에서도 작동합니다)
- Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`) – 버전 23.11 이상
- 설치되지 않은 글꼴을 참조하는 샘플 문서 (예: `MissingFont.docx`)
- 선호하는 C# IDE인 Visual Studio, VS Code 등  

추가적인 구성은 NuGet 패키지를 추가하는 것 외에 필요하지 않습니다.

---

## FontSettings를 사용한 대체 감지 방법

`FontSettings.Warning` 이벤트가 **대체 감지 방법**의 핵심입니다. Aspose.Words가 요청된 글꼴을 찾지 못하면 `WarningType.FontSubstitution` 경고를 발생시킵니다. 이 이벤트에 구독하면 원본 글꼴 이름과 대체로 사용된 글꼴을 포함한 실시간 알림을 받을 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**왜 작동하나요:**  
- `LoadOptions.FontSettings`는 방금 만든 `FontSettings` 객체를 Aspose.Words가 사용하도록 지정합니다.  
- `Warning`에 구독하면 누락된 글꼴뿐만 아니라 *모든* 글꼴 관련 문제를 한 곳에서 모니터링할 수 있습니다.  
- `WarningType.FontSubstitution` 필터는 관심 있는 정확한 상황에만 반응하도록 보장합니다 – 즉 **대체 감지 방법**의 핵심입니다.

### 예상 출력

위 코드를 존재하지 않는 글꼴을 참조하는 문서와 함께 실행하면 다음과 같은 내용이 출력됩니다:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

문서가 설치된 글꼴만 사용한다면 콘솔에 아무 출력도 없으며, 이는 **대체 감지 방법**이 오탐 없이 성공했음을 명확히 나타냅니다.

---

## 누락된 글꼴을 우아하게 처리하기

대체를 감지하는 것만으로는 절반에 불과합니다; 최종 출력이 의도대로 보이도록 **누락된 글꼴 처리** 전략도 필요합니다. 아래는 조합해서 사용할 수 있는 세 가지 실용적인 접근법입니다.

### 1. 대체 글꼴 폴더 제공

Aspose.Words는 추가 디렉터리에서 글꼴을 검색할 수 있습니다. 가장 일반적인 글꼴이 들어 있는 폴더를 지정하면 대체가 발생할 가능성을 완전히 줄일 수 있습니다.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**왜:** 원본 글꼴이 없을 경우, Aspose.Words는 이제 알려진 대체 글꼴 집합을 가지고 있어 시각적 결과가 더 예측 가능해집니다.

### 2. 프로그래밍 방식으로 누락된 글꼴 교체

전체 제어가 필요하다면, 감지 후 누락된 글꼴을 특정 글꼴로 교체할 수 있습니다.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**왜:** 엔진에 정확히 어떤 글꼴을 사용할지 알려주어 기업 브랜드나 접근성 표준을 적용할 수 있습니다.

### 3. 로그 기록 및 중단 (대체가 허용되지 않을 때)

때때로 누락된 글꼴은 문서가 사용 사례에 부적합함을 의미합니다(예: 법적 양식). 이런 경우 대체가 발생하면 즉시 예외를 발생시켜 중단할 수 있습니다.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**왜:** 즉시 실패하면 테이블 정렬 오류나 서명 손상 등 하위 오류를 방지할 수 있습니다.

---

## 전체 작업 예제 – 모든 단계 결합

아래는 **대체 감지 방법**과 **누락된 글꼴 처리** 여러 방법을 보여주는 복사‑붙여넣기 가능한 단일 프로그램입니다. 필요 없는 섹션은 주석 처리해도 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**예상 결과:**  
- `MissingFont.docx`가 머신에 없는 글꼴을 참조하면 콘솔에 대체 경고가 출력됩니다.  
- 저장된 `Processed.docx`는 구성한 대체 글꼴(또는 라이브러리 기본값)을 사용합니다.  
- 대체 시 중단하도록 명시적으로 설정하지 않는 한 처리되지 않은 예외는 발생하지 않습니다.

---

## 일반 질문 및 엣지 케이스

| 질문 | 답변 |
|----------|--------|
| *문서에 누락된 글꼴이 많이 포함된 경우는 어떻게 되나요?* | 경고 이벤트가 **각** 대체마다 발생하므로 여러 줄이 출력됩니다. 이를 목록으로 모아 요약 보고서를 만들 수 있습니다. |
| *PDF 변환에도 적용되나요?* | 물론입니다. `doc.Save("out.pdf")`를 호출할 때도 동일한 `FontSettings`가 적용됩니다. 대체 경고가 여전히 발생하므로 PDF의 시각적 정확성을 확인할 수 있습니다. |
| *문서를 이미 로드한 후에 대체를 감지할 수 있나요?* | 직접적으로는 불가능합니다. 경고는 로드 또는 저장 **중에** 발생합니다. 로드 후 분석이 필요하면 로드 단계에서 경고를 컬렉션에 저장하면 됩니다. |
| *DOCX에 포함된 사용자 정의 글꼴은 어떻게 되나요?* | 내장된 글꼴은 존재하는 것으로 간주되므로 대체가 발생하지 않습니다. 내장 글꼴이 손상된 경우에도 Aspose.Words는 경고를 발생시키며, 동일한 방법으로 잡을 수 있습니다. |
| *성능에 영향을 미치나요?* | 거의 없습니다. 경고 확인은 가벼우며 실제 비용은 문서를 로드하는 데 있습니다. 글꼴 폴더를 추가하면 검색 시간이 약간 늘어날 수 있지만 첫 로드 시에만 영향을 줍니다. |

---

## 전문가 팁 및 피해야 할 함정

- **전문가 팁:** 글꼴이 많은 폴더를 지정할 때는 항상 `recursive: true`를 설정하세요; 그렇지 않으면 하위 폴더가 무시됩니다.  
- **주의:** Linux에서는 대소문자를 구분합니다. Windows에서는 글꼴 이름이 대소문자를 구분하지 않지만 Linux에서는 구분하므로 정확한 이름을 사용하거나 두 변형을 모두 추가하세요.  
- **기억하세요:** 컨테이너 환경에서 실행 중이라면 글꼴 폴더가 이미지에 포함되었거나 런타임에 마운트되어 있는지 확인하세요.  
- **팁:** 최종 사용자에게 요약을 제공하거나 모니터링 시스템에 로그를 남겨야 할 경우 경고를 `List<string>`에 저장하세요.

---

## 결론

우리는 Aspose.Words에서 누락된 글꼴의 **대체 감지 방법**을 다루고, **누락된 글꼴 처리**를 위한 여러 방법을 소개했으며, .NET 프로젝트에 바로 넣어 사용할 수 있는 완전한 실행 예제를 제공했습니다. `FontSettings.Warning` 이벤트를 활용하면 글꼴 문제를 실시간으로 파악할 수 있고, 대체 폴더나 명시적인 대체 규칙을 사용하면 출력이 기대한 대로 유지됩니다.

다음 단계가 준비되셨나요? 솔루션을 확장하여 생성된 PDF에 대체 글꼴을 자동으로 삽입하거나, 대규모 문서 파이프라인을 위해 경고 핸들러를 중앙 로그 서비스에 연결해 보세요. 오늘 논의한 패턴—이벤트 기반 감지, 우아한 대체, 명시적 오류 처리—은 다른 Aspose API에도 적용되므로 이제 전반적인 글꼴 관련 문제를 해결할 준비가 되었습니다.

글꼴 처리, PDF 변환, Aspose.Words 팁에 대해 더 궁금한 점이 있나요? 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}