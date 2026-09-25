---
category: general
date: 2026-01-11
description: DOCX 파일을 변환하면서 마크다운에 이미지를 삽입하는 방법을 배우고, 작은 이미지는 Base64로, 큰 리소스는 별도로 저장합니다.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: ko
og_description: DOCX 파일을 변환하면서 Markdown에 이미지를 삽입하는 방법을 배우세요. 작은 이미지는 Base64로 인코딩하고,
  큰 리소스는 별도로 저장합니다.
og_title: DOCX 변환 시 마크다운에 이미지 삽입하는 방법
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: DOCX 변환 시 마크다운에 이미지 삽입 방법
url: /ko/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX 변환 시 Markdown에 이미지 삽입하는 방법

워드 문서에서 변환된 Markdown 파일에 **이미지를 삽입하는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 대부분의 개발자는 변환 과정에서 그림이 누락되거나 최종 레이아웃을 깨뜨리는 방식으로 저장되는 문제에 직면합니다.  

이 가이드에서는 작은 그래픽은 Base64 데이터 URI로 **이미지를 삽입하는 방법**을 보여주고, 큰 자산은 별도 폴더에 저장하는 완전하고 바로 실행 가능한 예제를 단계별로 살펴봅니다. 진행하면서 **convert docx to markdown**를 다루고, Aspose.Words를 사용한 **how to convert docx**에 대해 언급하며, 이미지를 Base64로 삽입하는 것과 별도 파일로 내보내는 것의 차이점을 설명합니다.  

> **Pro tip:** 빠른 개념 증명이 필요하다면, 아래 코드는 단일 Maven 의존성만으로 바로 작동합니다.

## 필요 사항

- **Java 17** (또는 최신 JDK) – API는 Java 중심이지만 개념은 다른 언어에도 적용됩니다.
- **Aspose.Words for Java** – DOCX → Markdown 변환을 지원하는 상용 라이브러리입니다.
- **sample DOCX** – 작은 아이콘과 큰 사진이 혼합된 문서입니다.
- Markdown과 그 리소스를 저장할 폴더.

추가 프레임워크나 외부 스크립트는 필요 없습니다. 순수 Java와 Aspose.Words만 있으면 됩니다.

## Step 1 – 프로젝트에 Aspose.Words 추가 (convert docx to markdown)

Maven을 사용한다면, 다음 스니펫을 `pom.xml`에 삽입하세요. 읽는 시점의 최신 릴리스 버전으로 교체해도 됩니다.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Why this matters:** Aspose.Words는 DOCX 구조 파싱, 이미지 추출, Markdown 구문 렌더링이라는 무거운 작업을 처리합니다. 직접 파서를 구현하려 하면 아마도 필요 없는 복잡한 작업에 빠지게 됩니다.

## Step 2 – 원본 DOCX 문서 로드

먼저, 변환하려는 Word 파일을 API에 지정합니다. `Document` 생성자가 모든 작업을 수행하므로 수동 XML 파싱이 필요 없습니다.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

주석이 이 라인이 왜 중요한지 설명합니다: `Document` 인스턴스가 없으면 변환할 것이 없습니다.

## Step 3 – Resource‑Saving 콜백이 포함된 MarkdownSaveOptions 준비

이것이 **이미지를 올바르게 삽입하는 방법**의 핵심입니다. 콜백은 변환기가 쓰고자 하는 각 리소스(이미지, 스타일 등)에 대한 후크를 제공합니다.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### 콜백이 필요한 이유

- **Control:** 이미지가 인라인 Base64 문자열이 될지 별도 파일이 될지를 직접 결정합니다.
- **Performance:** 작은 아이콘은 Markdown에 포함되어 추가 HTTP 요청을 없앱니다.
- **Portability:** 큰 사진은 외부 파일로 유지되어 Markdown 크기를 적절하게 유지합니다.

## Step 4 – 문서를 Markdown으로 저장

마지막으로, 앞서 설정한 옵션을 사용해 Aspose.Words에게 Markdown 파일을 작성하도록 지시합니다.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

프로그램을 실행하면 두 가지가 생성됩니다:

1. `output.md` – 원본 DOCX의 Markdown 표현.
2. `markdown_resources` 폴더 – 삽입되지 않은 큰 이미지들이 들어 있습니다.

## 전체 작업 예제 (모든 단계 한 곳에)

아래는 IDE에 복사‑붙여넣기 할 수 있는 완전한 소스 파일입니다. `YOUR_DIRECTORY`를 실제 경로로 교체하세요.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**예상 출력:** `output.md`를 任意 Markdown 뷰어에서 열어보세요. 작은 아이콘이 인라인으로 표시됩니다, 예시:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

큰 사진은 다음과 같이 참조됩니다:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

이것이 파일 크기를 관리 가능한 수준으로 유지하면서 **이미지를 삽입**하는 데 정확히 필요한 방법입니다.

## 일반적인 질문 및 엣지 케이스

### 이미지가 PNG가 아니라 JPEG인 경우는?

위 콜백은 항상 URI 앞에 `image/png`를 붙입니다. JPEG인 경우 `args.getData()`의 처음 몇 바이트를 확인하거나 `args.getFileName()`을 사용해 올바른 MIME 타입을 추론할 수 있습니다:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### 크기 임계값을 변경할 수 있나요?

물론 가능합니다. `10_000` 바이트 제한은 예시일 뿐입니다. 대역폭 여유가 있다면 50 KB 이상으로 올릴 수 있고, 초경량 Markdown 파일이 필요하면 낮출 수 있습니다.

### 표나 다른 Word 객체에도 작동하나요?

네. Aspose.Words는 표, 목록, 심지어 각주까지 자동으로 Markdown으로 변환합니다. 리소스 콜백은 이미지만 가로채므로 다른 요소에 대한 추가 코드는 필요 없습니다.

### 비 ASCII 파일명은 어떻게 처리하나요?

API는 `markdown_resources` 폴더에 쓸 때 Unicode 파일명을 안전하게 인코딩합니다. 파일 시스템이 UTF‑8을 지원하는지 확인하세요(대부분 최신 OS가 지원합니다).

## 원활한 변환을 위한 프로 팁

- **Keep the output folder clean.** 변환당 `Files.createDirectories`를 한 번만 실행하거나, 새로 시작하려면 각 실행 전 폴더를 삭제하세요.
- **Validate the Markdown.** `markdownlint`와 같은 도구는 잘못된 Base64 문자열로 인해 발생한 불필요한 문자를 잡아낼 수 있습니다.
- **Version lock Aspose.Words.** 특정 버전을 고정하면 주요 릴리스가 기본 동작을 바꾸더라도 코드가 계속 작동합니다.
- **Use a .gitignore** entry for `markdown_resources/`

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}