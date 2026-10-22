---
category: general
date: 2026-08-07
description: Aspose.Words와 Java를 이용해 각주를 편집하는 방법 – 사용자 정의 대시 추가, 각주 선 변경, 그리고 깔끔한
  문서를 위한 단락 정렬 설정.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: ko
lastmod: 2026-08-07
og_description: Aspose.Words를 사용한 Java에서 각주를 편집하는 방법. 맞춤 대시를 추가하고, 각주 선을 변경하며, 단락
  정렬을 몇 단계만에 설정하는 방법을 배워보세요.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Java에서 각주 편집하기 – 대시 추가, 줄 바꾸기, 정렬 설정
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Java와 Aspose.Words로 각주 편집하는 방법
url: /ko/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java와 Aspose.Words를 사용하여 각주를 편집하는 방법

If you need to **how to edit footnote** in a Word document using Java, this guide shows the complete workflow. You will learn to add a custom dash, change the footnote line, and set paragraph alignment so the footnote separator looks professional.

Java를 사용하여 Word 문서에서 **각주를 편집하는 방법**이 필요하다면, 이 가이드는 전체 워크플로를 보여줍니다. 사용자 정의 대시를 추가하고, 각주 라인을 변경하며, 단락 정렬을 설정하여 각주 구분선이 전문적으로 보이도록 하는 방법을 배울 수 있습니다.

Editing footnotes is a common requirement when preparing legal contracts, academic papers, or marketing brochures. The steps below cover everything you need—from loading the document to saving the final file—without requiring additional tools.

법률 계약서, 학술 논문, 마케팅 브로셔 등을 준비할 때 각주 편집은 흔히 요구되는 작업입니다. 아래 단계에서는 문서를 로드하는 것부터 최종 파일을 저장하는 것까지 추가 도구 없이 필요한 모든 내용을 다룹니다.

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed. → Java 17 이상이 설치되어 있어야 합니다.
* Aspose.Words for Java (latest version) added to your project’s classpath. → 프로젝트 클래스패스에 Aspose.Words for Java(최신 버전)를 추가합니다.
* A DOCX file (`input.docx`) that contains at least one footnote. → `input.docx`라는 DOCX 파일에 최소 하나의 각주가 포함되어 있어야 합니다.

These items guarantee that the code runs without runtime errors.

이 항목들은 코드가 런타임 오류 없이 실행되도록 보장합니다.

## How to edit footnote separator and line

The footnote separator is the paragraph that appears between the main text and the list of footnotes. Changing its appearance improves readability and matches corporate branding.

각주 구분선은 본문 텍스트와 각주 목록 사이에 나타나는 단락입니다. 구분선의 모양을 변경하면 가독성이 향상되고 기업 브랜딩에 맞출 수 있습니다.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Why each line matters

