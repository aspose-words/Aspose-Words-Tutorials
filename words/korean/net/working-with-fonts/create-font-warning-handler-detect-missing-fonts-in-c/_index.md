---
category: general
date: 2026-02-12
description: Aspose.Words에서 누락된 글꼴을 감지하고 추적하기 위해 글꼴 경고 처리기를 생성합니다. 경고를 효율적으로 기록하는
  방법을 배웁니다.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: ko
og_description: C#에서 글꼴 경고 핸들러를 만들어 누락된 글꼴을 감지하고, Aspose.Words가 글꼴을 대체할 때 경고를 기록하는
  방법을 배우세요.
og_title: 폰트 경고 핸들러 만들기 – 누락된 폰트 감지
tags:
- Aspose.Words
- C#
- Document Processing
title: 폰트 경고 핸들러 만들기 – C#에서 누락된 폰트 감지
url: /ko/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 폰트 경고 핸들러 만들기 – C#에서 누락된 폰트 감지

예상하지 못한 폰트가 Word 문서에서 조용히 교체된 적이 있나요? 당신만 그런 것이 아닙니다. Aspose.Words가 서버에 없는 폰트를 참조하는 DOCX를 로드하면 기본 폰트로 조용히 대체되어 레이아웃이 미묘하게 깨집니다.  

이 튜토리얼에서는 **누락된 폰트를 감지**하고, **누락된 폰트를 추적**하며, **경고를 로그**하는 방법을 정확히 보여드립니다. 최종적으로 모든 폰트 교체 이벤트를 콘솔(또는 원하는 로거)에 출력하는 재사용 가능한 경고 핸들러를 만들 수 있습니다. 미스터리가 아니라 명확하고 실행 가능한 코드만 제공합니다.

## Prerequisites

- .NET 6.0 이상 (.NET Framework 4.6+에서도 API는 동일)
- Aspose.Words for .NET 설치 (`dotnet add package Aspose.Words`)
- 머신에 설치되지 않은 폰트를 참조하는 Word 파일 (예: `MissingFont.docx`)

이미 준비되었다면, 바로 시작합니다.

## Step 1: Set Up LoadOptions with a Warning Callback  

**폰트 경고 핸들러**를 만들 때 가장 먼저 해야 할 일은 Aspose.Words에 문제가 발생할 때마다 콜백을 호출하도록 지시하는 것입니다. `LoadOptions`가 그 구성을 담는 컨테이너입니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**왜 중요한가:**  
`LoadOptions`는 `IWarningCallback`을 연결할 수 있는 유일한 장소입니다. 이를 설정하지 않으면 Aspose.Words는 내부적으로 경고를 기록하지만 여러분은 이를 볼 수 없습니다. `FontWarningHandler`를 지정함으로써 누락된 폰트가 교체될 때 발생하는 모든 일을 완전히 제어할 수 있습니다.

## Step 2: Implement the FontWarningHandler Class  

이제 실제로 **폰트 경고 핸들러** 코드를 **만듭니다**. 이 클래스는 `IWarningCallback`을 구현하고 Aspose.Words가 발생시키는 각 경고에 대해 `WarningInfo` 객체를 받습니다.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**설명:**  
- `info.Type`은 경고의 카테고리를 알려줍니다. 우리는 `WarningType.FontSubstitution`에 관심이 있습니다. 이것이 누락된 폰트를 나타냅니다.  
- `info.Description`에는 *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* 와 같은 사람이 읽을 수 있는 메시지가 들어 있습니다.  
- `Console.WriteLine`에 기록함으로써 **경고를 즉시 로그**합니다. 실제 애플리케이션에서는 `ILogger`, 파일 라이터, 혹은 텔레메트리 서비스로 교체할 수 있습니다.

> **프로 팁:** 나중에 보고하기 위해 모든 누락된 폰트를 수집해야 한다면, 출력 대신 `info.Description`을 `List<string>`에 저장하세요.

## Step 3: Load the Document Using the Configured LoadOptions  

콜백이 설정되면, 문서를 로드할 때 폰트가 누락될 경우 자동으로 핸들러가 호출됩니다.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**출력 예시:**  
프로그램을 실행하면 다음과 유사한 내용이 콘솔에 표시됩니다.

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

