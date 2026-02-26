---
category: general
date: 2026-02-26
description: Word를 markdown으로 변환하고, docx에서 이미지를 추출하며, 스트림을 파일에 복사하는 과정을 한 번에 보여주는
  C# 튜토리얼 폴더 만들기.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: ko
og_description: Create folder C# 튜토리얼은 Word를 마크다운으로 변환하고, docx에서 이미지를 추출하며, 스트림을 파일로
  복사하는 과정을 명확한 코드 예제로 안내합니다.
og_title: 폴더 생성 C# – Word를 Markdown으로 변환하고 이미지 추출
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: C#로 폴더 만들기 – Word를 Markdown으로 변환하고 이미지 추출
url: /ko/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create folder C# – Convert Word to Markdown & Extract Images

Word 문서를 markdown으로 변환하고 모든 그림을 추출하면서 **C#으로 폴더 만들기**가 필요했던 적 있나요? 이런 고민은 혼자만이 아닙니다. 많은 자동화 파이프라인에서 파일 시스템 작업, 포맷 변환, 바이너리 데이터 처리를 한 번에 다루게 됩니다.  

이 가이드에서는 목표 디렉터리를 생성하고, `.docx` 파일을 markdown으로 변환하며, 포함된 이미지를 각각 추출하고, **스트림을 파일로 복사**하는 로직을 사용해 이미지가 원하는 위치에 저장되도록 하는 완전하고 실행 가능한 솔루션을 단계별로 살펴보겠습니다. 외부 스크립트나 수동 작업 없이 순수 C#과 Aspose.Words 라이브러리만으로 구현합니다.

> **얻을 수 있는 것**  
> * markdown과 에셋을 위한 명확한 폴더 구조  
> * 추출된 그림을 올바르게 참조하는 markdown 파일  
> * 어떤 .NET 프로젝트에도 바로 넣을 수 있는 전체 소스 코드  

시작하기 전에 다음을 준비하세요:

* .NET 6.0 (또는 그 이후) SDK – 최신 언어 기능을 사용합니다.  
* **Aspose.Words for .NET** 라이선스 (무료 체험판으로 테스트 가능).  
* Visual Studio 2022 혹은 선호하는 편집기.  

왜 그림을 삽입하지 않고 추출해야 하는지 궁금하다면, 정적 사이트 생성기를 떠올려 보세요. 정적 사이트 생성기는 상대 경로 이미지가 포함된 markdown을 선호하고, 에셋을 전용 폴더에 보관하면 정리도 쉽고 캐시 친화적입니다.

---

## Create folder C# and prepare output structure

먼저 모든 파일이 저장될 디스크상의 위치가 필요합니다. 여기서 **C#으로 폴더 만들기** 작업이 이루어지며, `Directory.CreateDirectory` 덕분에 매우 간단합니다. 이 메서드는 멱등성을 가지고 있어 폴더가 이미 존재해도 예외를 발생시키지 않으므로 추가 검사가 필요 없습니다.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**왜 중요한가요:**  
미리 폴더를 생성해 두면 이후 저장 단계에서 `DirectoryNotFoundException`이 발생하지 않으며, `output/markdown`에 `.md` 파일을, `output/MyImages`에 추출된 모든 그림을 저장한다는 예측 가능한 레이아웃을 확보할 수 있습니다.

