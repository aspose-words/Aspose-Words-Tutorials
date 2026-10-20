---
category: general
date: 2026-04-28
description: Word를 markdown으로 변환할 때 마크다운 이미지 상대 경로를 설정하는 방법, Word에서 이미지를 추출하는 방법,
  그리고 내보낸 이미지용 resources 폴더를 만드는 방법을 배워보세요.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: ko
og_description: Word를 markdown으로 변환하면서 마크다운 이미지 상대 경로를 설정하고, Word에서 이미지를 추출하며, 내보낸
  이미지를 위한 resources 폴더를 생성합니다.
og_title: 마크다운 이미지 상대 경로 – Word를 마크다운으로 변환
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: 마크다운 이미지 상대 경로 – 워드에서 마크다운으로 변환
url: /ko/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown 이미지 상대 경로 – Word를 Markdown으로 변환

Word를 markdown으로 변환할 때 **markdown 이미지 상대 경로**가 필요했던 적이 있나요? 당신만 그런 것이 아닙니다. 대부분의 개발자는 생성된 Markdown이 평면 폴더에 이미지를 가리키게 되어 정적 사이트나 GitHub 저장소에서 기대하는 상대 링크 구조가 깨지는 문제에 부딪힙니다.

이 튜토리얼에서는 **Word에서 이미지 추출**, **리소스 폴더 생성**, 그리고 이미지 참조를 깔끔한 *markdown 이미지 상대 경로*로 재작성하는 완전한 엔드‑투‑엔드 솔루션을 단계별로 살펴봅니다. 최종적으로는 바로 게시할 수 있는 `.md` 파일과 원본 `.docx`에서 추출된 모든 그림이 정리된 `Resources` 디렉터리를 얻게 됩니다.

> **얻을 수 있는 것:** 외부 스크립트 없이 단일 C# 프로그램, 각 부분이 왜 중요한지에 대한 명확한 설명, 그리고 여러분의 프로젝트에 바로 복사‑붙여넣기 할 수 있는 실용적인 팁 몇 가지.

---

## 사전 요구 사항

- **.NET 6.0** 이상이 설치되어 있어야 합니다(.NET Framework 4.7+도 대상이 될 수 있지만, 새 프로젝트에는 .NET 6이 가장 적합합니다).
- **Aspose.Words for .NET** (작성 시점 최신 NuGet 패키지, 버전 23.12). 다음과 같이 설치합니다:
  ```bash
  dotnet add package Aspose.Words
  ```
- 실제로 이미지가 포함된 Word 문서—예를 들어 `WithImages.docx`.
- 출력 markdown과 이미지를 저장할 폴더, 예시: `C:\Projects\MarkdownExport`.

추가 라이브러리는 필요하지 않으며, 나머지는 모두 Aspose.Words가 처리합니다.

---

## Step 1: 원본 Word 문서 로드 (Word를 markdown으로 변환하기 위한 시작점)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Why this matters:* 문서를 로드하면 내부 노드 트리에 접근할 수 있게 되며, 여기에는 나중에 **export images from docx**가 필요한 이미지 파트가 포함됩니다. 로드에 실패하면 이후 단계가 전혀 실행되지 않으므로 경로와 파일 권한을 반드시 확인하세요.

---

## Step 2: `MarkdownSaveOptions`를 사용자 콜백으로 구성 (리소스 폴더 생성의 핵심)

`ResourceSavingCallback`을 사용하면 Aspose.Words가 이미지 파일을 쓰려 할 때마다 개입할 수 있습니다. 콜백 내부에서 **Resources 하위 폴더**를 만들고, 생성된 markdown이 *markdown 이미지 상대 경로*를 사용하도록 참조를 조정합니다.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

`resourcesFolder`를 콜백 생성자의 매개변수로 전달했으므로 폴더 경로를 유연하게 유지할 수 있고, 코드 전반에 문자열을 하드코딩하는 일을 피할 수 있습니다.

---

