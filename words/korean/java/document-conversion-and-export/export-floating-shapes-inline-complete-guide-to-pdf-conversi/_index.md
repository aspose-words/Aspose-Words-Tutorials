---
category: general
date: 2026-07-03
description: 워드에서 PDF로 변환할 때 떠다니는 도형을 인라인으로 내보냅니다. Java에서 PDF 옵션을 설정하고 워드를 PDF로 저장하는
  방법을 배워보세요.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: ko
og_description: Word 문서를 PDF로 변환할 때 떠 있는 도형을 인라인으로 내보냅니다. 이 튜토리얼에서는 PDF 옵션을 설정하고 Word를
  PDF로 저장하는 방법을 보여줍니다.
og_title: 플로팅 도형 인라인 내보내기 – Java PDF 변환 가이드
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: 플로팅 도형 인라인 내보내기 – PDF 변환 완전 가이드
url: /ko/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 인라인 부동 도형 내보내기 – PDF 변환 완전 가이드

Word 문서를 PDF로 변환할 때 **부동 도형을 인라인으로 내보내야** 했던 적이 있나요? 당신만 그런 것이 아닙니다—많은 개발자들이 다이어그램이나 아이콘이 신비롭게 별도 레이어로 이동하는 문제에 직면합니다. 좋은 소식은 단일 PDF 옵션으로 이러한 도형을 `<span>` 태그 안에 꼭 맞게 유지할 수 있어, Word에서 보는 레이아웃을 정확히 보존한다는 것입니다.

이 튜토리얼에서는 Java에서 **PDF 옵션 설정 방법**을 단계별로 안내하고, **Word를 PDF 옵션으로 저장**하는 정확한 코드를 보여주며, 기본 블록‑레벨 내보내기 대신 **Word를 PDF 인라인으로 변환**하고 싶을 때의 이유를 설명합니다. 끝까지 읽으면 Maven이나 Gradle 프로젝트에 바로 넣어 사용할 수 있는 실행 가능한 스니펫을 얻게 됩니다.

## 배울 내용

- 부동 도형에 대한 인라인 `<span>`과 블록 `<div>` 내보내기의 차이점.  
- `PdfSaveOptions`를 구성하여 인라인 렌더링을 강제하는 방법.  
- `.docx`를 로드하고 옵션을 적용한 뒤 PDF로 저장하는 단계별 코드.  
- 일반적인 함정(누락된 글꼴, 지원되지 않는 도형)과 이를 피하는 방법.  
- 출력 테스트 팁 및 이 접근 방식을 다른 문서 요소에 확장하는 방법.

**Prerequisites** – Java 8 이상, Aspose.Words for Java 라이브러리(또는 `PdfSaveOptions` 클래스를 그대로 제공하는 API), 부동 도형이 포함된 샘플 Word 파일(`FloatingShapes.docx` 사용). 다른 외부 도구는 필요하지 않습니다.

---

## Step 1: Load the Source Word Document

변환하려는 `.docx` 파일을 여는 것이 첫 번째 단계입니다. 이는 간단하지만 경로가 절대 경로나 클래스패스에서 올바르게 해석되는지 확인하세요.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*왜 중요한가:*  
문서를 올바르게 로드하지 못하면 이후 PDF 변환 시 `FileNotFoundException`이 발생합니다. `Document`를 사용하면 내부 객체 모델이 완전히 채워져 페이지에 존재하는 모든 부동 도형까지 포함됩니다.

## Step 2: Create PDF Save Options and Set Floating Shapes to Inline

여기서 마법이 일어납니다. 기본적으로 Aspose.Words는 부동 도형을 블록‑레벨 `<div>` 요소로 내보내어 HTML 기반 PDF에서 흐름을 깨뜨릴 수 있습니다. `setExportFloatingShapesAsInlineTag(true)`를 설정하면 엔진이 각 도형을 인라인 `<span>`으로 감싸도록 지시합니다.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*왜 중요한가:*  
- **레이아웃 정확도** – 인라인 태그는 도형을 주변 텍스트와 정렬된 상태로 유지하여 원치 않는 공백을 방지합니다.  
- **검색 가능성** – 인라인 요소는 PDF 리더가 올바르게 인덱싱할 가능성이 높습니다.  
- **스타일 제어** – 나중에 PDF를 HTML로 다시 변환할 경우 CSS로 `<span>`을 대상으로 할 수 있습니다.

> **Pro tip:** 특정 문서에 대해 기존 블록 동작이 필요하면 `false`를 전달하거나 호출 자체를 생략하면 됩니다.

## Step 3: Save the Document as a PDF Using the Configured Options

이제 로드한 `Document`와 `PdfSaveOptions`를 결합해 파일을 저장합니다. 이 한 줄이 모든 작업을 수행합니다.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*왜 중요한가:*  
`save` 메서드는 `pdfOptions`에 설정한 모든 플래그를 존중합니다. 옵션을 전달하지 않으면 기본 블록 내보내기로 돌아가 **부동 도형을 인라인으로 내보내기** 목적이 무효화됩니다.

## Full Working Example

