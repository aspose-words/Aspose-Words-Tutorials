---
category: general
date: 2026-06-05
description: DOCX에서 PDF로 저장하면서 떠다니는 도형을 인라인 태그로 보존하는 방법. DOCX를 PDF로 저장하고, 워드를 PDF로
  변환하며, 도형을 올바르게 내보내는 방법을 배워보세요.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- save word pdf inline
language: ko
og_description: 워드 문서에서 떠다니는 도형을 인라인 태그로 내보내면서 PDF로 저장하는 방법. 이 단계별 가이드를 따라 docx를 PDF로
  저장하고 워드를 올바르게 PDF로 변환하세요.
og_title: 워드에서 인라인 도형으로 PDF 저장하는 방법 – 전체 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  headline: How to Save PDF from Word with Inline Shapes – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  name: How to Save PDF from Word with Inline Shapes – Complete Guide
  steps:
  - name: Large Images
    text: 'If a floating shape contains a high‑resolution image, converting it to
      inline may cause the line height to expand dramatically. To keep the PDF tidy:'
  - name: Multiple Sections with Different Layouts
    text: 'When a document has sections with distinct page setups, you might need
      to apply the inline conversion only to a specific section:'
  - name: Converting Multiple DOCX Files in a Batch
    text: 'If you need to **convert word to pdf** for dozens of files, wrap the logic
      into a utility method:'
  - name: Expected Result
    text: Running the program should produce `inlineShapes.pdf`. Open it, and you’ll
      notice that any floating text boxes, callouts, or images now sit **inline**
      with the surrounding text, mirroring the layout you designed in Word.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF conversion
title: 워드에서 인라인 도형을 사용해 PDF 저장하는 방법 – 완전 가이드
url: /ko/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 워드에서 인라인 도형으로 PDF 저장하기 – 완전 가이드

워드 파일을 PDF로 저장할 때 떠다니는 이미지 레이아웃이 깨지는 **PDF 저장 방법**이 궁금하셨나요? 여러분만 그런 것이 아닙니다. 많은 보고서나 청구서 애플리케이션에서 텍스트 상자, 콜아웃, 장식 아이콘과 같은 떠다니는 도형은 “PDF로 저장”만 클릭하면 위치가 어긋나는 경우가 많습니다.  

다행히도, 떠다니는 도형을 `<inline>` 태그로 변환하도록 PDF 내보내기를 설정하면 객체를 정확히 원하는 위치에 유지할 수 있는 깔끔하고 프로그래밍적인 방법이 있습니다. 이번 튜토리얼에서는 **도형 내보내기 방법**, **docx를 pdf로 저장**하기, 그리고 **word를 pdf로 변환**하는 과정을 몇 줄의 Java 코드로 살펴보겠습니다. 마지막까지 따라오시면 모든 도형이 인라인으로 렌더링된 PDF를 바로 실행할 수 있는 스니펫을 얻게 됩니다.

## What You’ll Learn

- 디스크(또는 스트림)에서 DOCX 파일을 Aspose.Words for Java 로 로드하기.  
- 떠다니는 객체를 인라인 태그로 변환하도록 **save word pdf inline** 옵션 활성화하기.  
- 구성된 `PdfSaveOptions` 로 문서를 PDF로 저장하기.  
- 큰 이미지나 복잡한 표와 같은 엣지 케이스를 처리하기 위한 팁.  

외부 도구 없이, Word UI를 수동으로 조작하지 않고—그냥 깔끔한 코드를 Java 프로젝트에 바로 넣기만 하면 됩니다.

---

## Prerequisites

시작하기 전에 아래 항목들을 준비하세요:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | Aspose.Words for Java 는 최신 JDK에서 동작합니다. |
| **Aspose.Words for Java** library (latest version) | `Document`, `PdfSaveOptions`, `setExportFloatingShapesAsInlineTag` 메서드를 제공합니다. |
| 떠다니는 도형(예: 텍스트 상자)이 포함된 **DOCX** 파일 | 도형이 없으면 인라인 내보내기 효과를 확인할 수 없습니다. |
| 의존성 관리를 위한 IDE 또는 빌드 도구(Maven/Gradle) | 컴파일을 손쉽게 해줍니다. |

