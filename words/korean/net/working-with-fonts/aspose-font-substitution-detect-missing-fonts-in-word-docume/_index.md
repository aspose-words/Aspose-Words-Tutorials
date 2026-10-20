---
category: general
date: 2026-04-05
description: Aspose 글꼴 대체 가이드를 통해 Word 문서를 로드할 때 누락된 글꼴을 감지하고, 글꼴 설정을 구성하여 누락된 글꼴을
  효율적으로 처리하는 방법을 배워보세요.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: ko
og_description: 'Aspose 글꼴 대체 가이드: Word 문서를 로드할 때 누락된 글꼴을 감지합니다. 글꼴 설정을 구성하고 누락된 글꼴을
  효율적으로 처리하는 방법을 배워보세요.'
og_title: Aspose 글꼴 대체 – Word 문서에서 누락된 글꼴 감지
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose 폰트 대체 – Word 문서에서 누락된 폰트 감지
url: /ko/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Word 문서에서 누락된 글꼴 감지

한 컴퓨터에서는 완벽하게 보이던 Word 파일이 다른 컴퓨터에서는 이상한 글꼴 변경이 나타난 적이 있나요? 그것이 바로 클래식한 **aspose font substitution** 문제이며, 일반적으로 대상 시스템에 일부 글꼴이 없다는 의미입니다. 이 튜토리얼에서는 **Word 문서를 로드할 때 누락된 글꼴을 감지하는 방법**, **글꼴 설정을 구성하는 방법**, 그리고 **누락된 글꼴을 우아하게 처리하는 방법**을 단계별로 보여드립니다.

전체 실행 가능한 C# 예제를 단계별로 살펴보고, 각 라인이 왜 중요한지 설명하며, 기대되는 콘솔 출력도 보여드립니다. 끝까지 읽으면 문서가 로드되는 순간 글꼴 대체를 즉시 파악할 수 있게 됩니다—추측이 필요 없습니다.

## 배울 내용

- Aspose.Words의 글꼴 경고 진단 컬렉터를 활성화하는 방법.  
- 맞춤 **font settings**를 사용하여 **Word 문서를 로드**하는 데 필요한 정확한 코드.  
- `WarningInfo` 객체를 반복하여 모든 대체된 글꼴을 나열하는 방법.  
- 원치 않는 경고를 억제하거나 대체 글꼴을 제공하기 위한 팁.  
- Visual Studio에 복사‑붙여넣기 할 수 있는 바로 실행 가능한 샘플.

### 전제 조건

