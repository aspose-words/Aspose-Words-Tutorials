---
category: general
date: 2026-02-18
description: DOCX를 PDF로 변환하고 워드를 PDF로 저장하면서 떠 있는 도형을 보존하는 방법을 배워보세요. 이 가이드는 도형을 올바르게
  내보내는 방법을 보여줍니다.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: ko
og_description: DOCX를 PDF로 변환하고 도형 내보내는 방법을 배우세요. 적절한 태깅이 포함된 Word를 PDF로 저장하는 전체 튜토리얼을
  따라보세요.
og_title: DOCX를 PDF로 변환 – 인라인 도형 내보내기 가이드
tags:
- Aspose.Words
- Java
- PDF conversion
title: 인라인 도형 내보내기로 DOCX를 PDF로 변환 – 단계별 가이드
url: /ko/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 PDF로 변환 – 인라인 도형 내보내기 가이드

DOCX를 PDF로 **변환**하려는데 떠다니는 이미지나 텍스트 상자가 사라지거나 위치가 바뀔까 걱정되셨나요? 혼자가 아닙니다. 자동 보고서 생성기나 배치‑처리 파이프라인처럼 Word 문서의 정확한 레이아웃을 유지해야 하는 프로젝트가 많습니다.  

좋은 소식은? 몇 줄의 코드만으로 **Word를 PDF로 저장**하고 떠다니는 도형을 인라인 태그로 변환할지 블록‑레벨 요소로 유지할지를 제어할 수 있다는 것입니다. 아래에서는 **도형을 원하는 방식으로 내보내는 방법**을 정확히 보여주고, 흔히 겪는 함정을 피할 수 있는 팁도 함께 제공합니다.

---

## 배울 내용

* 디스크에서 `.docx` 파일을 로드합니다.  
* 떠다니는 도형을 인라인 태그로 내보내도록 `PdfSaveOptions`를 설정합니다.  
* 결과 PDF를 원하는 폴더에 저장합니다.  
* `setExportFloatingShapesAsInlineTag` 플래그가 왜 중요한지, 언제 값을 바꿔야 하는지 이해합니다.  

외부 서비스 없이, 마법 같은 “클릭‑투‑다운로드” UI 없이—그냥 순수 Java 코드만 있으면 Maven이나 Gradle 프로젝트 어디에든 넣어 사용할 수 있습니다.

---

## 사전 요구 사항

| Requirement | Why it matters |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 이상) | 예제에서 사용되는 `Document`와 `PdfSaveOptions` 클래스를 제공합니다. |
| **JDK 8+** | 라이브러리가 Java 8 이상에서 컴파일되었으며, 이전 런타임에서는 `UnsupportedClassVersionError`가 발생합니다. |
| **떠다니는 도형(이미지, 텍스트 상자, WordArt)이 포함된 DOCX 파일** | 도형‑내보내기 옵션의 효과를 확인하려면 실제로 떠다니는 객체가 들어 있는 문서가 필요합니다. |

이미 준비가 되었다면, 바로 시작해 보세요.

---

## Step 1 – 원본 문서 로드  

먼저 변환하려는 `.docx`를 가리키는 `Document` 인스턴스를 생성합니다. 생성자는 파일을 메모리로 읽어들여 OpenXML 패키지를 파싱하고 내부 객체 모델을 준비합니다.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tip:** 여러 파일을 루프에서 처리한다면 `doc.close()`를 호출한 뒤(또는 가비지 컬렉터에 맡겨) 동일한 `Document` 객체를 재사용하세요. 이렇게 하면 Windows에서 파일‑핸들 누수를 방지할 수 있습니다.

---

## Step 2 – 도형 내보내기를 위한 PDF 저장 옵션 설정  

튜토리얼의 핵심이 여기 있습니다. `PdfSaveOptions`를 사용하면 변환 동작을 세밀하게 제어할 수 있습니다. `setExportFloatingShapesAsInlineTag(true)`를 설정하면 모든 떠다니는 도형이 PDF 태그 구조에서 *인라인* 요소로 처리됩니다. 즉, 스크린리더가 주변 텍스트와 동일한 순서로 도형을 읽게 되며, 이는 접근성 준수에 자주 필요합니다.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**`false`로 설정하면 언제 사용할까요?**  
PDF가 인쇄 전용 배포용이고 도형이 원래 위치를 유지하면서 논리적 읽기 순서에 영향을 주지 않길 원한다면 블록‑레벨 태깅을 선호할 수 있습니다. 기본값은 `false`이므로, 이번 튜토리얼에서는 인라인 동작을 명시적으로 활성화했습니다.

---

## Step 3 – 문서를 PDF로 저장  

