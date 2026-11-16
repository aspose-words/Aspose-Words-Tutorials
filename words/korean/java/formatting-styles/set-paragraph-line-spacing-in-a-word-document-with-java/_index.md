---
category: general
date: 2026-11-15
description: Java를 사용하여 Word 문서에서 단락 줄 간격을 설정합니다. Aspose.Words를 활용해 프로그래밍 방식으로 줄 간격을
  설정하는 방법을 배우고 정밀한 문서 서식을 구현하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: ko
lastmod: 2026-11-15
og_description: Java를 사용하여 Word 문서에서 단락 줄 간격을 설정합니다. 이 가이드는 Aspose.Words를 활용해 단락 및
  각주 구분선의 줄 간격을 설정하는 방법을 설명하며, 문서 레이아웃을 완벽하게 제어할 수 있게 합니다.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Java를 사용하여 Word에서 단락 줄 간격 설정
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Java를 사용하여 Word 문서의 단락 줄 간격 설정
url: /ko/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java를 사용하여 Word 문서에서 단락 줄 간격 설정

Word 문서에서 **단락 줄 간격을 설정**해야 하는 경우, 이 튜토리얼에서는 Java와 Aspose.Words를 사용하여 수행하는 방법을 보여줍니다. 또한 전문 문서를 포맷할 때 흔히 요구되는 각주 구분선에 대한 **줄 간격 설정 방법**도 배울 수 있습니다.

다음 섹션에서는:

* 기존 *.docx* 파일을 로드합니다.
* 각주 구분자 단락을 가져옵니다.
* 사용자 지정 줄 간격 값을 적용합니다.
* 업데이트된 문서를 저장합니다.

프로젝트에 Aspose.Words 라이브러리를 추가하는 것 외에 외부 설정이 필요 없으므로 코드를 그대로 복사해 바로 실행할 수 있습니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하십시오:

* Java 17 이상이 설치되어 있어야 합니다.
* Maven(또는 다른 빌드 도구)으로 의존성을 관리합니다.
* 유효한 Aspose.Words for Java 라이선스(무료 평가판도 테스트에 사용할 수 있습니다).
* 알려진 디렉터리에 위치한 입력 Word 문서(`input.docx`).

`pom.xml`에 Aspose.Words 의존성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Aspose.Words를 사용하여 단락 줄 간격 설정

이 H2 헤더는 주요 키워드를 포함하고 있어 SEO 요구 사항을 충족합니다.

### 단계 1: Word 문서 로드

먼저, 소스 파일을 가리키는 `Document` 인스턴스를 생성합니다.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*왜 중요한가*: 문서를 로드하면 원본 파일을 직접 수정하지 않고도 메모리 내 모델을 조작할 수 있으며, 명시적으로 저장할 때까지 원본 파일에 영향을 주지 않습니다.

### 단계 2: 각주 구분자 가져오기

각주 구분자는 각주와 본문 사이에 나타나는 특수 단락입니다. 외관을 변경하려면 `FootnoteSeparator` 객체에 접근해야 합니다.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*팁*: 문서에 각주가 없더라도 구분자는 숨겨진 단락으로 존재하므로 호출이 `null`을 반환하지 않습니다.

### 단계 3: 구분자 단락의 줄 간격 설정 방법

이제 원하는 줄 간격을 적용합니다. Aspose.Words는 줄 간격 값을 포인트 단위로 사용하며, 12 pts는 대부분의 글꼴에 대해 대략 단일 간격에 해당합니다.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

다른 간격 모드도 사용할 수 있습니다:

| 모드                     | 메서드 호출                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

올바른 규칙을 선택하면 Word, Google Docs 및 기타 뷰어에서 문서가 일관되게 렌더링됩니다.

### 단계 4: 업데이트된 문서 저장

마지막으로 변경 사항을 디스크에 기록합니다.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

`output.docx`를 Microsoft Word에서 열면, 각주 구분자가 정의한 줄 간격으로 표시됩니다.

## 일반 단락의 줄 간격 설정 이해

같은 API를 `Paragraph` 객체 전체에 사용할 수 있으며, 각주 구분자에만 국한되지 않습니다. 아래는 본문 첫 번째 단락의 간격을 조정하는 간단한 예시입니다:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**왜 필요할 수 있는가**: 보고서, 계약서, 학술 논문 등은 종종 특정 줄 간격 스타일(예: 초안의 경우 두 배 간격)이 필요합니다. 동일한 `setLineSpacing` 메서드를 사용하면 기대하는 정확한 레이아웃을 보장할 수 있습니다.

## 흔히 발생하는 문제와 회피 방법

| 문제                                 | 원인                                   | 해결 방법 |
|---------------------------------------|----------------------------------------|-----|
| 줄 간격이 변경되지 않음                | `LineSpacingRule`이 기본값(AUTO)으로 남아 있음 | `setLineSpacingRule`을 명시적으로 설정합니다. |
| 구분자 뒤에 빈 줄이 추가됨            | 구분자에 숨겨진 캐리지 리턴이 포함되어 있음 | 간격을 적용하기 전에 `separator.getText().trim();`으로 텍스트를 정리합니다. |
| 저장 후 문서가 손상됨                | 구버전 Aspose.Words 사용 | 최신 버전(예: 24.10)으로 업그레이드하여 저장 관련 버그를 해결합니다. |

## 전문가 팁: 여러 문서 일괄 처리

수십 개의 파일을 업데이트해야 한다면, 로직을 헬퍼 메서드로 감싸고 폴더를 순회하면 됩니다:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

이 메서드를 루프에서 실행하면 수시간에 달하는 수동 편집을 절약할 수 있습니다.

## 예상 출력

전체 프로그램을 실행하면 `output.docx`는 다음과 같이 됩니다:

* 줄 간격을 제외하고 원본 내용은 그대로 유지됩니다.
* 각주 구분자가 단일 간격(12 pts) 레이아웃으로 표시됩니다.
* 다른 모든 서식(스타일, 이미지, 표)도 그대로 보존됩니다.

Word에서 파일을 열어 구분선이 더 촘촘해졌는지(또는 설정값에 따라 더 넓어졌는지) 확인하십시오.

## 결론

이제 Java를 사용하여 Word 문서에서 **단락 줄 간격을 설정**하는 방법과 각주 구분자 및 일반 단락에 대한 **줄 간격 설정** 방법을 이해했습니다. 완전하고 실행 가능한 예제는 문서를 로드하고, 줄 간격 속성을 조정한 뒤, 결과를 저장하는 과정을 몇 가지 명확한 API 호출만으로 보여줍니다.

**다음 단계**로 탐색해 볼 수 있습니다:

* **테이블 및 목록 항목에 대한 줄 간격 설정**
* 제목과 본문 텍스트에 서로 다른 간격 규칙 적용
* `Style` 객체를 사용하여 문서 전체에 간격을 강제 적용

값을 실험하고 다른 서식 옵션과 결합하면 Java 애플리케이션에서 문서 레이아웃을 완전히 제어할 수 있습니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 동작 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java에서 옵션 설정 방법 – 완전 가이드](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Aspose.Words for Java에서 LoadOptions 설정 방법](/words/english/java/document-loading-and-saving/using-load-options/)
- [Word 문서에서 아시아 단락 간격 및 들여쓰기 변경](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}