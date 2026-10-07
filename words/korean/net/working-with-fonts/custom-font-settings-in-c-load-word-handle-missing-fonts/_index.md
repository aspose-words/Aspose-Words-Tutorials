---
category: general
date: 2026-03-08
description: 맞춤 글꼴 설정을 사용하면 글꼴을 지정하고 Word 문서를 안전하게 로드하며 Aspose.Words로 누락된 글꼴을 처리할
  수 있습니다.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: ko
og_description: 맞춤 글꼴 설정을 사용하면 글꼴을 지정하고 Word 문서를 안전하게 로드하며 Aspose.Words로 누락된 글꼴을 처리할
  수 있습니다.
og_title: C#에서 사용자 정의 폰트 설정 – Word 로드 및 누락된 폰트 처리
tags:
- Aspose.Words
- C#
- Font Management
title: C#에서 사용자 정의 글꼴 설정 – Word 로드 및 누락된 글꼴 처리
url: /ko/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 사용자 정의 글꼴 설정 – Word 로드 및 누락된 글꼴 처리

Word 파일이 설치되지 않은 글꼴을 참조할 때 **custom font settings**가 어떻게 작동하는지 궁금한 적 있나요? 흔히 겪는 문제로, 한 컴퓨터에서는 문서가 정상적으로 보이지만 다른 컴퓨터에서는 모든 단락이 갑자기 대체 글꼴로 바뀝니다.  

좋은 소식은? Aspose.Words를 사용하면 **set font settings**, **load Word document** 내용을 한 번에 깔끔하게 처리하고 **handle missing fonts**도 할 수 있습니다. 아래에 정확히 어떻게 하는지 보여주는 완전한 실행 가능한 예제와 각 단계의 이유를 제공합니다.

## 배울 내용

이 가이드에서는 다음을 다룹니다:

* `LoadOptions` 객체를 생성하고 `FontSettings` 인스턴스를 연결하기.  
* 경고 콜백을 등록하여 어떤 글꼴이 대체되는지 확인하기.  
* 누락된 글꼴이 있을 수 있는 DOCX 파일을 로드하고, 대체 세부 정보를 콘솔에 출력하기.  

끝까지 읽으면 모든 누락된 글꼴 상황이 로그에 기록되고 나중에 처리할 수 있음을 알고 C# 앱을 자신 있게 배포할 수 있습니다.

> **전제 조건:** NuGet을 통해 설치된 Aspose.Words for .NET (v23.12 이상) 및 C# 콘솔 앱에 대한 기본적인 이해.

---

## 사용자 정의 글꼴 설정 – LoadOptions 구성

먼저 필요한 것은 `LoadOptions` 객체입니다. 이는 Aspose.Words에 들어오는 파일을 어떻게 처리할지 알려줍니다. 새 `FontSettings` 인스턴스를 할당함으로써 라이브러리에게 사용자 정의 글꼴을 찾을 위치를 지정합니다.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**왜 중요한가:**  
`FontSettings`를 생략하면 Aspose.Words는 시스템 기본 글꼴 컬렉션으로 대체합니다. 이는 누락된 글꼴이 조용히 대체되어 어떤 글꼴이 교체됐는지 알 수 없게 됩니다. 명시적인 `FontSettings` 컨테이너를 만들면 검색 과정을 완전히 제어할 수 있습니다.

## LoadOptions에 글꼴 설정 적용

이제 `FontSettings` 객체가 있으니, 이를 어디에 지정해야 할지 궁금할 수 있습니다. 일반적으로 애플리케이션과 함께 제공하는 글꼴이 들어 있는 폴더를 추가합니다:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*개인 폴더가 없으면 이 블록을 생략해도 됩니다—Aspose.Words는 여전히 경고 콜백을 통해 누락된 글꼴을 보고합니다.*

**팁:** 글꼴이 하위 폴더에 흩어져 있다면 `recursive: true` 플래그를 사용하세요. 각 경로를 수동으로 추가하는 번거로움을 줄여줍니다.

