---
category: general
date: 2026-06-27
description: Aspose.Words를 사용하여 docx를 markdown으로 변환하고 docx에서 이미지를 저장합니다. Word 파일에서
  이미지를 추출하고 Word 문서를 markdown으로 내보내는 방법을 배워보세요.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: ko
og_description: docx를 markdown으로 변환하고 docx에서 이미지를 저장합니다. 이 가이드는 Word 파일에서 이미지를 추출하고
  Word 문서를 markdown으로 내보내는 방법을 보여줍니다.
og_title: docx를 markdown으로 변환하고 docx에서 이미지 저장
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: docx를 markdown으로 변환하고 docx에서 이미지 저장
url: /ko/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx를 markdown으로 변환하고 docx에서 이미지 저장하기

Word 파일에 삽입된 그림을 잃지 않고 **convert docx to markdown** 하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다—개발자들은 종종 보고서의 깔끔한 Markdown 버전이 필요하면서도 모든 다이어그램, 로고, 스크린샷을 그대로 유지하고 싶어합니다.

이 튜토리얼에서는 **.docx를 Markdown으로 변환**, **docx에서 이미지를 폴더에 저장**, 그리고 강력한 Aspose.Words 라이브러리를 사용해 **Word 파일에서 이미지를 추출**하는 완전한 실행 가능한 예제를 단계별로 살펴봅니다. 마지막에는 **Word 문서를 markdown으로 내보내는** 방법을 한 줄 코드로 알게 됩니다.

## 필요 사항

- .NET 6+ (또는 .NET Framework 4.7.2+)가 머신에 설치되어 있어야 합니다  
- `Aspose.Words`에 대한 NuGet 참조 (무료 체험판으로 충분합니다)  
- 하나 이상의 그림이 포함된 샘플 `input.docx`  
- 선호하는 IDE—Visual Studio, Rider, 혹은 VS Code도 괜찮습니다  

추가 서드파티 도구 없이, 복잡한 명령줄 작업 없이 바로 C# 코드만 있으면 됩니다.

## docx를 markdown으로 변환 – 개요

핵심 아이디어는 간단합니다:

1. 소스 Word 문서를 로드합니다.  
2. Aspose.Words에게 외부 리소스(예: 이미지)를 어떻게 처리할지 알려줍니다.  
3. 문서를 Markdown으로 저장하고, 라이브러리가 무거운 작업을 수행하도록 합니다.

아래는 **전체 실행 가능한 프로그램**입니다. 새 콘솔 프로젝트에 복사‑붙여넣기하고 `Ctrl+F5`를 눌러 실행해 보세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### 코드 작동 방식

