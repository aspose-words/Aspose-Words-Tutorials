---
category: general
date: 2026-06-24
description: Aspose.Words 문서에서 누락된 글꼴을 감지하기 위해 IWarningCallback을 사용하는 방법. 전체 실행 가능한
  예제와 모범 사례를 배워보세요.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: ko
og_description: Aspose.Words에서 누락된 글꼴을 감지하기 위해 IWarningCallback을 사용하는 방법. 완전하고 프로덕션에
  바로 적용 가능한 솔루션을 위한 단계별 가이드를 따라보세요.
og_title: IWarningCallback 사용 방법 – 누락된 글꼴 감지
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: IWarningCallback 사용 방법 – Aspose.Words로 누락된 글꼴 감지
url: /ko/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# IWarningCallback 사용 방법 – Aspose.Words에서 누락된 폰트 감지

Aspose.Words를 사용하고 DOCX 파일에서 **누락된 폰트 감지**가 필요할 때 **IWarningCallback**을 사용하는 방법은 필수적입니다. 이 가이드에서는 IWarningCallback을 사용하여 폰트 대체 경고를 포착하는 방법, 그 중요성, 그리고 경고를 캡처한 후 해야 할 일을 정확히 보여주는 완전한 복사‑붙여넣기 예제를 단계별로 안내합니다.

문서를 열었을 때 사용자 정의 폰트가 설치되지 않아 글자가 깨진 경험이 있다면 그 불편함을 잘 아실 겁니다. 이 튜토리얼을 마치면 이러한 문제를 프로그래밍 방식으로 감지하고, 로그에 기록하거나, 자동으로 대체 폰트를 적용하는 신뢰할 수 있는 방법을 갖게 됩니다.

## What You’ll Learn

- **IWarningCallback**의 목적과 사용 시점.  
- **누락된 폰트 감지** 이벤트만을 분리하는 사용자 정의 경고 수집기 구현 방법.  
- **LoadOptions**에 수집기를 연결하여 모든 문서 로드 시 모니터링하는 방법.  
- 출력 확인 및 엣지 케이스 처리(여러 누락 폰트, 무시되는 경고 등).  

### Prerequisites

- .NET 6.0 이상(.NET Framework 4.6+에서도 작동).  
- NuGet(`Install-Package Aspose.Words`)을 통해 설치된 Aspose.Words for .NET.  
- 머신에 존재하지 않는 폰트를 참조하는 DOCX 파일(예: `DocumentWithMissingFont.docx`).  

추가 라이브러리는 필요하지 않습니다—모든 것이 Aspose.Words 안에 포함되어 있습니다.

---

## How to Use IWarningCallback to Detect Missing Fonts in Aspose.Words

아래는 **전체 실행 가능한 프로그램**입니다. 새 콘솔 프로젝트에 복사하고 파일 경로를 조정한 뒤 실행하세요. 누락된 폰트 경고마다 콘솔에 출력이 표시됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

`DocumentWithMissingFont.docx`가 설치되지 않은 *“MyFancyFont”* 폰트를 참조하고 있다면 다음과 같은 출력이 나타납니다:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

**[Missing Font]** 로 시작하는 각 라인은 우리 **IWarningCallback** 구현에 의해 생성된 것으로, **누락된 폰트 감지**에 성공했음을 증명합니다.

---

## Step 1: Implement the IWarningCallback Interface

왜 사용자 정의 클래스를 만들어야 할까요? Aspose.Words는 파일 형식 문제, 사용 중단된 기능, 그리고 우리에게 가장 중요한 폰트 대체와 같은 다양한 이유로 **경고**를 발생시킵니다. `IWarningCallback`을 구현하면 경고가 발생할 때마다 호출되는 후크를 얻을 수 있습니다. `WarningType.FontSubstitution`을 필터링하면 폰트가 누락된 특정 상황만을 분리할 수 있습니다.

**Pro tip:** 진단을 위해 *모든* 경고를 캡처하고 싶다면 `if` 조건을 제거하고 `info.Type`을 모두 로그에 기록하면 됩니다.

---

## Step 2: Wire the Callback into LoadOptions

