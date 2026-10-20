---
category: general
date: 2026-06-30
description: Aspose.Words for Java를 사용하여 DOCX를 Markdown으로 변환하고, DOCX에서 이미지를 추출하여 사용자
  지정 해상도로 폴더에 저장합니다.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- save images to folder
- save document as markdown
- set markdown image resolution
language: ko
og_description: Aspose.Words for Java를 사용하여 DOCX를 Markdown으로 변환하고, DOCX에서 이미지를 추출하며,
  마크다운 이미지 해상도를 설정하는 단일 가이드.
og_title: DOCX를 Markdown으로 변환 – 완전한 Java 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Convert DOCX to Markdown using Aspose.Words for Java, extract images
    from DOCX, and save them to a folder with custom resolution.
  headline: Convert DOCX to Markdown – Complete Java Tutorial
  type: TechArticle
- description: Convert DOCX to Markdown using Aspose.Words for Java, extract images
    from DOCX, and save them to a folder with custom resolution.
  name: Convert DOCX to Markdown – Complete Java Tutorial
  steps:
  - name: '**Loading the source DOCX** – Aspose.Words reads the Word file into a `Document`
      object.'
    text: '**Loading the source DOCX** – Aspose.Words reads the Word file into a `Document`
      object.'
  - name: '**Configuring Markdown options** – This is where we **set markdown image
      resolution** so the generated image files aren’t needlessly huge.'
    text: '**Configuring Markdown options** – This is where we **set markdown image
      resolution** so the generated image files aren’t needlessly huge.'
  - name: '**Providing a resource‑saving callback** – Here we **extract images from
      DOCX** and **save images to folder** with unique names, then tell the Markdown
      writer where to point to those files.'
    text: '**Providing a resource‑saving callback** – Here we **extract images from
      DOCX** and **save images to folder** with unique names, then tell the Markdown
      writer where to point to those files.'
  - name: '**Detect the original file extension** (`.png`, `.jpeg`, etc.) so the saved
      file keeps its format.'
    text: '**Detect the original file extension** (`.png`, `.jpeg`, etc.) so the saved
      file keeps its format.'
  - name: '**Create a GUID‑based filename** – this prevents overwriting when the source
      DOCX contains multiple images with the same name.'
    text: '**Create a GUID‑based filename** – this prevents overwriting when the source
      DOCX contains multiple images with the same name.'
  - name: '**Write the raw image bytes** to `YOUR_DIRECTORY/output/images/`. This
      is the core of **extract images from docx**.'
    text: '**Write the raw image bytes** to `YOUR_DIRECTORY/output/images/`. This
      is the core of **extract images from docx**.'
  - name: '**Tell the Markdown writer** to reference the newly saved file via `args.setResourceFileName(...)`.'
    text: '**Tell the Markdown writer** to reference the newly saved file via `args.setResourceFileName(...)`.'
  - name: '**Mark the event as handled** so Aspose doesn’t try to write the image
      a second time.'
    text: '**Mark the event as handled** so Aspose doesn’t try to write the image
      a second time.'
  - name: Load the DOCX with `Document`.
    text: Load the DOCX with `Document`.
  - name: Configure `MarkdownSaveOptions` (especially `setImageResolution`).
    text: Configure `MarkdownSaveOptions` (especially `setImageResolution`).
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words treats SVG as a vector image and will export it as a
      PNG by default, respecting the resolution you set.
    question: Does this work with DOCX files that contain SVG images?
  - answer: Replace the GUID generation with `args.getOriginalFileName()` (if the
      source DOCX stores a name) and ensure the filename is unique by appending a
      counter when needed.
    question: What if I need to keep the original image filenames?
  - answer: 'Absolutely. Wrap the `Document` loading and saving logic in a loop, passing
      a different source path each iteration. The callback remains the same. ## Recap
      We’ve covered everything you need to **convert docx to markdown** while **extracting
      images from docx**, **saving images to folder**, and **sett'
    question: Can I convert multiple DOCX files in a batch?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Markdown
title: DOCX를 Markdown으로 변환 – 완전한 Java 튜토리얼
url: /ko/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환 – 완전한 Java 튜토리얼

워드 파일 안에 포함된 그림을 잃지 않고 **DOCX를 Markdown으로 변환**하는 방법이 궁금했나요? 당신만 그런 것이 아닙니다. 많은 프로젝트—문서 생성기, 정적 사이트 파이프라인, 혹은 단순히 보고서를 백업하는 경우—개발자들은 `.docx`를 깔끔한 Markdown으로 변환하면서 모든 삽입된 이미지를 그대로 유지할 수 있는 신뢰할 수 있는 방법이 필요합니다.

이 가이드에서는 **Aspose.Words for Java**를 사용한 실습 예제를 통해 **DOCX에서 이미지를 추출**하고, **이미지를 폴더에 저장**한 뒤, 사용자 정의 **markdown 이미지 해상도 설정**과 함께 **문서를 Markdown으로 저장**하는 과정을 단계별로 설명합니다. 마지막까지 읽으면 어떤 Java 코드베이스에도 삽입할 수 있는 재사용 가능한 스니펫을 얻게 됩니다.

