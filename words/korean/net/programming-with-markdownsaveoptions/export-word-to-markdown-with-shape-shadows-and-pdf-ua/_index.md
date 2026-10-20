---
category: general
date: 2026-03-28
description: Aspose.Words를 사용하여 C#에서 Word를 마크다운으로 내보내고, 도형 그림자를 추가하며 PDF/UA를 저장하는
  방법을 단계별 가이드로 배워보세요.
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: ko
og_description: Aspose.Words를 사용하여 C#에서 Word를 마크다운으로 내보내고, 도형 그림자를 추가하며, PDF/UA로 저장합니다.
  코드와 팁이 포함된 완전한 튜토리얼.
og_title: Word를 Markdown으로 내보내기 – 도형 그림자 추가 및 PDF/UA 저장
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: '워드를 마크다운으로 내보내기: 도형 그림자 및 PDF/UA'
url: /ko/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 마크다운으로 내보내기 (Shape 그림자 및 PDF/UA 포함)

Word를 마크다운으로 **내보내야** 하면서 멋진 shape 그림자도 유지하고 PDF/UA 준수까지 해야 했던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 형식을 바꾸면서 시각적 충실도를 유지하려고 할 때, 특히 접근성(PDF/UA)이 필수일 때 벽에 부딪히곤 합니다.

이 가이드에서는 **Word를 마크다운으로 내보내기**, 그림에 **shape 그림자 추가**, 그리고 떠 있는 shape를 인라인으로 강제하여 **PDF/UA 저장**하는 전체 실행 가능한 예제를 단계별로 살펴봅니다. 강력한 문서 변환을 위한 대표 라이브러리인 Aspose.Words for .NET을 사용할 것입니다. 외부 스크립트나 직접 만든 파서는 필요 없으며, 오늘 바로 콘솔 앱에 넣어 사용할 수 있는 깔끔한 C# 코드만 제공됩니다.

> **Pro tip:** 아직 Aspose.Words를 설치하지 않았다면 최신 NuGet 패키지(`Install-Package Aspose.Words`)를 가져오세요 — .NET 6+, .NET Framework 4.8, 그리고 .NET Core에서도 작동합니다.

## 필요 사항

- **Visual Studio 2022** (.NET 6+를 지원하는 IDE라면 어느 것이든)
- **Aspose.Words for .NET** (NuGet 버전 23.8 이상)
- 최소 하나의 shape(예: 사각형)를 포함한 샘플 `input.docx`
- 기본 C# 지식 – 구문은 간단하게 유지합니다

필요 조건을 모두 준비했으니, 이제 시작해 봅시다.

![Word를 마크다운으로 내보내는 흐름 다이어그램](export_word_to_markdown_diagram.png){alt="Word를 마크다운으로 내보내는 예시"}

## 단계 1: 복구 모드로 Word 문서 로드  

무언가를 수정하기 전에 문서를 메모리로 로드해야 합니다. **RecoveryMode.Recover** 로 로드하면 폰트 대체 경고를 포착할 수 있어, 원본에 설치되지 않은 폰트가 사용된 경우에 유용합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*왜 RecoveryMode인가?*  
원본 파일이 누락된 폰트를 참조하면 Aspose가 대체하고 경고를 발생시킵니다. 이러한 경고를 포착하면 나중에 로그로 남길 수 있어 디버깅 및 준수 보고에 유용합니다.

## 단계 2: Shape 그림자 추가  

문서가 로드되었으니, 이제 shape의 외관을 개선해 보겠습니다. 첫 번째 `Shape` 노드를 가져와서 은은한 드롭 섀도우를 활성화합니다.

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*왜 그림자를 조정하나요?*  
그림자는 깊이를 부여해 shape가 Word와 내보낸 마크다운 이미지 모두에서 돋보이게 합니다(나중에 shape를 이미지로 변환한다면). 또한 시각적 속성이 변환 파이프라인을 통과하는지 빠르게 테스트할 수 있는 방법이기도 합니다.

## 단계 3: 문서를 마크다운으로 내보내기 (LaTeX 수식 포함)  

