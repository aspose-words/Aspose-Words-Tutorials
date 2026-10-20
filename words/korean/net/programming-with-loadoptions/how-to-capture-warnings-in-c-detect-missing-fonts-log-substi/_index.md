---
category: general
date: 2026-04-04
description: Aspose.Words LoadOptions를 사용하여 C#에서 경고를 캡처하고, 누락된 글꼴을 감지하며, 대체 이벤트를 기록하는
  방법을 배웁니다.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: ko
og_description: C#에서 Aspose.Words LoadOptions를 사용하여 경고를 캡처하고, 누락된 글꼴을 감지하며, 대체 이벤트를
  기록하는 방법.
og_title: C#에서 경고 캡처하기 – 누락된 글꼴 감지 및 대체 로그 기록
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: C#에서 경고 캡처 방법 – 누락된 폰트 감지 및 대체 로그 기록
url: /ko/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 경고 캡처하기 – 누락된 글꼴 감지 및 대체 로그 기록

워드 문서를 로드할 때 누락된 글꼴 때문에 나타나는 **경고를 캡처하는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 실제 프로젝트에서 글꼴은 마이그레이션 중에 사라지는 경우가 많으며, 조용한 대체가 레이아웃을 깨뜨릴 수 있습니다. 좋은 소식은? Aspose.Words는 이러한 경고를 청취하고, 누락된 글꼴을 감지하며, 나중에 원본을 수정할 수 있도록 모든 대체를 로그에 기록하는 깔끔한 방법을 제공합니다.

이 튜토리얼에서는 **경고를 캡처하는 방법**을 보여주고, **누락된 글꼴을 감지**하며, **대체 로그를 기록하는 방법**을 설명하는 완전하고 바로 실행 가능한 솔루션을 단계별로 살펴봅니다. 끝까지 진행하면 재사용 가능한 경고 핸들러, 완전히 구성된 `LoadOptions` 객체, 그리고 확인할 수 있는 샘플 콘솔 출력이 준비됩니다.

> **전제 조건:** NuGet을 통해 Aspose.Words for .NET (v24.x 이상)을 설치하고 기본 C# 개발 환경(Visual Studio 2022 또는 VS Code)만 있으면 됩니다.

---

## 문서를 로드할 때 경고 캡처하기

솔루션의 핵심은 `IWarningCallback`을 구현하는 클래스입니다. Aspose.Words는 문서를 로드하는 동안 발생하는 모든 경고, 특히 글꼴 대체 경고에 대해 이 콜백을 자동으로 호출합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **왜 이 단계인가?** `WarningType.FontSubstitution`으로 필터링하면 관련 없는 경고(예: 사용 중단된 기능)로 인한 잡음을 피할 수 있습니다. 이렇게 하면 로그가 당신이 관심 있는 정확한 문제, 즉 누락된 글꼴에 집중됩니다.

---

## Aspose.Words로 누락된 글꼴 감지하기

문서가 시스템에 설치되지 않은 글꼴을 참조하면 Aspose.Words는 가장 근접한 글꼴로 대체하고 경고를 발생시킵니다. 위의 핸들러가 각 발생을 포착하여 **누락된 글꼴을 감지**합니다.

이를 실제로 확인하려면 `LoadOptions`를 구성하고 핸들러를 연결해야 합니다:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **팁:** 경고를 나중에 처리하기 위해(예: 파일에 기록) 수집하고 싶다면 `Console.WriteLine`을 메시지를 `List<string>`에 추가하는 코드로 교체하세요.

---

## 대체 이벤트 로그 기록 방법

로그는 경고 출력을 영구 저장소로 보내는 것만큼 간단합니다. 아래 예시는 각 대체 경고를 `font-warnings.log`라는 텍스트 파일에 기록하는 간단한 예시입니다.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **왜 파일에 로그를 기록하나요?** 영구 로그를 통해 여러 실행에 걸친 글꼴 문제를 감사하고, 알림을 자동화하거나, 데이터를 빌드 파이프라인 검사에 활용할 수 있습니다.

---

## 전체 작동 예제

모든 것을 합쳐서 복사·붙여넣기만 하면 바로 실행할 수 있는 독립형 콘솔 애플리케이션을 제공합니다. 이 예제는 **경고를 캡처하는 방법**, **누락된 글꼴 감지**, 그리고 **대체 로그 기록**을 한 번에 보여줍니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### 예상 콘솔 출력

`input.docx`가 설치되지 않은 글꼴을 참조하면 다음과 같은 출력이 표시됩니다:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

`FileLoggingWarningHandler`로 전환하면 동일한 라인이 타임스탬프와 함께 `font-warnings.log`에 기록됩니다.

![how to capture warnings console output](image-placeholder.png)

---

## 일반적인 질문 및 엣지 케이스

### 글꼴 대체 경고만이 아니라 *모든* 경고를 캡처해야 한다면?

`if (info.Type == WarningType.FontSubstitution)` 검사를 삭제하면 됩니다. 콜백은 모든 경고 유형(`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` 등)을 받게 됩니다. 이후 `info.Type`에 따라 각 경우를 다르게 처리할 수 있습니다.

### 이 방법이 PDF에도 적용되나요, 아니면 워드 문서에만 적용되나요?

`LoadOptions`와 `IWarningCallback`은 Aspose.Words의 일부이므로 Word 호환 형식(`.docx`, `.doc`, `.rtf`, `.html`)에 적용됩니다. PDF의 경우 Aspose.PDF 고유의 경고 메커니즘을 사용해야 합니다.

### 경고를 로그에 기록하는 대신 억제하려면 어떻게 해야 하나요?

`LoadOptions.WarningCallback = null`로 설정하거나 콜백을 구현하되 메서드 본문을 비워두면 됩니다. 라이브러리는 여전히 조용히 대체를 수행합니다.

### 스레드 안전성은 어떨까요?

콜백 인스턴스는 문서를 로드하는 동일한 스레드에서 호출되므로, 핸들러를 병렬 로드에 공유하지 않는 한 추가 동기화가 필요하지 않습니다. 병렬 로드에서 공유한다면, 로그 파일과 같은 공유 자원을 lock으로 보호하거나 concurrent 컬렉션을 사용하세요.

---

## 결론

우리는 Aspose.Words에서 **경고를 캡처하는 방법**을 다루고, **누락된 글꼴을 감지하는 방법**을 보여주었으며, 나중에 분석할 수 있도록 **대체 이벤트를 로그에 기록하는 방법**을 설명했습니다. 간단한 `IWarningCallback` 구현을 `LoadOptions`에 연결하면 코드베이스를 어지럽히지 않고도 글꼴 관련 문제를 완전히 파악할 수 있습니다.

다음 단계는? 로거를 확장해 이메일을 보내거나 Azure Monitor와 통합하거나 빌드 서버에서 누락된 글꼴을 자동으로 설치하도록 해보세요. 또한 다른 경고 유형도 살펴볼 수 있습니다—`WarningType.DegradedDocument`는 변환 과정에서 손실된 기능을 알려줍니다.

글꼴 처리나 Aspose.Words에 대해 더 궁금한 점이 있나요? 댓글을 남기거나 Aspose 포럼에 새 이슈를 올려 주세요. 즐거운 코딩 되시고, 문서가 항상 올바른 서체로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}