- .NET 6.0 이상 (API는 .NET Framework에서도 동일하게 작동합니다).  
- Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`).  
- 설치되지 않은 글꼴을 참조하는 Word 파일 (예: `MissingFont.docx`).  

위 조건을 갖추셨다면, 시작해봅시다.

## Step 1 – 진단 컬렉터 활성화 (Font Settings 구성)

먼저, Aspose.Words는 명시적으로 설정하면 글꼴 대체 경고를 기록합니다. 이는 `FontSettings` 객체를 생성하고 이를 `LoadOptions` 인스턴스에 할당함으로써 이루어집니다. 글꼴 처리를 위한 “디버그 라이트”를 켜는 것과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**왜?**  
`FontSettings` 객체가 없으면 경고 컬렉터가 조용히 동작하며, 어떤 글꼴이 교체되었는지 알 수 없습니다. 빈 객체를 초기화함으로써 Aspose가 기본 시스템 글꼴을 사용하도록 하고 *또한* 모든 대체를 추적하도록 합니다.

> **Pro tip:** 특정 폴더에 회사 글꼴이 들어있다면 `SetFontsFolder("path")` 로 `FontSettings`에 지정하세요. 이렇게 하면 누락된 글꼴 경고 수를 줄일 수 있습니다.

## Step 2 – 구성된 옵션으로 문서 로드 (Word 문서 로드)

컬렉터가 활성화되었으니, 동일한 `LoadOptions`를 사용해 `.docx` 파일을 로드합니다. 이때 Aspose가 문서를 스캔하고 모든 글꼴 참조를 확인하여 대체가 필요한지 판단합니다.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**왜 중요한가요?**  
단순히 `new Document("MissingFont.docx")`를 호출하면 기본 설정이 적용되고 *경고 목록은 비어* 있습니다. `loadOptions`를 전달하면 진단 컬렉터가 로드 파이프라인에 연결됩니다.

## Step 3 – 글꼴 대체 경고 가져오기 및 표시 (누락된 글꼴 감지)

문서가 메모리에 로드된 후, Aspose는 모든 경고를 `document.WarningCallback.Warnings`에 저장합니다. 해당 컬렉션을 순회하면서 `WarningType.FontSubstitution`을 필터링하고 설명을 출력합니다. 각 설명은 어떤 글꼴이 누락되었고 대신 어떤 글꼴이 사용되었는지를 알려줍니다.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Expected console output**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

이 출력은 코드를 실행한 머신에서 정확히 어떤 글꼴이 누락되었는지를 알려줍니다. 이제 누락된 글꼴을 설치할지, 문서에 포함시킬지, 혹은 대체 상태를 유지할지 결정할 수 있습니다.

![aspose 글꼴 대체 경고를 보여주는 콘솔 출력](/images/aspose-font-substitution-console.png)

*이미지 대체 텍스트:* aspose 글꼴 대체 – 대체된 글꼴을 나열한 콘솔 출력

## Step 4 – 선택 사항: 대체 동작 사용자 정의 (누락된 글꼴 처리)

때때로 단순히 *대체가 발생했다*는 사실만 알면 충분하지 않고, *어떻게* 대체되는지를 제어하고 싶을 때가 있습니다. Aspose.Words는 사용자 정의 `IFontSubstitutionRule`을 등록할 수 있게 합니다. 아래 예시는 누락된 모든 글꼴을 `Tahoma`로 강제 대체하도록 합니다.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**언제 사용하나요?**  
웹 서비스용 PDF를 생성하고 모든 클라이언트가 `Tahoma`를 렌더링할 수 있다는 것을 안다면, 강제 대체를 통해 수십 개의 글꼴 파일을 배포하지 않아도 시각적 일관성을 보장할 수 있습니다.

## 전체 작업 예제 (모든 단계 결합)

새 콘솔 프로젝트에 붙여넣을 수 있는 전체 프로그램입니다. Aspose.Words NuGet 패키지를 설치했다고 가정하면 그대로 컴파일됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

프로그램을 실행하고 콘솔을 확인하면 모든 누락된 글꼴 이벤트가 출력되는 것을 볼 수 있습니다. 이를 통해 누락된 글꼴을 설치할지, 포함시킬지, 혹은 대체 상태를 유지할지 결정할 수 있습니다.

## 자주 묻는 질문

**Q: PDF 변환에도 적용되나요?**  
네. 나중에 `doc.Save("output.pdf")`를 호출하면 로드 중에 대체된 모든 글꼴이 PDF에 포함됩니다. 따라서 경고를 미리 포착하면 최종 PDF에서 예상치 못한 글꼴 변경을 방지할 수 있습니다.

**Q: 처리할 문서가 많다면 어떻게 해야 하나요?**  
로드 로직을 try‑catch 블록으로 감싸고 여러 문서에 걸쳐 단일 `FontSettings` 인스턴스를 재사용하세요. 이렇게 하면 오버헤드가 줄어들고 각 파일에 대해 경고 컬렉터가 활성화됩니다.

**Q: 경고를 완전히 억제할 수 있나요?**  
로드하기 전에 `loadOptions.WarningCallback = null;` 로 설정할 수 있지만, **누락된 글꼴을 감지**하는 기능을 잃게 됩니다—대부분의 경우 원하지 않는 동작입니다.

## 결론

우리는 **aspose font substitution**을 마스터하기 위해 필요한 모든 내용을 다루었습니다: 진단 컬렉터 활성화, 맞춤 **font settings**로 Word 파일 로드, 누락된 글꼴 목록 추출, 그리고 기본 대체 규칙을 재정의하여 **누락된 글꼴을 직접 처리**하는 방법까지. 몇 줄의 C# 코드만으로도 미묘한 레이아웃 변화 뒤에 숨겨진 글꼴 문제를 완전히 파악할 수 있습니다.

다음 단계는? `FontSettings.SetFontsFolder`를 사용해 원본 글꼴을 문서에 포함시키거나 `FontSourceBase`를 탐색해 데이터베이스에서 글꼴을 로드해 보세요. 또한 `Document.BuiltInStyle` 컬렉션을 실험해 스타일 수준의 글꼴 변경이 어떻게 전파되는지 확인할 수 있습니다.

Aspose.Words나 글꼴 관리에 대해 더 궁금한 점이 있나요? 댓글을 남기거나 공식 Aspose 문서를 살펴보거나 새로운 프로젝트를 시작해 위 코드를 직접 실험해 보세요. 즐거운 코딩 되시고, 문서가 항상 의도한 대로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}