Aspose.Words는 Word 파일을 깔끔한 마크다운으로 변환할 수 있습니다. 여기서는 OfficeMath 수식을 LaTeX로 내보내도록 지정하는데, 이는 과학 문서의 사실상 표준입니다.

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*예상 결과:*  
- 표준 마크다운 구문을 가진 `output.md` 파일.  
- 방금 그림자 효과를 적용한 shape를 포함한 모든 삽입 이미지가 `assets/`에 저장됩니다.  
- 모든 수식은 `$…$` 형태의 LaTeX 블록으로 표시되어 MathJax 또는 KaTeX로 렌더링할 수 있습니다.

## 단계 4: 동일 문서를 PDF/UA로 저장  

PDF/UA(PDF/Universal Accessibility)는 PDF가 ISO 14289‑1을 충족하도록 보장합니다. 또한 떠 있는 shape를 인라인 태그로 저장하도록 강제하여 접근성 태깅을 단순화합니다.

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*왜 PDF/UA인가?*  
청중에 스크린 리더 사용자가 포함되거나 법적 접근성 기준을 충족해야 한다면 PDF/UA가 적합합니다. `ExportFloatingShapesAsInlineTag` 플래그는 떠 있는 객체가 논리적 읽기 순서를 깨뜨리는 것을 방지합니다.

## 단계 5: 폰트 대체 경고 검토  

변환 단계가 끝난 후, **단계 1**에서 포착한 폰트 관련 경고를 표시하는 것이 좋은 습관입니다.

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

만약 *“Font 'Calibri' was substituted with 'Arial'”*와 같은 메시지가 보이면, 어떤 폰트가 누락되었는지 정확히 알 수 있으며, 대체 폰트를 포함시킬지 아니면 누락된 폰트를 애플리케이션과 함께 배포할지 결정할 수 있습니다.

## 전체 작업 예제  

모든 단계를 종합하면, 새 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 완전한 프로그램이 아래에 있습니다:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### 예상 결과  

- `output.md`는 깔끔한 마크다운, LaTeX 인코딩된 수식, 그리고 `![Shape](assets/shape0.png)`와 같은 이미지 링크를 포함합니다.  
- `output.pdf`는 Adobe Acrobat 접근성 검사기를 통과하는 PDF/UA‑준수 파일입니다.  
- 콘솔 출력은 폰트 대체 경고를 나열하여 누락된 폰트를 추적하는 데 도움을 줍니다.

## 일반적인 질문 및 엣지 케이스  

**문서에 여러 개의 shape가 있는 경우는?**  
`doc.GetChildNodes(NodeType.Shape, true)`를 순회하면서 각 요소에 그림자 설정을 적용합니다.  

**그림자 색상을 변경할 수 있나요?**  
예—저장하기 전에 `shape.ShadowFormat.Color = Color.Gray;`를 설정합니다.  

**웹 배포 시 assets 폴더 경로를 조정해야 하나요?**  
물론입니다. 상대 경로를 사용하거나 `ResourceSavingCallback`에서 CDN URL을 구성하여 이미지를 효율적으로 제공하세요.  

**마크다운 내보내기 시 Word 전용 기능이 손실되나요?**  
추적 변경, 댓글, 복잡한 SmartArt와 같은 기능은 마크다운에 표현되지 않습니다. 이러한 기능이 필요하면 PDF/UA 버전을 백업으로 유지하세요.  

## 결론  

이제 Aspose.Words를 사용해 C#에서 **Word를 마크다운으로 내보내기**, **shape 그림자 추가**, 그리고 **PDF/UA 저장**하는 방법을 배웠습니다. 전체 코드 예제는 폰트 경고 처리, 리소스 관리, 접근성 준수를 모두 포함한 프로덕션 수준 워크플로우를 한 번에 보여줍니다.

다음 단계는? 그림자 매개변수를 바꿔 보거나 다양한 `MarkdownSaveOptions`(예: `ExportImagesAsBase64`)를 실험해 보세요. 혹은 이 파이프라인을 ASP.NET Core API에 통합해 사용자가 업로드한 Word 파일을 실시간으로 변환하도록 할 수도 있습니다. 다른 출력 형식이 궁금하다면 Aspose의 **HTML**, **EPUB**, **TIFF** 내보내기 옵션을 확인해 보세요—각각은 비슷한 패턴을 따릅니다.

코딩을 즐기세요, 그리고 문서가 언제나 의도한 대로 정확히 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}