`LoadOptions`는 Aspose.Words에 들어오는 문서를 어떻게 처리할지 알려주는 관문입니다. `WarningCallback`을 우리 수집기 인스턴스로 설정하면 로드 작업 전체에 걸쳐 콜백이 활성화됩니다. 동일한 `LoadOptions` 객체를 여러 문서에 재사용할 수 있어 배치 처리 파이프라인에 편리합니다.

**Common question:** *LoadOptions를 지정하지 않고 문서를 로드하면 어떻게 되나요?*  
답변: Aspose.Words는 내부적으로 여전히 경고를 발생시키지만 콜백이 없으면 조용히 무시되어 **누락된 폰트 감지** 기회를 잃게 됩니다.

---

## Step 3: Load a Document and Capture Missing Font Warnings

파일 경로와 `LoadOptions`를 받는 `Document` 생성자는 무거운 작업을 수행합니다. 파일이 파싱되는 동안 누락된 폰트가 발생하면 우리 `FontWarningCollector.Warning` 메서드가 호출됩니다. 콘솔 출력이 메커니즘이 정상 작동함을 증명합니다.

**Edge case:** 하나의 문서에 여러 누락 폰트가 있을 수 있습니다. 콜백은 누락된 폰트마다 한 번씩 호출되므로 여러 라인이 출력되어 포괄적인 보고서를 만들기에 적합합니다.

---

## Why Use IWarningCallback Instead of Manual Font Checks?

문서를 로드한 뒤 `Run.Font` 속성을 일일이 스캔하여 폰트를 확인할 수도 있지만, 폰트가 완전히 없을 경우 문서 자체가 로드되지 않아 실패합니다. 경고 시스템은 **대체가 이루어지기 전**에 작동하므로 실제 누락된 폰트를 정확히 파악할 수 있습니다.

또한 콜백은 로딩 파이프라인의 **일부**로 실행되므로, 조기에 작업을 중단하거나, 실시간으로 폰트를 교체하거나, 문서 트리를 추가로 탐색하지 않고도 상세 진단 정보를 로그에 남길 수 있습니다.

---

## Handling Multiple Missing Fonts Gracefully

많은 누락 폰트를 예상한다면 이를 컬렉션에 모아두는 것이 좋습니다:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

로드가 끝난 뒤 `MissingFonts`를 순회하면서 예를 들어 디자인 팀을 위해 CSV 파일에 기록할 수 있습니다.

---

## Bonus: Logging Warnings to a File

콘솔 출력은 데모에 적합하지만, 실제 서비스에서는 영구 저장소에 로그를 남기는 것이 일반적입니다. `Console.WriteLine` 호출을 다음과 같이 교체하세요:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

이제 나중에 검토할 수 있는 감사 로그가 생성되어 컴플라이언스 요구사항을 충족합니다.

---

## Conclusion

우리는 **IWarningCallback**을 사용해 **누락된 폰트 감지**를 수행하는 방법을 구현부터 `LoadOptions`에 연결하고 경고를 처리하는 전체 흐름을 다루었습니다. 이 접근 방식은 폰트 관련 문제를 실시간으로 파악하게 해 주어, 문서가 렌더링되기 전에 로그를 남기거나 폰트를 교체하거나 사용자에게 알림을 보낼 수 있습니다.

다음에 탐색해 볼 수 있는 단계:

- **Fallback fonts:** 대체가 발생할 때 기본 폰트를 프로그래밍 방식으로 지정.  
- **Batch processing:** 폴더에 있는 여러 문서를 순회하면서 동일한 `AggregatingFontCollector` 재사용.  
- **User feedback:** 콘솔 대신 UI에 누락 폰트 경고를 표시.

프로젝트에 직접 적용해 보세요—더 이상 알 수 없는 깨진 텍스트가 아니라 명확하고 실행 가능한 진단 정보를 얻을 수 있습니다. Happy coding!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하여 관련 주제를 심도 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [DOCX 로드 및 누락된 폰트 감지 – 완전한 C# 가이드](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Aspose.Words에서 폰트 감지 – 경고 및 설정 처리](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words에서 LoadOptions 사용 – 완전한 가이드](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}