> **팁:** 프로그램을 여러 번 실행한다면 이미지 폴더를 먼저 비우는 것이 좋습니다 (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`). 이렇게 하면 오래된 파일이 남는 것을 방지할 수 있습니다.

---

## Convert Word to Markdown using Aspose.Words

디렉터리 구조가 준비되었으니 이제 Word 문서를 markdown으로 변환합니다. Aspose.Words가 무거운 작업을 담당하므로 OpenXML이나 서드파티 변환기를 직접 다룰 필요가 없습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**내부에서 무슨 일이 일어나나요?**  
`MarkdownSaveOptions`가 Aspose에 markdown 구문을 출력하도록 지시합니다. 기본적으로 라이브러리는 이미지들을 markdown 파일과 같은 폴더에 자동 생성된 이름으로 저장합니다. `ResourceSavingCallback`을 제공함으로써 이 동작을 가로채고 **스트림을 파일로 복사**하여 원하는 위치에 저장합니다.

---

## Extract images from DOCX and save them

콜백 클래스는 `IResourceSavingCallback`을 구현합니다. 여기서 `ResourceSavingArgs` 객체를 받아 원본 이미지 스트림과 제안된 파일 이름을 얻습니다. 그런 다음 스트림을 디스크에 쓰고, 필요하면 파일 이름을 바꾸고, Aspose에 처리를 완료했음을 알립니다.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### markdown이 어떻게 보일지

변환이 끝나면 생성된 `output.md`는 다음과 같은 라인을 포함합니다:

```markdown
![Image 1](MyImages/img_picture1.png)
```

`args.ResourceFileName`을 상대 경로로 바꿨기 때문에 markdown은 우리가 만든 폴더를 직접 가리킵니다. 이것이 정적 사이트 생성기가 기대하는 형태입니다.

**예외 상황 처리:**  
*문서에 중복된 이미지 이름이 있을 경우* `img_` 접두사와 원본 이름을 조합하면 보통 충돌을 피할 수 있지만, 절대적인 고유성을 위해 `Guid.NewGuid()`를 추가할 수도 있습니다.

---

## Copy stream to file – handling the image data

왜 `File.WriteAllBytes`를 바로 호출하지 않는지 궁금할 수 있습니다. 답은 **스트림 유연성**에 있습니다. `args.Stream`은 메모리 스트림, 네트워크 스트림 등 다양한 구현일 수 있습니다. `CopyTo`를 사용하면 .NET이 버퍼 크기를 효율적으로 관리하면서 스트림 종류에 구애받지 않고 복사할 수 있습니다.

다음은 필요할 때 언제든지 일반 스트림을 복사할 수 있는 간결한 유틸 메서드입니다:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

`ImageSavingCallback` 내부의 인라인 복사를 `CopyStreamToFile` 호출로 교체하면 단일 책임 원칙을 더 잘 따를 수 있습니다.

---

## Full runnable example

모든 조각을 합치면 명령줄에서 실행할 수 있는 독립형 프로그램이 완성됩니다:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**예상 결과**

* `output/markdown/output.md` – 이미지 참조가 `![Alt text](MyImages/img_picture1.png)` 형태인 markdown 파일.  
* `output/MyImages/` – 원본 `input.docx`에 포함된 각 이미지가 PNG/JPEG 파일로 저장된 폴더.  

markdown을 VS Code, GitHub, 혹은 정적 사이트 생성기 등에서 열면 원본 Word 파일에서 그림이 있던 정확한 위치에 이미지가 렌더링됩니다.

---

## Frequently asked questions & troubleshooting

| Question | Answer |
|----------|--------|
| **What if the target folder already has files?** | `Directory.CreateDirectory`는 기존 파일을 덮어쓰지 않습니다. 깨끗한 실행이 필요하면 파일들을 삭제하고 시작하세요. |
| **How do I handle very large images?** | 스트림 복사는 버퍼링을 자동으로 처리하므로 메모리 사용량을 최소화합니다. 필요하면 `CopyToAsync`를 사용해 비동기 처리도 가능합니다. |
| **Can I customize the markdown image syntax?** | `MarkdownSaveOptions`의 `ImageSavingCallback`에서 `args.ResourceFileName`을 원하는 형태로 조정하면 됩니다. |
| **What if Aspose throws an exception during conversion?** | 예외 메시지를 로그에 기록하고, `try‑catch` 블록으로 변환 과정을 감싸면 문제 원인을 쉽게 파악할 수 있습니다. |
| **Is there a way to process multiple DOCX files in a batch?** | 루프 안에서 위 로직을 호출하고, 각 파일마다 고유한 출력 폴더를 지정하면 배치 처리가 가능합니다. |

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}