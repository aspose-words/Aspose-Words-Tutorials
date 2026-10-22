---
category: general
date: 2026-07-20
description: DOCX 파일에서 각주 간격을 쉽게 변경하세요. 간격 설정, 각주 구분자 조정, 그리고 Java로 단락 줄 간격을 설정하는
  방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: ko
lastmod: 2026-07-20
og_description: DOCX 파일에서 각주 간격을 빠르게 변경하세요. 이 가이드는 Java에서 간격을 설정하고, 각주 구분자를 조정하며,
  단락 줄 간격을 사용자 정의하는 방법을 보여줍니다.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: DOCX에서 각주 간격 변경 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: DOCX에서 각주 간격을 변경하는 완전 가이드
url: /ko/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX에서 각주 간격 변경 – 완전 가이드

Word 문서에서 **각주 간격을 변경**해야 하는데 어디서 시작해야 할지 몰랐던 적이 있나요? 혼자가 아닙니다. 논문을 다듬거나 계약서를 수정할 때, 각주 구분자를 정확히 맞추는 것이 큰 차이를 만들 수 있습니다.  

이 튜토리얼에서는 **간격 설정 방법**, 각주 구분자 조정, 그리고 **단락 줄 간격 설정**을 Java 기반 라이브러리를 사용해 단계별로 안내합니다. 마지막에는 어떤 프로젝트에도 바로 넣어 사용할 수 있는 예제 코드를 제공할 것입니다.

## 준비물

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- Java 17 이상 (코드가 최신 언어 기능을 사용합니다)
- Maven 또는 Gradle (의존성 관리용)
- 최소 하나의 각주가 포함된 DOCX 파일 (직접 만들 수도 있습니다)
- **Aspose.Words for Java** 라이브러리 (또는 호환 가능한 API; 예제에서는 Aspose 사용)

그게 전부—무거운 프레임워크 없이 순수 Java와 하나의 라이브러리만 있으면 됩니다.

![DOCX에서 각주 간격 변경 예시](/images/footnote-spacing.png){alt="DOCX에서 각주 간격 변경 예시"}

## 1단계: DOCX 문서 로드 (각주 간격 변경)

먼저 Word 파일을 열어 `Document` 객체를 얻어야 합니다. 이 객체를 통해 문서를 조작할 수 있습니다.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*왜 중요한가*: 문서를 로드하는 것이 **각주 간격을 변경**하기 위한 진입점입니다. `Document` 인스턴스가 없으면 각주 구분자나 단락 형식에 접근할 수 없습니다.

## 2단계: 각주 구분자 가져와서 조정 (각주 구분자 조정)

각주 구분자는 본문 텍스트와 각주 목록 사이에 위치한 숨김 단락입니다. 이 단락의 줄 간격을 변경하려면 해당 단락을 가져와 형식을 수정해야 합니다.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### 문제 해결 방식

- **각주 구분자 가져오기** – 실제로 수정하려는 요소를 확보하여 *각주 구분자 조정* 요구를 만족합니다.
- **줄 간격 설정** – `setLineSpacing(12.0)`은 숨김 단락에 대한 *간격 설정*을 직접 수행합니다.
- **예외 상황 처리** – 문서에 구분자가 없을 경우 자동으로 생성하여 `NullPointerException`을 방지합니다.

## 3단계: 변경 내용 확인 및 저장 (단락 줄 간격 설정)

구분자를 수정한 뒤에는 변경 사항이 제대로 저장됐는지 확인해야 합니다. Word에서 저장된 파일을 열어 새로운 간격을 확인할 수 있으며, 프로그램matically도 검증할 수 있습니다.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

`main` 메서드에서 `doc.save(...)` 직전에 `verifySpacing(doc);` 호출을 추가하세요. 프로그램을 실행하면 다음과 같은 출력이 나타납니다:

```
Current footnote separator line spacing: 12.0
```

이 메시지는 **DOCX에서 줄 간격 변경** 작업이 성공했음을 확인시켜 줍니다.

## 흔히 겪는 문제와 전문가 팁

- **문제**: `setLineSpacing`에 “12”와 같은 값을 넣으면 “12 pts”(포인트)로 해석되는데, “12 lines”(줄)와 혼동될 수 있습니다. Aspose는 포인트 단위이므로 12는 12 pt를 의미합니다. 두 배 간격을 원한다면 `24.0`을 사용하세요.
- **팁**: 모든 각주 유형(구분자, 연속 구분자 등)에 일관된 모양을 적용하려면 `doc.getFootnoteContinuationSeparator()`와 `doc.getFootnoteContinuationNotice()`에 대해서도 동일한 과정을 반복하세요.
- **문제**: 수정 후 `save()` 호출을 잊는 경우. 메모리상의 문서는 변경되지만 디스크 파일은 그대로입니다.
- **팁**: 간격 변경과 함께 스타일 업데이트(`ParagraphStyle`)를 결합하면 각주 섹션을 완벽하게 다듬을 수 있습니다.

## 전체 작업 예제 (한 파일에 모든 단계 포함)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

위 코드를 새 Java 클래스에 복사하고 Aspose.Words Maven 의존성을 추가한 뒤 실행하세요. `output.docx` 파일의 각주 구분자 줄 간격이 **12 pt**로 설정되어 **각주 간격이 변경**된 것을 확인할 수 있습니다.

### Maven 의존성

`pom.xml`에 다음 스니펫을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Gradle을 선호한다면 동일한 내용은 다음과 같습니다:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## 결론

Java를 사용해 DOCX 파일에서 **각주 간격을 변경**하는 방법을 배웠습니다. 문서를 로드하고, **각주 구분자**를 가져와 **단락 줄 간격**을 설정함으로써 각주의 외관을 정밀하게 제어할 수 있게 되었습니다.  

이제 각주 텍스트 스타일 수정, 사용자 정의 구분자 추가, 여러 문서에 대한 일괄 업데이트 자동화 등 관련 작업을 탐색해 보세요.  

**각주 구분자 조정**이나 다른 Word 자동화 작업에 대해 궁금한 점이 있으면 댓글을 남겨 주세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 사용한 기술을 확장하여 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하므로 API 기능을 더욱 깊이 익히고 다양한 구현 방식을 프로젝트에 적용할 수 있습니다.

- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Change Asian Paragraph Spacing And Indents](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Change Asian Paragraph Spacing And Indents](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}