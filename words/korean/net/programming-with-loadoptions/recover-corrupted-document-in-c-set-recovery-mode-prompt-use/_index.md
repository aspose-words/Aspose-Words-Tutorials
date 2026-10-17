---
category: general
date: 2026-01-11
description: Aspose.Words를 사용하여 C#에서 손상된 문서를 복구합니다. 복구 모드를 설정하고, 복구와 함께 docx를 로드하며,
  오류 발생 시 사용자에게 알리는 방법을 몇 가지 간단한 단계로 배웁니다.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: ko
og_description: 복구 모드를 설정하고, 복구 기능으로 DOCX를 로드하며, 오류 발생 시 사용자에게 알림을 표시하여 C#에서 손상된 문서를
  복구합니다. 단계별 완전 튜토리얼.
og_title: C#에서 손상된 문서 복구 – 빠른 가이드
tags:
- Aspose.Words
- C#
- Document Recovery
title: C#에서 손상된 문서 복구 – 복구 모드 설정 및 사용자에게 알림
url: /ko/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 손상된 문서 복구 – 전체 가이드

DOCX 파일을 Word에서는 정상적으로 열리지만 코드에서는 예외가 발생한 적이 있나요? 아마 **손상된 문서 복구** 상황을 겪고 계실 겁니다. 좋은 소식은 Aspose.Words가 이러한 까다로운 파일을 어떻게 처리할지 세밀하게 제어할 수 있다는 점입니다—조용히 수정하든, 예외를 발생시키든, 사용자에게 선택을 물어보든 말이죠.

이 튜토리얼에서는 **손상된 문서 복구** 파일을 다루는 모든 과정을 단계별로 살펴봅니다. 라이브러리 설치부터 올바른 **복구 모드 설정** 옵션 선택, **복구와 함께 DOCX 로드**, 그리고 문제가 발생했을 때 **오류 시 사용자에게 알리기**까지. 불필요한 내용 없이 바로 실행 가능한 예제를 제공하니 .NET 프로젝트에 바로 적용해 보세요.

> **빠른 미리보기:** 최종적으로 손상될 가능성이 있는 `corrupt.docx`를 로드하고 경고를 기록하며, 복구에 실패했을 때 사용자가 계속 진행할지 물어보는 콘솔 앱을 만들 수 있습니다.

---

## 준비물

- **.NET 6.0** 이상 (코드는 .NET Framework 4.6+에서도 동작합니다).  
- **Aspose.Words for .NET** – NuGet으로 설치 (`Install-Package Aspose.Words`).  
- 테스트용 **손상된 DOCX** 파일 (헥스 에디터로 파일을 열어 손상시키거나 확장자를 바꿔서 만들 수 있습니다).  
- 원하는 IDE—Visual Studio, Rider, 혹은 VS Code 등.

> *프로 팁:* 원본 파일은 반드시 백업해 두세요. 복구 과정에서 문서 일부가 재작성될 수 있으며, 좋은 부분을 잃고 싶지는 않을 테니까요.

---

## 1단계 – Aspose.Words 설치 및 네임스페이스 추가

먼저 NuGet에서 라이브러리를 가져오고 필요한 네임스페이스를 선언합니다.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

이것만 있으면 나머지 가이드를 진행할 수 있습니다. `Aspose.Words.Loading` 네임스페이스에 포함된 `LoadOptions` 클래스가 **복구 모드 설정**의 핵심입니다.

---

## 2단계 – 복구 모드 선택 (Primary H2 with Keyword)

### 손상된 문서 복구 – 올바른 복구 모드 설정

Aspose.Words는 세 가지 복구 동작을 제공합니다:

| 모드 | 동작 내용 | 사용 시점 |
|------|-----------|-----------|
| **PromptUser** | 대화상자를 표시(또는 직접 구현한 프롬프트)하고 파일을 복구하려 시도합니다. | 사용자가 직접 선택할 수 있는 인터랙티브 도구에 적합합니다. |
| **Silent** | 자동으로 복구를 시도하고 UI를 표시하지 않습니다. | 배치 작업이나 서비스에 적합합니다. |
| **ThrowException** | 처리를 중단하고 예외를 발생시킵니다. | 엄격한 검증이 필요할 때 사용합니다. |

아래는 **복구 모드**를 `PromptUser`로 설정하는 예시입니다. 조용히 처리하고 싶다면 enum 값을 교체하면 됩니다.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **왜 중요한가:** **복구 모드 설정**을 명시함으로써 Aspose.Words에게 얼마나 적극적으로 복구할지 알려줄 수 있습니다. 기본값은 `PromptUser`이지만, 명시적으로 지정하면 유지보수자와 검색 엔진 모두에게 의도가 명확해집니다.

---

## 3단계 – 복구와 함께 DOCX 로드

이제 앞서 구성한 `LoadOptions`를 사용해 **복구와 함께 DOCX 로드**를 수행합니다. 파일이 손상돼 있으면 Aspose.Words가 복구를 시도하거나 모드에 따라 경고를 발생시킵니다.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

