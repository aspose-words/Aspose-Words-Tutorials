---
category: general
date: 2026-05-04
description: Word에서 Markdown으로 내보낼 때 해상도를 설정하는 방법. Markdown 이미지 해상도, 수식 내보내기 방법, 그리고
  Java에서 Word를 Markdown으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: ko
og_description: Word에서 Markdown 내보내기의 해상도 설정 방법. 이 가이드는 마크다운 이미지 해상도, 방정식 내보내기 및 Word를
  마크다운으로 저장하는 방법을 보여줍니다.
og_title: Word를 Markdown으로 저장할 때 해상도 설정 방법
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Word를 마크다운으로 저장할 때 해상도 설정 방법
url: /ko/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 저장할 때 해상도 설정 방법

Word 문서에서 생성된 Markdown 파일에 나타나는 이미지의 **해상도 설정 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 기본 래스터화된 수식 이미지가 특히 고 DPI 화면에서 흐릿하게 보이는 문제에 많은 개발자들이 부딪히곤 합니다.  

이 튜토리얼에서는 *markdown 이미지 해상도*를 제어하는 정확한 단계들을 살펴보고, **수식을 LaTeX로 내보내는 방법**과 마지막으로 Aspose.Words for Java를 사용하여 **Word를 markdown으로 저장하는 방법**을 보여드립니다. 끝까지 진행하면 수식은 깔끔하게, 이미지도 필요한 품질로 렌더링되는 선명하고 프로덕션 준비된 Markdown 파일을 얻게 됩니다.

## 사전 요구 사항

- Java 17 (또는 최신 JDK)  
- Aspose.Words for Java 23.6 이상 – Maven Central에서 가져올 수 있습니다  
- OfficeMath 객체(수식)와 경우에 따라 래스터 이미지가 포함된 Word 문서(`.docx`)  
- Maven/Gradle 및 IDE(IntelliJ IDEA, Eclipse, VS Code 등)에 대한 기본적인 이해

추가 라이브러리는 필요하지 않으며, 나머지는 모두 Aspose.Words가 처리합니다.

---

## Markdown 내보내기 시 해상도 설정 방법

> **팁:** 선택한 해상도는 생성된 이미지의 파일 크기에 직접 영향을 줍니다. **300 dpi** 값은 대부분의 웹 기반 Markdown 뷰어에 적절한 균형을 이룹니다.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

`setImageResolution(int dpi)` 호출은 **해상도 설정 방법**의 핵심입니다. 이 메서드는 수식이 순수 LaTeX로 표현될 수 없을 때와 같이 대체 이미지가 필요할 경우 지정한 DPI로 래스터화하도록 Aspose.Words에 지시합니다. 이 줄을 생략하면 라이브러리는 기본값인 220 dpi를 사용하게 되며, 레티나 디스플레이에서는 흐릿하게 보일 수 있습니다.

### 수식에 LaTeX를 사용하는 이유

수식을 LaTeX(`OfficeMathExportMode.LATEX`)로 내보내면 결과 Markdown에 `$…$` 또는 `$$…$$` 로 감싼 원시 LaTeX 코드가 포함됩니다. 대부분의 최신 Markdown 렌더러(GitHub, GitLab, MathJax가 포함된 MkDocs)는 이를 선명하고 확장 가능한 벡터 그래픽으로 렌더링하므로 해상도에 대한 고민이 없습니다. 해상도 설정은 Markdown에서 기본적으로 지원되지 않는 차트나 그림과 같은 래스터 대체 이미지의 **markdown 이미지 해상도**에만 영향을 미칩니다.

---

## Markdown 이미지 해상도를 효과적으로 사용하는 방법

Word 파일에 일반 사진(예: 스크린샷)을 삽입해야 하는 경우, Aspose.Words가 이를 PNG로 변환합니다. 동일한 `setImageResolution` 메서드가 적용되어 지정한 DPI가 PNG에 적용됩니다. 간단한 체크리스트를 확인해 보세요:

1. **대상 플랫폼에 맞는 DPI 선택** – 레거시 웹은 72 dpi, 일반 디스플레이는 150 dpi, 인쇄 품질 PDF는 300 dpi.  
2. **출력 테스트** – 생성된 `.md` 파일을 선호하는 뷰어에서 열고 확대하여 선명도를 확인합니다.  
3. **파일 크기 고려** – 높은 DPI는 PNG 파일 크기를 증가시킵니다; 대역폭이 문제라면 200 dpi로 실험해 보고 비교해 보세요.