Maven을 사용한다면 아래와 같이 의존성을 추가하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check for the latest version -->
</dependency>
```

---

## Step 1: Load the Source Document

먼저 Word 파일을 나타내는 `Document` 객체가 필요합니다. 이는 Aspose.Words 가 나중에 PDF로 그릴 캔버스와 같습니다.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters:* 파일을 메모리로 로드하면 문단, 런, 도형 등 객체 모델 전체에 접근할 수 있습니다. 경로가 잘못되면 `FileNotFoundException` 이 발생하니 파일 존재 여부를 반드시 확인하세요.

> **Pro tip:** DOCX 를 데이터베이스나 웹 서비스에서 가져오는 경우 파일 경로 대신 `InputStream` 생성자를 사용할 수 있습니다.

---

## Step 2: Configure PDF Save Options to Export Floating Shapes as Inline Tags

기본적으로 Aspose.Words 는 떠다니는 도형을 PDF에서도 떠다니게 유지하려고 합니다. 이는 PDF 뷰어가 레이아웃을 다르게 해석하면서 정렬이 깨질 수 있습니다. `PdfSaveOptions` 클래스를 사용하면 이 동작을 바꿀 수 있습니다.

```java
// Step 2: Configure PDF save options to export floating shapes as <inline> tags
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

*Why this matters:* `setExportFloatingShapesAsInlineTag(true)` 를 설정하면 각 떠다니는 도형을 주변 문단의 일부처럼 취급합니다. 결과적으로 도형이 텍스트와 함께 이동해 빈칸이나 겹침 현상이 사라집니다.

> **Common question:** *일부 도형은 여전히 떠다니게 유지하고 싶다면?*  
> Word 문서에서 개별 도형의 `WrapType` 을 조정하거나, 전체 문서에 대해 인라인 변환을 비활성화하고 해당 도형을 수동으로 처리하면 됩니다.

---

## Step 3: Save the Document as a PDF with the Configured Options

문서를 로드하고 내보내기 동작을 조정했으니 이제 PDF 파일을 디스크에 기록합니다.

```java
// Step 3: Save the document as a PDF with the configured options
doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);
```

*Why this matters:* `save` 메서드는 출력 경로와 `PdfSaveOptions` 인스턴스를 모두 받아 인라인‑도형 설정이 적용되도록 보장합니다. 옵션을 생략하면 기본 동작(떠다니는 도형 유지)으로 돌아갑니다.

> **Expected output:** `inlineShapes.pdf` 를 아무 PDF 뷰어에서 열어 보세요. 이전에 떠다니던 텍스트 상자나 이미지가 이제 **인라인** 으로 표시되어 Word에서 보던 레이아웃이 그대로 유지됩니다.

---

## Handling Edge Cases and Variations

### Large Images

떠다니는 도형에 고해상도 이미지가 포함된 경우 인라인 변환 시 행 높이가 크게 늘어날 수 있습니다. PDF 를 깔끔하게 유지하려면:

```java
// Reduce image size before export (optional)
Shape shape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
shape.getImageData().setImageBytes(resizeImage(shape.getImageData().getImageBytes(), 800, 600));
```

*Explanation:* 이미지를 리사이즈하면 차원 자체가 줄어들어 최종 PDF 에서 과도하게 큰 행이 생기는 것을 방지합니다.

### Multiple Sections with Different Layouts

문서에 페이지 설정이 다른 섹션이 여러 개 있을 때는 특정 섹션에만 인라인 변환을 적용할 수 있습니다:

```java
for (Section sec : doc.getSections()) {
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(sec.getPageSetup().getPaperSize() == PaperSize.A4);
    doc.save("section_" + sec.getId() + ".pdf", opts);
}
```

