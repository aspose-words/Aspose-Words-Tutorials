---
category: general
date: 2026-04-28
description: DOCX 파일에서 마크다운을 내보내고 이미지를 추출하는 방법. docx를 마크다운으로 변환하고, 이미지를 폴더에 저장하며,
  워드를 마크다운으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- how to export markdown
- convert docx to markdown
- extract images from docx
- how to place images
- save word as markdown
language: ko
og_description: Java에서 DOCX 파일을 마크다운으로 내보내는 방법. 이 튜토리얼에서는 DOCX를 마크다운으로 변환하고, 이미지를
  추출하며, 이를 정리하는 방법을 보여줍니다.
og_title: Word에서 마크다운을 내보내는 방법 – 완전 가이드
tags:
- Aspose.Words
- Java
- Markdown
- Document Conversion
title: Word에서 마크다운을 내보내는 방법 – 완전 가이드
url: /ko/java/document-conversion-and-export/how-to-export-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Export Markdown from Word – Complete Guide

Word 문서에서 **마크다운을 내보내는 방법**을 고민해 본 적 있나요? 삽입된 그림이 사라지지 않으면서요. 당신만 그런 것이 아닙니다. 정적 사이트 생성기, 문서 사이트, 혹은 GitHub README 파일을 위해 깔끔한 마크다운 파일과 정돈된 이미지 폴더가 필요할 때 많은 개발자들이 난관에 봉착합니다.  

이 튜토리얼에서는 **docx를 마크다운으로 변환**하고, 모든 그림을 원본에서 추출한 뒤 `img` 하위 폴더에 **이미지를 배치**하는 정확한 단계를 살펴봅니다. 최종적으로는 `output.md`와 `img` 디렉터리를 바로 배포할 수 있게 됩니다—수동 복사‑붙여넣기는 필요 없습니다.

> **얻을 수 있는 것:** Aspose.Words를 이용한 실행 가능한 Java 코드 스니펫, 각 라인의 의미에 대한 명확한 설명, SVG 이미지나 대용량 바이너리와 같은 엣지 케이스 처리 팁.  

*전제 조건:* Java 8+ 설치, IDE(IntelliJ IDEA, Eclipse, VS Code 중 하나), 그리고 유효한 Aspose.Words for Java 라이선스(무료 체험판으로도 실험 가능).

---

## How to Export Markdown from a Word Document

### Step 1: Load the Source Document  

변환을 시작하기 전에 DOCX 파일을 메모리로 로드해야 합니다. Aspose.Words는 Word 파일을 `Document` 클래스로 나타냅니다.  

```java
import com.aspose.words.Document;
import com.aspose.words.License;

// Load your license (optional for trial)
License license = new License();
license.setLicense("Aspose.Words.Java.lic");

// Step 1 – read the .docx file
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*왜 중요한가:* 파일을 로드하면 형식이 검증되고 문서 트리(단락, 실행, 이미지)에 접근할 수 있습니다. 파일이 손상된 경우 Aspose가 명확한 예외를 발생시켜 나중에 디버깅하는 시간을 크게 절약해 줍니다.

### Convert DOCX to Markdown – Setting Up the Options  

`MarkdownSaveOptions` 객체는 Aspose에게 문서를 어떻게 직렬화할지 알려줍니다. 기본 동작은 이미지 링크를 마크다운 파일과 같은 폴더에 작성합니다. 다음 단계에서 이를 변경할 것입니다.

```java
import com.aspose.words.MarkdownSaveOptions;
import com.aspose.words.ResourceSavingArgs;
import com.aspose.words.IResourceSavingCallback;
import com.aspose.words.ResourceType;

// Step 2 – configure Markdown export
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*팁:* GitHub‑flavored Markdown이 필요하면 `mdOptions.setExportImagesAsBase64(false);` 로 설정해 이미지를 별도 파일로 유지하고 data URI로 임베드되지 않게 합니다.

### Extract Images from DOCX While Exporting  

이제 핵심 단계입니다: DOCX에서 각 그림을 추출해 `img` 폴더에 저장합니다. `IResourceSavingCallback` 은 저장 작업 중 Aspose가 쓰는 모든 외부 리소스(이미지, 폰트 등)에 대해 호출됩니다.

```java
// Step 3 – tell Aspose where to put image resources
mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Build a path like "img/picture1.png"
            String newName = "img/" + args.getResourceFileName();
            args.setResourceFileName(newName);

            // Optional: you could compress the image here
            // InputStream original = args.getResourceStream();
            // args.setResourceStream(compress(original));
        }
    }
});
```

*콜백을 사용하는 이유:* 콜백이 없으면 Aspose가 `output.md`와 같은 디렉터리에 이미지를 흩뿌려 레포가 어수선해집니다. 콜백을 통해 파일명, 폴더 구조, 심지어 후처리(예: PNG 리사이즈)까지 완전 제어할 수 있습니다.

### Save Word as Markdown – The Final Write  

문서를 로드하고 저장 옵션을 조정했으니 이제 마크다운 파일을 실제로 씁니다. 이미지들은 우리가 정의한 `img` 하위 폴더에 자동으로 저장됩니다.

```java
// Step 4 – write the Markdown file
doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

문제가 없으면 다음과 같은 결과가 나옵니다:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ img/
   ├─ image1.png
   ├─ image2.jpg
   └─ ...
```

어떤 편집기에서든 `output.md`를 열면 `![Image 1](img/image1.png)` 와 같은 마크다운 이미지 구문을 볼 수 있습니다. 링크가 이미 상대 경로이므로 GitHub, MkDocs, 혹은 다른 정적 사이트 생성기에서도 바로 작동합니다.