`Document` 생성자가 핵심 작업을 수행합니다. **PromptUser** 모드에서는 콘솔 프롬프트(또는 `LoadOptions` 이벤트에 연결한 커스텀 UI)가 나타나 진행 여부를 묻습니다. **Silent** 모드에서는 가능한 한 자동 복구를 시도하고 계속 진행합니다.

---

## 4단계 – 경고 확인 및 사용자에게 알리기

Aspose.Words는 발생한 모든 문제를 `Warnings` 컬렉션에 기록합니다. 이를 순회하면서 사용자가 다음 행동을 선택하도록 할 수 있습니다.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

위 코드는 콘솔 환경에서 **오류 시 사용자에게 알리기**를 구현한 예시입니다. Windows Forms나 WPF 앱이라면 `Console.ReadLine`을 `MessageBox` 혹은 커스텀 다이얼로그로 교체하면 됩니다.

---

## 5단계 – 복구된 문서 활용

이 시점에서 문서는 메모리 상에 로드되어 Aspose.Words가 가능한 한 복구한 상태입니다. 이제 내용 읽기, 깨끗한 사본 저장, 혹은 필요한 모든 조작을 수행할 수 있습니다.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

손상된 파일에 대해 전체 프로그램을 실행하면 다음과 유사한 콘솔 출력이 나타납니다:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

파일이 실제로 정상이라면 “Document loaded without any warnings.” 라는 메시지가 표시되고, 깨끗한 사본은 원본과 동일합니다.

---

## 전체 작동 예제

아래는 한 파일에 모은 전체 프로그램입니다. 새 콘솔 프로젝트에 복사‑붙여넣기하고 **F5**를 눌러 실행해 보세요.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

실행하면서 테스트 파일을 손상시키면 복구 과정이 어떻게 진행되는지 확인할 수 있습니다. 🎉

---

## 엣지 케이스 및 변형

| 시나리오 | 변경 사항 | 이유 |
|----------|-----------|------|
| **배치 처리** (사용자 상호작용 없음) | `RecoveryMode = RecoveryMode.Silent` 로 설정하고 콘솔 프롬프트를 제거합니다. | 파이프라인을 자동으로 진행할 수 있습니다. |
| **엄격한 검증** (빠른 실패) | `RecoveryMode.ThrowException` 사용. 로드 호출을 try/catch 로 감싸고 예외를 로그에 남깁니다. | 부분적으로 복구된 파일을 절대 사용하지 않게 보장합니다. |
| **커스텀 UI** (WinForms/WPF) | `LoadOptions.LoadingProgress`에 구독하거나 `Document.LoadOptions` 이벤트를 활용해 다이얼로그를 표시합니다. | 콘솔보다 풍부한 사용자 경험을 제공합니다. |
| **대용량 문서** (메모리 제한) | `LoadOptions.LoadFormat = LoadFormat.Docx` 로 로드하고 `Document.SaveOptions` 로 스트리밍 저장을 고려합니다. | OutOfMemory 예외를 방지합니다. |

---

## 실전 팁 (E‑E‑A‑T 신호)

- **복구 시 항상 백업**을 먼저 만들고 진행하세요; 과정 중 파일 일부가 덮어쓰기될 수 있습니다.  
- **경고를 파일에 로그**해 두면 나중에 원인 분석에 도움이 됩니다(예: 누락된 파트, 손상된 XML).  
- **다양한 손상 유형**을 테스트하세요—파일을 잘라내기, XML 태그 손상, ZIP 구조 변경 등 각각의 모드가 어떻게 동작하는지 확인합니다.  
- **Aspose.Words를 정기적으로 업데이트**하세요; 최신 버전은 복구 알고리즘을 개선하고 새로운 경고 유형을 추가합니다.  
- **복구 후 검증**을 결합하세요—`document.UpdateFields()`와 `document.Save()`를 실행해 문서가 완전히 정상인지 확인합니다.

---

## 결론

이제 **복구 모드 설정**, **복구와 함께 DOCX 로드**, 그리고 **오류 시 사용자에게 알리기**를 통해 C#에서 **손상된 문서 복구** 방법을 완전히 이해했습니다. 전체 예제는 콘솔 앱, 서비스, UI 프로젝트 어디에서든 적용 가능한 깔끔한 엔드‑투‑엔드 흐름을 보여줍니다.

다음 단계는 무엇인가요? WinForms 앱에서 콘솔 프롬프트를 모달 다이얼로그로 교체해 보거나, 백그라운드 작업을 위해 **Silent** 모드를 실험해 보세요. 혹은 ASP.NET 파일 업로드 엔드포인트에 복구 로직을 통합해 사용자가 손상된 DOCX를 업로드하면 즉시 복구된 버전을 제공하도록 구현해 보세요.

코딩 즐겁게, 문서가 언제나 온전하길 바랍니다!  

---

![손상된 문서 복구 예시](/images/recover-corrupted-document.png "손상된 문서 복구")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}