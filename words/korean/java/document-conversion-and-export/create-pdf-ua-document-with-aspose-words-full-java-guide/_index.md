---
category: general
date: 2026-04-28
description: Aspose.Words for Java를 사용하여 PDF UA 문서를 생성합니다. 복구 기능으로 docx를 로드하고, 수식을
  LaTeX로 내보내며, Word에서 마크다운을 저장하고, 누락된 글꼴을 검색하는 방법을 배웁니다.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: ko
og_description: Aspose.Words for Java를 사용하여 PDF UA 문서를 생성합니다. 복구 로드, LaTeX 내보내기, Markdown
  저장 및 누락된 글꼴 검색을 다루는 단계별 가이드.
og_title: PDF UA 문서 만들기 – 완전한 Java 튜토리얼
tags:
- Aspose.Words
- Java
- PDF/UA
title: Aspose.Words로 PDF UA 문서 만들기 – 전체 Java 가이드
url: /ko/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF UA 문서 만들기 – 완전 Java 튜토리얼

Word 파일에서 손상된 콘텐츠를 처리하면서 **PDF UA 문서**를 만들고 싶으신가요? 이 튜토리얼에서는 복구 모드로 DOCX를 로드하고, 수식을 LaTeX로 내보내며, Word에서 Markdown을 저장하고, 누락된 글꼴을 검색하는 과정을 Aspose.Words for Java와 함께 안내합니다.  

깨진 .docx 파일을 바라보며 PDF가 접근성을 갖추지 못한 이유가 궁금했던 적이 있다면, 여기가 바로 맞는 곳입니다. 끝까지 따라오시면 완전하게 준수하는 PDF/UA 1 파일, LaTeX 수식이 포함된 Markdown 버전, 그리고 로드 과정에서 발생한 모든 글꼴 대체 목록을 얻게 됩니다.

## 필요 사항

- **Aspose.Words for Java** (2026년 현재 최신 버전) – Maven/Gradle 의존성을 추가하거나 JAR 파일을 클래스패스에 넣으세요.  
- Java 17 이상 (API가 스트림을 사용하므로 최신 JDK를 권장합니다).  
- 손상된 섹션, Office Math 수식, 그리고 떠다니는 도형이 포함될 수 있는 샘플 `input.docx`.  

추가 라이브러리는 필요하지 않으며, 모든 기능이 Aspose.Words 내부에 포함됩니다.

---

## 1단계 – 복구 모드로 DOCX 로드  

문서가 부분적으로 손상되면 기본 로더가 예외를 발생시킵니다. 복구 모드를 활성화하면 Aspose.Words가 계속 진행하면서 경고를 표시하도록 할 수 있습니다.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*왜 중요한가:* 복구 모드는 단일 손상된 단락 때문에 전체 파이프라인이 중단되는 것을 방지합니다. 또한 `doc.getWarnings()`를 채워 나중에 **누락된 글꼴** 및 기타 문제를 **검색**할 수 있게 합니다.

---

## 2단계 – Markdown 파일 안에 수식을 LaTeX로 내보내기  

대부분의 개발자는 문서화에 Markdown을 선호하지만, Word에 내장된 수식을 복사하는 것은 번거롭습니다. Aspose.Words는 이를 바로 LaTeX로 변환할 수 있습니다.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*팁:* 콜백을 사용하면 추출된 모든 이미지가 `imgs/` 아래에 저장됩니다. 이는 GitHub가 Markdown을 렌더링하는 방식과 동일하여 깔끔하고 이식성이 좋습니다.

---

## 3단계 – 적절한 태깅으로 PDF / UA 문서 만들기  

PDF/UA(Universal Accessibility) 준수는 많은 공공 부문 프로젝트에서 필수입니다. 아래 옵션들은 Aspose.Words가 떠다니는 도형에 올바르게 태그를 지정하고 PDF/UA 준수 플래그를 설정하도록 합니다.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*보이는 결과:* Adobe Acrobat Pro에서 `output.pdf`를 열면 문서 속성에 “PDF/UA‑1 compliant”가 표시됩니다. 모든 떠다니는 도형(텍스트 상자, 그림)에는 스크린 리더를 위한 적절한 태그가 부여됩니다.

