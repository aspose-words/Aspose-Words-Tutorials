---
category: general
date: 2026-06-02
description: C#에서 가변 두께 폰트를 사용하는 방법을 배우고, 동적 타이포그래피를 위해 폰트 스트레치를 변경하면서 폰트 두께를 프로그래밍적으로
  설정하는 방법을 알아보세요.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: ko
og_description: C#에서 가변 굵기 폰트를 사용해 프로그래밍 방식으로 글꼴 굵기를 설정하고 글꼴 스트레치 코드를 변경하여 문서에 동적
  타이포그래피를 구현합니다.
og_title: C#에서 가변 두께 폰트 사용 – 전체 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: C#에서 가변 굵기 폰트 사용 – 완전 프로그래밍 가이드
url: /ko/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 가변 굵기 폰트 사용 – 완전 프로그래밍 가이드

.NET 프로젝트에서 **가변 굵기 폰트**를 사용해야 했지만 무게와 스트레치를 사용자 입력에 반응하도록 만드는 방법을 몰라 고민한 적이 있나요? 당신만 그런 것이 아닙니다. 많은 UI 또는 보고 시나리오에서 텍스트가 적응하길 원합니다—예를 들어, 마우스를 올렸을 때 굵게 변하는 가벼운 헤드라인이나 강조를 위해 폭이 넓어지는 단락 등. 좋은 소식은 Aspose.Words를 사용하면 **프로그래밍 방식으로 폰트 굵기를 설정**하고 **폰트 스트레치 코드를 실시간으로 변경**할 수 있다는 것입니다.

이 튜토리얼에서는 가변 굵기 폰트를 로드하고, 사용자 지정 굵기를 적용하며, 스트레치 설정을 조정하는 방법을 단계별 예제로 보여드립니다—복사‑붙여넣기 가능한 명확한 C# 코드와 함께. 마지막까지 진행하면 효과를 보여주는 PDF를 생성하는 실행 가능한 콘솔 앱을 얻게 됩니다.

---

## 필요 사항

- **Aspose.Words for .NET** (v23.12 이상). 이 라이브러리는 가변 굵기 폰트에 대한 전체 지원을 제공합니다.
- 최소 하나의 가변 굵기 폰트 파일이 들어 있는 폴더, 예: *RobotoFlex‑Variable.ttf*. Google Fonts에서 다운로드할 수 있습니다.
- .NET 6 SDK(또는 최신 .NET 버전)와 원하는 IDE.
- 기본적인 C# 지식—특별한 것이 필요 없으며 몇 줄의 코드만 있으면 됩니다.

---

![가변 굵기 폰트 예시](https://example.com/variable-weight-sample.png "가변 굵기 폰트 시연")

*Alt text: 생성된 PDF 문서에서 가변 굵기 폰트를 사용한 모습을 보여주는 스크린샷.*

---

## 1단계: FontSettings 설정 및 폰트 폴더 지정  

먼저—Aspose.Words가 가변 굵기 폰트가 저장된 위치를 알아야 합니다. `FontSettings` 객체를 만들고 `FolderFontSource`를 연결하면 됩니다. `true` 플래그는 엔진이 하위 폴더까지 검색하도록 하며, 여러 폰트 패밀리를 함께 보관할 때 유용합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Why this matters:** 폰트 폴더를 등록하지 않으면 Aspose.Words는 시스템 폰트로 대체되고, 사용자 정의 폰트 파일에 포함된 가변 굵기 데이터가 무시됩니다. 이 단계가 이후 모든 작업의 기반이 됩니다.

---

## 2단계: FontSettings를 Document에 연결  

이제 새 `Document`(또는 기존 문서)를 만들고 방금 준비한 `FontSettings`를 사용하도록 지정합니다. 이 바인딩 덕분에 이후에 추가하는 모든 `Run`에서 가변 굵기 데이터를 사용할 수 있습니다.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

이미 템플릿이 있다면—예를 들어 자리 표시자가 들어 있는 Word 파일—`new Document()`를 `new Document("Template.docx")`로 바꾸면 됩니다. 동일한 `FontSettings`가 적용됩니다.

---

## 3단계: 가변 굵기 폰트를 사용할 텍스트 Run 추가  

`Run`은 Aspose.Words에서 텍스트 서식의 가장 작은 단위입니다. 하나를 만들고 새 단락에 삽입한 뒤 나중에 폰트 속성을 변경합니다.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

이 시점에서는 텍스트가 기본 폰트(보통 Times New Roman)로 렌더링됩니다. 가변 굵기 패밀리를 지정하면 마법이 시작됩니다.

---

## 4단계: 가변 굵기 폰트 패밀리 선택  

여기서 실제로 **가변 굵기 폰트를 사용**합니다. `Font.Name`을 가변 폰트 파일 내부에 정의된 정확한 패밀리 이름으로 설정합니다. Roboto Flex의 경우 이름은 `"Roboto Flex"`입니다.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

패밀리 이름이 확실하지 않다면 `.ttf` 파일을 폰트 뷰어로 열거나 `fontSettings.GetFonts()` 메서드를 사용해 사용 가능한 패밀리를 열거해 보세요.

---

## 5단계: 폰트 굵기와 스트레치를 프로그래밍 방식으로 설정  

이제 튜토리얼의 핵심 부분입니다: **프로그래밍 방식으로 폰트 굵기를 설정**하고 **폰트 스트레치 코드를 변경**합니다. 두 속성 모두 OpenType 사양에 매핑되는 정수 값을 받습니다.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). 가변 폰트가 지원하는 값을 선택하세요.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). 기본값은 100 (Normal)입니다.

