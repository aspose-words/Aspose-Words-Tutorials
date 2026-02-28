---
category: general
date: 2026-02-28
description: 문서를 마크다운으로 변환하면서 이미지를 삽입하는 방법을 배우세요. 이미지를 포함한 마크다운을 내보내고 Java를 사용해 마크다운에
  인라인 이미지를 삽입하세요.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: ko
og_description: 워드 문서를 마크다운으로 변환하면서 이미지를 삽입하는 방법을 알아보세요. 이 가이드는 이미지를 포함한 마크다운을 내보내고
  인라인으로 유지하는 방법을 보여줍니다.
og_title: 워드에서 마크다운으로 변환할 때 이미지 삽입 방법
tags:
- markdown
- java
- Aspose.Words
- image handling
title: 워드에서 마크다운으로 변환할 때 이미지 삽입 방법 – 완전 가이드
url: /ko/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 워드 파일을 마크다운으로 변환할 때 이미지 삽입하기 – 완전 가이드

워드 문서에서 생성한 마크다운 파일에 **이미지를 삽입하는 방법**이 궁금하셨나요? 빠르게 내보내기를 시도했지만 이미지 파일이 떠돌아다니고 링크가 깨지는 경우를 겪어보셨을 겁니다. 특히 단일하고 휴대 가능한 `.md` 파일을 정적 사이트 생성기나 GitHub README에 바로 넣어야 할 때 흔히 겪는 고충입니다.

좋은 소식은, 내보내기 설정을 통해 모든 그림을 Base64‑인코딩 문자열로 인라인 처리하도록 할 수 있다는 점입니다. 이렇게 하면 결과 마크다운이 자체 포함형이 됩니다. 이번 튜토리얼에서는 정확한 단계들을 차근차근 살펴보고, 전체 Java 코드를 보여드리며, 각 부분이 왜 중요한지 설명합니다. 끝까지 따라오시면 **이미지가 삽입된 doc을 markdown으로 변환**하는 방법을 익히게 되고, “이미지와 함께 markdown 내보내기” 혹은 “markdown에 이미지 인라인 삽입” 같은 다른 시나리오에 맞게 과정을 조정하는 방법도 알게 됩니다.

## 배울 내용

- 필요한 라이브러리와 최소 프로젝트 설정  
- `MarkdownSaveOptions`를 구성해 이미지를 Base64 데이터 URI로 변환하는 방법  
- `ResourceSavingCallback`을 사용하는 것이 이미지 처리를 제어하는 가장 깔끔한 방법인 이유  
- 마크다운 파일에 실제로 이미지가 삽입됐는지 확인하는 방법  
- 엣지 케이스(대용량 이미지, 다양한 MIME 타입, 성능 고려사항) 팁  

Aspose.Words 사용 경험은 필요 없으며, 기본적인 Java 배경만 있으면 됩니다.

---

## 사전 준비 사항

코드 작성을 시작하기 전에 아래 항목들을 준비하세요.

| 요구 사항 | 이유 |
|-------------|----------------|
| **Java 17+** (또는 최신 JDK) | Aspose.Words for Java API는 Java 8+를 지원하지만, 최신 JDK를 사용하면 내장 `Base64` 유틸리티를 바로 활용할 수 있습니다. |
| **Aspose.Words for Java** (최신 버전) | `MarkdownSaveOptions`와 콜백 인프라를 제공하는 라이브러리입니다. |
| **이미지가 포함된 워드 문서** (`.docx`) | 변환 대상이 필요합니다. 예제에서는 `sample.docx` 파일을 사용합니다. |
| **IDE 또는 텍스트 편집기** (IntelliJ, VS Code 등) | 샘플을 빠르게 컴파일하고 실행하기 위해 필요합니다. |

`pom.xml`(Maven) 또는 `build.gradle`(Gradle)에 Aspose 의존성을 추가합니다. Maven 스니펫은 다음과 같습니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Gradle을 선호한다면:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Aspose는 30일 무료 체험판을 제공합니다. 임시 라이선스 키를 받아 초기에 등록해 두면 워터마크 메시지를 피할 수 있습니다.

---

## 1단계: Markdown Save Options 만들기

먼저 `MarkdownSaveOptions` 객체를 인스턴스화합니다. 이 객체는 Aspose에게 변환 동작(폰트 처리, 리스트 포맷, 그리고 가장 중요한 이미지 처리)을 어떻게 할지 알려줍니다.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Java에서는 구문이 동일하므로, 나중에 코드 블록에서 `csharp` 키워드를 `java`로 교체하면 됩니다.  
**왜 중요한가요?** 옵션을 커스터마이징하지 않으면 Aspose는 각 이미지를 `.md` 옆에 별도 파일로 저장합니다. 옵션 객체를 미리 준비하면 기본 동작을 가로채는 훅을 얻을 수 있습니다.

---

## 2단계: 이미지 리소스를 가로채어 Base64로 인코딩하기

Aspose는 리소스(이미지, CSS 등)를 기록하려 할 때마다 콜백을 호출합니다. `IResourceSavingCallback`을 구현하면 각 리소스에 대해 원하는 작업을 지정할 수 있습니다. 아래 스니펫은 리소스가 이미지인지 확인하고, 파일 이름을 비워 외부 파일 생성을 방지한 뒤, 바이너리 데이터를 Base64 문자열로 변환하고, 적절한 MIME 타입을 설정합니다.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**내부에서 무슨 일이 일어나나요?**

