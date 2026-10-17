---
category: general
date: 2026-04-21
description: Aspose.Words를 C#에서 사용하여 글꼴을 감지하고, 경고를 캡처하며, 콜백을 구성하고, 경고를 열거하는 방법을 배웁니다.
  신뢰할 수 있는 글꼴 처리를 위한 단계별 가이드.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: ko
og_description: Aspose.Words에서 글꼴을 감지하는 방법은? 이 튜토리얼에서는 경고를 캡처하고, 콜백을 구성하며, C#에서 경고를
  열거하는 방법을 보여줍니다.
og_title: Aspose.Words에서 글꼴 감지 방법 – 완전 가이드
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose.Words에서 글꼴을 감지하는 방법 – 완전 가이드
url: /ko/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 폰트 감지하는 방법 – 완전 가이드

Word 문서를 로드할 때 누락된 **폰트를 감지하는 방법**이 궁금하셨나요? 특히 레거시 파일이나 크로스‑플랫폼 배포를 다룰 때 이런 상황이 생각보다 자주 발생합니다. 이 튜토리얼에서는 **경고를 캡처하고**, **콜백을 구성하며**, **경고를 열거**하는 완전하고 실행 가능한 예제를 단계별로 살펴보겠습니다. 이를 통해 어떤 폰트가 대체되었는지 항상 파악할 수 있습니다.

우리는 Aspose.Words for .NET (작성 시점 v24.9)과 순수 C#을 사용할 것입니다. 외부 서비스나 마법 같은 것은 없습니다—API와 몇 줄의 코드만 있으면 됩니다. 튜토리얼을 마치면 모든 폰트 대체를 찾아내고, 로그에 기록하며, 중요한 폰트가 누락된 경우 로드를 중단할지도 결정할 수 있게 됩니다.  

### 필요 사항
- **Aspose.Words for .NET** (NuGet 통해 설치: `Install-Package Aspose.Words`)
- .NET 6.0 이상 (.NET Framework에서도 동작)
- 머신에 존재하지 않는 폰트를 참조하는 샘플 DOCX (예: “MyCustomFont.ttf”)
- Visual Studio, Rider 또는 선호하는 C# 편집기

> **프로 팁:** 누락된 폰트가 포함된 문서가 없으면 시스템에서 폰트 파일 이름을 바꾸거나 DOCX XML을 편집해 존재하지 않는 폰트 패밀리를 참조하도록 하면 됩니다.

---

## Aspose.Words로 폰트 감지하기

핵심 아이디어는 Aspose.Words의 경고 시스템에 연결하는 것입니다. 라이브러리가 요청된 폰트를 찾지 못하면 `WarningType.FontSubstitution` 경고를 발생시킵니다. 사용자 정의 `IWarningCallback` 구현을 제공하면 로드 과정에서 **대체된 폰트를 감지**할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **왜 작동하나요:** Aspose.Words는 모든 비‑중요 이슈에 대해 `Warning` 메서드를 호출합니다. `WarningInfo` 객체를 저장하면 유형, 메시지, 컨텍스트에 완전히 접근할 수 있어 **대체된 폰트를 감지**하는 데 필요한 정보를 모두 얻을 수 있습니다.

---

## 문서 로드 시 경고 캡처하기

이제 컬렉터가 준비됐으니 `LoadOptions`에 이를 사용하도록 알려야 합니다. 이것이 **경고를 캡처하는** 퍼즐의 핵심 단계입니다.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **예외 상황:** 스트림(`new Document(stream, loadOptions)`)에서 문서를 로드할 경우에도 동일한 콜백이 작동합니다—파일 경로 대신 스트림만 전달하면 됩니다.

이 시점에서 문서는 완전히 로드되었으며, 모든 폰트 대체 경고는 `warningCollector.Warnings` 안에 안전하게 저장됩니다.

---

## 경고 열거 및 폰트 대체 보고하기

마지막으로 수집된 경고를 살펴보고 **폰트 대체와 관련된 경고만** 열거합니다. 이 단계는 원시 데이터를 읽기 쉬운 보고서로 변환합니다.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**예상 출력** (예시):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

문서에 누락된 폰트가 없으면 루프는 아무 출력도 생성하지 않으며, 걱정할 필요가 없습니다.

---

## 전체 작업 예제 (한 파일에 모든 단계 포함)

아래는 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. **폰트 감지**, **경고 캡처**, **콜백 구성**, **경고 열거**를 하나의 흐름으로 연결합니다.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**이 프로그램을 실행하면** Aspose.Words가 교체한 모든 폰트가 출력됩니다. 출력을 로그 파일로 리다이렉트하거나 알림을 발생시키고, 중요한 폰트가 누락된 경우 로드를 중단하도록 할 수도 있습니다.

---

## 흔히 묻는 질문 및 주의 사항

### 필수 폰트가 없을 때 로드를 중단하려면 어떻게 해야 하나요?
콜백 내부에서 `WarningInfo` 객체를 검사하고 특정 폰트 이름이 나타나면 예외를 발생시킬 수 있습니다. 예외가 발생하면 로드가 중단되어 완전한 제어가 가능합니다.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### PDF나 다른 형식에서도 작동하나요?
네. Aspose.Words는 PDF, RTF, HTML에서도 동일한 경고 인프라를 사용합니다. 파일 확장자를 바꾸기만 하면 나머지 코드는 그대로 동작합니다.

### 콘솔 대신 파일에 경고를 기록하려면?
`Console.WriteLine`을 선호하는 로깅 프레임워크(`Serilog`, `NLog` 등)로 교체하면 됩니다. `WarningInfo` 클래스는 `Message`, `Source`, `Exception`을 제공하므로 상세 로그 작성이 가능합니다.

### 성능에 영향을 미치나요?
오버헤드는 무시할 수준입니다—Aspose.Words 자체가 이미 경고를 생성합니다. 콜백을 추가하면 경고를 리스트에 저장할 뿐이며, 경고 수에 비례하는 O(n) 연산입니다. 일반적인 문서에서는 전체 로드 시간의 1 % 미만에 불과합니다.

---

## 시각적 요약

![Aspose.Words에서 폰트 감지 – 경고 흐름 다이어그램](https://example.com/images/font-detection-diagram.png "폰트 감지")

*Alt text:* **폰트 감지** – 경고 콜백, 컬렉션, 열거 단계가 표시된 다이어그램.

---

## 마무리

우리는 **경고 캡처**, **콜백 구성**, **경고 열거**를 통해 Aspose.Words에서 **폰트를 감지**하는 방법을 다루었습니다. 전체 코드 샘플은 어떤 .NET 애플리케이션에도 바로 적용할 수 있는 프로덕션‑레디 패턴을 보여줍니다.  

다음 단계로 살펴볼 내용:

- **다른 이슈**(예: 이미지 변환 문제)에 대한 **경고 캡처** 방법
- **맞춤 로깅 프레임워크**에 맞춘 **콜백 구성** 방법
- 배치 작업에서 **다수 문서에 대한 경고 열거** 방법
- **Aspose.Words.Fonts.FontSettings**를 사용해 폰트 폴더를 지정하고, 사전 대체를 최소화하는 방법

시도해 보고, 컬렉터를 로그 스타일에 맞게 조정하면 예상치 못한 폰트 교체에 놀라지 않을 것입니다. 궁금한 점이 있으면 아래 댓글에 남겨 주세요—행복한 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}