---
category: general
date: 2026-01-06
description: Aspose.Words를 사용하여 문서를 로드할 때 경고를 받는 방법과 글꼴을 모니터링하는 방법을 배웁니다. 이 가이드는 경고
  콜백 및 글꼴 대체 추적을 다룹니다.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: ko
og_description: Aspose.Words에서 경고를 받는 방법은? 문서를 로드하는 동안 글꼴을 모니터링하고 대체 메시지를 캡처하는 단계별
  튜토리얼을 따라보세요.
og_title: Aspose.Words에서 경고 받는 방법 – 폰트 모니터링
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Aspose.Words에서 경고 받는 방법 – C#에서 글꼴 모니터링
url: /ko/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 경고 받기 – C#에서 폰트 모니터링

워드 문서에 설치되지 않은 폰트가 포함되어 있을 때 **경고를 받는 방법**이 궁금했던 적 있나요? 흔히 겪는 문제로, 앱이 누락된 폰트를 조용히 대체하고 어떤 변화가 있었는지 알 수 없습니다. 좋은 소식은 Aspose.Words의 경고 시스템에 연결하여 실시간으로 **폰트를 모니터링**할 수 있다는 점입니다.

> **Pro tip:** 문서 변환 파이프라인을 구축 중이라면, 누락된 폰트를 일찍 로그에 기록함으로써 이후 발생할 수 있는 레이아웃 문제를 예방할 수 있습니다.

---

## 필요 사항

