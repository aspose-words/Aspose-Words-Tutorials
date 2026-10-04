---
category: general
date: 2026-10-04
description: Aspose.Words를 사용한 Java에서 각주 구분자 편집 – 각주 구분자를 변경하고 Word 문서에 사용자 정의 구분
  단어를 추가하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: ko
lastmod: 2026-10-04
og_description: Aspose.Words를 사용하여 Java에서 각주 구분자를 편집합니다. 이 튜토리얼에서는 각주 구분자를 변경하고 사용자
  정의 구분 단어를 삽입하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Java에서 각주 구분자 편집 – 완전한 Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: Java와 Aspose.Words를 사용하여 각주 구분자를 편집하는 방법
url: /ko/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java와 Aspose.Words로 각주 구분자 편집하기

Word 문서에서 **각주 구분자**를 **편집**해야 할 경우, 이 가이드는 Java에서 정확히 어떻게 수행하는지 보여줍니다. **각주 구분자**를 대시, 별표 또는 **사용자 정의 구분 단어**로 바꾸고 싶다면, 아래 단계가 모든 과정을 포괄합니다.

`.docx` 파일을 로드하고, 특수 구분자 섹션을 가져와 내용을 수정한 뒤 결과를 저장하는 방법을 배웁니다. 외부 스크립트나 수동 편집이 필요하지 않으며, 모든 작업은 Aspose.Words for Java 라이브러리를 사용해 프로그래밍 방식으로 이루어집니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- Java 17 이상이 설치되어 있어야 합니다.
- Maven 또는 Gradle을 사용해 종속성을 관리합니다 (예제는 Maven 사용).
- 유효한 Aspose.Words for Java 라이선스(또는 무료 평가 키).
- 이미 각주가 포함된 Word 문서(각주가 있을 때만 구분자가 존재합니다).

## Add Aspose.Words to your project

Maven을 사용하는 경우 `pom.xml`에 다음 종속성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Gradle을 사용하는 경우 다음을 추가합니다:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Step 1: Load the document that contains footnotes

첫 번째 단계는 수정하려는 Word 파일을 여는 것입니다. Aspose.Words는 파일을 `Document` 객체로 읽어 들이며, 이를 통해 각주 구분자를 포함한 문서의 모든 부분에 완전한 접근 권한을 제공합니다.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**왜 중요한가:** 문서를 메모리 상에 로드하면 원본 파일을 직접 건드리지 않고도 안전하게 노드를 수정할 수 있으며, 명시적으로 저장하기 전까지는 원본이 유지됩니다.

## Step 2: Retrieve the footnote separator section

Word는 각주 구분자를 특수 `Separator` 노드로 저장합니다. Aspose.Words는 `getFootnoteSeparator()` 메서드를 제공하여 이를 직접 가져올 수 있습니다.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Pro tip:** 구분자 노드는 문서에 최소 하나 이상의 각주가 있을 때만 존재합니다. 각주가 없는 문서에서 `getFootnoteSeparator()`를 호출하면 `null`을 반환하므로, 항상 이 상황을 확인하세요.

## Step 3: Insert a custom separator word

이제 구분자의 모양을 변경할 수 있습니다. 예제에서는 기본 선을 em 대시(`—`)로 교체합니다. 대신 `"NOTE:"`나 `"***"`와 같은 **사용자 정의 구분 단어**를 삽입할 수도 있습니다.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### What the code does

1. **`clearChildren()`**는 기존 런(run)을 모두 제거하여 구분자에 제공하는 텍스트만 남도록 합니다.
2. **`new Run(document, "—")`**는 원하는 구분자를 텍스트 노드로 생성합니다. `Run` 객체는 문서 스타일을 그대로 따르므로 구분자는 원래 각주 구분자의 서식을 상속합니다.
3. **`appendChild(customRun)`**은 새 런을 구분자 단락에 삽입합니다.

런에 서식을 적용할 수도 있습니다. 예:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Step 4: Save the modified document

구분자 편집이 끝났으면 문서를 디스크에 다시 저장합니다. 원본 파일을 보존하려면 새 파일 이름을 사용하세요.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**결과 확인:** Microsoft Word에서 `ModifiedNotes.docx`를 열면 각주 구분자가 기본 선 대신 사용자 정의 대시(또는 선택한 단어)로 표시됩니다.

## Handling multiple footnote separators

Word는 세 가지 특수 구분자 유형을 지원합니다:

| Separator type | Method |
|----------------|--------|
| Footnote separator | `getFootnoteSeparator()` |
| Footnote continuation separator | `getFootnoteContinuationSeparator()` |
| Footnote separator for the first page | `getFootnoteSeparatorForFirstPage()` |

모두 편집해야 한다면 **Step 2**와 **Step 3**을 각 메서드에 대해 반복하면 됩니다. 예:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Common pitfalls and how to avoid them

| Issue | Cause | Fix |
|-------|-------|-----|
| No separator appears after saving | Document had no footnotes → separator node is `null` | Add at least one footnote before editing, or create a dummy footnote programmatically. |
| Separator shows extra spaces | Existing runs were not cleared | Call `clearChildren()` before appending the new run. |
| Formatting looks different | Run inherits style from the original separator | Explicitly set font properties on the `Run` if you need a specific appearance. |

## Full working example

모든 조각을 합치면 다음과 같은 독립 실행형 Java 클래스를 얻을 수 있습니다. 복사, 컴파일, 실행하면 됩니다:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

프로그램을 실행한 뒤 `ModifiedNotes.docx`를 열어 구분자가 업데이트되었는지 확인하세요.

## Conclusion

이제 Java와 Aspose.Words를 사용해 Word 문서의 **각주 구분자**를 **편집**하는 방법을 알게 되었습니다. 튜토리얼에서는 문서 로드, 특수 구분자 노드 가져오기, **사용자 정의 구분 단어** 삽입, 결과 저장 순서를 다루었습니다. 이 단계들을 따라 하면 연속 섹션이나 첫 페이지 각주에 대한 **각주 구분자**도 **변경**할 수 있습니다.

다음으로 살펴볼 내용:

- 첫 페이지 각주용 다른 구분자 추가 (`getFootnoteSeparatorForFirstPage()`).
- 각주가 없을 때 프로그래밍 방식으로 각주 생성.
- Aspose.Words를 사용해 각주 텍스트 스타일링(폰트, 색상, 들여쓰기)하기.

문서 브랜드에 맞게 다른 문자나 단어를 실험해 보세요. 즐거운 코딩 되세요!


## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하며, 비슷한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 돕습니다.

- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}