---

## 4단계 – 도형 그림자 조정 (선택적 스타일링)  

접근성에 필수는 아니지만, 시각적 요소를 조정하면 내부 보고서에 유용할 수 있습니다.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*왜 할까?* PDF가 마케팅 자료이기도 하면, 은은한 그림자는 레이아웃을 세련되게 만들면서도 준수를 해치지 않습니다.

---

## 5단계 – 누락된 글꼴 및 기타 경고 검색  

복구 로드 중에 Aspose.Words는 모든 글꼴 대체 정보를 기록합니다. 이를 나열하면 올바른 글꼴을 임베드할지, 대체 글꼴을 사용할지 결정하는 데 도움이 됩니다.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*예시 출력* (콘솔에 다음과 같이 표시됩니다):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

핵심 글꼴이 누락된 경우, 서버에 해당 글꼴을 설치하거나 `PdfSaveOptions.setEmbedFullFonts(true)`를 통해 임베드하는 것을 고려하세요.

---

## 전체 작업 예제  

아래는 완전한 실행 가능한 Java 클래스입니다. IDE에 붙여넣고 경로를 조정한 뒤 **Run**을 클릭하세요.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**예상 결과**

| 출력 | 설명 |
|--------|-------------|
| `output.md` | Office Math 수식이 LaTeX (`$…$`) 형태로 나타나는 Markdown 파일. 이미지가 `imgs/`에 저장됩니다. |
| `output.pdf` | PDF/UA‑1 준수 문서; Acrobat에서 열면 파일 → 속성 → 표준에서 “PDF/UA‑1”이 표시됩니다. |
| Console | 누락된 글꼴 목록, 예: “Missing: Calibri → substituted: Arial”. |

---

## 자주 묻는 질문 (FAQ)

**Q: 이전 Aspose.Words 버전에서도 작동하나요?**  
A: `RecoveryMode`, `OfficeMathExportMode.LATEX`, `PdfCompliance.PDF_UA_1` 열거형은 22.8에 도입되었습니다. 이전 버전을 사용 중이라면 업그레이드하세요 – 접근성 기능은 이전 버전으로 이식되지 않습니다.

**Q: 원본 글꼴을 대체 대신 임베드하려면 어떻게 해야 하나요?**  
A: `pdfOptions.setEmbedFullFonts(true)`를 설정하고 JVM의 글꼴 경로에서 해당 글꼴 파일에 접근할 수 있도록 하세요.

**Q: LaTeX 수식을 유지하면서 다른 마크업 형식(예: HTML)으로 내보낼 수 있나요?**  
A: 가능합니다. `HtmlSaveOptions`를 사용하고 `setOfficeMathExportMode(OfficeMathExportMode.LATEX)`를 설정하면 동일한 열거형이 모든 형식에서 작동합니다.

**Q: DOCX에 떠다니는 도형이 많이 포함되어 있는데, 모두 태그가 지정되나요?**  
A: `setExportFloatingShapesAsInlineTag(true)`를 사용하면 Aspose.Words가 각 떠다니는 도형을 PDF/UA용 `<Figure>` 태그로 감싸며, 대부분의 스크린 리더 검사를 만족합니다.

---

## 마무리  

우리는 Word 소스에서 **PDF UA 문서**를 **복구 모드로 docx 로드**, **수식을 LaTeX로 내보내기**, **Word에서 Markdown 저장**, 그리고 **누락된 글꼴 검색**까지 수행하는 방법을 보여드렸습니다. 이 코드는 완전히 독립적이며 Java 17+ 환경에서 실행 가능하고, 접근성 감사와 개발자를 위한 자산을 모두 준비합니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}