---
category: general
date: 2026-05-26
description: Java용 Aspose.Words로 docx를 markdown으로 변환하면서 이미지를 base64로 삽입하세요. Word를
  markdown으로 변환하고, Word를 markdown으로 저장하며, 이미지를 처리하는 방법을 배워보세요.
draft: false
keywords:
- embed images as base64
- convert docx to markdown
- convert word to markdown
- convert images to base64
- save word as markdown
language: ko
og_description: Aspose.Words for Java를 사용하여 docx를 markdown으로 변환할 때 이미지를 base64로 삽입합니다.
  워드를 markdown으로 변환하고 markdown으로 저장하는 완전 가이드.
og_title: DOCX를 Markdown으로 변환할 때 이미지를 Base64로 삽입
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  headline: Embed Images as Base64 When Converting DOCX to Markdown
  type: TechArticle
- description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  name: Embed Images as Base64 When Converting DOCX to Markdown
  steps:
  - name: 'H3: Why Use `setSaveToMemory(true)`?'
    text: 'When `saveToMemory` is true, Aspose writes the image bytes to a memory
      stream instead of a file. The Markdown exporter then converts that stream to
      a Base64 string and inserts it directly into the Markdown image tag:'
  - name: Troubleshooting Checklist
    text: '| Issue | Likely Cause | Fix | |-------|--------------|-----| | Image appears
      as a broken link | `setSaveToMemory` was omitted | Ensure `args.setSaveToMemory(true);`
      is inside the callback | | Base64 string is truncated | Output file encoding
      mismatch | Save the Markdown using UTF‑8 (default for Asp'
  - name: Convert Only Selected Images
    text: 'If you only want to embed certain images (e.g., those larger than 100 KB),
      add a size check:'
  - name: Use a Different Image Format
    text: The `ResourceSavingArgs` gives you the raw bytes, so you could re‑encode
      JPEGs as PNGs before embedding—useful when the target Markdown consumer prefers
      PNG.
  type: HowTo
tags:
- Aspose.Words
- Java
- Markdown
- Base64
title: DOCX를 Markdown으로 변환할 때 이미지를 Base64로 삽입하기
url: /ko/java/document-conversion-and-export/embed-images-as-base64-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환할 때 이미지 Base64로 삽입하기

DOCX를 Markdown으로 변환하면서 **이미지를 Base64로 삽입**하는 방법이 궁금하셨나요? 여러분만 그런 것이 아닙니다—개발자들은 별도의 파일을 관리하지 않고 이미지를 인라인으로 유지하는 방법을 자주 묻습니다. 좋은 소식은 Aspose.Words for Java를 사용하면 손쉽게 Word 문서를 Markdown으로 변환하고 모든 그림을 자동으로 Base64 문자열로 삽입할 수 있다는 것입니다.

이 튜토리얼에서는 그림이 포함된 `.docx` 파일을 로드하는 것부터, 무거운 작업을 수행하는 `MarkdownSaveOptions` 콜백을 설정하고, 최종적으로 결과를 깔끔한 `.md` 파일로 저장하는 전체 과정을 단계별로 살펴봅니다. 끝까지 읽으면 **word를 markdown으로 변환**, **이미지를 base64로 변환**, 그리고 **word를 markdown으로 저장**하는 방법을 정확히 알게 됩니다. 별도의 이미지 폴더가 남지 않으며, 외부 도구나 수동 후처리 없이 순수 Java 코드만으로 어떤 프로젝트에도 바로 적용할 수 있습니다.

## 필요 사항

- **Java 17** (또는 최신 JDK) – 코드가 람다 구문을 사용하지만, 이전 버전에도 적용할 수 있습니다.
- **Aspose.Words for Java** 라이브러리 (2026년 현재 최신 버전). Maven 의존성을 추가하거나 JAR 파일을 클래스패스에 포함시키세요.
- 최소 하나의 이미지를 포함한 샘플 **DOCX** 파일.
- IDE 또는 간단한 텍스트 편집기—Visual Studio Code, IntelliJ IDEA, 혹은 `vim`도 충분합니다.

이미 준비되었다면, 좋습니다—바로 시작해봅시다.

## 단계 1: Word 문서 로드하기

먼저 소스 파일을 가리키는 `Document` 인스턴스를 생성합니다. 이는 **docx를 markdown으로 변환**하든, 파일을 다른 용도로 읽든 동일한 단계입니다.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX that contains images
        Document doc = new Document("YOUR_DIRECTORY/doc-with-images.docx");
```

> **왜 중요한가:** `Document` 객체는 모든 Aspose 작업의 진입점입니다. 이미지, 표, 스타일 등을 포함한 전체 Word 구조를 보유하고 있어, 이후 콜백에서 각 리소스를 검사할 수 있습니다.

## 단계 2: MarkdownSaveOptions 생성 및 Resource‑Saving 콜백 등록

`MarkdownSaveOptions`에 마법이 숨어 있습니다. `IResourceSavingCallback`을 연결하면 각 외부 리소스(예: 이미지)가 저장되는 방식을 제어할 수 있습니다.

```java
        // Configure Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // Register the callback that will embed images as Base64
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // The callback fires for every resource Aspose wants to write
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Tell Aspose we don’t want a separate image file
                    args.setKeepResourceOriginalName(false);
                    // Give the image a predictable name (optional)
                    args.setResourceFileName("image_" + args.getResourceFileName());
                    // Force in‑memory saving – this triggers Base64 embedding
                    args.setSaveToMemory(true);
                }
            }
        });
