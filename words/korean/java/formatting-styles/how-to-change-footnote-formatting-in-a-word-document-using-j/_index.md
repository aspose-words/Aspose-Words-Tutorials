---
category: general
date: 2026-09-11
description: Aspose.Words를 사용하여 Java에서 각주 서식을 변경하는 방법을 배워보세요. 이 가이드는 각주를 편집하고, 각주
  스타일을 업데이트하며, 각주 구분자를 수정하는 방법을 설명합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: ko
lastmod: 2026-09-11
og_description: Aspose.Words를 사용하여 Java에서 각주 서식을 변경하세요. 이 완전한 가이드를 따라 각주를 편집하고, 각주
  스타일을 업데이트하며, 각주 구분자를 수정하세요.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Java에서 각주 서식 변경 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Java를 사용하여 Word 문서에서 각주 서식을 변경하는 방법
url: /ko/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java를 사용하여 Word 문서에서 각주 서식 변경 방법

Word 문서에서 **각주 서식 변경**이 필요하다면, 이 튜토리얼은 Aspose.Words for Java를 사용한 정확한 단계들을 안내합니다. 퍼블리싱 파이프라인을 구축 중이든, 아니면 프로그래밍 방식으로 **각주 편집 방법**을 필요로 하든, 아래 솔루션은 파일 로드부터 업데이트된 버전 저장까지 모든 과정을 다룹니다.

이 튜토리얼을 통해 **각주 스타일 업데이트**, 각주 구분 기호를 굵게 만들기, 그리고 **각주 구분 기호**의 글꼴 크기나 색상 같은 속성을 **수정**하는 방법을 배울 수 있습니다. 기본적인 Java 지식과 정상적인 Aspose.Words for Java 라이선스가 있다고 가정합니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 이상이 설치되어 있어야 합니다.
* Aspose.Words for Java (버전 23.12 이상)를 프로젝트 클래스패스에 추가했습니다.
* 최소 하나의 각주가 포함된 Word 문서(`input.docx`)가 있습니다.
* 코드를 컴파일하고 실행할 IDE 또는 빌드 도구(Maven/Gradle)가 있습니다.

Aspose.Words를 Maven 프로젝트에 추가하는 방법이 확실하지 않다면, `pom.xml`에 다음 종속성을 포함하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Aspose.Words for Java로 각주 서식 변경하기

솔루션의 핵심은 문서를 로드하고, 각주 구분 기호 단락에 접근하여 서식을 변경한 뒤 결과를 저장하는 짧은 Java 프로그램입니다. 코드는 완전하게 독립적이므로 새 클래스로 복사해 바로 실행할 수 있습니다.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 각 단계가 중요한 이유

* **Loading the document** (`new Document`) creates an in‑memory representation that Aspose.Words can manipulate.  
* **Retrieving the footnote separator** (`getFootnoteSeparator`) gives you direct access to the paragraph that separates footnotes from the main text. This is the element you need to target when you want to **change footnote formatting**.  
* **Formatting the run** (`setBold`, `setItalic`, `setSize`, `setColor`) demonstrates how to **modify footnote separator** properties. You can add any additional font attributes here, such as underline or highlight, to fully control the appearance.  
* **Saving the document** writes the changes back to disk, producing a new file (`output.docx`) that reflects the updated footnote style.

> **Pro tip:** If your source document uses a custom footnote separator that contains multiple runs (e.g., a combination of symbols), loop through `footnoteSeparator.getRuns()` and apply the same `Font` settings to each run for consistent styling.

## 프로그래밍 방식으로 각주 구분 기호 편집하기

때때로 구분 기호뿐만 아니라 각주 텍스트 자체를 편집해야 할 수도 있습니다. 동일한 API를 사용해 각 각주에 접근하고, 단락 서식을 조정하거나 번호 매기기 스타일을 변경할 수 있습니다.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

위 스니펫은 구분 기호에 대해 이미 **각주 서식 변경**을 수행한 후 **각주 편집 방법**을 보여줍니다. `doc.getFootnotes()`를 반복함으로써 모든 각주가 동일한 스타일을 상속받게 하여, 전문적인 문서가 되도록 합니다.

## 일관된 문서 외관을 위한 각주 스타일 업데이트

개별 런 대신 스타일을 사용하고 싶다면, Aspose.Words는 `Style` 객체를 생성하거나 수정한 뒤 이를 각주와 구분 기호에 적용할 수 있게 해줍니다. 이 방법은 여러 문서에 걸쳐 **각주 스타일 업데이트**가 필요할 때 유용합니다.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

전용 스타일을 사용하면 향후 유지 관리가 쉬워집니다—스타일을 한 번만 변경하면 모든 각주와 구분 기호가 자동으로 업데이트됩니다. 이 기술은 대규모 퍼블리싱 워크플로에서 **각주 스타일 업데이트**를 수행하는 권장 방법입니다.

## 브랜드에 맞게 각주 구분 기호 수정하기

브랜드 가이드라인에 따라 각주 구분 기호가 특정 문자(예: 별표)나 맞춤형 선을 사용해야 할 때가 있습니다. Aspose.Words를 사용하면 기본 구분 기호 내용을 완전히 교체할 수 있습니다.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

위 코드는 기존 런을 모두 삭제하고 원하는 텍스트와 서식을 가진 새 런을 삽입함으로써 **각주 구분 기호**를 **수정**합니다. `\u2022`(불릿) 또는 `\u2014`(엔 대시)와 같은 유니코드 문자를 사용해 브랜드가 요구하는 정확한 시각 효과를 구현할 수도 있습니다.

## 예상 결과

프로그램을 실행한 후:

* `output.docx`의 각주 구분 기호가 **굵게**, **기울임꼴**, 10 pt, 회색(또는 설정한 색상)으로 표시됩니다.  
* 모든 각주 단락이 정의한 스타일을 적용받아 문서 전체에 일관된 모습을 제공합니다.  
* 구분 기호 텍스트를 교체한 경우, 원래 라인이 있던 정확한 위치에 새로운 맞춤형 라인이 표시됩니다.

결과 파일을 Microsoft Word 또는 LibreOffice Writer에서 열어 변경 사항을 확인하세요. 첫 번째 각주 바로 위에 업데이트된 구분 기호가 보이고, 각주 텍스트가 적용한 스타일 수정 사항을 반영하고 있어야 합니다.

## 일반적인 함정과 회피 방법

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` throws an exception | Some documents have an empty separator paragraph. | Add a defensive check and create a run if none exist (see the code example). |
| Font changes are not visible | The document uses a theme that overrides direct formatting. | Set `font.setThemeFont(null)` or apply a custom style instead of direct formatting. |
| Saved file does not reflect changes | The original file is still open in Word, locking the output path. | Close any instances of the file before running the program, or |

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And End Note Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to Display Aspose.Words Version Info in Java: A Comprehensive Guide](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}