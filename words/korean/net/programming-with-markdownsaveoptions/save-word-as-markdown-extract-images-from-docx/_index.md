---
category: general
date: 2026-02-13
description: C#에서 워드를 마크다운으로 저장하고 docx에서 이미지를 추출합니다. docx를 마크다운으로 변환하고, docx에서 이미지를
  저장하며, 리소스를 정리하는 방법을 배워보세요.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- how to extract images
- save images from docx
language: ko
og_description: Word를 마크다운으로 저장하고 docx에서 이미지를 추출하는 완전한 C# 예제. docx를 마크다운으로 변환하고, docx에서
  이미지를 저장하며, 모든 것을 깔끔하게 정리합니다.
og_title: 워드를 마크다운으로 저장 – docx에서 이미지 추출
tags:
- Aspose.Words
- C#
- Markdown conversion
title: 워드를 마크다운으로 저장 – docx에서 이미지 추출
url: /ko/net/programming-with-markdownsaveoptions/save-word-as-markdown-extract-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 markdown으로 저장 – docx에서 이미지 추출

원본 *.docx* 안에 들어 있는 모든 그림을 유지하면서 **Word를 markdown으로 저장**해야 했던 적이 있나요? 정적 사이트 생성기를 만들고 있거나, 레거시 Word 보고서를 Git‑친화적인 형식으로 옮기고 싶을 수도 있습니다. 어느 경우든 공통된 문제는 변환 과정에서 이미지가 사라지거나 깨진 링크가 생긴다는 점입니다.

핵심은—*.docx*의 ZIP 구조를 직접 파고들거나 커스텀 파서를 만들 필요가 없다는 것입니다. Aspose.Words를 사용하면 **docx를 markdown으로 변환**하면서 동시에 **docx에서 이미지를 저장**해 원하는 폴더에 넣을 수 있습니다. 이 가이드에서는 바로 실행 가능한 C# 프로그램 전체를 단계별로 살펴보겠습니다.

이 튜토리얼을 마치면 다음을 얻을 수 있습니다:

* 원본 Word 레이아웃을 그대로 반영한 markdown 파일
* 추출된 모든 이미지를 원본 파일에 나타난 이름 그대로 저장한 “MarkdownResources” 폴더
* PDF, HTML 등 Aspose가 지원하는 다른 형식에도 적용할 수 있는 재사용 가능한 콜백 패턴

> **Prerequisites** – .NET 6+ (또는 .NET Framework 4.7+), 유효한 Aspose.Words 라이선스(또는 무료 체험판), Visual Studio 또는 VS Code가 필요합니다. 추가 NuGet 패키지는 필요하지 않습니다.

---

## 튜토리얼에서 다루는 내용

솔루션을 논리적인 단계로 나눠 설명합니다:

1. **Load the source document** – 변환하려는 *.docx* 파일을 엽니다.  
2. **Create a resource‑saving callback** – 이미지가 저장될 위치를 Aspose에 알려줍니다.  
3. **Configure `MarkdownSaveOptions`** – 콜백을 markdown 내보내기에 연결합니다.  
4. **Save the markdown file** – 한 줄 코드로 전체 작업을 수행합니다.  

각 단계가 왜 중요한지, 폴더 권한 부족 같은 흔한 함정, PNG만 추출하거나 이미지 이름을 커스텀하는 방법 등 엣지 케이스에 대한 팁도 함께 제공합니다.

## Step 1 – Load the source document

먼저 Word 파일을 가리키는 `Document` 인스턴스를 생성해야 합니다. Aspose는 *.docx*의 ZIP 형식을 추상화하여 일반 문서 객체처럼 다룰 수 있게 해줍니다.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to where your .docx lives.
const string inputPath = @"YOUR_DIRECTORY\input.docx";

