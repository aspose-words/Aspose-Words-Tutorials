---
category: general
date: 2026-02-18
description: Java에서 docx 파일을 복구하고, LaTeX 수식을 포함한 markdown으로 내보내며, PDF/UA 준수를 달성하는
  방법을 배워보세요.
draft: false
keywords:
- how to recover docx
- export docx to markdown
- markdown with latex math
- pdf ua compliance
- save as pdf ua
language: ko
og_description: Java를 사용하여 docx 파일을 복구하고, LaTeX 수식이 포함된 마크다운으로 내보낸 뒤 PDF/UA로 저장하는
  방법.
og_title: DOCX 복구, 마크다운 및 PDF/UA 내보내기 – Java 튜토리얼
tags:
- Aspose.Words
- Java
- Document Conversion
- PDF/UA
title: DOCX 복구, Markdown 및 PDF/UA 내보내기 – 완전한 Java 가이드
url: /ko/java/document-conversion-and-export/how-to-recover-docx-export-to-markdown-pdf-ua-complete-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX 복구, Markdown 및 PDF/UA 내보내기 – 완전한 Java 가이드

DOCX 파일이 손상될 수 있다는 생각을 해본 적 있나요? Word 문서를 열었을 때 “파일이 손상되었습니다”라는 메시지를 본 적이 있을 겁니다. 제 경험상, 몇 줄의 Java 코드만 있으면 깨진 DOCX의 고통을 피할 수 있습니다—특히 복구 모드를 지원하는 라이브러리를 사용할 때 말이죠.  

이 튜토리얼에서는 **DOCX 복구 방법**을 보여줄 뿐만 아니라 **DOCX를 Markdown으로 내보내는 방법**(LaTeX 수식 지원 포함)과 최종적으로 **PDF/UA로 저장하는 방법**을 단계별로 안내합니다. 끝까지 따라오시면 불안정한 DOCX를 깔끔한 Markdown과 완전한 PDF/UA 파일로 변환하는 실행 가능한 프로그램을 얻게 됩니다.

> **얻을 수 있는 것:** 단계별 솔루션, 전체 소스 코드, 각 API 호출이 왜 중요한지에 대한 설명, 그리고 흔히 겪는 함정을 피할 수 있는 몇 가지 프로 팁.

## 사전 요구 사항

- Java 17 이상 (코드는 최신 JDK에서 모두 컴파일됩니다).  
- Aspose.Words for Java 23.10 이상 – `LoadOptions`, `MarkdownSaveOptions`, `PdfSaveOptions` 등을 제공하는 라이브러리.  
- 손상되었을 가능성이 있는 DOCX 파일(`input.docx`라고 부르겠습니다).  
- Java 문법에 대한 기본적인 이해—깊은 내부 구조는 필요 없습니다.

Aspose.Words JAR가 없으시다면 공식 Maven 저장소에서 받아오세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

이제 기본 준비가 끝났으니 실제 복구 과정을 살펴보겠습니다.

## DOCX 복구 – 복구 모드로 로드하기

DOCX가 부분적으로 손상된 경우, Aspose.Words는 *복구 모드*로 열 수 있습니다. 이 모드는 경고가 발생해도 계속 진행하도록 엔진에 지시하고, 나중에 검토할 수 있도록 경고를 표면에 드러냅니다.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load a possibly corrupted document using recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**왜 복구 모드인가?**  
복구 모드가 없으면 `Document` 생성자가 형식이 잘못된 부분을 만나자마자 예외를 던져 파이프라인 전체가 중단됩니다. `RECOVER_WITH_WARNINGS`를 선택하면 사용 가능한 `Document` 객체와 경고 목록을 얻을 수 있어, 오류의 심각도에 따라 로그를 남기거나 무시할 수 있습니다.

> **프로 팁:** 로드 후 `document.getWarnings()`를 순회하면서 문제를 로그에 기록하세요. 감사 추적에 유용합니다.

## 첫 번째 Shape의 그림자 미세 조정 (선택 사항이지만 예시)

복구 자체와는 직접적인 관련이 없지만, Shape를 조정하면 문서를 **구조화된 후** 어떻게 조작할 수 있는지 보여줍니다. 실제 상황에서는 손상된 후에도 남아 있는 요소들을 정리하거나 스타일을 다시 적용하고 싶을 때가 많습니다.

```java
        // Step 2: Fine‑tune the shadow of the first shape in the document
        Shape firstShape = (Shape) document.getChild(NodeType.SHAPE, 0, true);
        Shadow shapeShadow = firstShape.getShadow();
        shapeShadow.setBlurRadius(4);
        shapeShadow.setOffsetX(2);
        shapeShadow.setOffsetY(2);
        shapeShadow.setColor(Color.getRed());
        shapeShadow.setOpacity(0.5);
```

**무슨 일이 일어나나요?**  
파일 어디에서든 첫 번째 `Shape` 노드를 찾습니다(`true`는 깊은 탐색을 의미). 그런 다음 `Shadow` 속성—블러, 오프셋, 색상, 불투명도—을 조정해 은은한 드롭 섀도우 효과를 줍니다. 원본 DOCX에 Shape가 전혀 없으면 `firstShape`는 `null`이 되므로, 실제 코드에서는 이를 방어해야 합니다.

## DOCX를 Markdown으로 내보내기 – LaTeX 수식 지원

문서가 정상적으로 로드되었으니, 이제 **DOCX를 Markdown으로 내보내** 보겠습니다. `MarkdownSaveOptions` 클래스는 Office Math 수식을 어떻게 렌더링할지 제어합니다. `OfficeMathExportMode.LATEX`를 선택하면 대부분의 Markdown 뷰어에서 아름답게 표시되는 LaTeX 스니펫이 포함된 파일이 생성됩니다.

