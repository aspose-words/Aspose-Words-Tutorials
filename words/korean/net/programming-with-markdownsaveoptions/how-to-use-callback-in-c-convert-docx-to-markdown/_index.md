---
category: general
date: 2026-01-14
description: C#에서 콜백을 사용하여 DOCX를 마크다운으로 변환하고, Word에서 이미지를 추출하며, 고유한 이미지 이름을 생성하는 방법을
  배워보세요.
draft: false
keywords:
- how to use callback
- convert docx to markdown
- extract images from word
- save word as markdown
- generate unique image names
language: ko
og_description: C#에서 콜백을 사용하여 DOCX를 마크다운으로 변환하고, 이미지를 추출하며, 고유한 이미지 이름을 생성하는 방법.
og_title: C#에서 콜백 사용 방법 – DOCX를 마크다운으로 변환
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: C#에서 콜백 사용 방법 – DOCX를 마크다운으로 변환
url: /ko/net/programming-with-markdownsaveoptions/how-to-use-callback-in-c-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 콜백 사용 방법 – DOCX를 Markdown으로 변환

Word 문서를 깔끔한 markdown으로 변환해야 할 때 **콜백 사용 방법**이 궁금했던 적 있나요? 당신만 그런 것이 아닙니다. 대부분의 개발자는 변환 과정에서 이름이 충돌하는 이미지 파일들이 다량 생성되거나 markdown이 잘못된 폴더를 가리키게 되는 문제에 부딪히곤 합니다. 좋은 소식은? 작은 맞춤 콜백을 사용하면 각 리소스가 저장되는 위치를 정확히 제어하고, 모든 그림에 고유한 이름을 부여하여 markdown을 깔끔하게 유지할 수 있다는 것입니다.

이 가이드에서는 전체 과정을 단계별로 살펴보겠습니다: `.docx`를 로드하고, 이미지가 저장되는 **위치**와 **방법**을 결정하는 콜백을 구성한 뒤, 최종적으로 결과를 markdown으로 저장합니다. 끝까지 따라오면 **docx를 markdown으로 변환**, **Word에서 이미지 추출**, **고유한 이미지 이름 생성**을 매번 손을 대지 않고도 할 수 있게 됩니다. 외부 스크립트 없이 순수 C#과 Aspose.Words만 사용합니다.

> **Prerequisites**  
> • .NET 6+ (또는 .NET Framework 4.7+) 설치됨  
> • Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)  
> • C# 클래스와 파일 I/O에 대한 기본적인 이해  

![콜백 사용 방법 다이어그램](https://example.com/images/callback-diagram.png "이미지 추출을 위한 콜백 사용 방법을 보여주는 다이어그램")

## 리소스 저장 시 콜백 사용 방법

해결책의 핵심은 `IResourceSavingCallback`을 구현하는 클래스에 있습니다. Aspose.Words는 디스크에 기록해야 하는 모든 외부 리소스(예: 이미지)에 대해 이 인터페이스를 호출합니다. `ResourceSaving`을 오버라이드하면 대상 경로와 파일 이름을 완전히 제어할 수 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that decides where each image extracted from a Word document will be saved.
/// </summary>
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Choose the folder where images will be stored.
        string folder = @"YOUR_DIRECTORY/Images/";

        // 2️⃣ Create a unique name – Guid guarantees no collisions.
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Combine folder and file name, then tell Aspose to use it.
        args.SavePath = Path.Combine(folder, uniqueName);
        args.Cancel = false; // Let Aspose perform the actual write.
    }
}
```

**왜 중요한가:**  
- **Predictability** – 모든 이미지가 동일한 폴더에 저장되어 markdown 참조가 신뢰할 수 있습니다.  
- **Collision‑free naming** – `Guid.NewGuid()`를 사용하면 원본 문서에 중복 이름이 있더라도 기존 이미지를 절대 덮어쓰지 않습니다.  
- **Flexibility** – 변환 로직을 건드리지 않고 `folder`나 명명 방식을 변경할 수 있습니다.

## Markdown 저장 옵션 구성 (Word를 Markdown으로 저장)

이제 콜백을 `MarkdownSaveOptions`에 연결합니다. 이 객체는 Aspose에 변환 방식을 알려주고 어떤 콜백을 실행할지 지정합니다.

```csharp
// Step 4: Hook our custom callback into the markdown options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

여기서 `ExportImagesAsBase64`(별도 이미지 파일을 원하기 때문에 `false`로 설정)나 `ExportHeadersAsHtml`(헤딩 서식을 더 제어하고 싶을 때)와 같은 다른 옵션도 조정할 수 있습니다. 기본 설정만으로도 대부분의 정적 사이트 생성기에 적합한 깔끔한 markdown을 생성합니다.

## 문서를 로드하고 변환 수행 (DOCX를 Markdown으로 변환)

옵션이 준비되면 마지막 단계는 간단합니다: `.docx`를 로드하고 Aspose에 markdown으로 저장하도록 요청합니다.

