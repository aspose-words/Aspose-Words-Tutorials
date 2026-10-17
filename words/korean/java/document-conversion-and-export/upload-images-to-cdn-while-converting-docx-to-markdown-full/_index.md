---
category: general
date: 2026-04-24
description: Aspose.Words를 사용하여 DOCX를 마크다운으로 변환하면서 이미지를 CDN에 업로드합니다. 이미지 처리와 CDN 통합을
  포함한 Word를 마크다운으로 내보내는 방법을 배워보세요.
draft: false
keywords:
- upload images to cdn
- convert docx to markdown
- export word to markdown
- how to convert docx
- markdown conversion with images
language: ko
og_description: DOCX를 마크다운으로 변환하면서 이미지를 CDN에 업로드합니다. Word를 마크다운으로 내보내기, 이미지 처리 및 CDN
  업로드를 다루는 단계별 Java 가이드.
og_title: DOCX를 Markdown으로 변환하면서 이미지를 CDN에 업로드하기 – Java 튜토리얼
tags:
- Java
- Aspose.Words
- Markdown
- CDN
- Document Conversion
title: DOCX를 Markdown으로 변환하면서 이미지를 CDN에 업로드하기 – 전체 Java 가이드
url: /ko/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환하면서 CDN에 이미지 업로드하기

DOCX‑to‑Markdown 변환 과정에서 **이미지를 CDN에 업로드**해야 했던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 생성된 markdown이 로컬 이미지 파일을 가리키고 있어 프로덕션에 배포되지 못하는 문제에 부딪히곤 합니다. 좋은 소식은? Aspose.Words for Java를 사용하면 각 이미지가 정확히 어디에 저장될지 제어할 수 있습니다—로컬 “imgs” 폴더에 남겨두든, 원하는 CDN으로 푸시하든 말이죠.

이 튜토리얼에서는 **Word 문서를 markdown으로 변환**하고, 이미지를 하위 폴더에 저장한 뒤 로컬 경로를 CDN URL로 교체하는 완전한 실행 예제를 단계별로 살펴봅니다. 끝까지 진행하면 원하는 CDN에 호스팅된 이미지를 참조하는 배포 준비가 된 markdown 파일을 얻게 됩니다.

> **배우게 될 내용**
> - Aspose.Words로 DOCX 파일을 로드하는 방법
> - `MarkdownSaveOptions`를 구성하고 `IResourceSavingCallback`을 구현하는 방법
> - 자체 CDN 업로드 로직을 연결하는 위치
> - 최종 markdown 출력물을 검증하는 방법

핵심 단계에서는 외부 서비스를 사용할 필요가 없지만, 이미지를 Amazon S3, Cloudflare, Azure Blob Storage 등으로 푸시하고 싶을 경우 HTTP 클라이언트나 SDK를 연결하는 방법도 논의합니다.

---

## Prerequisites

- **Java 17** 이상 (코드는 이전 버전에서도 컴파일되지만, 17이 현재 LTS입니다).
- **Aspose.Words for Java** 23.9 이상. Maven Central에서 가져올 수 있습니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

- 변환하려는 **DOCX** 파일 (`input.docx`라고 부르겠습니다).
- 선택 사항: 실제로 이미지를 업로드할 경우 CDN 인증 정보.

---

## Step 1 – Load the Source Word Document

먼저 DOCX를 Aspose `Document` 객체로 읽어옵니다. 이를 통해 문서 구조(단락, 표, 임베디드 리소스 등)에 완전하게 접근할 수 있습니다.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source Word document from the file system
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **왜 중요한가:**  
> 문서를 미리 로드하면 markdown 라이터를 사용하기 전에 내용 검토나 수정이 가능합니다. 주석을 제거하거나 스타일을 적용해야 한다면 이 라인 바로 뒤에서 수행하면 됩니다.

---

## Step 2 – Set Up Markdown Save Options