```java
        // Step 3: Save the document as Markdown with LaTeX math and custom resource handling
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        markdownOptions.setResourceSavingCallback(args -> {
            String resourceFolder = "YOUR_DIRECTORY/md-res/";
            new java.io.File(resourceFolder).mkdirs();
            args.setOutputFileName(resourceFolder + args.getResourceFileName());
        });
        document.save("YOUR_DIRECTORY/demo.md", markdownOptions);
```

**왜 LaTeX인가?**  
GitHub, GitLab, Hugo, Jekyll 같은 Markdown 파서는 보통 MathJax 또는 KaTeX를 내장하고 있습니다. 수식을 LaTeX 형태로 내보내면 선명하고 확장 가능하며 편집이 쉬운 상태를 유지할 수 있습니다. 위 콜백은 추출된 이미지(예: 인라인 사진)를 전용 폴더에 저장해 Markdown을 깔끔하게 유지합니다.

### 예상되는 Markdown 출력

- 모든 일반 텍스트는 일반 Markdown 단락으로 표시됩니다.  
- 수식은 인라인은 `$…$`, 블록은 `$$…$$` 형태로 변환됩니다.  
- 이미지들은 `![](md-res/image1.png)`와 같이 생성한 폴더를 가리키며 참조됩니다.

좋아하는 편집기에서 `demo.md`를 열면 다음과 비슷한 내용이 보일 것입니다:

```markdown
Here is an inline equation $E = mc^2$ that renders nicely.

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$

![](md-res/shape1.png)
```

## PDF/UA 준수 – PDF/UA로 저장하기

마지막으로 **PDF/UA** 표준을 만족하도록 **pdf ua로 저장**합니다. `PdfSaveOptions` 클래스는 준수 여부를 토글하고 떠다니는 Shape의 처리 방식을 결정할 수 있게 해줍니다.

```java
        // Step 4: Save the document as PDF/UA, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        document.save("YOUR_DIRECTORY/demo-ua.pdf", pdfOptions);
    }
}
```

**`setExportFloatingShapesAsInlineTag(true)`는 무엇을 하나요?**  
떠다니는 Shape(텍스트 상자 등)는 스크린 리더가 놓칠 수 있어 접근성 문제를 일으킵니다. 이를 인라인 태그로 내보내면 Shape가 읽기 순서에 포함되어 **PDF/UA 준수** 요구사항을 만족합니다.

### PDF/UA 검증 방법

생성된 `demo-ua.pdf`를 Adobe Acrobat Pro에서 열고 *Accessibility Check* → *Full Check*를 실행하세요. PDF/UA‑1 준수에 대한 초록색 체크마크가 표시될 것입니다. 경고가 나타난다면, 아직 조치가 필요한 요소(예: 이미지에 대한 alt 텍스트 누락)를 알려줍니다.

## 전체 작업 예제 (복사‑붙여넣기 가능)

```java
import com.aspose.words.*;
import java.awt.Color;
import java.io.File;

public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Recover the possibly corrupted DOCX
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ (Optional) Tweak the first shape’s shadow
        Shape firstShape = (Shape) document.getChild(NodeType.SHAPE, 0, true);
        if (firstShape != null) {
            Shadow shapeShadow = firstShape.getShadow();
            shapeShadow.setBlurRadius(4);
            shapeShadow.setOffsetX(2);
            shapeShadow.setOffsetY(2);
            shapeShadow.setColor(Color.getRed());
            shapeShadow.setOpacity(0.5);
        }

        // 3️⃣ Export to Markdown with LaTeX math
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        markdownOptions.setResourceSavingCallback(args -> {
            String resourceFolder = "YOUR_DIRECTORY/md-res/";
            new File(resourceFolder).mkdirs();
            args.setOutputFileName(resourceFolder + args.getResourceFileName());
        });
        document.save("YOUR_DIRECTORY/demo.md", markdownOptions);

        // 4️⃣ Save as PDF/UA compliant file
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        document.save("YOUR_DIRECTORY/demo-ua.pdf", pdfOptions);
    }
}
```

IDE나 명령줄에서 이 클래스를 실행하세요—`YOUR_DIRECTORY` 자리표시자가 실제 존재하는 폴더를 가리키도록 수정해야 합니다. 모든 것이 정상적으로 진행되면 다음과 같은 결과물을 얻게 됩니다:

- `demo.md` – LaTeX 수식이 포함된 깔끔한 Markdown.  
- `md-res/` – 추출된 이미지가 들어 있는 폴더.  
- `demo-ua.pdf` – 배포 가능한 PDF/UA‑1 준수 PDF.

## 자주 묻는 질문 & 엣지 케이스

| 질문 | 답변 |
|----------|--------|
| **DOCX가 완전히 읽을 수 없을 경우는?** | 복구 모드가 최선을 다하지만 큰 섹션이 누락될 수 있습니다. 이 경우 먼저 서드‑파티 복구 도구를 사용한 뒤 Aspose로 로드하는 것을 권장합니다. |
| **다른 Markdown 변형으로 내보낼 수 있나요?** | 네—`MarkdownSaveOptions`는 `setSaveFormat(SaveFormat.MARKDOWN)`을 통해 GitHub‑flavored markdown도 지원합니다. LaTeX 내보내기는 동일하게 유지됩니다. |
| **PDF/UA를 만족하려면 이미지에 alt 텍스트를 설정해야 하나요?** | 반드시 필요합니다. 로드 후 `IMAGE` 타입 `Shape` 노드를 순회하면서 `setAlternativeText("설명")`을 호출하세요. 이렇게 하면 PDF가 *alternative text* 검사를 통과합니다. |
| **대용량 문서를 메모리 초과 없이 처리하려면 어떻게 해야 하나요?** |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}