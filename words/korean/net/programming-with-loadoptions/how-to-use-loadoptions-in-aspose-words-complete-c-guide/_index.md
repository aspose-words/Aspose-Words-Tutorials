---
category: general
date: 2026-04-10
description: Aspose.Words에서 LoadOptions를 사용하여 문서를 로드할 때 글꼴 대체 경고를 포착하는 방법. 전체 코드 예제가
  포함된 단계별 C# 솔루션을 배워보세요.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: ko
og_description: Aspose.Words에서 LoadOptions를 사용하여 문서를 로드할 때 글꼴 대체 경고를 캡처하는 방법. 이 가이드는
  전체 C# 구현 과정을 안내합니다.
og_title: Aspose.Words에서 LoadOptions 사용 방법 – 완전한 C# 가이드
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Aspose.Words에서 LoadOptions 사용 방법 – 완전한 C# 가이드
url: /ko/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words에서 LoadOptions 사용 방법 – 완전한 C# 가이드

LoadOptions를 사용하는 것은 문서 로드에 대한 세밀한 제어가 필요할 때 흔히 마주치는 난관입니다. 이 튜토리얼에서는 **LoadOptions 사용 방법**을 정확히 보여드리며, 폰트 대체 경고를 포착하고 C#에서 이를 처리하는 방법을 설명합니다.  

만약 누락된 폰트를 참조하는 DOCX 파일을 열었을 때 출력이 이상하게 보인 적이 있다면, 여기서 해결책을 찾을 수 있습니다. `LoadOptions` 인스턴스를 생성하는 단계부터 콘솔에 경고 세부 정보를 출력하는 전체 과정을 차근차근 살펴보겠습니다. 마지막에는 .NET 프로젝트에 바로 넣어 사용할 수 있는 실행 가능한 코드 스니펫을 제공합니다.

## 배울 내용

- 신뢰할 수 있는 문서 가져오기를 위해 `LoadOptions`가 왜 중요한지.  
- **폰트 대체 경고**만을 감시하는 **WarningCallback**을 연결하는 방법.  
- 이러한 옵션을 활성화한 상태로 Word 파일을 로드하는 정확한 코드.  
- 여러 개의 누락된 폰트를 포함한 문서와 같은 엣지 케이스를 처리하는 팁.  

외부 문서는 필요 없습니다—여기에 모든 것이 준비되어 있습니다.

## 사전 준비 사항

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 이상 | 예제에서 사용된 C# 10 구문을 실행할 런타임을 제공합니다. |
| Aspose.Words for .NET (최신 버전) | `LoadOptions`와 경고 인프라를 제공하는 라이브러리입니다. |
| 설치되지 않은 폰트를 참조할 수 있는 DOCX 파일 | 경고 콜백이 실제로 작동하는 모습을 확인하기 위해 필요합니다. |
| Visual Studio 2022 (또는 선호하는 IDE) | 디버깅 및 테스트를 손쉽게 할 수 있습니다. |

이미 준비가 되었다면, 바로 시작해 보세요.

## Step 1 – LoadOptions 객체 생성 및 WarningCallback 연결

**LoadOptions**를 **how to use LoadOptions** 할 때 가장 먼저 해야 할 일은 인스턴스를 만들고 `WarningCallback`에 대리자를 할당하는 것입니다. 이 대리자는 Aspose.Words가 상황을 알려줄 때마다 호출되며, 특히 누락된 폰트를 발견했을 때 작동합니다.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**왜 중요한가:** 콜백이 없으면 Aspose.Words는 누락된 폰트를 조용히 기본 폰트로 교체하고, 시각적 변화가 발생해도 눈치채지 못합니다. `WarningCallback`을 등록하면 모든 대체 작업을 실시간으로 로그에 남길 수 있어, 품질 보증이 필요한 문서 파이프라인에 필수적입니다.

## Step 2 – 폰트 대체 경고에만 반응하기

콜백이 관련 없는 경고(예: 사용 중단된 기능)까지 모두 전달할까 걱정될 수 있습니다. 답은 *예*이지만, 우리는 이를 필터링할 수 있습니다. 위 스니펫에서 이미 `args.WarningType == WarningType.FontSubstitution`을 확인하고 있습니다. 이 라인은 **폰트 대체 경고**를 구분하는 가드 역할을 하며, 출력이 해당 경고에만 집중되도록 합니다.

다른 경고 유형도 처리하고 싶다면 `if` 블록을 확장하면 됩니다:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

이 패턴은 **warningcallback** 메커니즘이 얼마나 유연한지 보여 주며, 필요에 따라 정확히 원하는 시나리오에만 대응하도록 맞출 수 있습니다.

## Step 3 – 구성한 LoadOptions로 문서 로드하기

