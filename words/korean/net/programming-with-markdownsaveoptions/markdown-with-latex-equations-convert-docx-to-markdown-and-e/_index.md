---
category: general
date: 2025-12-19
description: LaTeX 수식이 포함된 마크다운 가이드 – Aspose.Words를 사용하여 C#에서 docx를 마크다운으로 변환하고, 수식을
  LaTeX로 내보내며, 이미지를 고유한 이름으로 폴더에 저장하는 방법을 배웁니다.
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: ko
og_description: LaTeX 수식이 포함된 마크다운 튜토리얼은 docx를 마크다운으로 변환하고, 수식을 LaTeX로 내보내며, 저장된 이미지에
  대한 고유한 이미지 이름을 생성하는 방법을 보여줍니다.
og_title: LaTeX 방정식이 포함된 마크다운 – 전체 C# 변환 가이드
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'LaTeX 방정식이 포함된 마크다운: DOCX를 마크다운으로 변환하고 이미지 내보내기'
url: /ko/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown with latex equations: Convert DOCX to Markdown and Export Images

Word 파일에서 **markdown with latex equations** 를 추출하는 방법을 몰라 고민한 적 있나요? 혼자가 아닙니다—많은 개발자들이 Office에서 정적 사이트 생성기로 문서를 옮길 때 같은 문제에 부딪힙니다.  

이 튜토리얼에서는 **docx를 markdown으로 변환**, **수식을 latex로 내보내기**, 그리고 **이미지를 폴더에 저장**하면서 **고유 이미지 이름 생성** 로직을 적용하는 완전한 엔드‑투‑엔드 솔루션을 Aspose.Words for .NET을 사용해 단계별로 안내합니다.  

끝까지 따라오면 수동 복사‑붙여넣기 없이 깔끔한 Markdown 파일, LaTeX‑준비 수식, 정돈된 이미지 디렉터리를 생성하는 C# 프로그램을 바로 실행할 수 있습니다.

## What You’ll Need

- .NET 6 (또는 최신 .NET 런타임)  
- Aspose.Words for .NET 23.10 이상 (NuGet 패키지 `Aspose.Words`)  
- 일반 텍스트, Office Math 객체, 몇 개의 그림이 포함된 샘플 `input.docx`  
- 선호하는 IDE (Visual Studio, Rider, 또는 VS Code)  

그게 전부입니다. 추가 라이브러리나 복잡한 커맨드‑라인 도구는 필요 없으며 순수 C#만 사용합니다.

## Step 1: Load the Document Safely (Recovery Mode)

여러 사람이 편집한 파일을 다루다 보면 손상 위험이 현실적으로 존재합니다. Aspose.Words에서는 *RecoveryMode* 를 활성화해 로더가 예외를 발생시키는 대신 손상된 부분을 복구하도록 할 수 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**Why this matters:**  
소스 파일에 잘못된 XML 노드나 깨진 이미지 스트림이 포함돼 있어도 복구 모드를 사용하면 사용 가능한 `Document` 객체를 얻을 수 있습니다. 이 단계를 건너뛰면 특히 CI 파이프라인에서 업로드를 완전히 제어하지 못할 때 심각한 충돌이 발생할 수 있습니다.

> **Pro tip:** 배치를 처리할 때는 `try/catch` 로 로드를 감싸고 `DocumentCorruptedException` 을 로그에 남겨 나중에 검토하세요.

## Step 2: Convert DOCX to Markdown with LaTeX Equations

이제 튜토리얼의 핵심 단계입니다: **markdown with latex equations** 를 만들고자 합니다. Aspose.Words의 `MarkdownSaveOptions` 에서 `OfficeMathExportMode.LaTeX` 를 지정하면 각 Office Math 객체가 `$…$` 혹은 `$$…$$` 로 감싼 LaTeX 문자열로 변환됩니다.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