## 사용자 정의 글꼴 설정으로 Word 문서 로드

옵션을 준비했으니, 문서 로드는 아주 간단합니다. `Document` 생성자는 파일 경로와 방금 만든 `LoadOptions`를 받아들입니다.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**내부에서 무슨 일이 일어나나요?**  
Aspose.Words는 DOCX를 파싱하고 모든 `<w:font>` 참조를 확인한 뒤, 제공한 `FontSettings`를 참조합니다. 글꼴을 찾지 못하면 `FontSubstitution` 유형의 경고를 발생시킵니다. 다음에 보여줄 사용자 정의 핸들러가 이러한 경고를 잡아냅니다.

## 경고 콜백으로 누락된 글꼴 처리

`IWarningCallback` 인터페이스를 사용하면 로드 중 발생하는 모든 문제에 대응할 수 있습니다. 구현은 간단합니다:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

문서가 로드될 때, 누락된 각 글꼴은 다음과 같은 줄을 생성합니다:

```
Font substituted: Arial -> Liberation Sans
```

**왜 로그를 남겨야 할까요:**  
프로덕션 환경에서는 이러한 메시지를 파일이나 텔레메트리 시스템으로 전달해 어떤 글꼴을 번들에 포함하거나 라이선스를 받아야 하는지 쉽게 파악할 수 있습니다.

## 전체 작동 예제

아래는 모든 요소를 연결한 독립 실행형 콘솔 프로그램입니다. 새 .NET Core 콘솔 프로젝트에 복사·붙여넣기하고 **Run**을 클릭하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**예상 출력** (`input.docx`가 없는 글꼴을 사용한다고 가정할 때):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

모든 글꼴이 존재한다면 최종 확인 줄만 표시됩니다.

## 일반적인 질문 및 엣지 케이스

| Question | Answer |
|----------|--------|
| **PDF에 누락된 글꼴을 포함해야 하면 어떻게 해야 하나요?** | 로드 후 `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";`을 호출하고, `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`으로 임베딩을 활성화합니다. |
| **경고를 로그 대신 억제할 수 있나요?** | 예—`loadOptions.WarningCallback = null;`로 설정하거나, 콜백을 구현해 글꼴이 아닌 경고를 무시하도록 합니다. |
| **`.doc` 및 `.rtf` 파일에서도 작동하나요?** | 물론입니다. 동일한 `LoadOptions` 객체가 Aspose.Words가 지원하는 모든 형식에 적용됩니다. |
| **콜백이 스레드‑안전한가요?** | 콜백은 문서를 로드하는 동일한 스레드에서 실행되므로 콘솔에 안전하게 출력할 수 있습니다. 다중 스레드 환경에서는 동시 컬렉션이나 로깅 프레임워크를 사용하세요. |

## 팁 및 함정

* **팁:** 대상 머신에 설치되지 않은 글꼴을 배포한다면, `SetFontsFolder`에 전달하는 폴더에 추가하세요. 이렇게 하면 결정적인 렌더링을 보장합니다.  
* **라이선스 주의:** 일부 글꼴은 임베딩을 위해 상업적 라이선스가 필요합니다. 번들에 포함하기 전에 반드시 글꼴의 EULA를 확인하세요.  
* **성능 참고:** 대량의 글꼴 라이브러리를 로드하면 문서 파싱이 느려질 수 있습니다. 폴더를 가볍게 유지하고 실제로 필요한 글꼴만 포함하세요.  
* **엣지 케이스:** 문서가 글꼴을 패밀리 이름이 아닌 *PostScript name*으로 참조할 경우, 검색 경로에 글꼴 파일이 있으면 Aspose.Words가 여전히 해결합니다.

## 결론

이제 C#에서 **custom font settings**를 사용하는 완전하고 프로덕션 준비된 패턴을 갖추었습니다. `LoadOptions`를 구성하고, 경고 콜백을 등록하며, 필요에 따라 개인 글꼴 폴더를 지정함으로써 **set font settings**, **load Word document** 내용을 안정적으로 처리할 수 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}