Document doc = new Document(inputPath);
```

*Why this matters*: 파일 경로가 잘못되면 Aspose가 `FileNotFoundException`을 발생시키고 파이프라인 전체가 중단됩니다. 상수(또는 설정값)를 사용하면 코어 로직을 건드리지 않고도 파일을 쉽게 교체할 수 있습니다.

> **Pro tip** – 파일이 사용자 입력일 경우 `try/catch`로 로드를 감싸면 스택 트레이스 대신 친절한 오류 메시지를 표시할 수 있습니다.

## Step 2 – Define a callback that decides where each image is saved

Aspose는 `IResourceSavingCallback`을 통해 저장 과정을 후킹할 수 있습니다. 콜백은 각 외부 리소스(이미지, CSS 등)에 대해 `ResourceSavingArgs` 객체를 전달받습니다. 이를 이용해 이미지마다 전용 폴더에 원본 파일명을 유지하면서 저장합니다.

```csharp
// Step 2: Define a callback that decides where each image is saved.
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a path like: YOUR_DIRECTORY\MarkdownResources\image001.png
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
        Directory.CreateDirectory(resourcesFolder); // ensures the folder exists

        string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Tell Aspose where to write the file.
        args.ResourceFilePath = imagePath;
        args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
    }
}
```

*Why this matters*: 콜백이 없으면 Aspose는 이미지들을 markdown 파일과 같은 폴더에 일반적인 이름으로 저장합니다. 경로를 직접 제어하면 프로젝트 구조를 깔끔하게 유지하고 이름 충돌을 방지할 수 있습니다.

**Edge case** – 일부 Word 파일은 동일한 이미지를 여러 번 삽입합니다. `args.ResourceFileName`에는 이미 고유 해시가 포함돼 있어 덮어쓰기가 발생하지 않습니다. 순차적인 이름 지정이 필요하면 콜백 내부에 정적 카운터를 두어 관리하면 됩니다.

## Step 3 – Configure Markdown save options to use the custom callback

이제 콜백을 markdown 내보내기에 연결합니다. `MarkdownSaveOptions`에서는 헤딩 레벨, 코드 블록 fence, 이미지 Base64 임베드 여부 등도 조정할 수 있습니다(여기서는 Base64 임베드를 사용하지 않습니다).

```csharp
// Step 3: Configure Markdown save options to use the custom callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our resource‑saving logic.
    ResourceSavingCallback = new MyMarkdownResourceCallback(),

    // Optional: keep original line breaks for better diff‑friendliness.
    ExportHeadersFooters = false,
    ExportImagesAsBase64 = false
};
```

*Why this matters*: `ResourceSavingCallback` 속성은 문서 모델과 파일 시스템 사이의 다리 역할을 합니다. 이를 설정하지 않으면 이미지가 사라지고, markdown은 존재하지 않는 파일을 참조하게 됩니다.

## Step 4 – Save the document as Markdown, invoking the callback for each resource

마지막으로 Aspose에게 markdown 파일을 작성하도록 요청합니다. 라이브러리는 각 이미지마다 콜백을 호출해 이미지 파일을 저장하고, markdown에는 상대 경로 링크를 삽입합니다.

```csharp
// Step 4: Save the document as Markdown, invoking the callback for each resource.
const string outputPath = @"YOUR_DIRECTORY\output.md";