1. **Loading the document** – `new Document(...)` reads the DOCX file into memory, giving you access to all its nodes. → **문서 로드** – `new Document(...)`는 DOCX 파일을 메모리로 읽어들여 모든 노드에 접근할 수 있게 합니다.
2. **Fetching the separator** – `getFootnoteSeparator()` returns the special paragraph that Aspose.Words treats as the footnote line. This object is the only place you can safely modify the separator. → **구분선 가져오기** – `getFootnoteSeparator()`는 Aspose.Words가 각주 라인으로 취급하는 특수 단락을 반환합니다. 이 객체는 구분선을 안전하게 수정할 수 있는 유일한 위치입니다.
3. **Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)` changes the line’s alignment. The keyword *set paragraph alignment* is applied directly to the separator, ensuring a centered dash. → **단락 정렬 설정** – `setAlignment(ParagraphAlignment.CENTER)`는 라인의 정렬을 변경합니다. *set paragraph alignment* 키워드는 구분선에 직접 적용되어 중앙 대시가 되도록 합니다.
4. **Adding a custom dash** – By clearing existing runs and adding a new `Run` with the em‑dash character (`—`), you achieve the *add custom dash* effect while also *change footnote line* to your desired style. → **사용자 정의 대시 추가** – 기존 Run을 제거하고 em‑dash 문자(`—`)가 포함된 새로운 `Run`을 추가함으로써 *add custom dash* 효과를 얻고 동시에 *change footnote line*을 원하는 스타일로 바꿀 수 있습니다.
5. **Saving the document** – `doc.save(...)` writes the changes back to disk, producing an output file that reflects all modifications. → **문서 저장** – `doc.save(...)`는 변경 사항을 디스크에 기록하여 모든 수정이 반영된 출력 파일을 생성합니다.

## Add custom dash to the footnote separator

The code in **Step 4** demonstrates the *add custom dash* technique. You can replace the em‑dash with any string, such as `"***"` or `"---"`, to match your document’s visual language.

**Step 4**의 코드는 *add custom dash* 기법을 보여줍니다. em‑dash를 `"***"` 또는 `"---"`와 같은 문자열로 교체하여 문서의 시각적 스타일에 맞출 수 있습니다.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Using a custom dash is especially helpful when the default thin line does not meet branding guidelines.

기본 얇은 선이 브랜드 가이드라인에 맞지 않을 때 사용자 정의 대시를 사용하는 것이 특히 유용합니다.

## Change footnote line style

If you prefer a solid line instead of a dash, you can insert a Unicode box‑drawing character or a repeated underscore.

대시 대신 실선이 필요하면 유니코드 박스‑드로잉 문자나 연속된 밑줄을 삽입할 수 있습니다.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

The *change footnote line* step works the same way regardless of the character you choose, because the separator paragraph merely renders the text it contains.

*change footnote line* 단계는 선택한 문자와 관계없이 동일하게 작동합니다. 구분선 단락은 포함된 텍스트를 그대로 렌더링하기 때문입니다.

## Set paragraph alignment for footnote separator

The *set paragraph alignment* operation is not limited to center alignment. You can align left, right, or justify according to your layout needs.

*set paragraph alignment* 작업은 중앙 정렬에만 국한되지 않습니다. 레이아웃 요구에 따라 왼쪽, 오른쪽, 양쪽 정렬을 선택할 수 있습니다.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Aligning the separator to the right can be useful for documents that use right‑aligned footnotes, such as bilingual publications.

구분선을 오른쪽으로 정렬하면 양언어 출판물처럼 오른쪽 정렬 각주를 사용하는 문서에 유용합니다.

## Full, runnable example

Below is the complete program that incorporates all the concepts—loading a document, editing the footnote separator, adding a custom dash, changing the line style, and setting alignment.

다음은 모든 개념을 포함한 전체 프로그램 예제입니다—문서 로드, 각주 구분선 편집, 사용자 정의 대시 추가, 라인 스타일 변경, 정렬 설정.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** The `output.docx` file contains a centered em‑dash where the original thin line once was. All footnotes remain intact, and the document’s layout reflects the new separator style.

**예상 출력:** `output.docx` 파일에는 원래 얇은 선이 있던 위치에 중앙에 배치된 em‑dash가 포함됩니다. 모든 각주는 그대로 유지되며, 문서 레이아웃은 새로운 구분선 스타일을 반영합니다.

## Common pitfalls and how to avoid them

| Issue | Reason | Fix |
|-------|--------|-----|
| Separator not found | Document has no footnotes or uses a custom footnote style | Ensure the source DOCX contains at least one footnote before calling `getFootnoteSeparator()` |
| 구분선을 찾을 수 없음 | 문서에 각주가 없거나 사용자 정의 각주 스타일을 사용함 | `getFootnoteSeparator()`를 호출하기 전에 원본 DOCX에 최소 하나의 각주가 포함되어 있는지 확인하십시오. |
| Custom dash not visible | Font does not support the chosen character | Use a Unicode character that is supported by the document’s default font, or embed a compatible font |
| 사용자 정의 대시가 보이지 않음 | 폰트가 선택한 문자를 지원하지 않음 | 문서 기본 폰트가 지원하는 유니코드 문자를 사용하거나 호환 가능한 폰트를 포함시키세요. |
| Alignment appears unchanged | Paragraph format is overridden later in the code | Apply alignment **after** any other formatting calls that might reset it |
| 정렬이 변경되지 않음 | 코드에서 나중에 단락 형식이 재설정됨 | 정렬을 다른 서식 호출이 재설정할 수 있는 이후에 **적용**하십시오. |

Addressing these points prevents runtime errors and guarantees that the *how to edit footnote* process works reliably.

이러한 사항을 해결하면 런타임 오류를 방지하고 *각주를 편집하는 방법* 프로세스가 안정적으로 작동합니다.

## Next steps

Now that you know **how to edit footnote** elements, you can explore related tasks:

이제 **각주를 편집하는 방법**을 알게 되었으니 관련 작업을 탐색할 수 있습니다:

* **Add custom footnote reference style** – modify `FootnoteReference` nodes to change numbering or symbols. → **사용자 정의 각주 참조 스타일 추가** – `FootnoteReference` 노드를 수정하여 번호 매기기 또는 기호를 변경합니다.
* **Programmatically insert new footnotes** – use `DocumentBuilder.insertFootnote()` for dynamic content. → **프로그램matically 새로운 각주 삽입** – 동적 콘텐츠를 위해 `DocumentBuilder.insertFootnote()`를 사용합니다.
* **Apply conditional formatting** – change footnote appearance based on paragraph style or content length. → **조건부 서식 적용** – 단락 스타일이나 내용 길이에 따라 각주 모양을 변경합니다.

Each of these extensions builds on the same API surface you used to *add custom dash*, *change footnote line*, and *set paragraph alignment*.

각 확장은 *add custom dash*, *change footnote line*, *set paragraph alignment*에 사용한 동일한 API를 기반으로 합니다.

---

*Happy coding! If the tutorial helped you master footnote editing, consider sharing it with your team or contributing a pull request to improve the example further.*

*코딩 즐겁게! 이 튜토리얼이 각주 편집을 마스터하는 데 도움이 되었다면 팀과 공유하거나 예제를 개선하기 위해 풀 리퀘스트를 제출해 보세요.*

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 전체 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}