---
category: general
date: 2026-10-23
description: DOCX 파일을 변환하면서 markdown에 이미지를 삽입하는 방법을 배웁니다. 작은 그래픽은 Base64를 사용하고, 큰
  그림은 외부 파일을 사용합니다.
draft: false
keywords:
- how to embed images
- embed images in markdown
- convert docx to markdown
- extract images from docx
- embed images as base64
lastmod: 2026-10-23
og_description: DOCX 파일을 변환하면서 markdown에 이미지를 삽입하는 방법을 배웁니다. 작은 그래픽은 Base64를 사용하고,
  큰 그림은 외부 파일을 사용합니다. 이 가이드는 Aspose.Words for Java를 사용한 정확한 단계들을 보여줍니다.
og_image_alt: Screenshot of markdown output with embedded Base64 images generated
  by Aspose.Words for Java
og_title: markdown에 이미지 삽입 방법 – Java DOCX 변환 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to embed images in markdown when converting a DOCX file,
    using Base64 for tiny graphics and external files for larger pictures.
  headline: How to embed images in markdown when converting docx
  type: TechArticle
- questions:
  - answer: Yes. The same API works in any Java environment, including servlet containers
      and Spring Boot applications. Just stream the `output.md` back to the client
      after conversion.
    question: Can I use this approach in a web service that generates Markdown on
      the fly?
  - answer: A valid Aspose.Words license is required for production deployments. A
      free evaluation license is available for testing and development.
    question: Is a commercial license required for production use?
  - answer: Load the document with `new Document("file.docx", new LoadOptions("password"))`.
      The same conversion pipeline then applies.
    question: How do I handle password‑protected DOCX files?
  - answer: Convert the SVG to PNG or JPEG first, then let the callback treat it as
      any other image. Aspose.Words does not natively render SVG inside Markdown.
    question: What if I need to embed SVG images?
  - answer: Yes. Aspose.Words for Java is platform‑agnostic and runs wherever a compatible
      JDK is available.
    question: Does this work on Windows, macOS, and Linux?
  type: FAQPage
tags:
- Aspose.Words
- Java
- markdown
- image embedding
- docx conversion
- developer guide
title: DOCX 변환 시 markdown에 이미지를 삽입하는 방법
url: /ko/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx 변환 시 마크다운에 이미지를 삽입하는 방법

워드 문서에서 변환된 마크다운 파일에 **이미지를 삽입하는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 대부분의 개발자는 변환 과정에서 그림이 사라지거나 최종 레이아웃을 깨뜨리는 방식으로 저장되는 문제에 직면합니다.  

이 가이드에서는 작은 그래픽에 대해 Base64 데이터 URI로 **이미지를 삽입하는 방법**을 보여주는 완전하고 바로 실행 가능한 예제를 단계별로 살펴봅니다. 큰 자산은 별도 폴더에 기록됩니다. 진행하면서 **convert docx to markdown**을 다루고, Aspose.Words를 사용한 **how to convert docx**에 대해 언급하며, 이미지를 Base64로 삽입하는 것과 별도 파일로 내보내는 것의 차이점을 설명합니다.  

> **팁:** 빠른 개념 증명이 필요하다면, 아래 코드는 단일 Maven 의존성만으로 바로 작동합니다.

## 빠른 답변
- **변환을 담당하는 라이브러리는 무엇인가요?** Aspose.Words for Java performs DOCX → Markdown conversion and image extraction.
- **작은 이미지는 어떻게 저장되나요?** They are inlined as Base64 data URIs directly inside the Markdown file.
- **큰 이미지는 어디에 저장되나요?** Larger pictures are saved to a `markdown_resources` folder alongside the Markdown file.
- **Microsoft Word를 설치해야 하나요?** No, Aspose.Words works completely independently of Microsoft Office.
- **필요한 Java 버전은 무엇인가요?** Java 17 or any later LTS release.

## 이미지를 삽입하는 방법이란 무엇인가요?
`how to embed images`는 이미지 데이터를 직접 마크다운 문서에 삽입하는 기술을 의미하며, Base64‑인코딩된 데이터 URI 또는 외부 파일에 대한 상대 링크 형태가 될 수 있습니다. 이 접근 방식은 작은 그래픽에 대해 단일 휴대용 마크다운 파일을 유지하면서도 고해상도 자산은 별도 파일을 통해 지원할 수 있게 합니다.

