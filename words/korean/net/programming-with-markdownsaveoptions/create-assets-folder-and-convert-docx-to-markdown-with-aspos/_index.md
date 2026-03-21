---
category: general
date: 2026-03-21
description: DOCX를 Markdown으로 변환할 때 assets 폴더를 생성합니다. Word에서 이미지를 추출하고 C#으로 Word를
  Markdown으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- create assets folder
- convert docx to markdown
- extract images from word
- extract embedded images
- save word as markdown
language: ko
og_description: DOCX를 Markdown으로 변환할 때 assets 폴더를 생성합니다. 이 튜토리얼에서는 Word에서 이미지를 추출하고
  C#을 사용하여 Word를 Markdown으로 저장하는 방법을 보여줍니다.
og_title: assets 폴더 생성 및 DOCX를 Markdown으로 변환 – 완전 가이드
tags:
- Aspose.Words
- C#
- Document Conversion
title: assets 폴더를 만들고 Aspose.Words로 DOCX를 Markdown으로 변환하기
url: /ko/net/programming-with-markdownsaveoptions/create-assets-folder-and-convert-docx-to-markdown-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create assets folder and convert DOCX to Markdown with Aspose.Words

Word 파일을 Markdown으로 변환할 때 **assets 폴더를 만들** 필요가 있었나요? 여러분만 그런 것이 아닙니다—개발자들은 이미지 정리를 어떻게 할지, *docx를 markdown으로 변환*할 때 항상 물어봅니다. 좋은 소식은 Aspose.Words가 한 번의 실행으로 두 작업을 모두 깔끔하게 프로그래밍 방식으로 처리할 수 있다는 점입니다.

이 튜토리얼에서는 전체 과정을 단계별로 살펴봅니다: `.docx` 로드, Markdown 내보내기 옵션 구성, 포함된 이미지 추출, 그리고 최종적으로 `assets` 디렉터리를 참조하는 `.md` 파일로 저장합니다. 끝까지 따라오면 *Word에서 이미지를 추출*하고 *Word를 markdown으로 저장*하는 재사용 가능한 스니펫을 얻게 됩니다.

## What You’ll Need

- **Aspose.Words for .NET** (최신 버전, 예: 24.10).  
- .NET 개발 환경 (Visual Studio, Rider, 혹은 VS Code).  
- 최소 하나의 그림이 포함된 샘플 `input.docx`—그렇지 않으면 *포함된 이미지 추출* 단계가 동작하지 않습니다.

다른 서드파티 라이브러리는 필요하지 않습니다; 모든 것이 Aspose.Words 안에 포함되어 있습니다.

---

## Create assets folder and set up Markdown conversion

먼저 Word 문서에서 추출된 모든 이미지가 들어갈 전용 폴더가 필요합니다. 정적 사이트 생성기에서 흔히 보는 “assets” 버킷이라고 생각하면 됩니다. 파일 이름은 Aspose.Words가 결정하도록 하고, 앞에 폴더 경로를 붙여줍니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// 1️⃣ Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// 2️⃣ Prepare Markdown save options with a callback that decides where resources go
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        // 👉 Define the folder that will hold every extracted image
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder); // creates it if it doesn't exist

        // 👉 Tell Aspose to place the current resource inside that folder
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **Why a callback?**  
> `ResourceSavingCallback` 은 각 포함된 객체(이미지, OLE 객체 등)가 저장될 때마다 호출됩니다. 이를 가로채면 **Word에서 이미지를 추출**하면서 바로 저장할 수 있어, 나중에 파일을 이동시키는 작업이 필요 없게 됩니다. 이렇게 하면 *save word as markdown* 단계가 원자적으로 수행되고 I/O 오버헤드가 감소합니다.

---

## Step 1: Load the DOCX document  

*docx를 markdown으로 변환*하기 전에 `Document` 인스턴스가 필요합니다. 생성자는 경로, 스트림, 혹은 바이트 배열을 받을 수 있으니 파이프라인에 맞는 방식을 선택하세요.

```csharp
// Example using a relative path; adjust for your environment
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Tip:** 웹 API에서 업로드를 처리하는 경우, 임시 파일을 만들지 않고 업로드된 `Stream`을 바로 전달하면 됩니다.

---

## Step 2: Configure MarkdownSaveOptions – the heart of extraction  

`MarkdownSaveOptions` 은 변환 동작을 세밀하게 제어할 수 있게 해줍니다. 우리 목표와 가장 관련 깊은 속성은 이미 설정한 `ResourceSavingCallback` 입니다. 이미지 포맷, 링크 스타일 등도 여기서 조정할 수 있습니다.

```csharp
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // Ensure images are saved as PNG by default (you can change this)
    ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

    // The callback defined earlier handles the assets folder creation
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **What if two images share the same name?**  
> Aspose 가 자동으로 숫자 접미사(`image.png`, `image_1.png`, …)를 붙여 주므로 파일이 겹쳐서 사라지는 일은 없습니다.

---

## Step 3: Define the assets folder and handle image paths  

콜백은 *리소스당 한 번* 실행됩니다. 여기서 우리는:

1. `Path.Combine` 을 사용해 `assets` 폴더의 절대 경로를 만든다.  
2. `Directory.CreateDirectory` 를 호출한다—이 메서드는 여러 번 호출해도 안전하며, 첫 호출 시에만 폴더가 생성됩니다.  
3. `info.FileName` 을 전체 경로로 덮어써서 Markdown 라이터가 올바른 상대 링크를 기록하도록 한다.

```csharp
ResourceSavingCallback = new ResourceSavingCallback(info =>
{
    string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
    Directory.CreateDirectory(assetsFolder);
    info.FileName = Path.Combine(assetsFolder, info.FileName);
})
```