- **Aspose.Words for .NET** (최신 버전; API는 v23.10 이후 변경되지 않음)
- .NET 개발 환경 (Visual Studio, Rider, 혹은 C# 확장 기능이 포함된 VS Code)
- 설치되지 않은 폰트를 참조하는 샘플 `.docx` 파일 (예: **“NonExistentFont”**)

이것만 있으면 됩니다—Aspose.Words 외에 추가 NuGet 패키지는 필요 없습니다.

---

## Step 1 – 경고 수집기 설정 (헤더의 주요 키워드)

먼저, 발생하는 경고를 저장할 장소가 필요합니다. Aspose.Words는 이를 위해 `LoadOptions`의 `WarningCallback` 속성을 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**왜 중요한가:**  
라이브러리가 누락된 폰트를 만나면 예외를 발생시키지 않고 `WarningInfo` 객체를 내보냅니다. 수집기를 연결하면 모든 대체 이벤트를 완전히 파악할 수 있어, 관련 없는 메시지로 콘솔을 어지럽히지 않으면서 **폰트를 모니터링**할 수 있습니다.

---

## Step 2 – 경고 활성 옵션으로 문서 로드

이제 실제로 파일을 읽습니다. 이전 단계에서 준비한 `LoadOptions`가 폰트와 관련된 모든 경고를 캡처하도록 보장합니다.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**내부에서 무슨 일이 일어나고 있나요?**  
Aspose.Words는 워드 파일을 파싱하고 폰트를 해석합니다. 요청된 폰트를 찾지 못하면 대체 폰트(보통 Arial)로 전환합니다. 이 대체 과정에서 `WarningType.FontSubstitution` 경고가 발생하며, 이는 `warningCollector`에 전달됩니다.

---

## Step 3 – 수집된 경고 검사 (핵심 키워드 재등장)

문서가 로드된 후, `warningCollector`를 순회하며 폰트 대체 메시지를 출력합니다.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**예상 출력** (누락된 폰트가 *“FancyScript”*라고 가정):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

문서에 여러 개의 알 수 없는 폰트가 포함되어 있으면, 대체마다 한 줄씩 표시됩니다—로그 기록이나 알림에 적합합니다.

---

## Step 4 – 선택 사항: 경고 정보를 로그 또는 영구 저장

실제 운영 환경에서는 `Console.WriteLine`보다 더 많은 작업이 필요할 것입니다. 아래는 경고를 JSON 파일에 기록하여 나중에 분석할 수 있는 간단한 예시입니다.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

이제 모니터링 대시보드에 전달하거나 누락된 폰트 파일을 자동으로 요청하는 데 사용할 수 있는 영구 기록이 생겼습니다.

---

## Step 5 – 결과 확인 및 정리

프로그램을 실행하세요. 대체 메시지가 표시되면 **경고를 성공적으로 받았으며** 이제 **폰트를 적극적으로 모니터링**하고 있는 것입니다. 아무 것도 표시되지 않으면 테스트 문서가 실제로 시스템에 설치되지 않은 폰트를 참조하고 있는지 다시 확인하세요.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

카운트가 0이면 보통 다음 중 하나를 의미합니다:

1. 모든 폰트가 해결됨(폰트가 로컬에 설치되어 있을 수 있음), 혹은
2. 문서에 대체가 필요한 폰트 참조가 전혀 없었습니다.

---

## Common Pitfalls & How to Avoid Them

| 문제점 | 발생 원인 | 해결 방법 |
|---------|----------------|-----|
| **경고가 나타나지 않음** | 폰트가 실제로 시스템에 존재하거나 문서가 기본 제공 폰트만 사용함. | 소스 파일에서 폰트 이름을 존재할 수 없는 것으로 바꾸세요(예: `XYZ123`). 다시 시도하십시오. |
| **경고가 너무 많음(노이즈)** | 컬렉터를 초기화하지 않은 채 루프에서 다수의 문서를 로드하고 있음. | 각 문서마다 `WarningInfoCollection`을 새로 만들거나 처리 후 `warningCollector.Clear()`를 호출하세요. |
| **성능 영향** | 디스크에 과도하게 로그를 기록하면 배치 처리 속도가 느려질 수 있음. | 경고를 메모리에 버퍼링하고 일괄 기록하거나 비동기 파일 I/O를 사용하세요. |
| **`using Aspose.Words.Loading;` 누락** | `LoadOptions` 클래스가 해당 네임스페이스에 존재함. | Step 1에 표시된 대로 누락된 `using` 지시문을 추가하세요. |

---

## 솔루션 확장 – 다른 경고 유형 모니터링

폰트 대체가 가장 눈에 띄지만, Aspose.Words는 다음과 같은 경우에도 경고를 발생시킬 수 있습니다:

- **Deprecated features** (`WarningType.Deprecated`),
- **Potential data loss** (`WarningType.DataLoss`),
- **Unsupported file formats** (`WarningType.UnsupportedFileFormat`).

필요에 따라 Step 3에서 필터를 확장하여 이러한 경고도 포착할 수 있습니다:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

이렇게 하면 **폰트를 모니터링하는 방법**뿐만 아니라 애플리케이션이 마주할 수 있는 모든 시나리오에 대한 **경고를 받는 방법**도 확보할 수 있습니다.

---

## 전체 작업 예제 (복사‑붙여넣기 가능)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Run it:** 프로젝트를 빌드하고 실행하면 경고가 출력되고 저장됩니다. 이것이 Aspose.Words로 **경고를 받는 방법**과 **폰트를 모니터링하는 방법**에 대한 완전한 답변입니다.

---

## 결론

이제 Aspose.Words에서, 특히 폰트 대체 상황에 대한 **경고를 받는 방법**과 문서 로드 과정 전반에 걸쳐 **폰트를 모니터링하는 방법**을 알게 되었습니다. `WarningCallback`을 연결하고 수집된 `WarningInfo` 객체를 순회하며, 필요에 따라 데이터를 영구 저장함으로써 누락된 폰트 이벤트에 대한 완전한 투명성을 확보할 수 있습니다—이는 모든 문서 처리 파이프라인에 필수적인 기능입니다.

다음 단계는? 경고 필터를 확장하여 데이터 손실이나 사용 중단된 기능에 대한 경고도 포함시키거나, JSON 로그를 Grafana와 같은 모니터링 대시보드에 연동해 보세요. 동일한 패턴이 모든 경고 유형에 적용되므로 Aspose.Words가 발생시키는 어떤 문제도 손쉽게 감시할 수 있습니다.

코딩을 즐기세요, 그리고 문서가 언제나 기대한 대로 정확히 렌더링되길 바랍니다! 

---

<img src="font-warnings.png" alt="Aspose.Words에서 경고 받는 방법" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}