## 왜 마크다운에 이미지를 삽입해야 할까요?
이미지를 Base64로 삽입하면 아이콘 및 작은 그래픽에 대한 HTTP 요청이 감소하여 저지연 네트워크에서 페이지 로드 속도가 최대 30 %까지 향상될 수 있습니다. 동시에 큰 사진을 외부에 유지하면 마크다운 파일이 5 MB를 초과해 부피가 커지는 것을 방지하여 편집기 성능과 버전 관리 차이를 유지합니다.

## 필수 조건
- **Java 17** (또는 최신 JDK). API는 Java 중심이지만 개념은 다른 언어에도 적용됩니다.
- **Aspose.Words for Java** – DOCX → Markdown 변환을 지원하는 상용 라이브러리입니다.
- 작은 아이콘과 큰 사진이 혼합된 **sample DOCX**.
- 마크다운 파일과 리소스가 저장될 쓰기 가능한 폴더.

추가 프레임워크나 외부 스크립트가 필요 없습니다. 순수 Java와 Aspose.Words만 있으면 됩니다.

## 프로젝트에 Aspose.Words를 추가하려면 (convert docx to markdown)
Maven을 사용한다면, 아래 스니펫을 `pom.xml`에 삽입하세요. 읽는 시점의 최신 릴리스 버전으로 교체해도 됩니다.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **왜 중요한가:** Aspose.Words는 DOCX 구조 파싱, 이미지 추출, 마크다운 구문 렌더링 등 무거운 작업을 처리합니다. 직접 파서를 구현하려 하면 아마도 필요 없는 복잡한 작업에 빠지게 됩니다.

## Document 클래스는 어떻게 작동하나요?
`Document`는 메모리 내에서 단일 워드 파일을 나타내는 Aspose.Words의 핵심 객체입니다. 다양한 형식으로 문서를 로드, 수정, 저장하는 메서드를 제공합니다.  
전체 문서 구조(섹션, 단락, 표, 임베디드 리소스 등)를 캡슐화하여 기본 XML을 직접 다루지 않고도 프로그래밍 방식으로 내용을 조작할 수 있습니다.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

## 콜백을 사용해 Base64와 외부 파일 중 선택하는 방법
리소스 콜백은 `IResourceSavingCallback` 구현으로, 변환 중 각 이미지를 가로챌 수 있게 합니다.  
이는 **이미지를 삽입하는 방법**의 핵심입니다. 콜백은 변환기가 쓰고자 하는 각 리소스(이미지, 스타일 등)에 대한 후크를 제공합니다. 이미지 크기를 검사하여 데이터 URI로 삽입할지 외부 파일로 저장할지 결정함으로써 성능과 파일 크기 사이의 균형을 맞출 수 있습니다.

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

### 왜 콜백인가?
- **Control:** 이미지를 인라인 Base64 문자열로 할지 별도 파일로 할지 직접 결정합니다.
- **Performance:** 작은 아이콘이 마크다운에 포함되어 추가 HTTP 요청을 없앱니다.
- **Portability:** 큰 사진은 외부 파일로 유지되어 마크다운 크기를 적절하게 유지합니다.

## 문서를 마크다운으로 저장하는 방법
SaveOptions는 Aspose.Words가 출력물을 쓰는 방식을 제어하는 구성 객체로, 형식, 인코딩, 리소스 처리 등을 포함합니다.  
마지막으로, 방금 구성한 옵션을 사용해 Aspose.Words에 마크다운 파일을 쓰도록 지시합니다. `SaveOptions` 객체를 통해 출력 폴더, 리소스 콜백 및 기타 서식 선호도를 지정할 수 있어 생성된 마크다운이 프로젝트 규칙에 맞게 됩니다. 또한 목차 생성 여부를 켜거나 끌 수 있고, 각주 렌더링 방식을 제어할 수 있습니다.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

프로그램을 실행하면 두 가지가 생성됩니다:

1. `output.md` – 원본 DOCX의 마크다운 변환본.  
2. `markdown_resources` 폴더 – 삽입되지 않은 큰 이미지들을 포함합니다.

## 전체 작동 예제 (모든 단계 한 곳에)
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

**예상 출력:** `output.md`를 마크다운 뷰어에서 열어보세요. 작은 아이콘이 인라인으로 표시됩니다, 예시:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

[삽입된 아이콘](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)

큰 사진은 다음과 같이 참조됩니다:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

[사진](markdown_resources/photo1.jpg)

파일 크기를 관리 가능한 수준으로 유지하면서 **이미지를 삽입**하는 바로 그 방법입니다.

