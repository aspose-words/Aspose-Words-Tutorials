---
category: general
date: 2026-03-22
description: Aspose.Words를 사용하여 Word 문서를 저장하고 누락된 글꼴을 감지합니다. C#에서 누락된 글꼴을 추적하고 글꼴
  오류를 포착하는 방법을 배워보세요.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: ko
og_description: C#에서 Word 문서를 저장하고 누락된 글꼴을 감지합니다. 이 가이드는 누락된 글꼴을 추적하고 경고 콜백을 사용하여
  글꼴 오류를 캡처하는 방법을 보여줍니다.
og_title: Word 문서 저장 – Aspose.Words로 누락된 글꼴 감지
tags:
- Aspose.Words
- C#
- Document Processing
title: Word 문서 저장 – Aspose.Words로 누락된 글꼴 감지
url: /ko/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서 저장 – Aspose.Words로 누락된 글꼴 감지

문서를 **save word document** 해야 하는데 내부 글꼴 중 일부가 라운드‑트립을 견딜 수 있을지 확신이 없었던 적이 있나요? 생각보다 자주 발생합니다. 특히 서로 다른 글꼴 라이브러리를 가진 컴퓨터 간에 문서를 주고받을 때 그렇습니다. 좋은 소식은? Aspose.Words는 **save word document** 하는 동안 **detect missing fonts** 할 수 있는 내장 기능을 제공하므로, 파일이 사용자 화면에 나타나기 전에 로그를 남기거나 경고를 표시하거나 교체할 수 있습니다.

이 튜토리얼에서는 Word 문서를 저장할 뿐만 아니라 **tracks missing fonts**와 **captures font errors**를 사용자 정의 경고 핸들러로 처리하는 완전한 실행 예제를 단계별로 살펴봅니다. 끝까지 읽으면 경고 콜백이 왜 중요한지, 어떻게 연결하는지, 대체가 발생했을 때 콘솔에 어떤 출력이 나타나는지 정확히 알 수 있습니다. 별도 부가 설명 없이 바로 .NET 프로젝트에 복사해 사용할 수 있는 코드만 제공합니다.

> **Prerequisites**  
> • .NET 6 (또는 최신 .NET Framework) 설치  
> • Visual Studio 2022 또는 선호하는 IDE  
> • **Aspose.Words for .NET** 라이선스 사본 (무료 체험판으로 테스트 가능)  

위 조건을 갖췄다면, 시작해봅시다.

---

## Word 문서 저장 및 누락된 글꼴 감지

핵심 아이디어는 간단합니다: `Document.Save`를 호출하기 전에 `IWarningCallback`을 구현한 객체를 `Document.WarningCallback`에 할당합니다. Aspose.Words는 발견한 모든 경고에 대해 이 객체를 호출하는데, 여기에는 시스템에 해당 글꼴이 없을 때 발생하는 **font substitution** 경고도 포함됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**What you’ll see:**  
`input.docx`가 설치되지 않은 글꼴을 참조하면 콘솔에 다음과 같은 내용이 출력됩니다:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

이 라인은 어떤 글꼴이 누락되었고 Aspose.Words가 대신 사용한 글꼴이 무엇인지 정확히 알려주므로, 파일을 배포하기 전에 **capturing font errors** 하는 데 최적입니다.

---

## Warning Callback으로 누락된 글꼴 추적 (Step‑by‑Step)

### 1️⃣ Install Aspose.Words

프로젝트의 NuGet 콘솔을 열고 다음 명령을 실행합니다:

```bash
dotnet add package Aspose.Words
```

이 명령은 최신 안정 버전(현재 24.10)을 가져옵니다. 라이브러리를 최신 상태로 유지하면 최신 **detect missing fonts** 기능과 버그 수정 혜택을 받을 수 있습니다.

### 2️⃣ Define the Warning Handler

왜 별도의 클래스를 만들어야 할까요? `IWarningCallback`을 구현하면 모든 경고 로직을 한 곳에 집중시킬 수 있습니다. 파일에 로그를 남기거나, 텔레메트리를 전송하거나, 누락된 글꼴이 워크플로우에 치명적인 경우 예외를 발생시킬 수도 있습니다.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** 여러 문서에서 **track missing fonts** 해야 한다면, 핸들러 내부에 `List<string>`을 두고 메시지를 수집한 뒤 나중에 보고용으로 노출하면 편리합니다.

### 3️⃣ Load Your Source Document