```csharp
// Step 5: Load the source DOCX and save it as Markdown.
Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

// The output markdown will reference the images saved by MyResourceSaver.
doc.Save(@"YOUR_DIRECTORY/output.md", mdOptions);
```

**출력 결과:**  
- `output.md`에는 지정한 이미지 폴더를 가리키는 markdown 구문(`![Alt text](Images/img_…png)`)이 포함됩니다.  
- `input.docx`에서 추출된 모든 이미지는 `YOUR_DIRECTORY/Images/` 아래에 고유한 GUID 기반 이름으로 저장됩니다.

---

## 일반적인 변형 및 엣지 케이스

### 1️⃣ 명명 방식 변경
GUID 대신 읽기 쉬운 이름(예: `figure_1.png`)을 선호한다면 `uniqueName` 라인을 다음과 같이 교체하세요:

```csharp
int counter = 0;
string uniqueName = $"figure_{++counter}{Path.GetExtension(args.ResourceFileName)}";
```

단, `counter`를 정적 필드로 만들거나 콜백 생성자를 통해 전달하여 호출 간에 유지되도록 해야 합니다.

### 2️⃣ 하위 폴더 처리
일부 프로젝트에서는 장별로 이미지를 정리합니다. `args.ResourceFileName`을 확인하거나 주변 문단 텍스트를 검사하여 하위 폴더를 결정할 수 있습니다:

```csharp
string chapterFolder = Path.Combine(folder, $"Chapter_{args.ResourceFileName.Substring(0,1)}");
Directory.CreateDirectory(chapterFolder);
args.SavePath = Path.Combine(chapterFolder, uniqueName);
```

### 3️⃣ 특정 이미지 건너뛰기
PNG만 추출하고 싶다면 조건을 추가하세요:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase))
{
    args.Cancel = true; // Skip non‑PNG images.
    return;
}
```

### 4️⃣ 출력 검증
변환 후, markdown에 참조된 모든 이미지가 실제로 존재하는지 프로그래밍적으로 검증할 수 있습니다:

```csharp
string markdown = File.ReadAllText(@"YOUR_DIRECTORY/output.md");
var matches = System.Text.RegularExpressions.Regex.Matches(markdown, @"!\[.*?\]\((.*?)\)");
foreach (System.Text.RegularExpressions.Match m in matches)
{
    string imgPath = Path.Combine(@"YOUR_DIRECTORY", m.Groups[1].Value);
    Console.WriteLine(File.Exists(imgPath) ? "OK" : $"Missing: {imgPath}");
}
```

---

## 원활한 사용을 위한 전문가 팁

- **Create the Images folder ahead of time.** Aspose가 자동으로 생성하지만, 미리 생성해 두면 다중 스레드 상황에서 경쟁 조건을 방지할 수 있습니다.  
- **Use `Path.GetInvalidFileNameChars()`** 원본 문서에서 가져온 이름을 정리해야 할 경우 사용하세요.  
- **Dispose of `Document`** 사용이 끝났을 때(`using` 블록으로 감싸서) 즉시 네이티브 리소스를 해제하세요.  
- **Test with a document that contains SVGs.** Aspose는 기본적으로 SVG를 PNG로 변환합니다; 원본 형식이 필요하면 콜백을 적절히 조정하세요.

## 기대 결과

두 개의 그림이 포함된 샘플 `input.docx`에 스크립트를 실행하면 다음과 같은 결과가 나옵니다:

**`output.md` (발췌)**
```markdown
# Sample Document

Here is the first image:

![Image 1](Images/img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png)

And here is the second one:

![Image 2](Images/img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg)
```

**폴더 구조**
```
YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ Images/
   ├─ img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png
   └─ img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg
```

모든 이미지 참조가 올바르게 해결되며, **Word를 markdown으로 저장**하고 **Word에서 이미지를 추출**하며 **고유한 이미지 이름을 생성**하는 작업을 성공적으로 수행했습니다.

## 결론

우리는 Aspose.Words에서 **콜백 사용 방법**을 다루어 DOCX를 markdown으로 변환하고, 모든 삽입된 그림을 추출하며, 각 파일에 고유하고 충돌 없는 이름을 부여하는 방법을 살펴보았습니다. 이 접근 방식은 가볍고 완전히 커스터마이즈 가능하며, Aspose.Words를 지원하는 모든 .NET 버전에서 작동합니다.

다음 단계는? Hugo나 Jekyll과 같은 정적 사이트 생성기와 연결해 보거나, 전체 문서 폴더에 대한 배치 변환을 자동화해 보세요. 또한 테이블을 markdown으로 내보내거나, 이미지 크기가 문제가 되지 않을 때 Base64로 삽입하도록 콜백을 조정해 볼 수도 있습니다.

궁금한 변형이 있나요? 댓글을 남겨 주세요. 함께 탐구해 봅시다. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}