이 라인은 **누락된 폰트를 성공적으로 감지**했으며, 이제 **실시간으로 누락된 폰트를 추적**하고 있음을 확인시켜 줍니다.

## Step 4: Verify the Handler Works with Different Scenarios  

핸들러가 DOCX 파일에만 작동한다고 생각하기 쉽지만, Aspose.Words는 다양한 형식을 지원합니다. 임베디드 폰트를 참조하는 PDF나 오래된 `.doc` 파일을 로드해 보세요. 폰트 해석 파이프라인을 통과하는 모든 형식에서 동일한 콜백이 발생합니다.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

PDF가 설치되지 않은 폰트를 참조하면 동일한 콘솔 출력이 나타납니다. 이는 **폰트 경고 핸들러** 솔루션이 형식에 구애받지 않음을 보여줍니다.

## Step 5: Extending the Handler – Logging to a File  

콘솔 출력은 데모에 편리하지만, 실제 코드에서는 보통 로그 파일에 기록합니다. 간단히 수정해 보세요.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

이제 폰트가 교체될 때마다 메시지가 `font-warnings.log`에 추가됩니다. 이는 **경고를 로그하는 방법**을 충족시키며 영구적인 감사 기록을 제공합니다.

## Step 6: Putting It All Together – Full, Runnable Example  

아래는 콘솔 앱에 복사·붙여넣기 할 수 있는 완전한 프로그램입니다. 누락된 부분은 없으며, 파일 경로만 자신의 문서에 맞게 바꾸면 됩니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**예상 결과:**  

- 콘솔에 각 교체 라인이 출력됩니다.  
- `font-warnings.log`에 타임스탬프와 함께 모든 누락된 폰트 이벤트가 기록됩니다.  
- `output.pdf` 파일이 교체된 폰트를 사용해 생성되며, 원본 폰트가 없어도 변환이 성공합니다.

## Common Questions & Edge Cases  

| Question | Answer |
|----------|--------|
| *특정 폰트를 무시하고 싶다면?* | `Warning` 내부에서 `info.Description`에 폰트 이름을 확인하고, 해당 폰트가 허용되는 경우 `return;`으로 조기에 종료합니다. |
| *임베디드 폰트에도 핸들러가 작동하나요?* | 아니요—임베디드 폰트는 문서에 항상 포함되어 있으므로 교체 경고가 발생하지 않습니다. |
| *다른 경고 유형(예: 이미지 해상도 문제)도 캡처할 수 있나요?* | 물론입니다. `if (info.Type == WarningType.FontSubstitution)` 조건을 제거하거나 `WarningType.ImageResolution` 등에 대한 추가 `if` 블록을 넣으세요. |
| *핸들러가 스레드‑안전한가요?* | 예시 구현은 파일에 동기화 없이 쓰므로 멀티스레드 환경에서는 파일 쓰기를 `lock`으로 감싸거나 동시 로거를 사용해야 합니다. |

## Next Steps  

이제 **누락된 폰트에 대한 경고를 로그**하는 방법을 알았으니, 다음과 같은 확장을 고려해 보세요:

- 배치 가져오기 과정에서 **누락된 폰트를 감지**하고 요약 보고서를 생성.  
- 여러 문서에 걸쳐 **누락된 폰트를 추적**하고 특정 폰트가 자주 나타날 때 이메일 알림 전송.  
- 모니터링 시스템(예: Azure Application Insights)과 **통합**하여 시간 경과에 따른 폰트 교체 추세를 시각화.  

이 모든 확장은 우리가 만든 `IWarningCallback` 기반 위에 구축됩니다.

---

*즐거운 코딩 되세요! 커스텀 폰트 폴더나 네트워크 공유 등 특수 상황에 부딪히면 아래에 댓글을 남겨 주세요. 커뮤니티와 제가 언제든지 여러분의 폰트 경고 전략을 미세 조정하도록 도와드리겠습니다.* 

![폰트 경고 핸들러 예시](image-placeholder.png "폰트 경고 핸들러 예시")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}