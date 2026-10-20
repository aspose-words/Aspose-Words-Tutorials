---
category: general
date: 2026-06-30
description: LoadOptions를 사용하여 .NET에서 글꼴을 로드하는 방법을 배우고, 글꼴 설정을 지정하며, 사용자 정의 글꼴을 활성화하고,
  경고 콜백으로 누락된 글꼴을 감지합니다.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: ko
og_description: .NET에서 폰트를 로드하는 방법은? 이 가이드는 폰트 설정을 지정하고, 사용자 정의 폰트를 활성화하며, 경고 콜백을
  통해 누락된 폰트를 감지하는 방법을 보여줍니다.
og_title: .NET에서 폰트 로드하는 방법 – 폰트 설정 및 경고
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: .NET에서 글꼴 로드하는 방법 – 글꼴 설정 및 경고
url: /ko/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# .NET에서 글꼴 로드하기 – 글꼴 설정 및 경고

.NET 문서에서 **글꼴을 로드하는 방법**을 고민해 본 적 있나요? 혼자만 그런 것이 아닙니다. 누락된 글리프, 조용히 대체되는 폰트, 그리고 이해하기 어려운 경고는 간단한 보고서 생성기를 악몽으로 만들 수 있습니다.  

이 튜토리얼에서는 **글꼴을 로드하는 방법**, **글꼴 설정** 구성, **사용자 정의 글꼴 활성화**, 그리고 경고를 처리하여 **누락된 글꼴 감지**하는 완전한 실행 예제를 단계별로 살펴봅니다. 끝까지 따라오시면 Aspose.Words 또는 유사 라이브러리 프로젝트에 바로 적용할 수 있는 견고한 패턴을 얻을 수 있습니다.

> **빠른 살펴보기:** `LoadOptions` 객체를 만들고, 경고 콜백을 연결한 뒤, 의도적으로 누락된 글꼴을 참조하는 DOCX를 로드합니다. 엔진이 글꼴을 대체할 때마다 콘솔에 명확한 메시지가 출력됩니다.

## 필요 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 작동합니다)  
- Aspose.Words for .NET (무료 체험 NuGet 패키지 사용 가능)  
- 설치되지 않은 글꼴을 참조하는 DOCX 파일 (예: `MissingFont.docx`)  

그것만 있으면 됩니다—추가 서비스나 복잡한 설정 파일은 필요 없습니다. 위 세 가지가 준비되었다면 바로 따라하실 수 있습니다.