## Step 3: **리소스 폴더 생성** 및 경로 재작성 콜백 구현

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Why this works:* `args.Stream`에는 원시 이미지 바이트가 들어 있습니다. 이를 `Resources` 폴더 안의 파일에 복사함으로써 **export images from docx**를 안전하게 수행합니다. 그런 다음 `args.ResourceFileName`을 상대 URL(`Resources/image.png`)로 교체합니다. 이후 Aspose.Words가 markdown을 쓸 때 정확히 그 문자열을 삽입해 원하는 *markdown 이미지 상대 경로*를 얻을 수 있습니다.

---

## Step 4: 생성된 Markdown 확인 (최종 출력 예시)

텍스트 편집기에서 `Doc.md`를 열어보세요. 다음과 비슷한 내용이 표시됩니다:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

중요한 점은 각 이미지 참조가 `Resources/...`를 가리키고 있다는 것입니다—우리가 원했던 **markdown 이미지 상대 경로**가 바로 그것입니다.

![markdown 이미지 상대 경로 예시](example.png "markdown 이미지 상대 경로 예시")

*Tip:* VS Code 미리보기, GitHub, 혹은 정적 사이트 생성기와 같이 상대 링크를 지원하는 뷰어에서 markdown을 열면 별도 설정 없이도 그림이 올바르게 표시됩니다.

---

## Step 5: Common pitfalls and pro‑tips

| 문제 | 발생 원인 | 해결 방법 |
|-------|----------------|---------------|
| 이미지가 `Resources`가 아닌 루트 폴더에 저장됨 | 콜백이 연결되지 않았거나 `args.ResourceFileName`이 덮어쓰기되지 않음 | `doc.Save`를 호출하기 **전** `ResourceSavingCallback`이 설정되어 있는지 확인 |
| 파일 이름에 금지 문자 포함 | Word가 이미지 이름에 공백이나 유니코드 기호를 사용할 때 발생 | 콜백 내부에서 `Path.GetInvalidFileNameChars()`를 사용해 `args.ResourceFileName`을 정리 |
| 대용량 문서 처리 시간이 오래 걸림 | 각 이미지를 동기식으로 기록하기 때문 | .NET 6 이상에서 비동기 I/O(`await args.Stream.CopyToAsync(fileStream)`)로 전환 |
| markdown을 이동하면 상대 경로가 깨짐 | 경로가 markdown 파일 위치를 기준으로 상대적이기 때문 | `Doc.md`와 `Resources` 폴더를 함께 두거나, 콜백에서 다른 상대 접두사(e.g., `../assets`)를 사용하도록 조정 |

---

## Step 6: Extending the solution (what if you need more control?)

- **다중 출력 포맷:** `MarkdownSaveOptions` 대신 `HtmlSaveOptions` 혹은 `PdfSaveOptions`를 사용해도 동일한 콜백이 적용됩니다—Aspose.Words는 포맷에 관계없이 모든 이미지에 대해 콜백을 호출합니다.
- **맞춤 이미지 명명:** 이미지 이름을 `figure-01.png`처럼 바꾸고 싶다면 파일을 쓰기 전에 `args.ResourceFileName`을 수정하면 됩니다.
- **이미지를 Base64로 임베드:** `args.ResourceFileName`을 데이터 URI(`data:image/png;base64,...`)로 설정하고 파일 쓰기를 건너뛰세요. 단일 파일 markdown을 내보낼 때 유용합니다.

---

## Conclusion

이제 **Word를 markdown으로 변환**, **word에서 이미지 추출**, **리소스 폴더 생성**, 그리고 모든 그림에 대해 깔끔한 **markdown 이미지 상대 경로**를 보장하는 완전한 C# 프로그램을 갖추었습니다. 코드는 자체 포함형이며 최신 Aspose.Words 버전과 호환되고, 최소한의 노력으로 어떤 .NET 프로젝트에도 바로 적용할 수 있습니다.

다음 단계는? 생성된 markdown을 Hugo나 Jekyll 같은 정적 사이트 생성기에 넣어 보거나, 콜백을 수정해 이미지를 직접 Base64 문자열로 임베드해 보세요. SVG 이미지나 매우 큰 파일 같은 특수 케이스가 발생하면 “Common pitfalls” 표를 다시 참고하세요—작은 조정만으로도 대부분 해결됩니다.

행복한 코딩 되시고, markdown이 언제나 올바른 폴더를 가리키길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}