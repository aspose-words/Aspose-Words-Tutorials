---
category: general
date: 2026-05-26
description: Word를 Markdown으로 변환하고 docx에서 이미지를 추출할 때 assets 폴더를 생성하세요. Aspose.Words에서
  이미지 스트림을 작성하고 리소스를 처리하는 방법을 배우세요.
draft: false
keywords:
- create assets folder
- convert word to markdown
- extract images from docx
- convert docx with images
- write image stream
language: ko
og_description: Word를 Markdown으로 변환할 때 assets 폴더를 생성하세요. 이 단계별 가이드를 따라 docx에서 이미지를
  추출하고 Aspose.Words로 이미지 스트림을 작성하세요.
og_title: Word를 Markdown으로 변환하기 위한 Assets 폴더 만들기
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create assets folder while you convert Word to Markdown and extract
    images from docx. Learn how to write image stream and handle resources in Aspose.Words.
  headline: Create Assets Folder for Convert Word to Markdown
  type: TechArticle
tags:
- Aspose.Words
- C#
- Markdown
- Docx
- Image Extraction
title: 워드 파일을 마크다운으로 변환하기 위한 에셋 폴더 만들기
url: /ko/net/programming-with-markdownsaveoptions/create-assets-folder-for-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환하기 위한 Assets 폴더 만들기

Word를 Markdown으로 변환할 때 **assets 폴더를 만들** 필요가 있었나요? DOCX에서 이미지를 추출한다면, 해당 폴더를 올바르게 설정하는 것이 원활한 변환의 첫 단계입니다.  

이 튜토리얼에서는 사진이 포함된 `.docx` 파일을 Markdown 파일로 변환하면서, 사진들을 자동으로 **assets** 하위 디렉터리로 추출하는 전체 과정을 단계별로 안내합니다. 끝까지 따라오시면 **docx에서 이미지 추출**, **이미지 스트림 쓰기** 파일 방법, 그리고 Markdown 참조를 깔끔하게 유지하는 방법을 알게 됩니다.

## 배울 내용

- **Aspose.Words** 를 Markdown 내보내기에 맞게 설정하는 방법  
- **assets 폴더를 실시간으로 생성** 하는 정확한 코드  
- **ResourceSavingCallback** 을 이용해 **docx에서 이미지 추출** 및 **이미지 스트림 쓰기** 파일을 구현하는 방법  
- 생성된 Markdown이 이미지와 올바르게 연결되는지 확인하는 방법  
- 중복 이미지 이름이나 쓰기 권한 부족 등 예외 상황을 처리하는 팁  

> **Prerequisites** – .NET 6+ (또는 .NET Framework 4.7.2+)와 Aspose.Words for .NET 라이브러리에 대한 참조가 필요합니다. 다른 서드파티 도구는 필요하지 않습니다.

---

## Markdown 변환을 위한 Assets 폴더 만들기

먼저 **assets** 디렉터리가 출력 Markdown 파일 옆에 존재하는지 보장해야 합니다. 이 폴더는 변환 과정에서 추출되는 모든 이미지를 보관합니다.

```csharp
// Ensure the assets folder exists before any conversion starts.
string assetsFolder = Path.Combine(outputDirectory, "assets");
Directory.CreateDirectory(assetsFolder);   // This call is idempotent – it won’t throw if the folder already exists.
```

> **Pro tip:** `Directory.CreateDirectory` 는 여러 번 호출해도 안전합니다. 폴더가 없을 때만 생성하므로 “폴더가 이미 존재합니다” 오류 없이 변환을 여러 번 실행할 수 있습니다.

---

## 이미지 추출과 함께 Word를 Markdown으로 변환하기

이제 Aspose.Words 를 `MarkdownSaveOptions` 객체에 연결합니다. 핵심은 `ResourceSavingCallback` 입니다. 콜백 내부에서 **이미지 스트림** 데이터를 앞서 만든 assets 폴더에 **쓰기** 하고, 파일 이름을 재작성해 Markdown 파일이 올바른 위치를 가리키도록 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// -------------------------------------------------------------------
// 1️⃣ Load the source .docx that contains images.
// -------------------------------------------------------------------
Document doc = new Document(@"YOUR_DIRECTORY\WithImages.docx");

// -------------------------------------------------------------------
// 2️⃣ Configure Markdown save options with a custom callback.
// -------------------------------------------------------------------
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This delegate runs for every embedded resource (images, PDFs, etc.).
    ResourceSavingCallback = new ResourceSavingCallback(resourceInfo =>
    {
        // 2a️⃣ Build the full path for the output file inside the assets folder.
        string fileName = Path.GetFileName(resourceInfo.FileName); // Keep the original name.
        string outputPath = Path.Combine(assetsFolder, fileName);

        // 2b️⃣ Write the incoming stream (the image data) to disk.
        using (FileStream outStream = File.Create(outputPath))
        {
            // The stream contains the raw bytes of the image.
            resourceInfo.Stream.CopyTo(outStream);
        }

        // 2c️⃣ Update the reference that will appear in the Markdown file.
        // This tells Markdown to look for the image under the "assets" sub‑folder.
        resourceInfo.FileName = $"assets/{fileName}";
    })
};

