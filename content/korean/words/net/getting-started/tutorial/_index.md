---
language: ko
url: /korean/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Aspose.Words 문서에서 누락된 폰트 감지 – 완전한 C# 가이드

Aspose.Words로 Word 파일을 로드할 때 **누락된 폰트를 감지**하는 방법이 궁금하셨나요? 일상 업무에서 원본 문서가 설치되지 않은 폰트를 사용해서 몇몇 PDF가 이상하게 보인 적이 있습니다. 좋은 소식은? Aspose.Words는 폰트를 대체할 때 정확히 알려주며, 간단한 warning callback으로 그 정보를 캡처할 수 있습니다.  

이 튜토리얼에서는 **완전하고 실행 가능한 예제**를 통해 모든 폰트 대체를 로그하는 방법, 콜백이 왜 중요한지, 그리고 견고한 누락 폰트 감지를 위한 몇 가지 추가 팁을 보여드립니다. 불요한 내용은 없으며, 오늘 바로 작동하도록 필요한 코드와 논리만 제공합니다.

---

## 배울 내용

- **Aspose.Words warning callback**을 구현하여 폰트 대체 이벤트를 포착하는 방법.  
- **LoadOptions C#**을 구성하여 문서를 로드하는 동안 콜백이 호출되도록 하는 방법.  
- 누락된 폰트 감지가 실제로 작동했는지 확인하는 방법 및 콘솔 출력 예시.  
- 대량 처리나 헤드리스 환경을 위한 선택적 조정 사항.  

**Prerequisites** – 최신 버전의 Aspose.Words for .NET(코드는 23.12 버전에서 테스트됨), .NET 6 이상, 그리고 C#에 대한 기본적인 이해가 필요합니다. 이 조건만 충족한다면 바로 시작할 수 있습니다.

---

## Warning Callback을 사용한 누락된 폰 감지

이 솔루션의 핵심은 `IWarningCallback` 구현입니다. Aspose.Words는 다양한 상황에서 `WarningInfo` 객체를 발생시키지만, 여기서는 `WarningType.FontSubstitution`만 신경 씁니다. 어떻게 연결하는지 살펴보겠습니다.

### Step 1: Font‑Warning Collector 만들기

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Why this matters*: `WarningType.FontSubstitution`만 필터링하면 관련 없는 경고(예: 사용 중단된 기능)로 인한 잡음을 피할 수 있습니다. `info.Description`에는 원본 폰트 이름과 사용된 대체 폰트가 이미 포함되어 있어 명확한 감사 로그를 제공합니다.

---

## Callback을 사용하도록 LoadOptions 구성

이제 Aspose.Words가 파일을 로드할 때 우리 컬렉터를 사용하도록 지시합니다.

### Step 2: LoadOptions 설정

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Why this matters*: `LoadOptions`는 콜백, 암호, 기타 로딩 동작을 플러그인할 수 있는 유일한 위치입니다. `Document` 생성자와 분리하면 여러 파일에 대해 코드를 재사용할 수 있습니다.

---

## 문서를 로드하고 누락된 폰트 캡처

콜백이 연결되었으니 이제 문서를 로드하기만 하면 됩니다.

### Step 3: DOCX(또는 지원되는 형식) 로드

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

`Document` 생성자가 파일을 파싱할 때, 누락된 폰트가 있으면 `FontWarningCollector`가 트리거됩니다. 콘솔에는 다음과 같은 라인이 표시됩니다:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

이 라인은 **누락된 폰트를 감지**했음을 입증하는 구체적인 증거입니다.

---

## 출력 확인 – 기대 결과

터미널이나 Visual Studio에서 프로그램을 실행하세요. 원본 문서에 설치되지 않은 폰트가 포함되어 있으면 최소 하나 이상의 “Font substituted” 라인이 표시됩니다. 문서가 설치된 폰트만 사용한다면 콜백은 조용히 동작하고 “Document loaded successfully.” 메시지만 표시됩니다.

**Tip**: 두 번 확인하려면 Microsoft Word에서 해당 파일을 열고 폰트 목록을 확인하세요. *Home → Font* 그룹 아래 *Replace Fonts*에 나타나는 폰트는 대체 후보가 됩니다.

---

## 고급: 대량 파일에서 누락된 폰트 감지

수십 개의 파일을 스캔해야 할 때가 많습니다. 동일한 패턴을 그대로 확장하면 됩니다:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

`FontWarningCollector`가 호출될 때마다 콘솔에 기록하므로 별도의 로직 없이 파일별 보고서를 얻을 수 있습니다. 실제 운영 환경에서는 파일이나 데이터베이스에 로그를 남기고 싶을 수 있는데, `Console.WriteLine`을 원하는 로거로 교체하면 됩니다.

---

## 흔히 발생하는 문제 & 전문가 팁

| 문제 | 발생 원인 | 해결 방법 |
|------|-----------|-----------|
| **경고가 전혀 나타나지 않음** | 문서에 실제로 설치된 폰트만 포함되어 있음 | Word에서 파일을 열어 확인하거나 시스템에서 일부 폰트를 의도적으로 제거해 보세요. |
| **Callback이 호출되지 않음** | `LoadOptions.WarningCallback`이 할당되지 않았거나 이후에 새로운 `LoadOptions` 인스턴스를 사용함 | 단일 `LoadOptions` 객체를 유지하고 모든 로드에 재사용하세요. |
| **관련 없는 경고가 너무 많음** | `WarningType.FontSubstitution`으로 필터링하지 않음 | 예시와 같이 `if (info.Type == WarningType.FontSubstitution)` 조건을 추가하세요. |
| **대용량 파일에서 성능 저하** | 콜백이 모든 경고마다 실행돼 대량 문서에서 많음 | `LoadOptions.WarningCallback`을 통해 다른 경고 유형을 비활성화하거나, 파일 형식을 알고 있다면 `LoadOptions.LoadFormat`을 지정하세요. |

---

## 전체 작업 예제 (복사‑붙여넣기 가능)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Expected console output** (when a missing font is encountered):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

대체가 발생하지 않으면 성공 라인만 표시됩니다.

---

## 결론

이제 Aspose.Words로 처리하는 모든 문서에서 **완전하고 프로덕션 수준의 누락 폰트 감지** 방법을 갖추었습니다. **Aspose.Words warning callback**과 **LoadOptions C#**을 활용하면 모든 폰트 대체를 로그하고 레이아웃 문제를 진단하며 PDF가 의도한 모양을 유지하도록 할 수 있습니다.  

단일 파일이든 대량 배치이든 패턴은 동일합니다—`IWarningCallback`을 구현하고 `LoadOptions`에 연결하면 Aspose.Words가 무거운 작업을 처리합니다.  

다음 단계가 궁금하신가요? **폰트 임베딩**이나 **fallback font families**와 결합해 문제를 자동으로 해결하거나, **DocumentVisitor** API를 탐색해 더 깊은 콘텐츠 분석을 시도해 보세요. 즐거운 코딩 되시고, 모든 폰트가 기대한 위치에 머물길 바랍니다!  

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}