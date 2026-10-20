---
category: general
date: 2026-07-16
description: Aspose.Words for Java를 사용하여 Word 문서에서 버튼 크기를 프로그래밍 방식으로 설정합니다. ActiveX
  버튼 삽입, 버튼 위치 설정 및 기타 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: ko
lastmod: 2026-07-16
og_description: Java를 사용하여 Word 문서에서 버튼 크기를 설정합니다. 이 단계별 가이드는 ActiveX 버튼을 삽입하고, 버튼
  위치를 설정하며, 프로그래밍 방식으로 버튼을 추가하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Java로 Word에서 버튼 크기 설정 – 전체 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Java로 Word에서 버튼 크기 설정 – 완전한 Aspose.Words 가이드
url: /ko/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java로 Word에서 버튼 크기 설정 – 완전한 Aspose.Words 가이드

Ever wondered how to **set button size** inside a Word file without opening the UI? You're not the only one. When you need to generate a form‑filled document on the fly—say, an onboarding packet with a “Submit” button—doing it programmatically saves hours of manual work.

In this tutorial we’ll walk through the exact steps to **insert ActiveX button**, adjust its dimensions, position it correctly, and finally save the file. By the end you’ll be able to **programmatically add button** controls to any Word document using Aspose.Words for Java.

## 사전 요구 사항 – 시작하기 전에 필요한 것

- **Java Development Kit (JDK) 8+** – 코드는 최신 JDK에서 실행됩니다.
- **Aspose.Words for Java** 라이브러리 (공식 사이트에서 최신 JAR 다운로드).  
- 원하는 **IDE**—IntelliJ IDEA, Eclipse, 혹은 간단한 텍스트 편집기도 사용 가능.
- Java 문법에 대한 기본적인 이해; Word 자동화에 대한 깊은 지식은 필요 없음.

> *Pro tip:* Keep the Aspose.Words JAR on your project’s classpath, otherwise you’ll hit `ClassNotFoundException` the moment you try to import `com.aspose.words.*`.

## 단계 1: 새 Word 문서 만들기

The first thing we do is spin up a blank document and a `DocumentBuilder`. Think of the builder as a pen that lets us draw anything inside the file.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** The `Document` object represents the entire .docx file, while the `DocumentBuilder` is the workhorse that lets us insert paragraphs, tables, and—yes—ActiveX controls.

## 단계 2: ActiveX 버튼 삽입 – “Insert ActiveX Button” 순간

Now we actually **insert activex button** into the document. Aspose.Words exposes a convenient method `insertForms2OleControl` that returns a `Forms2OleControl` object.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *What’s happening under the hood?* `Forms2OleControlType.COMMAND_BUTTON` tells Word we want a classic CommandButton, the same kind you’d drop from the Developer tab in the UI.

## 단계 3: 버튼 크기 및 위치 설정 – 핵심 “Set Button Size” 로직

Here’s where the primary keyword shines. We’ll **set button size** and also **set button location** so the control appears exactly where we want it on the page.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Why you should care:** Points are the native measurement unit in Word (1 point = 1/72 inch). By tweaking `setLeft`, `setTop`, `setWidth`, and `setHeight` you gain pixel‑perfect control—no more “it looks right on my screen but not on the printer”.

> *Common pitfall:* Forgetting to set either width or height will leave the button at the default size, which can be too small to click. Always specify both.

## 단계 4: 문서 저장 – “Create Word Document Button” 완료

Finally, we write the file to disk. The name suggests we’re **creating a Word document button** inside a .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

When you open `CommandButtonDemo.docx` in Microsoft Word, you’ll see a **Submit** button placed 100 pt from the left edge and 150 pt from the top, sized at 80 × 30 pt. Clicking it in the UI will trigger the default ActiveX behavior (which you can later wire up with VBA if needed).

### 예상 출력 스크린샷

![삽입된 버튼과 설정된 버튼 크기가 표시된 Word 문서](https://example.com/images/set-button-size.png "Aspose.Words for Java를 사용하여 버튼 크기가 설정된 Word 파일의 스크린샷")

*Alt text:* Java를 사용한 Word 문서에서 버튼 크기 설정

## 단계 5 (옵션): 추가 컨트롤 추가 또는 버튼 스타일링

If you need to **programmatically add button** controls beyond a single Submit button, just repeat the insertion block with new names and captions. You can also adjust font, background color, or even bind VBA macros later.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* Keep all button dimensions consistent for a professional look. A quick way is to store width/height in constants.

## 일반적인 질문 및 엣지 케이스

### “버튼 크기를 포인트 대신 센티미터로 설정할 수 있나요?”

Word’s API only accepts points, but you can convert centimeters to points (`points = cm * 28.3465`). Write a small helper method if you prefer metric units.

### “특정 페이지에 버튼을 표시하려면 어떻게 해야 하나요?”

After inserting the button, you can move the cursor to a particular page using `builder.moveToPage(pageNumber)`. Insert the control right after the move, then set its location as shown above.

### “.doc (Word 97‑2003) 파일에서도 작동하나요?”

Yes—Aspose.Words automatically handles older formats. Just change the file extension in `doc.save("Demo.doc")`.

## 전체 실행 가능한 예제

Below is the entire program you can copy‑paste into a Java class and run immediately (assuming the Aspose.Words JAR is on the classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Run the program, open the generated `CommandButtonDemo.docx`, and you’ll see two neatly sized buttons ready for interaction.

## 결론 – Word에서 버튼 크기 설정을 마스터했습니다

We just walked through a complete, end‑to‑end solution for **set button size** and **set button location** using Aspose.Words for Java. By following the steps you can **insert activex button**, **programmatically add button** controls, and ultimately **create word document button** elements that behave exactly as you need.

What’s next? Try embedding the button inside a table cell, or attach a VBA macro that validates form fields before submission. The same pattern works for other ActiveX controls like check boxes or combo boxes—just swap `Forms2OleControlType.COMMAND_BUTTON` for the appropriate enum value.

If you hit any snags, drop a comment below. Happy coding, and enjoy the power of automated Word document creation!

## 다음에 배울 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words for Java에서 LoadOptions 설정 방법](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words for Java를 사용하여 Word 문서에서 바닥글 제거하는 방법](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Word 문서 처리 종합 가이드](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}