// -------------------------------------------------------------------
// 3️⃣ Save the document as Markdown.
// -------------------------------------------------------------------
string markdownPath = Path.Combine(outputDirectory, "DocWithImages.md");
doc.Save(markdownPath, mdOptions);
```

### 왜 이렇게 동작하나요?

- **`ResourceSavingCallback`** 은 *모든* 임베디드 리소스에 대해 호출되므로 별도의 파싱 로직 없이 자동으로 **docx에서 이미지 추출** 할 수 있습니다.  
- `resourceInfo.FileName = "assets/" + fileName;` 으로 설정하면 생성된 Markdown에 `![Image](assets/picture.png)` 와 같은 상대 경로가 들어갑니다.  
- 콜백은 **이미지 스트림이 준비된 후** 실행되므로, 안전하게 **이미지 스트림을** 디스크에 **쓰기** 할 수 있습니다.

---

## 결과 확인하기

코드가 실행된 후 `YOUR_DIRECTORY` 에는 두 가지가 보여야 합니다:

1. `DocWithImages.md` – 이미지 참조가 `![Image](assets/picture.png)` 형태인 Markdown 파일.  
2. 실제 이미지 파일(`picture.png`, `photo.jpg`, …)을 포함한 `assets` 폴더.

VS Code, GitHub, 혹은 정적 사이트 생성기 등 어떤 뷰어에서든 Markdown 파일을 열어보세요. 사진이 정상적으로 표시되면 **이미지가 포함된 docx 변환**에 성공한 것입니다.

---

## 흔히 발생하는 예외 상황 처리

| 상황 | 해결 방법 |
|-----------|------------|
| **중복 이미지 이름** (예: 동일한 `image1.png` 파일이 두 개) | 저장하기 전에 `fileName` 에 GUID 또는 증가 카운터를 붙입니다: <br>`string uniqueName = $"{Path.GetFileNameWithoutExtension(fileName)}_{Guid.NewGuid()}{Path.GetExtension(fileName)}";` |
| **읽기 전용 소스 폴더** | 쓰기 권한이 있는 계정으로 실행하거나 `assetsFolder` 를 사용자 쓰기 가능한 위치(예: `%TEMP%`)로 변경합니다. |
| **대용량 문서** (수백 개 이미지) | 배치 스트리밍 변환을 고려하거나 프로세스 메모리 제한을 늘립니다; Aspose.Words 는 큰 파일을 처리하지만 파일 시스템이 병목이 될 수 있습니다. |
| **이미지가 아닌 리소스** (예: 임베디드 PDF) | 동일한 콜백이 작동하지만 Markdown에서는 PDF를 직접 삽입할 수 없으니 링크 형식을 수동으로 조정해야 합니다. |

---

## 전체 작업 예제 (복사‑붙여넣기 가능)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class WordToMarkdownWithAssets
{
    static void Main()
    {
        // -------------------------------------------------------------------
        // Define input and output locations.
        // -------------------------------------------------------------------
        string inputPath   = @"C:\Temp\WithImages.docx";
        string outputDir   = @"C:\Temp\Output";
        string markdownPath = Path.Combine(outputDir, "DocWithImages.md");
        string assetsFolder = Path.Combine(outputDir, "assets");

        // -------------------------------------------------------------------
        // Step 1: Ensure the assets folder exists.
        // -------------------------------------------------------------------
        Directory.CreateDirectory(assetsFolder);

        // -------------------------------------------------------------------
        // Step 2: Load the Word document.
        // -------------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -------------------------------------------------------------------
        // Step 3: Set up Markdown save options with a resource callback.
        // -------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ResourceSavingCallback(resourceInfo =>
            {
                // Determine a safe file name.
                string originalName = Path.GetFileName(resourceInfo.FileName);
                string outputPath   = Path.Combine(assetsFolder, originalName);

                // Write the image (or other binary) stream to the assets folder.
                using (FileStream outStream = File.Create(outputPath))
                {
                    resourceInfo.Stream.CopyTo(outStream);
                }

                // Update the Markdown reference.
                resourceInfo.FileName = $"assets/{originalName}";
            })
        };

        // -------------------------------------------------------------------
        // Step 4: Save as Markdown.
        // -------------------------------------------------------------------
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Assets folder: {assetsFolder}");
    }
}
```

**예상 출력** (콘솔):

```
Conversion complete!
Markdown: C:\Temp\Output\DocWithImages.md
Assets folder: C:\Temp\Output\assets
```

`DocWithImages.md` 를 열면 `assets/…` 로 연결된 이미지 링크를 확인할 수 있습니다. 이미지 파일 자체는 방금 만든 `assets` 디렉터리에 저장됩니다.

---

## 결론

우리는 **Word를 Markdown으로 변환**하면서 **assets 폴더를 자동으로 생성**하고, **docx에서 이미지 추출**을 위해 **이미지 스트림을 쓰는** 방법을 보여주었습니다. 완전하고 실행 가능한 예제는 Aspose.Words 를 사용해 **이미지가 포함된 docx 변환**을 수행하면서 Markdown 내용과 연관 리소스를 한 번에 깔끔하게 처리하는 권장 방식을 입증합니다.

다음 단계가 궁금하신가요? 콜백을 커스터마이징해 이미지 파일명을 alt‑text 기반으로 바꾸거나, 같은 assets‑folder 로직을 재사용해 HTML이나 PDF 같은 다른 출력 형식에도 적용해 보세요. 이 패턴은 모든 문서‑텍스트 변환 시나리오에 잘 확장됩니다.

문제가 발생하거나 개선 아이디어가 있으면 아래에 댓글을 남겨 주세요.


## 관련 튜토리얼

- [Word 이미지 저장 – Aspose를 사용한 Word를 Markdown으로 변환](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Word를 Markdown으로 변환 – 이미지를 Base64로 삽입](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [C#에서 Word를 Markdown으로 변환 – 이미지 추출 전체 가이드](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-in-c-full-guide-with-image-extracti/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}