---
category: general
date: 2026-03-14
description: Aspose.Words를 사용하여 docx에서 이미지를 추출하면서 Word를 Markdown으로 빠르게 변환합니다. 개발자를
  위한 단계별 C# 예제.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: ko
og_description: Aspose.Words를 사용하여 Word를 Markdown으로 변환하고 docx에서 이미지를 추출하세요. 번거로움 없는
  변환을 위해 이 상세 가이드를 따라보세요.
og_title: Word를 Markdown으로 변환 – 완전 C# 튜토리얼
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Word를 Markdown으로 변환 – 이미지 추출 포함 전체 가이드
url: /ko/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환 – 완전한 C# 튜토리얼

Word를 Markdown으로 **변환**하고 삽입된 그림을 그대로 유지하는 방법을 찾고 계셨나요? 혼자만 그런 것이 아닙니다. 텍스트는 변환되지만 이미지가 사라지는 문제에 직면한 개발자가 많습니다. 좋은 소식은 몇 줄의 C# 코드와 강력한 Aspose.Words 라이브러리를 사용하면 **Word를 Markdown으로 변환**하면서 *docx에서 이미지 추출*까지 한 번에 처리할 수 있다는 것입니다.

이 튜토리얼에서는 NuGet 패키지 설치, `.docx` 파일 로드, markdown 저장 옵션 설정, 각 그림을 사용자 지정 폴더에 저장하고 이미지 링크를 다시 쓰는 콜백 구성까지 모든 과정을 단계별로 안내합니다. 최종적으로는 사용 가능한 Markdown 파일과 원본 Word 문서의 모든 그림이 들어 있는 깔끔한 `resources` 디렉터리를 얻게 됩니다.

## 배울 내용

- C# 프로젝트에 Aspose.Words for .NET을 설정하는 방법.  
- 이미지를 보존하면서 **Word를 Markdown으로 변환**하는 정확한 코드.  
- `ResourceSavingCallback`이 **docx에서 이미지 추출**에 왜 필수인지.  
- 일반적인 함정(예: 경로 구분자, 파일명 중복)과 이를 피하는 방법.  
- 생성된 Markdown이 올바르게 렌더링되는지 빠르게 확인하는 단계.