`Document` 생성자는 파일 경로, 스트림, 혹은 원시 바이트 배열을 받을 수 있습니다. 대부분의 경우 사용자가 업로드했거나 다른 시스템에서 받은 `.docx` 파일을 지정하면 됩니다.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

파일이 크다면 `LoadOptions`를 활용해 지연 로딩을 활성화하면 메모리 사용량을 줄일 수 있습니다.

### 4️⃣ Attach the Callback

인스턴스를 `doc.WarningCallback`에 할당합니다. 이제부터 발생하는 모든 경고(글꼴 대체 포함)는 이 핸들러를 통해 전달됩니다.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Save the Document

이제 안심하고 `Save`를 호출하면 됩니다. 경고 핸들러는 저장 작업 중 **synchronously** 실행되므로 콘솔 출력이 즉시 나타납니다.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

다른 형식(PDF, HTML 등)으로 저장하고 싶다면 동일한 경고 메커니즘이 작동합니다—변환 전에 Aspose.Words가 누락된 글꼴을 보고합니다.

---

## Font Errors 캡처 – 일반적인 엣지 케이스

기본 흐름만으로도 대부분의 상황을 커버하지만, 실제 프로젝트에서는 몇 가지 트러블이 발생할 수 있습니다. 아래에 흔히 마주치는 변형 사례와 해결 방법을 정리했습니다.

### Missing Font in a Header/Footer

헤더와 푸터는 별도 노드이지만, 경고 시스템은 본문 텍스트와 동일하게 처리합니다. 추가 코드 없이도 콜백이 해당 글꼴에 대해 호출됩니다. 전체 문서를 로드했는지 확인하세요(기본 동작이 이를 보장합니다).

### Multiple Substitutions in One Document

문서에 여러 알 수 없는 글꼴이 사용된 경우, 핸들러는 대체마다 한 번씩 호출됩니다. 콘솔이 과도하게 출력되는 것을 방지하려면 메시지를 중복 제거할 수 있습니다:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Turning Warnings into Exceptions

때때로 누락된 글꼴은 작업을 중단시켜야 할 정도로 심각합니다. 핸들러 내부에서 예외를 발생시켜 저장을 중단할 수 있습니다:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

`doc.Save`를 `try/catch` 블록으로 감싸서 예외를 우아하게 처리하는 것을 잊지 마세요.

---

## 결과 확인 – 기대되는 모습

저장이 완료된 후 `output.docx`를 Microsoft Word(또는 호환 뷰어)에서 엽니다. 원본과 동일한 레이아웃이 유지되지만, 콘솔에 표시된 대체 글꼴이 폴백 글꼴로 적용된 것을 확인할 수 있습니다. 추가로 확인하려면 다음을 수행하세요.

1. **File → Options → Advanced → Show document content → Use draft quality**를 열어 Word가 숨겨진 글꼴 대체를 표시하도록 강제합니다.  
2. Word의 **Replace Fonts** 대화상자(`Ctrl+Shift+F`)를 사용해 실제로 포함된 글꼴을 확인합니다.

모든 것이 일치한다면 **saved word document**를 성공적으로 수행하면서 **detecting missing fonts**와 **capturing font errors**를 모두 구현한 것입니다. 🎉

---

## 전체 작업 예제 (복사‑붙여넣기 바로 사용)

아래 코드는 새 콘솔 앱 프로젝트에 바로 넣을 수 있는 전체 프로그램입니다. `YOUR_DIRECTORY`를 실제 폴더 경로로 교체하면 됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Expected console output** (example):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

이것이 전부입니다—숨겨진 단계도 없고, 찾아볼 외부 문서도 없습니다.

---

## 결론

이번 글에서는 Aspose.Words의 warning callback을 활용해 **save word document**하면서 **detect missing fonts**, **track missing fonts**, **capture font errors**를 적극적으로 수행하는 방법을 보여드렸습니다. 작은 `IWarningCallback` 구현만으로 저장 시점에 글꼴 대체 상황을 완전히 파악할 수 있어, 로그를 남기거나 교체하거나 작업을 중단하는 등 원하는 조치를 취할 수 있습니다.

다음 단계에 도전해 보시겠어요? 핸들러를 확장해 경고를 구조화된 JSON 로그로 기록하거나, Aspose.PDF와 결합해 같은 문서를 변환하면서 글꼴 정보를 보존해 보세요. 또한 `LoadOptions.FontSettings`를 이용해 누락된 글꼴을 직접 출력 파일에 임베드하는 방법도 있습니다.

코드를 직접 실행해 보고 파이프라인에 맞게 조정한 뒤, 사용 경험을 알려 주세요. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}