> **Pro tip:** 모든 가변 폰트가 전체 범위를 제공하는 것은 아닙니다. 지원되지 않는 값을 설정하면 엔진이 가장 가까운 가용 무게 또는 스트레치로 클램프합니다.

---

## 6단계: 문서를 저장하고 결과 확인  

마지막으로 문서를 PDF(또는 DOCX)로 저장하고 열어 효과를 확인합니다. PDF는 플랫폼 간 렌더링이 일관되어 시각적 검증에 적합합니다.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

*VariableWeightDemo.pdf*를 열면 “Variable‑weight text demo”라는 문구가 Roboto Flex의 가벼우면서 약간 확장된 형태로 렌더링된 것을 볼 수 있습니다. `FontWeight`를 `700`으로, `FontStretch`를 `80`으로 바꾸고 다시 실행하면 텍스트가 굵고 더 압축된 모습을 확인할 수 있습니다.

---

## 일반적인 질문 및 엣지 케이스  

### 폰트가 전혀 나타나지 않을 경우  

- **Missing FontSettings**: `doc.FontSettings = fontSettings;`가 텍스트를 추가하기 **이전**에 실행되었는지 다시 확인하세요.
- **Incorrect family name**: `fontSettings.GetFonts()`를 사용해 발견된 모든 패밀리를 나열하고 정확한 문자열을 복사하세요.
- **Unsupported weight/stretch**: 일부 가변 폰트는 100‑900 무게 범위의 일부만 지원합니다. 안전하게 `run.Font.FontWeight = 400;`을 사용하세요.

### 문서를 저장한 뒤에도 무게를 변경할 수 있나요?  

네. `Run` 객체는 변경 가능하므로 최종 `Save` 전에 언제든 `FontWeight`나 `FontStretch`를 조정할 수 있습니다. 사용자 상호 작용에 따라 무게를 토글해야 한다면 각 상태마다 별도의 Run을 생성하는 것을 고려하세요.

### DOCX 출력에서도 작동하나요?  

물론입니다. 가변 굵기 메타데이터는 기본 OpenXML에 저장되며 최신 Word 버전은 이를 해석할 수 있습니다. 다만 오래된 Word 버전은 스트레치 설정을 무시할 수 있습니다.

---

## 전체 작업 예제  

아래는 즉시 컴파일하고 실행할 수 있는 완전한 콘솔 프로그램입니다. 필요한 `using` 지시문, 오류 처리 및 주석이 모두 포함되어 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Expected output:** 콘솔에 저장 경로가 출력되고, 생성된 PDF는 가볍고 확장된 스타일의 텍스트를 보여줍니다—우리가 설정한 그대로입니다.

---

## 요약  

우리는 C#에서 Aspose.Words를 사용해 **가변 굵기 폰트를 사용하는 방법**, **프로그래밍 방식으로 폰트 굵기를 설정하는 방법**, 그리고 **스트레치를 변경하는 정확한 코드**를 다뤘습니다. 단계는 간단합니다: `FontSettings` 구성 → `Document`에 연결 → `Run` 생성 → 가변 굵기 패밀리 선택 → 마지막으로 `FontWeight`와 `FontStretch` 조정.

---

## 다음 단계  

- **Dynamic UI integration**: 동일한 로직을 WinForms 또는 WPF 앱에 연결해 사용자가 슬라이더로 무게/스트레치를 선택하도록 합니다.
- **Multiple runs**: 같은 단락에 서로 다른 무게를 가진 여러 Run을 결합해 풍부한 타이포그래피 계층을 만듭니다.
- **Advanced axes**: 일부 가변 폰트는 추가 축(예: 슬랜트, 옵티컬 사이즈)을 제공합니다. `run.Font.FontStyle`을 사용하거나 `FontVariationSettings`를 탐색해 더 세밀한 제어를 구현하세요.
- **Performance tips**: 다수의 문서를 처리할 때는 `FontSettings` 인스턴스를 캐시해 폴더 스캔을 반복하지 않도록 합니다.

자유롭게 실험해 보세요—*Roboto Flex*를 *Inter Variable* 등 다른 OpenType 가변 폰트로 교체하면 문서에 새로운 시각적 유연성이 추가됩니다. Happy coding!

## 다음에 배워야 할 내용

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 관련 주제를 깊이 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [대상 머신에서 폰트 사용](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [대상 머신에서 폰트 사용](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [대상 머신에서 폰트 사용](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}