### 전제 조건

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 이상 (또는 .NET Framework 4.7 이상) | Aspose.Words는 두 환경을 모두 지원하며 최신 런타임이 더 나은 성능을 제공합니다. |
| Visual Studio 2022 (또는 any C# IDE) | 디버깅 및 패키지 관리를 쉽게 해줍니다. |
| NuGet 복원을 위한 인터넷 연결 | 공식 피드에서 라이브러리를 가져옵니다. |
| 텍스트 **와** 이미지가 모두 포함된 샘플 `input.docx` | 이미지 추출 과정을 확인하기 위해 필요합니다. |

추가 서드파티 도구는 필요하지 않습니다—Aspose.Words가 모든 작업을 내부에서 처리합니다.

---

## Step 1: Install Aspose.Words via NuGet

먼저 프로젝트에 Aspose.Words 패키지를 추가합니다. **Package Manager Console**을 열고 다음을 실행합니다:

```powershell
Install-Package Aspose.Words
```

또는 UI를 사용할 수도 있습니다: 프로젝트 우클릭 → *Manage NuGet Packages* → “Aspose.Words” 검색 → **Install** 클릭. 이렇게 하면 핵심 DLL과 나중에 사용할 `Saving` 네임스페이스가 포함됩니다.

> **Pro tip:** 버전을 고정(e.g., `22.12.0`)해 두면 라이브러리가 자동 업데이트될 때 발생할 수 있는 예기치 않은 깨짐을 방지할 수 있습니다.

---

## Step 2: Load the Source Word Document

라이브러리가 준비되었으니 이제 `.docx` 파일을 로드합니다. 절대 경로나 상대 경로 중 편한 것을 사용해 소스 문서를 지정하세요.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Why this matters:** `Document`는 전체 Word 패키지를 파싱해 단락, 표, 그리고 나중에 추출할 숨겨진 이미지 파트에 접근할 수 있게 해줍니다.

---

## Step 3: Create Markdown Save Options

Aspose.Words에는 변환 동작을 세부 조정할 수 있는 `MarkdownSaveOptions` 클래스가 포함되어 있습니다. 최소한 인스턴스를 생성하고, 이후에 콜백을 연결합니다.

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

`ExportImagesAsBase64`를 `false`(별도 이미지 파일을 원하기 때문)로 설정하거나, Markdown에 헤더·푸터가 필요하면 `ExportHeadersFooters`와 같은 속성을 조정할 수 있습니다.

---

## Step 4: Configure the ResourceSavingCallback – Extract Images from DOCX

이 단계가 튜토리얼의 핵심입니다. `ResourceSavingCallback`은 저장 과정에서 **각 리소스**(이미지, 폰트 등)를 기록하려 할 때마다 호출됩니다. 자체 핸들러를 제공하면 이미지가 저장되는 위치와 Markdown 파일에서의 참조 방식을 직접 결정할 수 있습니다.

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### What This Does

1. `resources` 하위 폴더가 아직 없으면 **생성**합니다.  
2. 들어오는 각 이미지 스트림을 해당 폴더에 **복사**하고, 혼동을 피하기 위해 원본 파일명을 그대로 유지합니다.  
3. Markdown 링크(`![alt](resources/Image1.png)`)를 **업데이트**해 파일이 렌더링될 때 그림이 보이도록 합니다.

> **Edge case:** 두 이미지가 같은 이름을 가질 경우, 뒤에 오는 이미지가 앞의 이미지를 덮어씁니다. 이를 방지하려면 GUID를 앞에 붙이거나 `Path.GetUniqueFileName`(사용자 정의 헬퍼) 등을 활용해 저장하기 전에 파일명을 고유하게 만들 수 있습니다.

---

## Step 5: Save the Document as Markdown

콜백을 연결했으니 이제 한 줄 코드로 Markdown 파일을 저장합니다.

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

이 호출이 끝나면 다음이 생성됩니다:

- 이미지 링크가 `![Image1](resources/Image1.png)` 형태로 포함된 `output.md` 파일.  
- 원본 `.docx`에서 추출된 모든 그림이 들어 있는 `resources` 폴더.

---

## Step 6: Verify the Result

`output.md`를任意의 Markdown 뷰어(VS Code, GitHub, Typora 등)에서 열어 보세요. 원본 문서의 제목, 리스트, **이미지**가 정상적으로 렌더링되어야 합니다. 이미지가 보이지 않을 경우:

1. `resources` 폴더에 해당 파일이 존재하는지 확인합니다.  
2. Markdown에 적힌 상대 경로(`resources/<filename>`)가 폴더명과 정확히 일치하는지 확인합니다(Linux에서는 대소문자 구분).  
3. 이미지 파일이 손상되지 않았는지 – 이미지 뷰어로 직접 열어 봅니다.

---

## Full Working Example

아래는 완전한 실행 가능한 예제입니다. `YOUR_DIRECTORY` 자리표시자를 실제 폴더 경로로 교체하세요.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**Expected output:** `output.md`를 열면 다음과 같은 내용이 표시됩니다.

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

모든 이미지가 텍스트와 나란히 표시되며, 원본 Word 파일과 동일한 레이아웃을 유지합니다.

---

## Common Questions & Gotchas

**Q: 추출 과정에서 이미지 포맷을 변경할 수 있나요?**  
A: 가능합니다. 콜백 내부에서 스트림을 재인코딩(e.g., PNG)한 뒤 저장하면 됩니다. `System.Drawing`이나 `ImageSharp`를 사용해 `args.Stream`을 조작하세요.

**Q: Word 문서에 SVG나 EMF 이미지가 포함돼 있으면 어떻게 되나요?**  
A: Aspose.Words는 대부분의 벡터 포맷을 기본적으로 래스터 PNG로 변환합니다. 원본 벡터가 필요하면 `mdOptions.ExportImageResolution`을 설정하고 스트림을 직접 처리하세요.

**Q: .NET Core를 Linux에서 실행할 수 있나요?**  
A: 전혀 문제 없습니다. `resources` 경로에 슬래시(`/`)를 사용하거나 예시와 같이 `Path.Combine`을 활용하면 됩니다. Linux 파일 시스템은 대소문자를 구분하므로 폴더명과 경로 표기를 일관되게 유지하세요.

**Q: 각주나 주석을 제외하고 싶다면?**  
A: 저장 전에 `mdOptions.ExportFootnotes` 또는 `mdOptions.ExportComments` 속성을 조정하면 됩니다.

---

## Conclusion

우리는 **Word를 Markdown으로 변환**하면서 **docx에서 이미지 추출**까지 확실히 수행할 수 있는 **완전한 엔드‑투‑엔드 솔루션**을 다뤘습니다. Aspose.Words의 `MarkdownSaveOptions`와 `ResourceSavingCallback`을 활용하면 텍스트 변환과 이미지 처리 모두에 세밀한 제어가 가능합니다. 코드는 독립형이며 모든 .NET 플랫폼에서 동작하고, 기존 파이프라인에 최소한의 수정만으로 쉽게 통합할 수 있습니다.

다음 단계가 궁금하신가요? 대량 변환 자동화, ASP.NET API에 이 로직 통합, 혹은 추출된 각 이미지에 썸네일을 생성하도록 콜백을 확장하는 등 다양한 활용이 가능합니다. 핵심 변환 로직을 확보했으니 이제 무한히 확장해 보세요.

---

![convert word to markdown example](convert-word-to-markdown.png "convert word to markdown example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}