1. **`args.getResourceType()`** – Aspose가 모든 출력 블롭을 분류합니다. 여기서는 `ResourceType.IMAGE`만 관심 있습니다.  
2. **`args.setResourceFileName(null)`** – 파일 이름을 `null`로 지정하면 라이브러리에게 물리 파일을 쓰지 말라고 지시합니다.  
3. **`Base64.getEncoder().encodeToString(...)`** – 원시 바이트 배열을 마크다운 데이터 URI에 안전하게 삽입할 수 있는 텍스트 문자열로 변환합니다.  
4. **`args.setResourceContentType("image/png")`** – 생성된 마크다운 태그가 `![alt](data:image/png;base64,…)` 형태가 되도록 합니다. 원본 문서에 JPEG가 포함돼 있다면 원본 바이트를 검사해 `"image/jpeg"`을 선택할 수 있습니다.

> **왜 Base64인가요?**  
> 데이터 URI를 지원하는 마크다운 프로세서는 이미지를 직접 렌더링하며, 결과 파일은 별도 자산 없이도 휴대성이 유지됩니다. GitHub README나 외부 리소스를 허용하지 않는 문서 사이트에 특히 유용합니다.

---

## 3단계: 변환 수행하기

옵션이 준비됐으니 워드 문서를 로드하고 `save`를 호출하면 됩니다. 지정한 경로가 생성될 마크다운 파일의 위치가 됩니다.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

이게 전부입니다—실제 변환 코드는 두 줄뿐입니다. DOCX 읽기, 이미지 추출, 단락 변환 등 무거운 작업은 모두 Aspose가 처리합니다.

---

## 4단계: 결과 확인 – 인라인 이미지가 보이는지 검사

`output/doc.md`를 텍스트 편집기로 열어보세요. 다음과 같은 내용이 보일 것입니다:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

데이터 URI를 지원하는 뷰어(GitHub, VS Code 프리뷰, 정적 사이트 생성기 등)에 마크다운을 붙여넣으면 별도 파일 없이 그림이 렌더링됩니다.

**간단한 검증**:

- **`data:image/` 검색** – 긴 문자열이 몇 개 보이면 삽입이 성공한 것입니다.  
- **`![](` 패턴 개수 세기** – 원본 워드 파일에 있는 이미지 수와 일치해야 합니다.

---

## 엣지 케이스 처리

### 대용량 이미지

Base64는 원본 크기에 비해 약 **33 %** 정도 부피가 늘어납니다. 고해상도 사진 같은 큰 이미지가 많으면 마크다운 파일이 다루기 힘들어질 수 있습니다. 다음 전략을 고려하세요:

| 전략 | 사용 시점 |
|----------|--------------|
| **변환 전 리사이즈** – `java.awt.Image`를 사용해 축소 | 원본 문서에 고해상도 자산이 있지만 전체 크기가 필요 없는 경우 |
| **JPEG로 전환** – `args.setResourceContentType("image/jpeg")` | PNG의 무손실 포맷이 과도한 사진에 적용 |
| **문서 청크화** – 워드 파일을 섹션별로 나누어 각각 내보내기 | 마크다운 파일을 특정 크기 제한(예: GitHub 10 MB 파일 제한) 이하로 유지해야 할 때 |

### PNG가 아닌 이미지

워드 문서에 혼합 포맷이 포함돼 있다면 MIME 타입을 동적으로 감지할 수 있습니다:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose는 이미 `ResourceContentType`을 채워 주므로, 보통 `"image/png"`를 하드코딩할 필요가 없습니다.

### 성능 팁

- **이미지를 많이 변환한다면 `Base64.Encoder` 인스턴스를 재사용**하세요.  
- **API 버전이 지원한다면 `markdownSaveOptions.setExportImagesAsBase64(true)`**를 활성화해 콜백 없이 처리할 수 있습니다.  
- **대량 문서를 서버 환경에서 처리할 때는 백그라운드 스레드에서 변환**을 실행하세요.

---

## 전체 동작 예제 (전체 코드)

아래는 import, 예외 처리, 전체 흐름을 포함한 복사‑붙여넣기 가능한 Java 프로그램입니다.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**예상 출력**: 인라인 Base64 이미지가 포함된 단일 `doc.md` 파일이 생성되며, 어떤 마크다운‑지원 도구에서도 바로 사용할 수 있습니다.

---

## 자주 묻는 질문

**Q1: 오래된 Aspose.Words 버전에서도 동작하나요?**  
*대부분 가능합니다.* 콜백 API는 버전 19부터 안정적으로 제공됩니다. 다만 `setExportImagesAsBase64` 단축 옵션은 최신 릴리스에 추가됐으므로, 구버전을 사용한다면 위에서 보여준 명시적 콜백 구현이 필요합니다.

**Q2: GitHub Flavored Markdown(GFM)으로 내보내려면 어떻게 해야 하나요?**  
Aspose의 `MarkdownSaveOptions`는 이미 GFM 호환 구문을 출력합니다. 추가로 확인할 점은 저장소 렌더링 엔진이 데이터 URI를 지원하는지 여부인데, GitHub는 이를 지원합니다.

**Q3: HTML 같은 다른 포맷에도 이 방법을 적용할 수 있나요?**  
물론 가능합니다. 동일한 `ResourceSavingCallback`이 `HtmlSaveOptions`에서도 동작합니다. 옵션 클래스만 HTML용으로 교체하고 Base64 로직은 그대로 유지하면 됩니다.

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}