모두 합치면 지금 바로 컴파일하고 실행할 수 있는 간결한 프로그램이 됩니다. `YOUR_DIRECTORY`를 실제 경로로 바꾸세요.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output** – 프로그램을 실행한 뒤 `FloatingShapes.pdf`를 열면 도형이 텍스트와 딱 맞게 배치되고 여분의 공백이 없으며, PDF 내부 구조를 검사하면 각 도형 주위에 `<span>` 태그가 포함되어 있음을 확인할 수 있습니다.

![인라인 부동 도형 내보내기 예시](https://example.com/export-inline.png "PDF에서 인라인으로 렌더링된 부동 도형을 보여주는 스크린샷")

*이미지 대체 텍스트:* **인라인 부동 도형 내보내기** PDF에서 인라인 도형이 포함된 스크린샷.

## Common Questions & Edge Cases

### 1. “문서에 복잡한 SmartArt가 포함되어 있으면 어떻게 하나요?”

SmartArt는 그림 객체로 처리됩니다. 인라인 플래그는 대부분의 벡터 도형에 적용되지만, 매우 복잡한 SmartArt는 여전히 이미지로 렌더링될 수 있습니다. 이런 경우 변환 전에 Word에서 SmartArt를 평면화하거나 `pdfOptions.setExportSmartArtAsImage(true)`를 사용해 이미지 내보내기를 강제하세요.

### 2. “같은 문서에서 인라인과 블록 내보내기를 혼합할 수 있나요?”

안타깝게도 API는 설정을 전역적으로 적용합니다. 혼합 동작이 필요하면 문서를 섹션으로 나누고 각 섹션을 다른 옵션으로 별도 내보낸 뒤 `PdfMerger`를 사용해 PDF를 병합하세요.

### 3. “폰트 임베딩에 영향을 줍니까?”

아니요. 폰트 임베딩은 `pdfOptions.setEmbedFullFonts(true)`(기본값)로 제어됩니다. 인라인 도형 플래그와는 무관하게 안전하게 켜거나 끌 수 있습니다.

### 4. “도형이 실제로 `<span>`인지 어떻게 확인하나요?”

**PDF.js** 또는 **Adobe Acrobat** → **Edit PDF** → **Object Inspector** 같은 도구로 결과 PDF를 열면 기본 XML에서 도형이 `<span>` 요소로 감싸져 있는 것을 볼 수 있습니다. `<div>`가 보이면 옵션이 적용되지 않은 것입니다.

## Extending the Approach – Related Options

여기까지 오셨다면 다른 PDF 변환 옵션도 살펴볼 가치가 있습니다:

| 옵션 | 기능 설명 | 일반적인 사용 사례 |
|------|----------|-------------------|
| `setCompressImages(true)` | 이미지 크기 감소 | 빠른 다운로드 |
| `setUseHighQualityRendering(true)` | 벡터 렌더링 향상 | 인쇄용 PDF |
| `setExportDocumentStructure(true)` | 접근성을 위한 구조 태그 추가 | WCAG 준수 |
| `setSaveFormat(SaveFormat.PDF)` | 형식을 명시적으로 설정 (드물게 필요) | 다중 형식 파이프라인 |

## Testing Your Conversion

1. **시각적 확인** – 두 뷰어(Chrome 및 Adobe Reader)에서 PDF를 열어 도형이 정렬되는지 확인합니다.  
2. **자동 차이점 검사** – `pdfbox`와 같은 라이브러리를 사용해 XML을 추출하고 `<span>` 태그 존재를 검증합니다.  
3. **성능 벤치마크** – `setCompressImages` 사용 여부에 따른 소요 시간을 측정해 트레이드오프를 확인합니다.

A quick JUnit example:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

## Conclusion

이제 **부동 도형을 인라인으로 내보내기**와 **Word를 PDF 인라인으로 변환**하기 위한 견고한 엔드‑투‑엔드 솔루션을 갖추었습니다. `PdfSaveOptions`를 구성하면 각 도형에 사용되는 HTML 태그를 제어해 PDF를 깔끔하고 검색 가능하게 유지할 수 있습니다. 출력물을 테스트하고 이미지 압축 같은 관련 옵션을 조정하며 복잡한 SmartArt와 같은 예외 상황을 처리하는 것을 잊지 마세요.

다음 단계가 준비되셨나요? 같은 기술을 **부동 표를 인라인으로 내보내기**에 적용하거나 Aspose의 `HtmlSaveOptions`를 활용해 CSS‑스타일 PDF를 실험해 보세요. 로드 → 구성 → 저장이라는 동일한 패턴이 거의 모든 문서‑to‑PDF 시나리오에 적용됩니다.

**pdf 옵션 설정 방법**이나 다른 라이브러리의 **Word를 PDF 옵션으로 저장**에 대해 더 궁금한 점이 있으면 댓글을 남겨 주세요. 즐거운 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 연관된 주제를 다룹니다. 각 자료에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 다양한 구현 방식을 탐색할 수 있습니다.

- [Aspose.Words for Java를 사용한 Word를 PDF로 변환](/words/english/java/document-converting/)
- [Aspose.Words for Java로 문서를 PDF로 저장하는 방법](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word 문서 구조를 PDF 문서로 내보내기](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}