Aspose.Words는 변환을 세밀하게 조정할 수 있는 `MarkdownSaveOptions` 클래스를 제공합니다. 여기서는 인스턴스를 생성하고 다음 단계에서 구현할 리소스 저장 콜백을 활성화합니다.

```java
        // Create save options for Markdown output
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

        // Optional: tweak options (e.g., use GitHub‑flavored markdown)
        saveOptions.setExportImagesAsBase64(false); // keep images as external files
```

> **팁:** `ExportImagesAsBase64`를 `false`로 유지하는 것이 CDN에 이미지를 업로드하려면 필수입니다. Base64‑인코딩된 이미지는 markdown에 직접 삽입돼 외부 호스팅 목적을 무력화합니다.

---

## Step 3 – Implement the Resource‑Saving Callback

튜토리얼의 핵심 부분입니다. `IResourceSavingCallback`은 Aspose가 외부 리소스(이미지, CSS 등)를 기록할 때마다 호출됩니다. 여기서 호출을 가로채 이미지를 CDN에 업로드하고 markdown 참조를 재작성할 수 있습니다.

```java
        // Define a callback to control how external resources (e.g., images) are saved
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Only act on image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a local relative path first (e.g., imgs/picture1.png)
                    String localPath = "imgs/" + args.getResourceFileName();
                    args.setResourceFileName(localPath);

                    // --------------------------------------------------------------
                    // OPTIONAL: Upload to CDN here.
                    // --------------------------------------------------------------
                    // For illustration we’ll pretend to upload and get a CDN URL.
                    // Replace the stub with real SDK calls (AWS S3, Azure Blob, etc.).
                    String cdnUrl = uploadToCdn(args.getResourceBytes(), args.getResourceFileName());

                    // If the upload succeeded, tell Aspose to use the CDN URL instead.
                    if (cdnUrl != null && !cdnUrl.isEmpty()) {
                        args.setResourceUri(cdnUrl);
                    }
                    // --------------------------------------------------------------
                }
            }

            // ----- Helper method that you would replace with real upload logic -----
            private String uploadToCdn(byte[] imageBytes, String fileName) {
                // Placeholder: simulate a CDN URL.
                // In production you might use an HTTP client or cloud SDK.
                // Example: return "https://cdn.example.com/images/" + fileName;
                return "https://cdn.example.com/images/" + fileName;
            }
        });
```

### 왜 콜백을 사용하나요?

- **파일명 제어:** 모든 파일을 `imgs/` 폴더 아래에 저장해 markdown을 깔끔하게 유지합니다.
- **CDN 연동:** `args.setResourceUri(...)`를 설정하면 markdown 라이터가 로컬 경로 대신 CDN URL을 삽입합니다.
- **미래 대비:** 나중에 CDN 공급자를 바꾸더라도 `uploadToCdn` 메서드만 수정하면 됩니다.

> **흔한 실수:** `args.setResourceFileName(...)` 호출을 빼먹으면 Aspose가 markdown 파일 옆에 무작위 이름으로 이미지를 저장해 상대 경로가 깨집니다.

---

## Step 4 – Save the Document as Markdown

콜백을 연결했으니 마지막 단계는 markdown 파일을 한 줄 코드로 저장하는 것입니다. 이미지마다 콜백이 자동으로 실행됩니다.

