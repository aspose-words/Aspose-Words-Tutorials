---
category: general
date: 2026-06-17
description: Word를 빠르게 Markdown으로 변환하고 콜백을 사용하여 DOCX에서 이미지를 추출하는 방법을 배워보세요. Aspose.Words에
  대한 단계별 예제.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to use callback
- convert docx to markdown
language: ko
og_description: Aspose.Words를 사용해 Word를 Markdown으로 변환하고 콜백을 이용해 DOCX에서 이미지를 추출하는 방법을
  배워보세요. 전체 코드 예제.
og_title: Word를 Markdown으로 변환 – 전체 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Convert Word to Markdown quickly and learn how to extract images from
    DOCX using a callback. Step‑by‑step example for Aspose.Words.
  headline: Convert Word to Markdown – Complete Guide with Image Extraction
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Conversion
title: Word를 Markdown으로 변환 – 이미지 추출을 포함한 완전 가이드
url: /ko/net/programming-with-markdownsaveoptions/convert-word-to-markdown-complete-guide-with-image-extractio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환 – 이미지 추출 포함 완전 가이드

한 장의 사진도 놓치지 않고 **Word를 Markdown으로 변환**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 `.docx` 파일을 깔끔한 Markdown으로 변환하면서 모든 삽입된 이미지를 추출하는 신뢰할 수 있는 방법을 필요로 합니다—레거시 문서에서 정적 사이트 콘텐츠를 생성하는 것을 생각해 보세요. 이 튜토리얼에서는 정확히 그 작업을 수행하는 실전 솔루션을 단계별로 살펴보고, **콜백 사용 방법**을 보여드려 이미지가 디스크에 저장되는 위치를 제어하는 방법도 설명합니다.

이 가이드를 마치면 다음을 할 수 있습니다:

* 한 번의 호출로 Word 문서를 Markdown으로 변환  
* DOCX 파일에서 이미지를 추출하여 전용 폴더에 저장  
* 세밀한 리소스 처리를 위해 Aspose.Words가 제공하는 콜백 패턴을 이해  

불필요한 내용 없이, 바로 프로젝트에 넣어 사용할 수 있는 실용적인 실행 예제입니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요:

| 요구 사항 | 중요한 이유 |
|-----------|--------------|
| **.NET 6.0+** (or .NET Framework 4.6.2+) | Aspose.Words는 두 버전을 모두 지원하며, 최신 런타임은 더 나은 성능을 제공합니다. |
| **Aspose.Words for .NET** NuGet package | `Document`, `MarkdownSaveOptions`, 및 콜백 API를 제공합니다. |
| A **sample DOCX** file with images (e.g., `input.docx`) | 콜백을 시연하기 위해 해당 이미지들을 추출합니다. |
| An IDE such as **Visual Studio 2022** or **VS Code** | C#을 컴파일할 수 있는 환경이면 충분합니다. |

CLI를 통해 라이브러리를 설치할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

이게 전부입니다—추가 의존성은 필요 없습니다.

## 1단계: 원본 Word 문서 로드

첫 번째로 `.docx` 파일을 엽니다. 이는 나중에 HTML, PDF, 또는 Markdown으로 변환하든 동일합니다.

```csharp
using Aspose.Words;
using System.IO;

// Load the Word document from disk
Document document = new Document(@"C:\Docs\input.docx");
```

> **Pro tip:** 스트림(예: 웹 폼에서 파일 업로드)으로 작업하는 경우 `new Document(stream)`도 동일하게 작동합니다.

## 2단계: 콜백 정의 – 리소스 저장을 위한 콜백 사용 방법

Aspose.Words는 `IResourceSavingCallback`을 통해 저장 프로세스를 가로챌 수 있게 해줍니다. 이는 우리 튜토리얼의 **이미지 추출** 부분입니다. 콜백을 제공함으로써 각 이미지 파일이 정확히 어디에 기록될지, 혹은 원하지 않는 리소스를 건너뛸지 결정합니다.

```csharp
using Aspose.Words.Saving;

// Create the callback that controls image output
ResourceSavingCallback resourceCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // Folder where all extracted images will live
        string resourcesFolder = @"C:\Docs\MarkdownResources";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string fileName = $"img_{args.Index}{args.Extension}";
        args.Path = Path.Combine(resourcesFolder, fileName);

        // Uncomment the next line if you ever need to skip a resource
        // args.Cancel = true;
    });
```

### 왜 콜백을 사용하나요?

* **세밀한 제어** – 파일명 체계와 위치를 직접 결정합니다.  
* **성능** – 필요한 리소스만 디스크에 기록됩니다.  
* **유연성** – 이미지, 임베디드 폰트 또는 기타 외부 자산에 모두 적용됩니다.

## 3단계: Markdown 저장 옵션 구성 – DOCX를 Markdown으로 변환

이제 콜백을 Markdown 내보내기와 연결합니다. 여기서 **convert docx to markdown** 마법이 일어납니다.

```csharp
// Set up Markdown options and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback defined above will be invoked for each image
    ResourceSavingCallback = resourceCallback,

    // Optional: keep original image formats (PNG, JPEG, etc.)
    ExportImagesAsBase64 = false
};
```

이미지를 Markdown 안에 Base64 문자열로 직접 삽입하고 싶다면 `ExportImagesAsBase64 = true`로 설정하세요. 대부분의 정적 사이트 생성기에서는 별도 이미지 파일이 더 깔끔합니다.

## 4단계: 문서 저장 – 최종 Word를 Markdown으로 변환 호출

모든 설정이 완료되면, 단일 `Save` 호출이 변환과 이미지 추출이라는 무거운 작업을 수행합니다.

