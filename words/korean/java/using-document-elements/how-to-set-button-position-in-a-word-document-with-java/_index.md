---
category: general
date: 2026-09-24
description: Java와 Aspose.Words를 사용하여 Word 문서에서 버튼 위치를 설정합니다. 버튼 삽입, ActiveX 컨트롤 추가
  및 Java 스타일로 Word 문서를 만드는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: ko
lastmod: 2026-09-24
og_description: Java를 사용하여 Word 문서에서 버튼 위치를 설정합니다. 이 가이드는 버튼 삽입, ActiveX 컨트롤 추가 및
  Aspose.Words를 활용한 Java Word 문서 생성 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Java로 Word 문서에서 버튼 위치 설정 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Java를 사용하여 Word 문서에서 버튼 위치 설정 방법
url: /ko/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java로 Word 문서에서 버튼 위치 설정하기

Word 파일 안에서 **버튼 위치 설정**이 필요하다면, 이 가이드는 완전하고 실행 가능한 솔루션을 보여줍니다. 사용자 상호 작용이 필요한 템플릿을 만들거나 양식을 자동화하든, Aspose.Words for Java를 사용하여 **버튼 삽입 방법**을 정확히 배우고 배치 방법을 제어할 수 있습니다.

이 튜토리얼은 Word 문서에 **ActiveX 컨트롤 추가**에 필요한 모든 것을 다루고, **Word에 버튼 추가** 방법을 설명하며, **Java 스타일 Word 문서 생성** 전체 과정을 시연합니다. 외부 참고 자료는 필요 없으며, 복사하고 실행한 뒤 결과를 확인하기만 하면 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 (또는 Java 8 이상 런타임)
* Maven 또는 Gradle (의존성 관리용)
* Aspose.Words for Java 라이선스 (평가용 무료 체험판 사용 가능)
* Java 문법에 대한 기본 이해

> **Pro tip:** Aspose.Words JAR 파일을 `libs/` 폴더에 보관하고 프로젝트 클래스패스에 추가하면 버전 충돌을 방지할 수 있습니다.

## Step 1: Set up the Maven project

간단한 Maven 프로젝트(또는 Gradle)를 만들고 Aspose.Words 의존성을 추가합니다:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

`mvn clean compile`을 실행하면 라이브러리가 다운로드되고 빌드 경로가 준비됩니다.

## Step 2: Create a new Word document

첫 번째 작업은 **Java 스타일 Word 문서 생성**입니다. `Document` 객체와 파일을 편집할 수 있는 `DocumentBuilder`를 인스턴스화합니다.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 클래스는 전체 .docx 파일을 나타내고, `DocumentBuilder`는 콘텐츠 삽입을 위한 유창한 API를 제공합니다.

## Step 3: How to insert button – add ActiveX control

Aspose.Words는 CommandButton과 같은 레거시 ActiveX 컨트롤을 삽입하기 위해 `Forms2OleControl` 클래스를 제공합니다. 이 단계에서는 문서에 **버튼 삽입 방법**을 정확히 보여줍니다.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

`insertForms2OleControl` 메서드는 구성할 수 있는 `Forms2OleControl` 인스턴스를 반환합니다. 이것이 **ActiveX 컨트롤 추가** 프로세스의 핵심입니다.

## Step 4: Set button position

이제 실제로 **버튼 위치 설정**을 합니다. 컨트롤의 `setLeft`와 `setTop` 메서드는 포인트 단위(1 pt = 1/72 in) 값을 받습니다. 일반 화면 좌표와 맞추려면 픽셀을 포인트로 변환하면 됩니다(1 px ≈ 0.75 pt). 예시에서는 버튼을 왼쪽 가장자리에서 100 px, 위쪽 가장자리에서 150 px 떨어진 위치에 배치합니다.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

**버튼 위치 설정** 로직이 여기서 캡슐화되므로, 컨트롤을 이동해야 할 때마다 이 코드를 재사용할 수 있습니다. 레이아웃 요구에 맞게 숫자를 조정하세요.