---

## How to Place Images in a Sub‑Folder (Advanced Options)

때때로 `assets/images/` 와 같이 더 깊은 계층 구조가 필요할 수 있습니다. 콜백만 약간 수정하면 됩니다:

```java
String newName = "assets/images/" + args.getResourceFileName();
args.setResourceFileName(newName);
```

또는 파일명을 주변 단락을 기반으로 더 의미 있게 바꾸고 싶다면 콜백 안에서 `args.getResourceFileName()` 와 `args.getDocumentNode()` 를 검사하면 됩니다. 이 유연성이 **이미지를 어떻게 배치할지**에 대한 질문이 종종 난관이 되는 이유이며, Aspose는 훅을 제공하고 여러분이 로직을 구현하는 형태입니다.

### Handling SVG or Unsupported Formats  

Aspose.Words는 대부분의 래스터 포맷을 바로 변환합니다. SVG의 경우 먼저 래스터화가 필요할 수 있습니다:

```java
if (args.getResourceFileName().endsWith(".svg")) {
    // Convert SVG to PNG on the fly (requires a third‑party lib)
    InputStream svgStream = args.getResourceStream();
    InputStream pngStream = convertSvgToPng(svgStream);
    args.setResourceStream(pngStream);
    args.setResourceFileName(args.getResourceFileName().replace(".svg", ".png"));
}
```

*엣지 케이스 참고:* 모든 마크다운 렌더러가 SVG 인라인을 지원하는 것은 아닙니다. PNG로 변환하면 호환성이 보장됩니다.

---

## Save Word as Markdown – Full Working Example  

아래는 완전한 실행 가능한 프로그램입니다. `Main.java` 파일에 복사‑붙여넣기하고 경로만 조정한 뒤 **Run**을 클릭하세요.

```java
// Main.java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) throws Exception {
        // --------------------------------------------------------------------
        // 1️⃣ Load the DOCX file
        // --------------------------------------------------------------------
        License license = new License();
        // Uncomment the next line if you have a license file
        // license.setLicense("Aspose.Words.Java.lic");

        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // --------------------------------------------------------------------
        // 2️⃣ Prepare Markdown options
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        // Keep images as separate files (GitHub‑flavored)
        mdOptions.setExportImagesAsBase64(false);

        // --------------------------------------------------------------------
        // 3️⃣ Callback – extract and relocate images
        // --------------------------------------------------------------------
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Place every image in the "img" folder
                    String newName = "img/" + args.getResourceFileName();
                    args.setResourceFileName(newName);

                    // Example: compress PNGs (pseudo‑code)
                    // if (newName.endsWith(".png")) {
                    //     args.setResourceStream(compressPng(args.getResourceStream()));
                    // }
                }
            }
        });

        // --------------------------------------------------------------------
        // 4️⃣ Save as Markdown
        // --------------------------------------------------------------------
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        System.out.println("✅ Markdown export complete! Check the img folder for pictures.");
    }
}
```

**예상 결과:** `output.md`에 깔끔한 마크다운 텍스트가 들어가고, 모든 이미지 참조가 `img/<filename>`을 가리킵니다. VS Code의 마크다운 미리보기로 파일을 열어 그림이 정상적으로 렌더링되는지 확인하세요.

---

## Common Questions & Pitfalls

| Question | Answer |
|----------|--------|
| *DOCX에 임베드된 폰트가 포함되어 있으면 어떻게 하나요?* | 필요하다면 `mdOptions.setExportFontsAsBase64(true)` 로 설정하세요. 대부분의 마크다운 프로세서는 폰트를 무시합니다. |
| *다른 폴더 구조로 내보내고 싶다면?* | 콜백 안의 `newName` 문자열을 원하는 경로로 바꾸면 됩니다. |
| *.doc 파일도 지원하나요?* | 지원합니다. `Document` 생성자에 파일 확장자를 `.doc` 로 바꾸기만 하면 됩니다. |
| *대용량 이미지가 있으면?* | 콜백 안에 압축 로직을 추가하세요(예: `javax.imageio` 로 품질 낮추기). |
| *프로덕션에 라이선스가 필요하나요?* | 무료 체험판은 첫 페이지에 워터마크를 삽입합니다. 상업적 사용 시 라이선스를 구매해 워터마크를 제거하세요. |

---

## Conclusion

이제 **Word 파일에서 마크다운을 내보내는 방법**, **docx를 마크다운으로 변환하는 방법**, **docx에서 이미지를 추출하는 방법**, 그리고 **이미지를 전용 폴더에 배치하는 방법**을 모두 알게 되었습니다—모두 Aspose.Words를 이용한 몇 줄의 Java 코드로 구현됩니다. 위 전체 예제는 어떤 프로젝트에도 바로 넣어 사용할 수 있으며, 콜백을 커스터마이징해 파일명 규칙이나 추가 후처리를 자유롭게 적용할 수 있습니다.

다음 단계는? 생성된 마크다운을 Jekyll이나 Hugo 같은 정적 사이트 생성기에 넣어 보세요, 다양한 이미지 포맷을 실험해 보세요, 혹은 CI 파이프라인에 자동 변환을 연결해 보세요. 동일한 패턴을 PDF, HTML, 심지어 일반 텍스트에도 적용할 수 있습니다—`SaveOptions` 클래스만 교체하면 됩니다.

행복한 코딩 되시고, 문서가 언제나 깔끔하고 이미지가 풍부하길 바랍니다!  

---  

![Diagram illustrating how to export markdown from Word – the flow from DOCX to Markdown with images in a sub‑folder](https://example.com/placeholder.png "how to export markdown diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}