- **문서 로드** (`new Document(inputPath)`)는 Word 파일의 모든 부분—단락, 표, **이미지**—을 메모리 내에 표현합니다.  
- **`MarkdownSaveOptions`**가 마법이 일어나는 곳입니다. `ResourceSavingCallback`을 연결하면 Aspose.Words가 외부 리소스를 기록하려 할 때마다 완전한 제어권을 가집니다.  
- 콜백 내부에서는 `args.ResourceType == ResourceType.Image`를 확인해 **Word 파일에서 이미지를 추출**합니다. 콜백은 이미지 바이트, 원본 확장자, 그리고 우리가 즉석에서 만든 폴더에 설정한 `SavePath` 속성을 받습니다. `Guid.NewGuid()`를 사용하면 파일명이 고유해져 이전 실행을 우연히 덮어쓰는 일이 없습니다.  
- **CSS는 건너뜁니다** (`ResourceType.CssStyleSheet`)—일반 Markdown에는 스타일시트가 필요 없으므로 출력이 깔끔해집니다.  
- 마지막으로 `doc.Save(outputPath, mdOptions)`가 Markdown 파일을 작성하고, Word 구조를 Markdown 등가물(``#`` 헤딩, 파이프 구분 행의 표 등)로 교체합니다.

## Save images from docx – Custom folder strategy

맞춤 폴더가 왜 필요할까요? CI 파이프라인용 문서를 생성한다고 상상해 보세요. Markdown 파일과 그 자산이 깔끔하고 재현 가능한 레이아웃으로 나란히 배치되길 원합니다.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

몇 가지 **전문 팁**:

- 폴더 경로를 프로젝트 루트에 **상대적으로** 유지하세요. 이렇게 하면 Markdown 파일이 상대 링크(`![Alt text](Images/abc123.png)`)로 이미지를 참조할 수 있어 GitHub, GitLab, 혹은 모든 정적 사이트 생성기에서 작동합니다.  
- **결정적인 파일명**이 필요하면(예: 동일 이미지가 항상 같은 파일명을 가져야 할 경우) GUID 대신 이미지 바이트의 해시를 사용하세요: `MD5.Create().ComputeHash(args.Data)`. 작은 트윅이지만 캐싱에 유용합니다.

## Extract images from Word file – Edge cases

1. **다양한 이미지 포맷** – Aspose.Words는 PNG, JPEG, GIF, BMP, 심지어 SVG도 지원합니다. `args.Extension` 속성에 이미 올바른 파일 확장자가 들어 있으니 추측할 필요가 없습니다.  
2. **매우 큰 이미지** – 소스 문서에 고해상도 사진이 포함되어 있으면 생성된 파일이 크게 될 수 있습니다. 콜백 후 `System.Drawing`이나 `ImageSharp`을 사용해 압축 단계를 추가하는 것을 고려하세요.  
3. **숨겨진 이미지** – Word는 헤더/푸터 혹은 텍스트 상자에 이미지를 저장할 수 있습니다. 콜백은 모든 이미지를 감지하므로 **보이는 이미지뿐만 아니라 모든** 그림을 추출합니다. 본문 이미지만 원한다면 `args.ImageIndex`로 필터링하거나 `args.ImageType`을 검사하세요.

## Export Word document as markdown – Verifying the result

프로그램을 실행한 뒤, `output.md`를 任意의 Markdown 뷰어에서 열어 보세요. 다음과 같은 내용이 표시될 것입니다:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

이미지 링크가 우리가 만든 **Images** 폴더를 가리키는 것을 확인하세요. 이것이 성공적인 **export Word document as markdown** 작업의 특징입니다.

### Quick sanity check

- VS Code 미리보기 창에서 Markdown 파일이 오류 없이 열리나요? ✅  
- GitHub에서 파일을 볼 때 모든 그림이 표시되나요? ✅  
- `Images` 디렉터리에 원본 `.docx`의 그림당 하나씩 파일이 들어 있나요? ✅  

위 검사 중 하나라도 실패하면 `ResourceSavingCallback` 로직을 다시 확인하고 `YOUR_DIRECTORY` 자리표시자가 쓰기 가능한 위치를 가리키는지 확인하세요.

## Common pitfalls and how to avoid them

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **이미지가 나타나지 않음** | `ResourceSavingCallback`이 할당되지 않아 콜백이 전혀 실행되지 않음. | `doc.Save`를 호출하기 **전에** 콜백을 할당하세요. |
| **이미지 폴더가 비어 있음** | `args.Cancel = true`가 모든 리소스에 잘못 설정됨. | CSS(`ResourceType.CssStyleSheet`)만 취소하고, 이미지는 그대로 두세요. |
| **Windows에서 파일 경로가 너무 김** | 깊게 중첩된 폴더와 GUID 조합으로 경로 길이가 260자를 초과할 수 있음. | 폴더 구조를 얕게 유지하거나 Windows 10 이상에서 긴 경로 지원을 활성화하세요. |
| **중복 이미지 이름** | `DateTime.Now.Ticks`를 사용하면 빠른 루프에서 충돌 가능. | 고유성을 위해 `Guid.NewGuid()`를 사용하세요. |

## Wrap‑up

우리는 이제 **docx를 markdown으로 변환**, **docx에서 이미지를 저장**, 그리고 **Word 파일에서 이미지를 추출**하면서 **Word 문서를 markdown으로 내보내는** 과정을 깔끔하고 반복 가능한 방식으로 수행했습니다. 전체 과정은 Aspose.Words의 `ResourceSavingCallback`에 기반하며, 이를 통해 모든 외부 자산을 세밀하게 제어할 수 있습니다.

### What’s next?

- **Markdown 스타일링** – Jekyll이나 Hugo용 front‑matter 블록을 추가하세요.  
- **파이프라인 자동화** – 이 코드를 Azure DevOps 또는 GitHub Action 단계에 삽입하세요.  
- **표와 각주 처리** – `ExportTableBorderStyles`와 같은 다른 `MarkdownSaveOptions` 플래그를 탐색하세요.  

폴더 구조를 조정하거나 이미지 압축을 추가하고, `MarkdownSaveOptions`를 `HtmlSaveOptions`로 교체해 출력 형식을 HTML로 바꾸는 등 자유롭게 변형해 보세요. **convert docx to markdown**에 대한 탄탄한 기반이 있다면 가능성은 무한합니다.

Happy coding, and may your documentation always stay both beautiful **and** machine‑readable!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하며, 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 돕습니다.

- [Word 이미지 저장 – Aspose로 Word를 Markdown으로 변환](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Word를 Markdown으로 변환 – 이미지를 Base64로 삽입](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [DOCX를 Markdown으로 변환할 때 이미지 이름 바꾸는 방법](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}