doc.Save(outputPath, mdOptions);
```

코드 실행이 끝나면 디스크에 두 가지가 생성됩니다:

1. **output.md** – 원본 Word 내용의 Markdown 표현  
2. **MarkdownResources/** – 추출된 모든 이미지가 들어 있는 폴더(예: `image001.png`, `image002.jpg`)

**Verification** – `output.md`를 任意의 markdown 뷰어에서 열어보세요. `![image001.png](MarkdownResources/image001.png)`와 같은 이미지 태그가 보일 것입니다. 이미지가 정상적으로 렌더링되면 성공한 것입니다.

## Common variations and what‑if scenarios

### 1. Want images embedded as Base64?

`MarkdownSaveOptions`에서 `ExportImagesAsBase64 = true`로 설정하면 이미지가 인라인 data URI 형태로 하나의 markdown 파일에 포함됩니다. 단일 파일 문서에는 편리하지만 파일 크기가 크게 늘어납니다.

### 2. Need only PNG images?

확장자를 기준으로 필터링하도록 콜백을 수정합니다:

```csharp
if (Path.GetExtension(args.ResourceFileName).Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Save as before.
}
else
{
    // Skip non‑PNG resources.
    args.Cancel = true;
}
```

### 3. Changing the output folder at runtime

명령줄 인수나 설정 파일을 통해 폴더 경로를 전달하고, `resourcesFolder`를 구성할 때 해당 변수를 사용합니다. 이렇게 하면 도구를 여러 프로젝트에서 재사용할 수 있습니다.

### 4. Handling large documents

대용량 Word 파일의 경우 전체를 메모리에 로드하지 않도록 스트리밍 출력을 고려하세요. Aspose의 `Document` 클래스는 이미 낮은 메모리 사용량을 제공하지만, `LoadOptions`에서 `MemoryOptimization = MemoryOptimization.MemoryOptimized`를 설정하면 더욱 최적화됩니다.

## Full, runnable example

아래는 새 콘솔 앱(`dotnet new console`)에 복사·붙여넣기 할 수 있는 전체 프로그램입니다. `YOUR_DIRECTORY`를 실제 경로로 바꾸고 Aspose.Words NuGet 패키지를 추가하세요(`dotnet add package Aspose.Words`).

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdown
{
    // Step 2: Callback that saves each image into a dedicated folder.
    class MyMarkdownResourceCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
            Directory.CreateDirectory(resourcesFolder);

            string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFilePath = imagePath;
            args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Load the source document.
            const string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);

            // Step 3: Configure the markdown options.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyMarkdownResourceCallback(),
                ExportImagesAsBase64 = false,
                ExportHeadersFooters = false
            };

            // Step 4: Save as markdown.
            const string outputPath = @"YOUR_DIRECTORY\output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images folder: {Path.Combine("YOUR_DIRECTORY", "MarkdownResources")}");
        }
    }
}
```

**Expected output** (콘솔에 표시):

```
Conversion complete!
Markdown file: C:\Projects\MyDocs\output.md
Images folder: C:\Projects\MyDocs\MarkdownResources
```

`output.md`를 열면 `MarkdownResources` 폴더를 가리키는 이미지 참조가 포함된 markdown 구문을 확인할 수 있습니다. 모든 이미지가 원본 파일명 그대로 유지되므로 필요 시 원본 Word 파일과 쉽게 매핑할 수 있습니다.

## Conclusion

우리는 Aspose.Words를 사용해 **Word를 markdown으로 저장**하면서 동시에 **docx에서 이미지를 추출**하는 방법을 살펴보았습니다. 핵심은 `IResourceSavingCallback`이며, 이를 통해 각 리소스가 저장되는 위치를 완전히 제어함으로써 markdown을 깔끔하게 유지하고 이미지 관리를 효율적으로 할 수 있습니다.

단일, 독립 실행형 프로그램으로 다음을 수행할 수 있습니다:

* 모든 *.docx*를 깔끔한 markdown으로 변환 (`convert docx to markdown`)  
* 모든 그림을 보존 (`save images from docx`)  
* 다운스트림 파이프라인을 위한 출력 레이아웃을 맞춤 설정

다음 단계는? 동일한 콜백 패턴을 사용해 HTML이나 PDF로 변환해 보거나, CI 작업에 연결해 Word 보고서를 자동으로 정적 사이트 저장소와 동기화해 보세요. 가능성은 무궁무진하며, 이제 튼튼한 기반이 마련되었습니다.

궁금한 점이나 멋진 팁이 있으면 아래에 댓글을 남겨 주세요—행복한 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}