*Why this works:* 루프를 통해 섹션별로 별도의 PDF 를 생성하고, 용지 크기에 따라 인라인 변환을 조건부로 적용합니다.

### Converting Multiple DOCX Files in a Batch

수십 개의 파일을 **convert word to pdf** 해야 한다면 로직을 유틸 메서드로 감싸세요:

```java
public static void convertDocxToPdfInline(String inputPath, String outputPath) throws Exception {
    Document doc = new Document(inputPath);
    PdfSaveOptions options = new PdfSaveOptions();
    options.setExportFloatingShapesAsInlineTag(true);
    doc.save(outputPath, options);
}
```

그런 다음 `Files.list(Paths.get("batch_folder"))` 스트림 안에서 이 메서드를 호출하면 됩니다.

---

## Full Working Example (All Steps Combined)

아래는 **how to save pdf** with inline shapes from a DOCX file 을 보여주는 완전한 실행 가능한 Java 프로그램입니다.

```java
import com.aspose.words.*;

public class InlineShapePdfExporter {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Set PDF options to export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF
            doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);

            System.out.println("PDF saved successfully with inline shapes!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Expected Result

프로그램을 실행하면 `inlineShapes.pdf` 가 생성됩니다. 파일을 열어 보면 떠다니던 텍스트 박스, 콜아웃, 이미지가 모두 주변 텍스트와 **인라인** 으로 배치되어 Word 에서 디자인한 레이아웃과 동일하게 보입니다.

---

## Frequently Asked Questions

| Question | Answer |
|----------|--------|
| **Does this work with .doc files?** | Yes. Aspose.Words can load older `.doc` formats; the same `PdfSaveOptions` apply. |
| **Can I keep some shapes floating?** | You’d need to adjust the shape’s `WrapType` to `INLINE` manually before export, or run a second export without the inline flag for those sections. |
| **Is there any performance impact?** | The extra conversion step adds negligible overhead—usually a few milliseconds per document. |
| **What about password‑protected DOCX?** | Load the document with `LoadOptions` that include the password, then proceed as usual. |
| **Will this work on Linux/macOS?** | Absolutely. Aspose.Words for Java is platform‑agnostic. |

---

## Next Steps & Related Topics

이제 **how to export shapes** 와 **save docx as pdf** 를 마스터했으니 다음 주제들을 살펴보세요:

- **Styling PDFs** – `PdfSaveOptions.setCompliance(PdfCompliance.PDF_A_1_B)` 로 보관용 PDF 생성.  
- **Adding Watermarks** – 저장 전에 `Watermark` 객체를 삽입.  
- **Converting to other formats** – `doc.save("output.html", SaveFormat.HTML)` 로 웹용 HTML 출력.  
- **Batch processing** – 유틸 메서드와 스케줄러를 결합해 자동 문서 파이프라인 구축.  

위 내용들은 지금까지 다진 기반 위에 추가 기능을 쌓아 **convert word to pdf** 를 더욱 정교하게 활용할 수 있게 해줍니다.

---

## Conclusion

우리는 **how to save pdf** from a Word document while ensuring floating shapes become inline tags 라는 기술을 다뤘습니다. DOCX 를 로드하고, `PdfSaveOptions` 에 `setExportFloatingShapesAsInlineTag(true)` 를 설정한 뒤 저장하면 레이아웃이 깨지지 않는 깔끔한 변환이 가능합니다—보고서, 청구서, 자동화된 문서 워크플로우에 최적입니다.  

코드를 실행해 보고 옵션을 조정해 보세요. 개발자가 **save word pdf inline** 를 문제 없이 구현할 수 있는 이유를 직접 확인하실 수 있을 겁니다. Happy coding, and may your PDFs always look exactly as you intended!

## What Should You Learn Next?

다음 튜토리얼들은 이번 가이드에서 다룬 기술을 확장하고, 여러분의 프로젝트에 다양한 API 기능을 적용할 수 있도록 도와줍니다. 각 자료는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가적인 기능을 빠르게 습득할 수 있습니다.

- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [save docx as pdf with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}