> **Tip:** 이 방법은 최신 Java 8+ 런타임에서 동작하며 Aspose.Words 라이브러리만 있으면 됩니다—추가 이미지 처리 도구는 필요하지 않습니다.

## What You’ll Need

- Java 8 이상 (코드는 JDK 11에서도 컴파일됩니다)  
- Aspose.Words for Java JAR (Maven Central 또는 Aspose 웹사이트에서 제공)  
- `input.docx` 샘플 파일 (최소 하나의 그림 포함)  
- Markdown 파일과 추출된 이미지가 저장될 빈 디렉터리  

그게 전부입니다—무거운 프레임워크도, 외부 변환기도 필요 없습니다. 시작해 봅시다.

![Convert DOCX to Markdown example](images/example.png "Illustration of converting a DOCX file to Markdown with images saved to a folder")

## DOCX를 Markdown으로 변환 – 개요

코드에 들어가기 전에 변환 과정의 세 가지 핵심 요소를 정리해 보겠습니다:

1. **소스 DOCX 로드** – Aspose.Words가 Word 파일을 `Document` 객체로 읽어들입니다.  
2. **Markdown 옵션 구성** – 여기서 **markdown 이미지 해상도 설정**을 하여 생성된 이미지 파일이 불필요하게 커지는 것을 방지합니다.  
3. **리소스 저장 콜백 제공** – 여기서 **DOCX에서 이미지를 추출**하고 **이미지를 폴더에 저장**하며 고유한 이름을 부여하고, Markdown 작성자에게 해당 파일을 가리키도록 알려줍니다.  

이 모든 과정은 하나의 간결한 `main` 메서드에서 이루어집니다. 준비되셨나요? IDE를 열고 따라 해 보세요.

## Step 1 – DOCX 문서 로드

먼저, 소스 Word 파일을 나타내는 `Document` 인스턴스를 생성합니다. 파일 경로가 잘못되면 Aspose가 상세한 `FileNotFoundException`을 발생시키므로 경로를 다시 확인하세요.

```java
import com.aspose.words.*;

public class MarkdownConverter {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **왜 중요한가:** 문서를 로드하는 것이 *convert docx to markdown*의 시작점입니다. `Document` 객체가 없으면 이후 옵션이나 콜백을 설정할 수 없습니다.

## Step 2 – MarkdownSaveOptions 생성 및 이미지 해상도 설정

Aspose.Words에는 출력물을 세밀하게 조정할 수 있는 `MarkdownSaveOptions` 클래스가 포함되어 있습니다. 우리 시나리오에 가장 관련 깊은 설정은 `setImageResolution(int dpi)`입니다. **200 DPI** 값은 품질과 파일 크기 사이의 좋은 균형을 제공합니다.

```java
        // Create Markdown save options and set the desired image resolution.
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions();
        mdOpts.setImageResolution(200); // set markdown image resolution
```

> **프로 팁:** 고해상도 블로그에 Markdown을 삽입하려면 DPI를 300으로 올리세요. 가벼운 GitHub README 파일의 경우 96 DPI면 충분합니다.

## Step 3 – 콜백 구현하여 이미지 추출 및 폴더에 저장

Aspose는 쓰고자 하는 모든 외부 리소스(예: 이미지)에 대해 콜백을 호출합니다. `IResourceSavingCallback`을 구현하면 **각 추출된 이미지를 저장하는 방식**을 완전히 제어할 수 있어, 충돌을 방지하는 GUID 기반 이름으로 **이미지를 폴더에 저장**할 수 있습니다.

```java
        // Provide a callback to control how each extracted image is saved.
        mdOpts.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Generate a unique file name for the image.
                String extension = args.getOriginalExtension(); // e.g. ".png"
                String guid = java.util.UUID.randomUUID().toString();
                String imagePath = "YOUR_DIRECTORY/output/images/" + guid + extension;

                // Write the image bytes to the chosen location.
                try (FileOutputStream fos = new FileOutputStream(imagePath)) {
                    fos.write(args.getResourceData());
                }

                // Update the reference that will appear in the Markdown file.
                args.setResourceFileName("images/" + guid + extension);
                args.setHandled(true); // we have saved the resource ourselves
            }
        });