## 수식을 LaTeX로 내보내는 방법

`saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` 라인은 Aspose.Words에게 모든 OfficeMath 객체를 LaTeX로 변환하도록 지시합니다. 이 방법이 권장되는 이유는 다음과 같습니다:

- **확장성** – LaTeX는 어떤 크기로 확대해도 품질이 손실되지 않습니다.  
- **편집 가능성** – 나중에 Markdown 파일에서 직접 LaTeX를 수정할 수 있습니다.  
- **호환성** – 대부분의 정적 사이트 생성기와 문서 도구가 이미 LaTeX 렌더링을 지원합니다.

이미지 기반 대체가 필요하다면 `OfficeMathExportMode.IMAGE` 로 전환하면 됩니다. 이 경우 설정한 해상도가 더욱 중요해집니다.

## Word를 Markdown으로 저장 – 전체 엔드‑투‑엔드 예제

아래는 의존성 선언부터 실행까지 전체 흐름을 보여주는 완전하고 실행 가능한 Maven 프로젝트 스니펫입니다.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**예상 결과:** `MathExport.md`에는 각 수식에 대한 LaTeX 블록이 포함되고, 삽입된 그림은 DPI가 300인 PNG 링크로 표시됩니다. MathJax를 지원하는 Markdown 뷰어(예: Markdown Preview Enhanced 확장 기능이 있는 VS Code)에서 파일을 열면 완벽하게 선명한 수식과 이미지를 확인할 수 있습니다.

## 일반적인 질문 및 엣지 케이스

### 하나의 이미지에만 다른 DPI가 필요하면 어떻게 하나요?

Aspose.Words는 `setImageResolution`을 통해 DPI를 전역적으로 적용합니다. 이미지별 DPI를 다루려면 생성된 Markdown을 사후 처리하여 PNG 파일을 고해상도 버전으로 교체하고 이미지 링크를 수동으로 조정해야 합니다. 이상적이지는 않지만 몇몇 특수한 경우에는 가능합니다.

### Linux/macOS에서도 작동하나요?

물론입니다. 이 라이브러리는 순수 Java이므로 JDK가 실행되는 모든 환경에서 동일하게 동작합니다. 파일 경로는 슬래시(`/`)를 사용하거나 `Paths.get(...)`을 이용해 플랫폼에 독립적인 처리를 해 주세요.

### SVG 출력은 어떻게 되나요?

차트에 벡터 이미지를 선호한다면 `saveOptions.setExportImagesAsSvg(true);` 로 설정할 수 있습니다. SVG는 DPI를 무시하므로 **markdown 이미지 해상도** 문제는 사라집니다. 다만 모든 Markdown 렌더러가 SVG를 원활히 처리하는 것은 아니므로, 먼저 대상 플랫폼에서 테스트해 보세요.

### 생성된 Markdown을 정적 사이트 생성기에 삽입할 수 있나요?

네. 출력은 표준 Markdown 구문과 LaTeX 구분자를 포함한 순수 `.md` 파일입니다. 대부분의 생성기(Jekyll, Hugo, MkDocs)는 별다른 설정 없이도 받아들입니다. 사이트 설정에서 MathJax 또는 KaTeX를 활성화하는 것을 잊지 마세요.

## 결론

우리는 **Word를 markdown으로 저장할 때 이미지 해상도 설정 방법**을 다루었고, **markdown 이미지 해상도**의 세부 사항을 살펴보았으며, **수식을 LaTeX로 내보내는 방법**을 시연하고 전체 Java 구현을 보여주었습니다. `setImageResolution`을 조정하고 적절한 `OfficeMathExportMode`를 선택함으로써 시각적 품질과 파일 크기를 정확히 제어할 수 있습니다.

다음 단계가 준비되셨나요? 이 방식을 Aspose.PDF와 결합해 동일한 Word 소스를 직접 PDF로 변환하거나, `setExportImagesAsSvg(true)`를 사용해 벡터 기반 그래픽을 실험해 보세요. 여기서 배운 기술은 모든 자동화 문서 파이프라인의 기본 블록이 됩니다.

이 가이드가 도움이 되었다면 GitHub에 별을 달고, 팀원과 공유하거나 아래에 여러분만의 팁을 댓글로 남겨 주세요. 즐거운 코딩 되세요!  

![해상도 설정 예시](resolution.png "Word를 Markdown으로 저장할 때 해상도 설정")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}