## 일반적인 질문 및 예외 상황

### 이미지가 PNG가 아니라 JPEG인 경우는 어떻게 하나요?
위 콜백은 항상 URI 앞에 `image/png`를 붙입니다. JPEG인 경우 `args.getData()`의 처음 몇 바이트를 확인하거나 `args.getFileName()`을 사용해 올바른 MIME 타입을 추론할 수 있습니다:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### 크기 임계값을 변경할 수 있나요?
물론 가능합니다. `10_000` 바이트 제한은 예시일 뿐입니다. 대역폭 여유가 있다면 50 KB 이상으로 올릴 수 있습니다. 반대로 초경량 마크다운 파일이 필요하면 낮출 수도 있습니다.

### 테이블이나 다른 워드 객체에서도 작동하나요?
예. Aspose.Words는 테이블, 리스트, 심지어 각주까지 자동으로 마크다운으로 변환합니다. 리소스 콜백은 이미지만 가로채므로 다른 요소에 대한 추가 코드는 필요 없습니다.

### ASCII가 아닌 파일 이름은 어떻게 처리하나요?
API는 `markdown_resources` 폴더에 쓸 때 Unicode 파일 이름을 안전하게 인코딩합니다. 파일 시스템이 UTF‑8을 지원하는지 확인하면 됩니다(대부분 최신 OS는 지원합니다).

## 문제 해결 팁 및 일반적인 함정
- **Missing images after conversion:** 변환 후 이미지가 누락된 경우: 콜백의 `args.getData()`가 null이 아닌지와 출력 폴더에 쓰기 권한이 있는지 확인하세요.  
- **Base64 strings appear broken:** Base64 문자열이 깨진 경우: `Base64.getEncoder().encodeToString()` 호출이 전체 바이트 배열을 받는지 확인하세요; 스트림을 완전히 읽지 않으면 잘릴 수 있습니다.  
- **Large Markdown files:** 큰 마크다운 파일: 결과 `.md`가 5 MB를 초과하면 임계값을 낮추거나 리소스 폴더에 저장하기 전에 큰 이미지를 압축하는 것을 고려하세요.  
- **Version incompatibilities:** 버전 호환성 문제: Aspose.Words 24.9+는 35개 이상의 출력 형식을 지원하며 일반적인 2.5 GHz 서버에서 500페이지 DOCX를 4 초 미만에 처리할 수 있습니다. 주요 릴리스 후 예상치 못한 동작을 방지하려면 Maven 버전을 고정하세요.

## 자주 묻는 질문
**Q: 이 방식을 실시간으로 마크다운을 생성하는 웹 서비스에 사용할 수 있나요?**  
A: 예. 동일한 API는 서블릿 컨테이너와 Spring Boot 애플리케이션을 포함한 모든 Java 환경에서 작동합니다. 변환 후 `output.md`를 클라이언트에 스트리밍하면 됩니다.

**Q: 상용 라이선스가 프로덕션 사용에 필요합니까?**  
A: 프로덕션 배포에는 유효한 Aspose.Words 라이선스가 필요합니다. 테스트 및 개발을 위한 무료 평가 라이선스도 제공됩니다.

**Q: 비밀번호로 보호된 DOCX 파일을 어떻게 처리하나요?**  
A: `new Document("file.docx", new LoadOptions("password"))` 로 문서를 로드합니다. 이후 동일한 변환 파이프라인이 적용됩니다.

**Q: SVG 이미지를 삽입해야 하면 어떻게 하나요?**  
A: 먼저 SVG를 PNG 또는 JPEG로 변환한 뒤 콜백이 다른 이미지와 동일하게 처리하도록 하면 됩니다. Aspose.Words는 마크다운 내에서 SVG를 기본적으로 렌더링하지 않습니다.

**Q: 이것이 Windows, macOS, Linux에서 모두 작동하나요?**  
A: 예. Aspose.Words for Java는 플랫폼에 구애받지 않으며 호환 가능한 JDK가 있는 어디서든 실행됩니다.

---

**마지막 업데이트:** 2026-10-23  
**테스트 대상:** Aspose.Words for Java 24.10  
**작성자:** Aspose

## 관련 튜토리얼
- [Java로 Word 이미지 저장 및 Docx를 Markdown으로 변환](/words/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Docx를 Markdown으로 변환하면서 CDN에 이미지 업로드 전체](/words/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/)
- [Docx를 Markdown으로 변환하는 완전한 Java 가이드](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}