```

### H3: `setSaveToMemory(true)`를 사용하는 이유

`saveToMemory`가 true이면, Aspose는 이미지 바이트를 파일이 아닌 메모리 스트림에 기록합니다. 그 후 Markdown 내보내기 기능이 해당 스트림을 Base64 문자열로 변환하여 Markdown 이미지 태그에 직접 삽입합니다:

```markdown
![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

이것이 **이미지를 Base64로 삽입**하는 핵심입니다.

## 단계 3: 문서를 Markdown으로 저장하기

콜백이 설정되었으니, 마지막 단계는 간단히 `save`를 호출하는 것입니다. 여기서 실제로 **word를 markdown으로 변환**하고, 콜백 덕분에 **이미지를 base64로 변환**합니다.

```java
        // Save the document as Markdown – this triggers the callback
        doc.save("YOUR_DIRECTORY/out.md", mdOptions);
    }
}
```

> **결과:** `out.md`에는 모든 이미지가 `data:` URI 형태로 표현된 Markdown 텍스트가 포함됩니다. 디스크에 별도의 이미지 파일이 생성되지 않아 폴더가 깔끔하게 유지됩니다.

## 단계 4: 출력 확인 및 일반적인 함정

생성된 `out.md`를 any Markdown 뷰어(VS Code, GitHub, 정적 사이트 생성기 등)에서 열어보세요. 다음과 같은 내용이 표시될 것입니다:

```markdown
# Sample Document

Here is an inline image:

![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

### 문제 해결 체크리스트

| 문제 | 가능한 원인 | 해결 방법 |
|------|-------------|-----------|
| 이미지가 깨진 링크로 표시됨 | `setSaveToMemory`가 누락됨 | `args.setSaveToMemory(true);`가 콜백 안에 포함되어 있는지 확인하세요 |
| Base64 문자열이 잘림 | 출력 파일 인코딩 불일치 | Markdown을 UTF‑8( Aspose 기본값)로 저장하세요 |
| 예상치 못한 파일 이름 | `setKeepResourceOriginalName(true)` | `false`로 설정하여 사용자 지정 명명 로직을 강제하세요 |

## 단계 5: 고급 변형 (선택 사항)

### 선택된 이미지만 변환하기

특정 이미지(예: 100 KB 이상)만 삽입하고 싶다면, 크기 검사를 추가하세요:

```java
if (args.getResourceType() == ResourceType.IMAGE) {
    if (args.getResourceData().length > 100_000) {
        args.setSaveToMemory(true);
    }
}
```

### 다른 이미지 포맷 사용하기

`ResourceSavingArgs`는 원시 바이트를 제공하므로, 삽입하기 전에 JPEG를 PNG로 재인코딩할 수 있습니다—대상 Markdown 뷰어가 PNG를 선호할 때 유용합니다.

```java
if (args.getResourceFileName().endsWith(".jpg")) {
    // Convert JPEG bytes to PNG bytes (requires an image library)
    byte[] pngBytes = convertJpegToPng(args.getResourceData());
    args.setResourceData(pngBytes);
    args.setResourceFileName(args.getResourceFileName().replace(".jpg", ".png"));
    args.setSaveToMemory(true);
}
```

이러한 조정은 **docx를 markdown으로 변환**할 때 **이미지를 Base64로 삽입** 접근 방식이 얼마나 유연한지 보여줍니다.

## 결론

이제 Aspose.Words for Java를 사용하여 **docx를 markdown으로 변환**하면서 **이미지를 Base64로 삽입**하는 방법을 배웠습니다. 간단한 `IResourceSavingCallback`을 연결하면 라이브러리가 모든 복잡한 작업을 수행합니다: **word를 markdown으로 변환**, **이미지를 base64로 변환**, 그리고 최종적으로 단일 `save` 호출로 **word를 markdown으로 저장**합니다.

자유롭게 실험해 보세요—다양한 이미지 필터링 규칙을 시도하거나 HTML 출력으로 전환하고, 이 단계를 정적 사이트 생성기와 연결할 수 있습니다. 동일한 패턴은 다른 포맷(HTML, EPUB)에도 적용 가능하므로, 인라인 리소스가 필요한 곳 어디에서든 콜백을 재사용할 수 있습니다.

**다음 단계:**
- HTML‑with‑Base64 이미지를 위한 `HtmlSaveOptions` 탐색하기.
- CI 파이프라인과 결합하여 문서 생성을 자동화하기.
- 변환 프로세스를 보다 세밀하게 제어하려면 Aspose의 `DocumentVisitor`를 살펴보기.

코딩을 즐기시고, 깔끔하고 자체 포함된 Markdown 파일을 만끽하세요!

## 관련 튜토리얼

- [DOCX 변환 시 Markdown에 이미지 삽입 방법](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [docx를 markdown으로 변환 – Aspose.Words로 수식 내보내기(LaTeX)](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Word에서 이미지 저장 – Aspose.Words for Java 가이드](/words/english/java/document-loading-and-saving/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}