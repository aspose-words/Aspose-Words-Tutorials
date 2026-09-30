---
category: general
date: 2026-02-18
description: 문서에서 마크다운을 생성하고, 문서를 마크다운으로 내보내며 이미지를 하위 폴더에 저장하는 쉬운 단계. C#에서 문서를 마크다운으로
  저장하는 방법을 배워보세요.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: ko
og_description: C#에서 문서로부터 마크다운을 생성하고, 이미지를 하위 폴더에 저장하면서 문서를 마크다운으로 내보내는 방법을 배워보세요.
  단계별 가이드를 따라하세요.
og_title: 문서에서 마크다운 만들기 – 이미지 내보내기 및 저장
tags:
- C#
- Aspose.Words
- Markdown export
title: 문서에서 마크다운 만들기 – 이미지 내보내기 및 저장
url: /ko/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

placeholder.png "문서에서 마크다운 만들기 예시")

Now ensure shortcodes at end remain.

Let's craft translation.

Be careful with markdown syntax: keep ** for bold.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문서에서 마크다운 만들기 – 내보내기 및 이미지 저장

문서에서 **마크다운 만들기**가 필요했지만 삽입된 그림을 깔끔하게 유지하는 방법을 몰라 고민한 적이 있나요? 당신만 그런 것이 아닙니다. 많은 프로젝트에서 보고서, 매뉴얼, 블로그 초안을 프로그래밍 방식으로 생성하는데, 출력 폴더에 이미지 파일이 여기저기 흩어지는 상황은 원하지 않죠.  

이 튜토리얼에서는 **문서를 마크다운으로 내보내기**하고, 모든 이미지를 전용 *md‑resources* 하위 폴더에 저장한 뒤, Aspose.Words for .NET API를 사용해 **문서를 마크다운으로 저장**하는 완전한 실행 가능한 솔루션을 단계별로 살펴봅니다. 마지막까지 진행하면 어떤 C# 코드베이스에도 바로 끼워 넣을 수 있는 단일 메서드와, 엣지 케이스를 처리하기 위한 몇 가지 팁을 얻을 수 있습니다.

> **빠른 살펴보기:**  
> • `MarkdownSaveOptions` 설정  
> • 이미지를 하위 폴더로 리다이렉트하는 `IResourceSavingCallback` 제공  
> • 구성된 옵션으로 `Document.Save` 호출  

콜백을 선택한 이유가 궁금하다면 계속 읽어보세요 – 이유를 단계별로 설명합니다.