생성된 `output_math.md` 는 다음과 같은 형태를 가집니다:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**Why you’d want this:**  
대부분의 정적 사이트 생성기(Hugo, Jekyll, MkDocs)는 MathJax 또는 KaTeX 플러그인을 활성화하면 LaTeX 구분자를 바로 인식합니다. LaTeX 로 직접 내보내면 별도의 정규식 후처리 단계가 필요 없으므로 작업 흐름이 간단해집니다.

### Edge Cases

- **Complex equations:** 매우 깊게 중첩된 구조도 올바르게 렌더링되지만, `OutOfMemoryException` 이 발생하면 `MathRenderer` 메모리 제한을 늘려야 할 수 있습니다.  
- **Mixed content:** 단락에 일반 텍스트와 수식이 섞여 있으면 Aspose.Words가 자동으로 분리해 주변 markdown을 그대로 보존합니다.

## Step 3: Save Images to Folder with Unique Names

Word 문서에 그림이 포함돼 있다면, markdown에서 참조할 수 있도록 별도의 이미지 파일로 저장하고 싶을 것입니다. `MarkdownSaveOptions` 의 `ResourceSavingCallback` 을 사용하면 각 이미지가 어떻게 저장될지 완전히 제어할 수 있습니다.

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**What the markdown looks like now:**

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**Why generate unique names?**  
같은 그림이 여러 번 등장하면 원본 파일명을 그대로 사용하면 덮어쓰기 문제가 발생합니다. GUID 기반 이름을 사용하면 모든 파일이 고유해지므로 특히 병렬 작업을 수행할 때 유용합니다.

### Tips & Gotchas

- **Performance:** 각 이미지마다 GUID를 생성하는 비용은 무시할 수준이지만, 수천 개의 이미지를 처리한다면 이미지 바이트의 SHA‑256 해시와 같은 결정적 해시로 전환할 수 있습니다.  
- **File format:** `resource.Save` 는 원본 포맷 그대로 저장합니다. 모든 이미지를 PNG로 통일하고 싶다면 `resource.Save(imageFile);` 를 `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));` 로 교체하세요.

## Step 4: Export PDF with Inline Shapes (Optional)

때때로 같은 문서의 PDF 버전이 필요할 수 있습니다(예: 법률 검토). `ExportFloatingShapesAsInlineTag` 를 설정하면 텍스트 상자와 같은 떠 있는 객체가 PDF에서 인라인 태그로 유지돼 레이아웃 정확도가 보존됩니다.

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

PDF 출력이 워크플로에 포함되지 않는다면 이 단계를 건너뛰어도 전혀 문제되지 않습니다.

## Full Working Example (All Steps Combined)

아래는 콘솔 앱에 복사‑붙여넣기 할 수 있는 전체 프로그램 예시입니다. `YOUR_DIRECTORY` 를 실제 절대 경로나 상대 경로로 교체하세요.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

이 프로그램을 실행하면 다음 세 파일이 생성됩니다:

| File | Purpose |
|------|---------|
| `output_math.md` | LaTeX‑준비 수식이 포함된 Markdown |
| `output_images.md` | 고유 이름 PNG를 가리키는 이미지 링크가 포함된 Markdown |
| `output_shapes.pdf` | 떠 있는 도형을 인라인 태그로 보존한 PDF (선택 사항) |

## Conclusion

이제 **markdown with latex equations** 파이프라인을 갖추었습니다. **docx를 markdown으로 변환**, **수식을 latex로 내보내기**, **이미지를 폴더에 저장**하면서 **각 그림에 고유 이미지 이름 생성**까지 자동화되었습니다. 이 접근 방식은 완전 독립형이며 최신 .NET 프로젝트 어디서든 동작하고, 필요한 것은 Aspose.Words NuGet 패키지 하나뿐입니다.

다음 단계는? 생성된 markdown을 Hugo 같은 정적 사이트 생성기에 연결하고 MathJax를 활성화하면, 폐쇄형 오피스 형식에서 아름답고 웹에 최적화된 문서로 변신하는 모습을 확인할 수 있습니다. 표가 필요하신가요? Aspose.Words는 `MarkdownSaveOptions.ExportTableAsHtml` 도 지원하므로 복잡한 레이아웃도 그대로 유지할 수 있습니다.

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}