## Step 5: Define size and caption

라벨이 없는 버튼은 혼란을 줍니다. `setWidth`, `setHeight`, `setCaption`을 사용해 눈에 보이는 모양을 지정합니다.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

크기도 포인트 단위이므로 일관성을 위해 픽셀에서 변환합니다.

## Step 6: Save the document – complete the create Word document java flow

마지막으로 파일을 디스크에 저장합니다. 경로는 절대 경로나 프로젝트 루트에 대한 상대 경로가 될 수 있습니다.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

프로그램을 실행하면 `output` 폴더 안에 `CommandButtonDemo.docx`가 생성됩니다. Microsoft Word에서 파일을 열면 설정한 위치에 정확히 배치된 클릭 가능한 버튼이 표시됩니다.

### Expected output

* **CommandButtonDemo.docx**라는 이름의 `.docx` 파일
* 문서 안에 **CommandButton**이 “Click Me” 라벨과 함께 왼쪽 여백에서 100 px, 위쪽 여백에서 150 px 떨어진 위치에 표시
* Word에서 문서를 열면 버튼을 클릭할 수 있으며(사용자 정의 VBA 코드를 연결하지 않은 경우 기본 ActiveX 메시지가 표시됩니다)

## Step 7: Common variations and edge cases

### Adding multiple buttons

**Word에 버튼 추가**를 여러 번 해야 한다면, 3‑5단계를 새 `Forms2OleControl` 인스턴스로 반복합니다. 버튼이 겹치지 않도록 `setTop` 값을 조정하는 것을 잊지 마세요.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Working without a license

라이선스 없이 사용할 경우 Aspose.Words가 워터마크를 삽입합니다. 실제 서비스에서는 라이선스를 구매하고 `main` 시작 부분에 적용하세요:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibility with older Office versions

ActiveX 컨트롤은 `.doc`(Word 97‑2003) 형식에서도 지원됩니다. 레거시 파일을 만들려면 저장 형식을 변경하세요:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Full source code (runnable)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

파일을 `src/main/java/CommandButtonDemo.java`로 저장하고 `mvn exec:java -Dexec.mainClass=CommandButtonDemo`를 실행한 뒤, 생성된 문서를 열어 결과를 확인합니다.

## Frequently asked questions

**Q: Does this work with OpenJDK?**  
A: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation, including OpenJDK.

**Q: Can I change the button’s font or color?**  
A: ActiveX button appearance is controlled by the host application (Word). You can attach VBA code to modify properties at runtime, but the static appearance is limited to the default style.

**Q: What if I need to place the button inside a table cell?**  
A: Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`. The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop` for fine‑tuning.

## Conclusion

이제 Java를 사용해 Word 문서에서 **버튼 위치 설정**, **버튼 삽입 방법**, **ActiveX 컨트롤 추가**, 그리고 **Word에 버튼 추가**를 수행하는 방법을 알게 되었습니다. 전체 예제는 프로젝트 설정부터 기능성 CommandButton이 포함된 `.docx` 파일 저장까지 전체 워크플로를 보여줍니다.

### Next steps

* `Forms2OleControl.ControlType`의 다른 값들(예: `CHECKBOX`, `TEXTBOX`)을 탐색해 더 풍부한 양식을 구축하세요.
* VBA 매크로와 버튼을 결합해 사용자 정의 클릭 처리를 구현하세요.
* Aspose.Words의 메일‑머지 기능을 활용해 인터랙티브 컨트롤이 이미 포함된 개인화된 문서를 자동 생성하세요.

Happy coding, and enjoy automating Word documents with Java!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 작업 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움을 줍니다.

- [Aspose.Words for Java에서 DocumentBuilder를 사용해 양식 필드를 만들고 콘텐츠를 추가하는 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for .NET에서 콤보 박스 폼 필드를 Word 문서에 추가하기](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aspose.Words Java로 Word 문서를 로드하는 포괄적인 가이드](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}