---

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 동작)  
- Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`)  
- 소스 `Document` 객체 (예: .docx, .pdf, .rtf 등)  

추가 라이브러리는 필요하지 않습니다; 콜백 API는 Aspose.Words에 내장되어 있습니다.

---

## 1단계: 문서에서 마크다운 만들기 – 저장 옵션 구성

먼저 `MarkdownSaveOptions`를 인스턴스화합니다. 이 객체는 변환 동작을 제어하는데, 예를 들어 어떤 Markdown flavor를 사용할지, 이미지를 Base64로 삽입할지, 생성된 파일을 어디에 둘지 등을 지정합니다.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **왜 중요한가:**  
> `MarkdownSaveOptions`를 명시적으로 만들지 않으면 라이브러리는 기본 설정을 사용해 이미지를 Base64 문자열로 직접 Markdown 파일에 삽입합니다. 이렇게 하면 파일 크기가 커지고 깔끔한 *images* 폴더를 유지하려는 목적에 어긋납니다.

---

## 2단계: 문서를 마크다운으로 내보내고 리소스 처리 정의

이제 저장기가 각 이미지를 **어디에** 저장할지 알려줍니다. `IResourceSavingCallback` 인터페이스는 내보내기 중 발견되는 모든 리소스(이미지, SVG 등)에 대해 호출되는 훅을 제공합니다. 콜백 내부에서 우리는:

1. 대상 폴더(`md-resources/`)가 존재하는지 확인합니다.  
2. `OutputFileName`을 폴더 경로와 원본 리소스 이름을 합친 값으로 설정합니다.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **자주 묻는 질문:** *이미지를 저장하지 않고 삽입하고 싶다면?*  
> 콜백을 생략하거나 `args.OutputFileName = null;` 로 설정하면 저장기가 자동으로 이미지를 Base64 문자열로 삽입합니다.

> **엣지 케이스:** 일부 오래된 문서는 중복 이미지 이름을 포함합니다. 위 콜백은 기존 파일을 덮어씁니다. 이를 방지하려면 GUID를 추가할 수 있습니다:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## 3단계: 문서를 마크다운으로 저장하고 이미지 확인

옵션 구성이 완료되면, 최종 호출은 한 줄로 Markdown 파일과 연관된 이미지를 디스크에 기록합니다.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

문제가 없으면 다음과 같은 결과를 확인할 수 있습니다:

- `MyReport.md` – 소스 문서의 Markdown 표현.  
- `md-resources/` – .md 파일 옆에 생성된 폴더로, 추출된 모든 이미지가 들어 있습니다(예: `image001.png`, `image002.jpg`).  

**샘플 Markdown 스니펫** (Aspose.Words가 자동 생성):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **프로 팁:** 생성된 `.md` 파일을 VS Code 혹은 任意 Markdown 미리보기 도구에서 열면, 이미지가 즉시 표시됩니다. 상대 경로가 폴더 구조와 일치하기 때문입니다.

---

## 전체 실행 가능한 예제

아래 코드는 새 .NET 프로젝트에 붙여넣고 바로 실행할 수 있는 콘솔 프로그램입니다. 간단한 Word 문서를 만들고 이미지를 추가한 뒤, **문서에서 마크다운 만들기**를 수행하면서 이미지를 하위 폴더에 저장합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**실행 후 기대되는 출력**:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

`ExportedDoc.md`를 열면 이미지 참조가 `md-resources/sample-image.png`를 가리키며, 모든 Markdown 뷰어에서 이미지가 올바르게 표시됩니다.

---

## 자주 묻는 변형들

| 시나리오 | 코드 적용 방법 |
|----------|----------------|
| **이미지 내보내기 건너뛰기** (Base64 삽입) | `ResourceSavingCallback`을 완전히 생략하거나 콜백 내부에서 `args.OutputFileName = null;` 로 설정 |
| **이미지 포맷 변경** (예: 모두 PNG) | 콜백 내부에서 `args.ResourceFileName`을 수정하고, 필요하면 스트림을 변환 후 저장 |
| **커스텀 폴더 이름** | `"md-resources/"` 대신 원하는 상대 또는 절대 경로 문자열로 교체 |
| **배치 처리 시 다수 문서** | `Document` 컬렉션을 순회하면서 동일한 `MarkdownSaveOptions` 인스턴스를 재사용 (단, 폴더를 비우거나 실행마다 고유하게 지정) |

---

## 결론

우리는 **문서에서 마크다운 만들기**, **문서를 마크다운으로 내보내기**, 그리고 **이미지를 하위 폴더에 저장**하는 깔끔한 콜백 기반 접근 방식을 살펴보았습니다. 핵심 포인트는:

- `MarkdownSaveOptions`를 사용해 내보내기를 세밀하게 제어한다.  
- `IResourceSavingCallback`을 구현해 이미지를 전용 폴더로 유도함으로써 Markdown을 정돈한다.  
- 동일한 패턴을 다른 리소스 유형(SVG, 오디오 등)에도 적용할 수 있다 – `args.ResourceType`을 확인하면 된다.  

다음 단계로는 사용자 정의 헤딩 스타일로 **문서를 마크다운으로 저장**하거나, 이 루틴을 ASP.NET Web API에 통합해 `.md` 파일과 리소스를 ZIP으로 반환하는 작업을 고려해 보세요. 어쨌든 이제 빌딩 블록은 여러분의 도구 상자에 들어갔습니다.

궁금한 점이나 다루지 않은 코너 케이스가 있나요? 아래 댓글로 알려주시고, 즐거운 코딩 되세요!

---

![문서에서 마크다운 만들기 예시](placeholder.png "문서에서 마크다운 만들기 예시")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}