옵션이 준비되었으니, 대상 파일명과 옵션 객체를 전달해 `save`를 호출합니다. 라이브러리가 레이아웃 엔진, 폰트 임베딩, 태그 생성 등 무거운 작업을 처리합니다.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

호출이 끝나면 지정한 폴더에 `shapes.pdf`가 생성됩니다. Adobe Acrobat이나 태그를 표시하는 PDF 뷰어(**File → Properties → Tags**)에서 열어 보면 떠다니는 도형이 인라인 태그로 표시된 것을 확인할 수 있습니다.

---

## 전체 실행 가능한 예제  

전체 코드를 한데 모은 아래 Java 클래스를 컴파일하고 실행해 보세요. Aspose.Words JAR가 클래스패스에 포함되어 있어야 합니다.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**예상 결과:**  
- PDF 파일에 원본 DOCX와 동일한 텍스트 내용이 포함됩니다.  
- 모든 떠다니는 이미지나 텍스트 상자가 *인라인*으로 태깅되어 읽기 순서에 포함됩니다.  
- PDF의 **Tags** 패널을 열면 `<Paragraph>` 안에 `<Figure>` 요소가 중첩된 것을 볼 수 있습니다—`setExportFloatingShapesAsInlineTag(true)`가 보장하는 바로 그 형태입니다.

---

## 자주 묻는 질문 & 예외 상황  

### 1️⃣ 비밀번호로 보호된 DOCX 파일도 작동하나요?  
네—로드하기 전에 비밀번호를 전달하면 됩니다.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Word 파일 안에 SVG나 EMF 이미지가 있으면 어떻게 되나요?  
Aspose.Words는 PDF 저장 시 벡터 그래픽을 자동으로 래스터화합니다. 벡터 형태를 유지하려면 다음을 설정하세요.

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ 변환하면서 하이퍼링크를 유지하려면?  
링크는 기본적으로 보존됩니다. 다만 `pdfOptions.setSaveFormat(SaveFormat.PDF)`만 사용하고 옵션을 지정하지 않으면 논리 구조가 사라질 수 있습니다. 태그와 링크를 모두 유지하려면 `PdfSaveOptions` 객체를 사용하세요.

### 4️⃣ 폴더에 있는 여러 DOCX 파일을 일괄 처리할 수 있나요?  
물론 가능합니다. `DocxToPdfWithShapes` 로직을 `Files.list(Paths.get("YOUR_DIRECTORY"))` 루프에 감싸면 됩니다. 파일당 예외를 처리해 하나의 문서 오류가 전체 실행을 멈추지 않도록 하세요.

---

## 현장 팁  

* **누락된 폰트에 주의** – 원본 DOCX가 서버에 설치되지 않은 사용자 정의 폰트를 사용하면 PDF가 대체 폰트로 교체되어 레이아웃이 깨질 수 있습니다. `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)`를 사용해 모든 폰트를 강제로 임베드하세요.  
* **접근성 테스트** – 변환 후 Acrobat의 **Accessibility Checker**를 실행하세요. 인라인 태깅은 점수를 보통 올려주지만, 이미지에 대체 텍스트를 수동으로 추가해야 할 수도 있습니다.  
* **성능 팁** – 100페이지 이상 대용량 문서의 경우 `pdfOptions.setMemoryOptimization(true)`를 활성화해 힙 사용량을 줄이세요.

---

## 시각적 확인  

아래는 Adobe Acrobat에서 PDF를 열어 **Tags** 패널에 인라인‑태깅된 도형이 강조 표시된 스크린샷입니다.

![Convert DOCX to PDF example output](image.png)

*Alt text: 인라인 도형 태그가 표시된 PDF 예시 출력 화면.*

---

## 마무리  

이제 **DOCX를 PDF로 변환**하면서 떠다니는 객체가 어떻게 내보내지는지 제어하는 방법을 알게 되었습니다. `setExportFloatingShapesAsInlineTag`를 토글하면 도형이 읽기 순서에 포함될지 독립 블록으로 남을지를 선택할 수 있어, 접근성과 시각적 정확성 모두에 중요한 역할을 합니다.  

다음 단계로 할 수 있는 일:

* **Word를 PDF로 대량 저장**해 보관용으로 활용하기.  
* `setCompliance(PdfCompliance.PDF_A_1B)`와 같은 다른 `PdfSaveOptions`를 실험해 장기 보존을 위한 PDF/A 생성하기.  
* `setExportDocumentStructure(true)` 플래그를 사용해 더 풍부한 태그 트리를 탐색하며 **도형 내보내기**에 대해 깊이 파고들기.

옵션을 직접 만져보고, PDF가 원하는 대로 나오는지 확인해 보세요. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}