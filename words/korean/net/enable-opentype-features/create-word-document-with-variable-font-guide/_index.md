---
category: general
date: 2026-03-19
description: Aspose.Words와 가변 폰트를 사용하여 Word 문서를 만들고, C#에서 글꼴 두께를 변경하고, 글꼴 너비를 설정하며,
  글꼴 변형을 정의하는 방법을 배웁니다.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: ko
og_description: Aspose.Words를 사용하여 가변 폰트가 적용된 Word 문서를 만드세요. 이 튜토리얼에서는 폰트를 로드하고, 폰트
  두께를 변경하며, 폰트 너비를 설정하고, 폰트 변형을 정의하는 방법을 보여줍니다.
og_title: 가변 폰트로 워드 문서 만들기 – 완전 가이드
tags:
- Aspose.Words
- C#
- Variable Font
title: 가변 폰트로 워드 문서 만들기 – 가이드
url: /ko/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 가변 폰트를 사용한 Word 문서 만들기 – 가이드

현대적인 가변 폰트를 사용하여 **create word document**를 만들어야 할 때, 어디서 시작해야 할지 몰라 고민한 적이 있나요? 당신만 그런 것이 아닙니다. 많은 프로젝트—예를 들어 동적 보고서나 브랜드 일관성을 유지한 브로셔—에서 실시간으로 **change font weight**를 할 수 있다는 것은 큰 변화를 가져옵니다.  

이 튜토리얼에서는 전체 과정을 단계별로 안내합니다: Aspose.Words에 가변 폰트를 로드하고, 무게와 폭을 설정한 뒤, 디자인 그대로 보이는 DOCX 파일을 저장하는 방법까지. 모호한 설명이 아니라 지금 바로 C# 프로젝트에 복사해 넣을 수 있는 구체적인 코드를 제공합니다.

## 배워게 될 내용

- `FontSettings`를 사용하여 Aspose.Words에 **load variable font** 파일을 로드하는 방법.  
- `wght`(weight)와 `wdth`(width)와 같은 **define font variation** 축의 구문.  
- 단일 `Run`에서 **set font width**와 **change font weight**를 적용하는 방법.  
- 일반적인 문제(누락된 글리프, 잘못된 폴더 경로 등)를 해결하기 위한 팁.  
- 즉시 복사‑붙여넣기하고 테스트할 수 있는 완전한 실행 가능한 예제.  

> **Prerequisites**: .NET 6+ (or .NET Framework 4.6+), Aspose.Words for .NET installed via NuGet, and a variable‑font file like *RobotoFlex.ttf* placed in a local *Fonts* folder.

## Step 1 – Aspose.Words에 가변 폰트 로드하기

먼저, Aspose.Words에 사용자 정의 폰트를 어디서 찾을지 알려줘야 합니다. `FontSettings` 클래스가 이 작업을 담당합니다.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Why this matters**: 폴더를 등록하지 않으면 Aspose.Words는 시스템 폰트로 대체하고 나중에 적용하려는 OpenType 변형 데이터를 무시합니다. 특정 디렉터리를 지정하면 코드가 실행될 때마다 *RobotoFlex*(또는 다른 가변 폰트)를 확실히 찾을 수 있습니다.  

> **Pro tip**: `SetFontsFolder`의 두 번째 매개변수를 `true`로 설정하면 Aspose가 하위 폴더도 검색합니다. 스타일이나 무게별로 폰트를 정리할 때 유용합니다.

## Step 2 – 새 문서를 만들고 샘플 텍스트 추가

폰트 엔진이 검색 위치를 알게 되었으니, 빈 `Document`를 만들고 `Run`이 포함된 단락을 삽입합니다.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**What’s happening**: `Run`은 동일한 서식을 가진 연속 텍스트 조각을 나타냅니다. 먼저 `Run`을 만들면 서식 로직을 분리할 수 있어, 필요에 따라 다른 변형 축을 별도의 `Run`에 적용하기에 이상적입니다.

## Step 3 – 원하는 변형 축 정의 (Weight & Width)

가변 폰트는 런타임에 조정할 수 있는 *축*을 제공합니다. 가장 흔한 두 축은 `wght`(폰트 무게)와 `wdth`(폰트 폭)입니다. Aspose.Words는 이를 `OpenTypeFontVariation` 컬렉션으로 모델링합니다.  

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Why these numbers**: OpenType 사양에 따르면 `wght`는 폰트의 최소 무게부터 최대 무게까지(보통 100–900) 범위가 있습니다. **700** 값은 굵은(bold) 모양에 해당합니다. `wdth`도 마찬가지이며, **100**은 기본(보통) 폭을 의미하고 100 이하 값은 글리프를 압축합니다.  

> **Edge case**: 일부 가변 폰트는 특정 축을 지원하지 않을 수 있습니다. 지원되지 않는 태그를 제공하면 Aspose는 조용히 무시합니다. 폰트 사양(보통 `.ttf` 또는 `.otf` 파일 메타데이터)을 항상 확인하세요.

## Step 4 – 폰트 이름을 사용해 Run에 변형 적용