```csharp
// Output Markdown file path
string markdownPath = @"C:\Docs\Doc.md";

// Perform the conversion
document.Save(markdownPath, markdownOptions);
```

이 라인이 실행된 후 다음을 찾을 수 있습니다:

* `Doc.md` – Word 문서의 Markdown 변환본.  
* `C:\Docs\MarkdownResources\` – `img_0.png`, `img_1.jpg` 등 이미지 파일이 들어 있는 폴더.

### 예상 Markdown 스니펫

원본 DOCX에 이미지가 포함된 단락이 있었다고 가정하면, 생성된 Markdown은 다음과 같습니다:

```markdown
![Image](MarkdownResources/img_0.png)
```

그 라인은 추출된 이미지 파일을 직접 가리키며, 정적 사이트 빌드에 바로 사용할 수 있습니다.

## 5단계: 출력 확인 – 이미지 추출 확인

`Doc.md`를 텍스트 편집기에서 열어 보세요. 표준 Markdown 구문이 보이고, 모든 이미지 참조가 `MarkdownResources` 내부 파일로 해석됩니다. VS Code의 Markdown 미리보기와 같은 뷰어에서 파일을 열면 이미지가 정상적으로 렌더링됩니다.

이미지가 누락된 경우, 콜백 로직을 다시 확인하세요:

* 폴더 경로에 쓰기 권한이 있나요?  
* `args.Cancel`이 실수로 `true`로 설정되었나요?  

이 두 부분을 수정하면 대부분의 문제를 해결할 수 있습니다.

## 엣지 케이스 및 일반적인 함정

| 상황 | 주의할 점 | 권장 해결책 |
|------|----------|--------------|
| **DOCX에 SVG 이미지가 포함된 경우** | Aspose.Words는 기본적으로 SVG를 PNG로 변환합니다. | PNG 출력을 그대로 사용하거나, 원본 SVG가 필요하면 후처리하세요. |
| **대용량 문서 (100+ MB)** | 변환 중 메모리 사용량이 급증합니다. | `LoadOptions`에 `LoadFormat.Docx`를 지정하고, 가능한 경우 스트리밍을 활성화하세요. |
| **맞춤 파일명 체계가 필요할 경우** | 기본 `img_{index}`가 기존 파일과 충돌할 수 있습니다. | 콜백 내부에서 `fileName` 구성을 GUID 또는 원본 이미지 이름(`args.FileName`)을 포함하도록 수정하세요. |
| **장식용 이미지 건너뛰기** | 일부 이미지는 장식용이며 Markdown에 필요하지 않을 수 있습니다. | 콜백에서 `args.Image` 메타데이터(예: `args.Image.Title`)를 검사하고, 무시하려는 경우 `args.Cancel = true`로 설정하세요. |

## 전체 작동 예제 (전체 코드가 하나의 파일에 포함)

아래는 복사‑붙여넣기만 하면 되는 완전한 프로그램입니다. 경로를 자신의 디렉터리로 교체하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source DOCX
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Set up the callback to extract images
            ResourceSavingCallback imgCallback = new ResourceSavingCallback(
                (sender, callbackArgs) =>
                {
                    string resourcesFolder = @"C:\Docs\MarkdownResources";
                    Directory.CreateDirectory(resourcesFolder);

                    string fileName = $"img_{callbackArgs.Index}{callbackArgs.Extension}";
                    callbackArgs.Path = Path.Combine(resourcesFolder, fileName);
                    // Uncomment to skip a specific resource
                    // callbackArgs.Cancel = false;
                });

            // 3️⃣ Configure Markdown options and attach the callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = imgCallback,
                ExportImagesAsBase64 = false // Keep images as separate files
            };

            // 4️⃣ Save as Markdown – this also triggers image extraction
            string outputPath = @"C:\Docs\Doc.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images saved in: C:\\Docs\\MarkdownResources");
        }
    }
}
```

프로그램을 실행하세요(`dotnet run` 또는 Visual Studio에서 **F5**). 콘솔에 *“Conversion complete!”*가 출력되면 **convert word to markdown**과 **extract images from docx**를 한 번에 성공적으로 수행한 것입니다.

## 요약 – 다룬 내용

* **MarkdownSaveOptions**를 사용한 Word to Markdown 변환.  
* `IResourceSavingCallback` 구현을 통한 이미지 추출 방법.  
* 파일명, 위치 제어 및 리소스 건너뛰기를 위한 콜백 사용 방법.  
* 완전 실행 가능한 C# 예제로 DOCX를 Markdown으로 엔드‑투‑엔드 변환.

## 다음 단계

이제 탄탄한 기반이 마련되었으니 다음 확장 기능을 고려해 보세요:

* **배치 처리** – DOCX 파일 폴더를 순회하며 대응하는 Markdown 세트를 생성.  
* **Front‑matter 삽입** – Hugo나 Jekyll 같은 정적 사이트 생성기를 위해 각 Markdown 파일에 YAML front‑matter를 앞에 추가.  
* **이미지 최적화** – 추출된 이미지를 **ImageMagick** 같은 도구로 파이프하여 게시 전에 파일 크기를 줄이기.  

자유롭게 실험해 보세요—맞춤 Markdown 렌더러를 추가하거나 CI 파이프라인에 통합할 수도 있습니다. 가능성은 무한합니다.

---

*Happy coding! If you hit any snags, drop a comment below and I’ll help you troubleshoot.*

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 연관된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – 이미지 Base64로 삽입](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [DOCX를 Markdown으로 변환할 때 이미지 이름 바꾸는 방법](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}