> **Pro tip:** Markdown 파일이 웹 친화적인 URL(예: `/static/assets/`)을 사용하도록 하려면 `Path.Combine` 대신 원하는 상대 URL을 조합하는 문자열을 사용하면 됩니다.

---

## Step 4: Save the document as Markdown  

이제 모든 설정이 끝났으니 마지막은 간단히 `Save` 호출입니다. Aspose 가 Word DOM을 순회하면서 Markdown 구문을 `output.md`에 기록하고, 각 이미지를 앞서 만든 `assets` 디렉터리에 저장합니다.

```csharp
// 5️⃣ Perform the conversion – this writes both the .md file and the images
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

프로세스가 끝나면 다음과 같은 폴더 구조를 확인할 수 있습니다:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ assets/
   ├─ image1.png
   └─ image2.png
```

*Figure 1: Folder layout after conversion (alt text: “create assets folder diagram”).*  

Markdown 파일에는 `![](assets/image1.png)` 와 같은 링크가 들어가며, 이는 대부분의 정적 사이트 생성기가 기대하는 형태와 정확히 일치합니다.

---

## Full Working Example  

아래는 콘솔 앱으로 바로 실행할 수 있는 복사‑붙여넣기용 프로그램입니다. `YOUR_DIRECTORY` 를 소스 파일이 위치한 경로로 바꾸세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 👉 Step 1 – Load the DOCX you want to convert
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 👉 Step 2 – Set up Markdown options and the assets folder callback
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
        {
            // Optional: force PNG output for all images
            ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

            // This callback runs for each extracted resource (image, etc.)
            ResourceSavingCallback = new ResourceSavingCallback(info =>
            {
                // 👉 Define where the extracted images will live
                string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
                Directory.CreateDirectory(assetsFolder);

                // 👉 Save each image inside that folder
                info.FileName = Path.Combine(assetsFolder, info.FileName);
            })
        };

        // 👉 Step 3 – Save as Markdown; assets are created automatically
        document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);

        // 🎉 Done! Check YOUR_DIRECTORY for output.md and the assets folder.
    }
}
```

### Expected Result

- `output.md` 에는 원본 Word의 제목, 글머리표 목록, 표 등이 Markdown 형태로 그대로 반영됩니다.  
- `input.docx` 의 모든 그림이 `![](assets/<imageName>.png)` 형태로 Markdown 파일에 삽입됩니다.  
- `assets` 폴더에는 실제 PNG 파일이 들어 있어, 어떤 정적 사이트 호스트에서도 바로 제공할 수 있습니다.

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if the DOCX has no images?** | 콜백이 한 번도 호출되지 않으므로 `assets` 폴더는 비어 있게 됩니다. 별다른 문제가 없습니다. |
| **Can I change the image format to JPEG?** | 가능합니다—`MarkdownSaveOptions` 안에서 `ImageSavingFormat = ImageSaveOptions.SaveFormat.Jpeg` 로 설정하면 됩니다. |
| **Do I need to clean up the assets folder on subsequent runs?** | 동일한 Markdown 파일을 다시 생성한다면 오래된 파일을 삭제하거나 덮어쓰는 것이 좋습니다. 그렇지 않으면 사용되지 않는 이미지가 쌓일 수 있습니다. |
| **How does relative linking work on different OSes?** | 물리 경로는 `Path.Combine` 로 만들고, Aspose 가 기록하는 *상대* 링크(`assets/image.png`)는 Windows, macOS, Linux 모두에서 동일하게 동작합니다. |
| **Can I embed the assets folder inside a zip?** | 물론입니다—변환이 끝난 뒤 `output.md` 와 `assets` 디렉터리를 함께 압축하면 됩니다. 폴더 구조가 유지되는 한 Markdown 링크는 그대로 유효합니다. |

---

## Next Steps

이제 **assets 폴더 생성**, **docx를 markdown으로 변환**, **Word에서 이미지 추출** 방법을 알았으니 다음을 살펴볼 수 있습니다:

- **Markdown 스타일 커스터마이징** – `MarkdownSaveOptions` 의 `ExportHeadersAsBold`, `ExportTableHeaders` 등 플래그를 조정합니다.  
- **배치 처리** – 디렉터리 내 여러 `.docx` 파일을 순회하면서 대응되는 Markdown/asset 쌍을 자동으로 생성합니다.  
- **Hugo** 혹은 **Jekyll** 같은 정적 사이트 생성기와 통합—방금 만든 폴더 레이아웃을 그대로 사용하면 됩니다.  

보다 고급 시나리오(예: Word 각주 보존, 포함된 OLE 객체 처리)에 관심이 있다면 공식 Aspose.Words 문서에서 “MarkdownSaveOptions”와 “ResourceSavingCallback”을 검색해 보세요.

---

## Conclusion

우리는 **assets 폴더를 만들고**, **포함된 이미지를 추출**하며, **Aspose.Words for .NET**을 사용해 Word 문서를 Markdown으로 저장하는 완전한 엔드‑투‑엔드 솔루션을 살펴보았습니다. 핵심 포인트는 `ResourceSavingCallback` 을 활용해 이미지 저장 위치를 완전히 제어함으로써 Markdown을 깔끔하게 유지하고 바로 배포할 수 있다는 점입니다.

코드를 실행해 보고, 이미지 포맷을 바꾸거나 로직을 재사용 가능한 서비스로 래핑해 보세요—어떤 선택을 하든 이제 *docx를 markdown으로 변환*하면서 *Word에서 이미지를 추출*하고 *Word를 markdown으로 저장*하는 견고한 기반을 갖추게 되었습니다.

Happy coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}