이제 변형 데이터를 실제 텍스트에 바인딩합니다. `FontInfo` 클래스는 폰트 패밀리 이름과 축 컬렉션을 보관합니다.  

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explanation**: `FontInfo`를 설정하면 일반적인 `Font.Name` 속성을 우회하고 엔진에 완전한 폰트 구성을 전달합니다. 이것이 Aspose.Words에 커스텀 축을 가진 가변 폰트를 사용하도록 지시하는 유일한 방법입니다.  

> **Common mistake**: 폰트 파일 내부의 정확한 패밀리 이름(`RobotoFlex` 예시)을 일치시키지 않으면 Aspose가 기본 폰트로 대체하고 변형이 적용되지 않습니다.

## Step 5 – 문서를 저장하고 결과 확인

마지막으로 문서를 디스크에 기록합니다. 생성된 DOCX에는 가변 폰트 지시가 포함되며, Microsoft Word(2016+)에서 올바르게 렌더링됩니다.  

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Word에서 결과 파일을 열고 텍스트를 선택한 뒤 **Font** 대화상자를 확인하세요. *Roboto Flex*가 목록에 표시되고, 텍스트가 주변 내용보다 더 굵게 보일 것입니다—즉 `wght = 700` 설정이 정확히 적용된 결과입니다.  

> **Verification tip**: 텍스트가 변하지 않았다면 폰트 파일이 실제로 `wght` 축을 지원하는지 다시 확인하세요. 일부 “가변” 폰트는 `ital`(italic)이나 `opsz`(optical size)만 노출합니다.

## Optional: 추가 변형 적용 – 폭 동적으로 변경

다른 단락에서 *set font width*를 다르게 적용하고 싶다면, 새로운 `OpenTypeFontVariation` 컬렉션을 사용해 단계 3‑4를 다시 수행하면 됩니다.  

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

이제 두 개의 `Run`이 있습니다—하나는 굵게, 다른 하나는 약간 넓게—같은 문서에서 **change font weight**와 **set font width**를 모두 시연합니다.

## 전체 작업 예제

아래 코드를 새 콘솔 앱(`Program.cs`)에 복사하고 실행하세요. `Fonts` 폴더에 `RobotoFlex.ttf`(또는 원하는 다른 가변 폰트)가 포함되어 있는지 확인합니다.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Expected output**: `VariableFont.docx` 파일에서 “Variable‑weight text” 문구가 `wght = 700` 축 덕분에 굵게 표시되고, 기본 폭을 유지합니다.

## 자주 묻는 질문 및 엣지 케이스

| Question | Answer |
|----------|--------|
| *What if the font isn’t found?* | 폴더 경로를 확인하고 파일 이름이 일치하는지, 프로세스에 읽기 권한이 있는지 검증하세요. `fontSettings.GetFonts()`를 호출해 감지된 폰트를 나열할 수도 있습니다. |
| *Can I combine multiple runs with different variations?* | 가능합니다. 각 `Run`은 자체 `FontInfo`를 가질 수 있습니다. 각 `Run`마다 단계 3‑4를 반복하면 됩니다. |
| *Do older versions of Word support variable fonts?* | Word 2016(Build 16.0.8001)부터 기본 지원이 도입되었습니다. 이전 버전을 대상으로 하면 문서는 가장 가까운 정적 폰트 인스턴스로 대체됩니다. |
| *Is there a limit to how many axes I can set?* | 폰트가 정의한 축 수만큼 설정할 수 있습니다. 일반적인 태그는 `wght`, `wdth`, `ital`, `opsz`, `GRAD` 등이며, 지원되지 않는 태그는 효과가 없습니다. |
| *How do I debug missing glyphs?* | `FontSettings.GetFontSources()`로 로드된 폰트를 검사하고, `FontInfo.HasGlyph(char)`를 사용해 개별 문자에 글리프가 있는지 테스트하세요. |

## 결론

몇 단계만 거치면 **how to create word document** 파일에 가변 폰트의 힘을 활용해 **change font weight**, **set font width**, **load variable font** 파일, **define font variation** 축을 모두 적용할 수 있음을 보여드렸습니다—모두 Aspose.Words for .NET을 사용했습니다.  

핵심 아이디어는 간단합니다: 폰트 폴더를 등록하고, 원하는 축을 정의한 뒤, 이를 `Run`에 연결하고 저장합니다. 여기서부터는 이 기술을 전체 섹션, 표, 혹은 브랜드‑특화 보고서를 프로그래밍 방식으로 생성하는 데 확장할 수 있습니다.  

**Next steps**: `RobotoFlex`를 다른 가변 폰트로 교체해 보거나, `ital`(italic) 축을 실험하거나, 같은 문서를 Aspose.PDF를 사용해 PDF 버전으로 생성해 보세요. 동일한 패턴—로드, 정의, 적용, 저장—이 적용됩니다.  

코딩을 즐기시고, 가변 폰트가 Word 자동화 프로젝트에 가져다 주는 유연성을 마음껏 활용하시기 바랍니다!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}