```java
        // Save the document as Markdown, applying the custom resource handling
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

프로그램이 종료되면 다음을 확인할 수 있습니다:

1. `output.md` – CDN을 가리키는 이미지 참조가 포함된 markdown 텍스트 (예: `![](https://cdn.example.com/images/picture1.png)`).
2. 원본 이미지를 담은 `imgs/` 폴더 – 디버깅이나 폴백 시나리오에 유용합니다.

---

## Expected Output

`input.docx`에 `chart.png`라는 단일 그림이 포함되어 있다고 가정하면, 생성된 `output.md`는 다음과 같습니다:

```markdown
# My Document Title

Here is an introductory paragraph.

![](https://cdn.example.com/images/chart.png)

More text follows...
```

이미지가 이제 CDN을 통해 제공되므로, GitHub, 정적 사이트 생성기 등 모든 다운스트림 소비자는 전 세계에 분산된 엣지 위치에서 이미지를 가져오게 됩니다.

---

## Pro Tips & Edge Cases

| 상황 | 해결 방법 |
|-----------|------------|
| **수십 개의 이미지를 포함한 대용량 DOCX** | 메인 스레드 차단을 피하기 위해 이미지를 비동기적으로 배치 업로드합니다. |
| **CDN에서 지원하지 않는 이미지 포맷** | 업로드 전에 `args.getResourceBytes()`를 지원 포맷(PNG 등)으로 변환합니다. |
| **문서별 맞춤 폴더 구조가 필요할 때** | `args.setResourceFileName("docs/" + docId + "/" + args.getResourceFileName());`를 사용합니다. |
| **CDN이 인증 헤더를 요구할 때** | `uploadToCdn` 구현에서 서명된 URL이나 인증을 처리하는 SDK를 사용합니다. |
| **오프라인 문서를 위한 base64 폴백이 필요할 때** | `saveOptions.setExportImagesAsBase64(true)`를 설정하고, 원한다면 CDN 업로드 콜백도 유지합니다. |

---

## Frequently Asked Questions

**Q: 오래된 Aspose.Words 버전에서도 작동하나요?**  
A: `IResourceSavingCallback` API는 버전 20.5에서 도입되었습니다. 이전 버전을 사용 중이라면 업그레이드하세요—코드는 앞으로도 호환되며 성능 향상도 얻을 수 있습니다.

**Q: 아직 CDN이 없으면 어떻게 하나요?**  
A: 예제의 `uploadToCdn` 메서드는 단순히 가짜 URL을 반환합니다. CDN 업로드 없이 변환을 실행하면 markdown이 로컬 `imgs/` 경로를 참조합니다.

**Q: 여러 DOCX 파일을 한 번에 변환할 수 있나요?**  
A: 가능합니다. 로직을 루프에 넣어 각 iteration마다 다른 `input.docx`와 출력 경로를 전달하면 됩니다. 많은 파일을 처리할 경우 속도를 위해 `MarkdownSaveOptions` 인스턴스를 재사용하세요.

---

## Conclusion

우리는 Aspose.Words for Java를 사용해 **DOCX를 markdown으로 변환하면서 이미지를 CDN에 업로드**하는 방법을 살펴보았습니다. 핵심 흐름은 다음 세 단계로 요약됩니다:

1. Word 문서를 로드한다.
2. 각 이미지를 업로드하고 markdown 링크를 재작성하는 `IResourceSavingCallback`을 연결한다.
3. `MarkdownSaveOptions`로 문서를 저장한다.

이제 별도의 후처리 스크립트나 이미지 URL을 수동 복사할 필요 없이 정적 사이트 생성기, 문서 포털, 기타 markdown 친화적인 플랫폼에 바로 사용할 수 있는 깔끔한 markdown 파일을 얻었습니다.

다음 도전 과제는? **Azure Blob Storage** SDK 호출로 CDN 업로드 부분을 교체하거나, **GitHub‑flavored markdown** 옵션(`saveOptions.setExportImagesAsBase64(true)`)을 실험해 보세요. CI/CD 파이프라인에 통합해 커밋마다 자동으로 최신 문서를 배포하도록 할 수도 있습니다.

문제에 부딪히거나 멋진 팁을 발견했다면 아래 댓글에 공유해 주세요. 즐거운 코딩 되시고, 엣지에서 제공되는 이미지 속도를 만끽하세요!

---

![DOCX를 Markdown으로 변환하는 동안 이미지 CDN 업로드 워크플로우를 나타낸 다이어그램](upload-images-to-cdn-diagram.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}