리스너가 준비되었으니, 이제 `LoadOptions` 인스턴스를 `Document` 생성자에 전달하면 됩니다. 바로 이 순간에 **Aspose.Words LoadOptions example**이 진가를 발휘합니다.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**예상 결과:** DOCX가 머신에 설치되지 않은 폰트를 참조하고 있다면, 콘솔에 다음과 같은 라인이 출력됩니다:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

이 출력은 **how to use LoadOptions**를 성공적으로 활용해 폰트 문제를 모니터링하고 있음을 확인시켜 줍니다.

## 전체 작동 예제 (복사‑붙여넣기 즉시 사용)

아래는 바로 컴파일하고 실행할 수 있는 완전한 프로그램입니다. 세 단계 전체를 하나로 모으고, 친절한 배너와 오류 처리를 추가했습니다.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### 예상 출력

`input.docx`에 존재하지 않는 폰트가 포함된 머신에서 프로그램을 실행하면 다음과 유사한 결과가 나타납니다:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

모든 폰트가 존재한다면 성공 메시지만 표시되고, 경고 라인은 나타나지 않습니다.

## 흔히 저지르는 실수 & 전문가 팁

- **실수:** `WarningCallback`을 설정하지 않음. 코드는 여전히 로드되지만 대체 세부 정보를 놓칩니다.  
  **전문가 팁:** `LoadOptions` 생성 직후 바로 콜백을 할당하세요; 비용이 거의 없고 나중에 큰 도움이 됩니다.

- **실수:** 잘못된 폴더를 가리키는 상대 경로 사용.  
  **전문가 팁:** `Path.Combine(Environment.CurrentDirectory, "input.docx")`를 사용해 파일 조회를 보다 견고하게 만드세요.

- **실수:** 경고가 로드를 중단할 것이라 기대함.  
  **전문가 팁:** 폰트 대체 경고는 *정보* 수준이며 로드를 중단하지 않습니다. 더 엄격한 검증이 필요하면 콜백 내부에서 예외를 발생시켜 처리하세요.

- **실수:** 폰트가 전혀 설치되지 않은 서버(예: 최소 Docker 이미지)에서 실행.  
  **전문가 팁:** 필요한 폰트를 미리 설치하거나 앱에 번들링하고, 콜백을 통해 프로덕션 환경에서 대체가 발생하지 않는지 확인하세요.

## LoadOptions 사용 vs. 로드 후 검사 시점

“로드 후에 문서를 검사하면 안 될까?” 라는 질문이 있을 수 있습니다. 답은 성능과 정확성에 있습니다. 로드 **중에** 경고를 처리하면 레이아웃 계산이나 PDF 변환이 일어나기 전에 문제를 조기에 포착할 수 있습니다. 특히 배치 처리 파이프라인에서는 한 단계씩 추가될 때마다 시간이 늘어나기 때문에 이 접근법이 큰 이점을 제공합니다.

## 예제 확장: 모든 대체 폰트 보고서 저장하기

영구적인 기록이 필요하다면(예: 규정 준수 목적) 콜백을 수정해 메시지를 리스트에 수집하고 로드가 끝난 뒤 파일로 기록하도록 할 수 있습니다:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

이제 콘솔 피드백과 함께 지속 가능한 로그 파일도 확보했습니다.

## 다음에 탐색해 볼 관련 주제

- **Aspose.Words에서 사용자 정의 폰트 임베드 방법** – 대체를 완전히 방지합니다.  
- **LoadOptions를 사용해 문서 크기 제한** – 악의적인 대용량 파일로부터 보호합니다.  
- **타이포그래피를 유지한 Word → PDF 변환** – 경고 콜백 접근법과 잘 어울립니다.  

이 모든 주제는 방금 만든 `LoadOptions` 기반 토대를 기반으로 확장됩니다.

## 결론

우리는 **Aspose.Words에서 LoadOptions 사용 방법**을 처음부터 끝까지 다뤘습니다: 옵션 객체 생성, **폰트 대체 경고**에 집중하는 `WarningCallback` 연결, 그리고 자신감 있게 문서를 로드하는 과정까지. 전체 예제는 바로 실행 가능하며, 추가 팁을 통해 흔히 발생하는 함정을 피할 수 있습니다.  

자유롭게 실험해 보세요—콜백을 다른 경고 유형으로 바꾸거나 데이터베이스에 로그를 남기거나, 업로드된 Word 파일을 검증하는 웹 서비스에 통합하는 등 활용 범위는 무궁무진합니다. 이 패턴은 유연하고 신뢰할 수 있으며, 무엇보다도 문서 렌더링을 망칠 수 있는 숨은 폰트 대체 과정을 명확히 보여줍니다.

행복한 코딩 되시고, 문서가 언제나 의도한 대로 정확히 렌더링되길 바랍니다! 

![Diagram showing the flow of using LoadOptions with a warning callback in Aspose.Words](https://example.com/images/loadoptions-flow.png "How to use LoadOptions diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}