```

### 콜백이 수행하는 작업, 단계별

1. **원본 파일 확장자 감지** (`.png`, `.jpeg` 등)하여 저장 파일이 형식을 유지하도록 합니다.  
2. **GUID 기반 파일명 생성** – 소스 DOCX에 동일한 이름의 이미지가 여러 개 있을 때 덮어쓰기를 방지합니다.  
3. `YOUR_DIRECTORY/output/images/`에 **원시 이미지 바이트 쓰기**. 이것이 **extract images from docx**의 핵심입니다.  
4. `args.setResourceFileName(...)`을 통해 **Markdown 작성자에게** 새로 저장된 파일을 참조하도록 알립니다.  
5. **이벤트를 처리됨으로 표시**하여 Aspose가 이미지를 두 번 쓰려고 하지 않게 합니다.  

> **흔한 실수:** `args.setHandled(true)`를 빼먹으면 기본 임시 위치에 이미지 파일이 중복으로 작성됩니다. 저장 과정을 직접 제어할 때는 항상 설정하세요.

## Step 4 – 문서를 Markdown으로 저장

옵션과 콜백이 준비되었으니, 마지막 한 줄 코드로 **문서를 markdown으로 저장**합니다. 이 메서드는 앞서 설정한 모든 내용을 반영합니다.

```java
        // Save the document as Markdown, using the custom callback for images.
        doc.save("YOUR_DIRECTORY/output/WithImages.md", mdOpts);
    }
}
```

프로그램이 종료되면 다음을 확인할 수 있습니다:

- `WithImages.md` 파일에 `![image](images/123e4567-e89b-12d3-a456-426614174000.png)`와 같은 이미지 링크가 포함된 Markdown 구문이 들어 있습니다.  
- 추출된 그림 파일이 들어 있는 `images` 하위 폴더  

이것이 40줄 이하의 Java 코드로 구현한 전체 **convert docx to markdown** 워크플로우입니다.

## 출력 검증

생성된 `WithImages.md`를 any Markdown 뷰어(VS Code, GitHub, 정적 사이트 생성기 등)에서 열어 보세요. 원본 텍스트와 함께 올바르게 렌더링되는 인라인 이미지가 보여야 합니다. 이미지가 깨져 보이면 Markdown 파일의 상대 경로가 `images` 폴더 위치와 일치하는지 다시 확인하세요.

### 예상 Markdown 스니펫

```markdown
# Sample Document

Here is a paragraph with an image:

![image](images/9f8c2d4a-5b6e-4c9f-a3d2-7e8f9a0b1c2d.png)
```

위에서 참조한 PNG 파일을 열면 원본 DOCX에 삽입된 그림과 동일한 복사본이어야 합니다.

## 고급 변형

- **출력 폴더 구조 변경** – 프로젝트 레이아웃에 맞게 `imagePath`와 `args.setResourceFileName`을 수정합니다.  
- **이미지 유형 필터링** – `resourceSaving` 내부에서 `extension`을 검사하여 예를 들어 큰 BMP 파일 저장을 건너뛸 수 있습니다.  
- **Base64 이미지 삽입** – 외부 파일 대신 인라인 data URI를 원한다면 `mdOpts.setExportImagesAsBase64(true)`를 설정합니다.  

이러한 조정으로 변환을 **save images to folder** 형태로 CI 파이프라인이 기대하는 정확한 구조에 맞출 수 있습니다.

## 자주 묻는 질문

**Q: SVG 이미지를 포함한 DOCX 파일에서도 작동하나요?**  
A: 네. Aspose.Words는 SVG를 벡터 이미지로 처리하며 기본적으로 PNG로 내보내며, 설정한 해상도를 적용합니다.

**Q: 원본 이미지 파일명을 유지해야 하면 어떻게 하나요?**  
A: GUID 생성 대신 `args.getOriginalFileName()`(소스 DOCX에 이름이 저장된 경우)를 사용하고, 필요할 경우 카운터를 추가해 파일명이 고유하도록 합니다.

**Q: 여러 DOCX 파일을 배치로 변환할 수 있나요?**  
A: 물론입니다. `Document` 로드 및 저장 로직을 루프로 감싸고 각 반복마다 다른 소스 경로를 전달하면 됩니다. 콜백은 동일하게 유지됩니다.

## 요약

우리는 **convert docx to markdown**를 수행하면서 **extract images from docx**, **save images to folder**, 그리고 **markdown 이미지 해상도 설정**까지 모두 다루었습니다. 핵심 요점은 다음과 같습니다:

1. `Document`로 DOCX 로드.  
2. `MarkdownSaveOptions` 구성(특히 `setImageResolution`).  
3. `IResourceSavingCallback`에 연결하여 이미지 추출 및 저장을 제어.  
4. `doc.save(..., mdOpts)`를 호출해 최종 Markdown 파일 생성.  

DPI, 폴더 레이아웃을 조정하거나 Base64 삽입으로 전환하는 등 자유롭게 변경해 보세요—Aspose.Words가 이를 손쉽게 처리합니다.

## 다음 단계

- 다른 `MarkdownSaveOptions` 속성을 조정하여 **Markdown 출력 스타일링**(테이블, 코드 블록 등)을 탐색합니다.  
- 이 변환기를 ...

## 다음에 배워야 할 내용

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [DOCX를 Markdown으로 변환 – Aspose.Words로 수학 방정식을 LaTeX로 내보내기](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [DOCX 변환 시 Markdown에 이미지 삽입하는 방법](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Word에서 LaTeX 내보내기: DOCX를 Markdown으로 변환하고 PDF로 저장하는 방법](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}