![글꼴 로드 예제 다이어그램](https://example.com/how-to-load-fonts-diagram.png)

*Image alt text: 글꼴 로드 예제 다이어그램*

## 단계 1: Load Options 생성 및 사용자 정의 글꼴 설정 활성화  

글꼴 설정을 **설정**하려면 먼저 `LoadOptions` 객체를 인스턴스화합니다. 그 안에 사용자 정의 `.ttf` 또는 `.otf` 파일이 들어 있는 폴더를 가리키는 `FontSettings` 인스턴스를 배치합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**왜 중요한가:** 기본적으로 Aspose.Words는 시스템에 설치된 글꼴만 검색합니다. 네트워크 공유에 있는 기업 브랜드 글꼴을 사용한다면, 라이브러리에게 해당 위치를 알려줘야 합니다. 이것이 **사용자 정의 글꼴 활성화**의 핵심입니다.

## 단계 2: 경고 핸들러 연결하여 누락된 글꼴 감지  

경고 처리를 생략하면 누락된 글리프가 조용히 대체 글꼴(대부분 Times New Roman)로 교체됩니다. 이는 브랜드 일관성을 해치거나 레이아웃이 어긋날 수 있습니다. **경고를 처리하는 방법**을 보여주기 위해 `WarningType.FontSubstitution`을 검사하는 콜백을 연결합니다.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**프로 팁:** `WarningCallback`은 *모든* 경고에 대해 호출됩니다. `WarningType.FontSubstitution`으로 필터링하면 출력이 깔끔해지고 **누락된 글꼴 감지**라는 질문에 직접 답할 수 있습니다.

## 단계 3: 구성된 옵션을 사용하여 문서 로드  

옵션을 준비했으니 이제 **글꼴을 로드하는 방법**대로 문서를 로드합니다. `Document` 생성자는 파일 경로와 방금 만든 `LoadOptions`를 인수로 받습니다.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

소스 파일이 시스템 폴더 *또는* 앞서 지정한 사용자 정의 폴더에 없는 글꼴을 참조하면, 2단계에서 만든 경고 콜백이 콘솔에 유용한 라인을 출력합니다.

## 단계 4: 로드된 글꼴 집합 확인 (선택 사항이지만 유용함)  

때때로 실제로 어떤 글꼴이 해결되었는지 다시 확인하고 싶을 때가 있습니다. Aspose.Words는 전달한 `FontSettings`를 노출하므로, 해결된 글꼴 소스를 열거할 수 있습니다.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

로드 후 이 스니펫을 실행하면 다음과 같은 출력이 나타납니다:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

경고 라인은 우리가 **누락된 글꼴을 감지**했음을 확인시켜 주고, 리스트는 시스템 폴더와 사용자 정의 폴더 모두가 검색되었음을 보여줍니다.

## 단계 5: 문서 저장 또는 렌더링  

문서를 로드하고 글꼴을 확인했으면 이제 원하는 처리를 진행할 수 있습니다—PDF로 저장, 이미지로 렌더링, 혹은 DOM 조작 등. 완전성을 위해 결과를 PDF로 저장하는 한 줄 코드를 보여드립니다:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

PDF를 열면, 누락된 글리프가 콘솔 출력에서 본 대체 글꼴로 교체된 것을 확인할 수 있습니다. `C:\MyCustomFonts`에 누락된 글꼴을 추가하고 프로그램을 다시 실행하면 경고가 사라집니다—이는 **사용자 정의 글꼴 활성화**가 실제로 작동한다는 증거입니다.

---

## 전체 작업 예제

아래 전체 블록을 새 콘솔 프로젝트에 복사하고 Aspose.Words NuGet 패키지를 추가한 뒤 **Run**을 클릭하세요. 파일 경로는 환경에 맞게 조정하십시오.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### 예상 출력

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

누락된 `Papyrus.ttf` 파일을 `C:\MyCustomFonts`에 넣고 프로그램을 다시 실행하면 경고 라인이 사라져, 사용자 정의 폴더가 올바르게 검색되었음을 확인할 수 있습니다.

---

## 일반적인 질문 및 주의사항

| 질문 | 답변 |
|------|------|
| **경고 콜백이 없으면 어떻게 되나요?** | 문서는 여전히 로드되지만 대체가 언제 발생했는지 알 수 없습니다. 콜백을 추가하는 것이 **경고를 처리하는 방법** 중 가장 간단합니다. |
| **ZIP 파일에서 글꼴을 로드할 수 있나요?** | 예—`new FolderFontSource(zipPath, true)`를 사용하거나 사용자 정의 `IFontSource`를 구현하세요. 이는 여전히 **사용자 정의 글꼴 활성화**에 해당합니다. |
| **PDF에 글꼴을 포함해야 하나요?** | 저장 전에 `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;`를 설정하세요. 글꼴 포함은 PDF가 어떤 기기에서도 동일하게 보이도록 보장합니다. |
| **문서가 라이선스가 있어 재배포할 수 없는 글꼴을 사용할 경우는?** | 경고를 통해 *누락된 글꼴을 감지*할 수는 있지만, 권한이 없으면 포함해서는 안 됩니다. 비슷한 오픈소스 글꼴로 대체하는 것을 고려하세요. |

---

## 요약

우리는 .NET에서 **글꼴을 로드하는 방법**을 다음과 같이 정리했습니다:

1. `LoadOptions`를 생성하고 **글꼴 설정**을 구성합니다.  
2. 폴더를 지정하여 **사용자 정의 글꼴 활성화**합니다.  
3. `WarningCallback`을 사용해 **경고를 처리하는 방법**을 구현하고, 글꼴 대체 메시지를 출력합니다.  
4. `WarningType.FontSubstitution`을 필터링하여 **누락된 글꼴 감지**를 수행합니다.  
5. 문서를 저장하고, 대체가 정상적으로 이루어졌는지 확인합니다.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 다룬 기술을 확장하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [시스템 및 사용자 정의 폴더에 글꼴 폴더 설정](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [Aspose.Words에서 글꼴 감지 – 경고 및 설정 처리](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Aspose.Words에서 글꼴 캡처 – 완전 가이드](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}