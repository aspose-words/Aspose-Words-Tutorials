---
category: general
date: 2026-07-26
description: Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼을 삽입하는 방법 – 몇 줄만으로 버튼 캡션, 위치 및
  크기를 설정하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: ko
lastmod: 2026-07-26
og_description: Aspose.Words를 사용하여 Word 문서에 ActiveX 버튼을 삽입하는 방법. 버튼 캡션, 위치 및 크기를 설정하는
  단계별 튜토리얼을 따라보세요.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Word에서 ActiveX 버튼 삽입 방법 – 빠른 가이드
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Word에서 ActiveX 버튼 삽입 방법 – 버튼 캡션 설정
url: /ko/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에 ActiveX 버튼 삽입 방법 – 버튼 캡션 설정

Ever wondered **how to insert ActiveX** controls into a Word file without opening the UI? You're not the only one. In many enterprise apps you need a clickable button that runs a macro, and doing it programmatically saves hours. This guide shows you exactly **how to insert ActiveX** CommandButton using Aspose.Words for Java, and—yes—how to **set button caption** so the user knows what to click.

Word 파일을 UI를 열지 않고 **ActiveX 삽입 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 많은 기업 애플리케이션에서 매크로를 실행하는 클릭 가능한 버튼이 필요하며, 이를 프로그래밍 방식으로 구현하면 시간을 크게 절약할 수 있습니다. 이 가이드에서는 Aspose.Words for Java를 사용하여 **ActiveX** CommandButton을 삽입하는 정확한 방법과—예—사용자가 클릭할 내용을 알 수 있도록 **버튼 캡션 설정** 방법을 보여줍니다.

We'll walk through the whole process: from setting up the library, creating a fresh document, dropping the button, tweaking its size and location, giving it a friendly caption, and finally saving the file. By the end you’ll have a runnable `.docx` that opens in Word with a fully functional ActiveX button ready to fire your macro.

전체 과정을 단계별로 안내합니다: 라이브러리 설정, 새 문서 생성, 버튼 삽입, 크기와 위치 조정, 친절한 캡션 지정, 마지막으로 파일 저장까지. 최종적으로 Word에서 열 수 있는 실행 가능한 `.docx` 파일을 얻으며, 완전한 ActiveX 버튼이 매크로를 실행할 준비가 됩니다.

---

## 배울 내용

- Install and reference Aspose.Words in a Java project.  
- Create a new `Document` and `DocumentBuilder`.  
- **Insert ActiveX** CommandButton control with a single line of code.  
- **Set button caption**, adjust its position, and define its dimensions.  
- Save the document and open it in Word to see the result.

- Java 프로젝트에 Aspose.Words를 설치하고 참조합니다.  
- `Document`와 `DocumentBuilder`를 새로 생성합니다.  
- 한 줄의 코드로 **ActiveX** CommandButton 컨트롤을 삽입합니다.  
- **버튼 캡션을 설정하고**, 위치를 조정하며, 크기를 정의합니다.  
- 문서를 저장하고 Word에서 열어 결과를 확인합니다.

No prior experience with ActiveX is required; just basic Java knowledge and a copy of Aspose.Words.

ActiveX에 대한 사전 경험은 필요하지 않으며, 기본 Java 지식과 Aspose.Words 사본만 있으면 됩니다.

---

## 사전 요구 사항

- Java 8 or newer installed on your machine.  
- Maven or Gradle for dependency management (we’ll show the Maven snippet).  
- A licensed or evaluation copy of **Aspose.Words for Java** (the free trial works fine for this demo).  
- Microsoft Word (any recent version) to test the generated file.

- 머신에 Java 8 이상이 설치되어 있어야 합니다.  
- 의존성 관리를 위한 Maven 또는 Gradle (Maven 예시를 보여드립니다).  
- **Aspose.Words for Java** 라이선스 또는 평가판 사본 (무료 체험판으로도 충분합니다).  
- 생성된 파일을 테스트할 Microsoft Word (최근 버전).

---

## 단계 1: 프로젝트에 Aspose.Words 설정

First things first—add the Aspose.Words dependency. If you use Maven, drop this into your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle users can add:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

After a quick `mvn clean install` (or `gradle build`) the library will be on your classpath and you’re ready to code.

빠르게 `mvn clean install`(또는 `gradle build`)를 실행하면 라이브러리가 클래스패스에 추가되고 코딩을 시작할 준비가 됩니다.

---

## 단계 2: 새 Document와 Builder 생성

A `Document` represents the whole Word file, while `DocumentBuilder` lets you edit it. Think of the builder as a pen that draws on a fresh canvas.

`Document`는 전체 Word 파일을 나타내며, `DocumentBuilder`는 이를 편집할 수 있게 해줍니다. Builder를 새 캔버스에 그리는 펜이라고 생각하면 됩니다.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Why start with a blank document? It guarantees you have full control over every element you add, and there’s no hidden formatting to surprise you later.

왜 빈 문서부터 시작하나요? 추가하는 모든 요소를 완벽히 제어할 수 있고, 나중에 숨겨진 서식 때문에 놀라지 않게 해줍니다.

---

## 단계 3: ActiveX CommandButton 컨트롤 삽입

Now for the star of the show. Aspose.Words exposes `insertForms2OleControl` which can place any ActiveX control you specify. Here we ask for a **CommandButton**.

이제 핵심 단계입니다. Aspose.Words는 지정한 모든 ActiveX 컨트롤을 배치할 수 있는 `insertForms2OleControl` 메서드를 제공합니다. 여기서는 **CommandButton**을 요청합니다.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

The method returns a `Forms2OleControl` object, giving you programmatic access to the button’s properties. This is where **how to insert activex** becomes a one‑liner—no fiddling with low‑level COM APIs.

이 메서드는 `Forms2OleControl` 객체를 반환하여 버튼 속성에 프로그래밍적으로 접근할 수 있게 합니다. 여기서 **ActiveX 삽입 방법**이 한 줄 코드로 구현됩니다—저수준 COM API를 다룰 필요가 없습니다.

---

## 단계 4: 위치, 크기 및 버튼 캡션 설정

A button that floats in the middle of the page isn’t very useful. You’ll want to place it where users expect it, give it a sensible size, and—most importantly—**set button caption** so they know what clicking will do.

페이지 중앙에 떠 있는 버튼은 별로 유용하지 않습니다. 사용자가 기대하는 위치에 배치하고, 적절한 크기를 지정하며, 가장 중요한 **버튼 캡션을 설정**하여 클릭 시 어떤 동작이 일어나는지 알려줘야 합니다.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Why these numbers?** Word uses points (1 pt ≈ 1/72 inch). `100 pt` ≈ 1.4 in from the left, `150 pt` ≈ 2.1 in from the top—roughly the centre of a standard A4 page. Adjust them to suit your layout.

**왜 이 숫자인가요?** Word는 포인트 단위를 사용합니다(1 pt ≈ 1/72 인치). `100 pt`는 왼쪽에서 약 1.4 인치, `150 pt`는 위쪽에서 약 2.1 인치에 해당해 표준 A4 페이지의 대략 중앙에 해당합니다. 레이아웃에 맞게 조정하세요.

Setting the caption is crucial; without it the button looks like a blank rectangle. The `setCaption` method accepts any string, so you can localise it later if needed.

캡션 설정은 필수입니다; 캡션이 없으면 버튼이 빈 사각형처럼 보입니다. `setCaption` 메서드는 문자열을 받아들이므로 필요에 따라 나중에 현지화할 수 있습니다.

---

## 단계 5: 문서 저장

Finally, write the document to disk. You can choose any folder you like; just make sure the path exists.

마지막으로 문서를 디스크에 기록합니다. 원하는 폴더를 선택하면 되며, 경로가 존재하는지 확인하세요.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

When you open `ActiveXButton.docx` in Word, you’ll see a nicely placed button labeled **“Click Me.”** If you double‑click it, Word will prompt you to enable macros (since ActiveX controls are considered macro‑enabled). From there you can bind a VBA routine to the button’s `Click` event.

Word에서 `ActiveXButton.docx`를 열면 **“Click Me.”** 라는 라벨이 붙은 깔끔한 버튼이 보일 것입니다. 더블 클릭하면 Word가 매크로 사용을 허용하도록 요청합니다(ActiveX 컨트롤은 매크로 활성화로 간주됩니다). 이후 버튼의 `Click` 이벤트에 VBA 루틴을 연결할 수 있습니다.

---

## 놓치기 쉬운 상황 및 팁

- **Macro‑Enabled Format**: Word disables ActiveX controls in plain `.docx` files unless the user enables macros. If you need the button to work out‑of‑the‑box, consider saving as `.docm` (macro‑enabled) by using `doc.save(outputPath, SaveFormat.DOCM);`.  
- **Compatibility**: Older versions of Word (pre‑2007) use the binary `.doc` format. Aspose.Words can save to that format, but the control’s properties may render slightly differently.  
- **Security Settings**: Some corporate environments lock down ActiveX. If your button doesn’t appear, check Word’s Trust Center → ActiveX Settings.  
- **Multiple Buttons**: Want more than one? Just repeat the `insertForms2OleControl` call and adjust each button’s `Left`/`Top` values. Keep track of the returned objects so you can set individual captions.  
- **Styling the Caption**: The caption inherits the default font. To change it, you’d need to edit the underlying XML or apply a Word style after insertion—beyond the scope of this quick guide, but doable with Aspose.Words’ `ParagraphFormat` API.

- **Macro‑Enabled Format**: 사용자가 매크로를 활성화하지 않으면 일반 `.docx` 파일에서 ActiveX 컨트롤이 비활성화됩니다. 버튼을 바로 사용할 수 있게 하려면 `doc.save(outputPath, SaveFormat.DOCM);`을 사용해 `.docm`(매크로 활성화) 형식으로 저장하는 것을 고려하세요.  
- **Compatibility**: Word 2007 이전 버전은 이진 `.doc` 형식을 사용합니다. Aspose.Words는 해당 형식으로 저장할 수 있지만, 컨트롤 속성이 약간 다르게 표시될 수 있습니다.  
- **Security Settings**: 일부 기업 환경에서는 ActiveX를 차단합니다. 버튼이 보이지 않으면 Word의 신뢰 센터 → ActiveX 설정을 확인하세요.  
- **Multiple Buttons**: 버튼을 여러 개 만들고 싶나요? `insertForms2OleControl` 호출을 반복하고 각 버튼의 `Left`/`Top` 값을 조정하면 됩니다. 반환된 객체를 추적하여 개별 캡션을 설정하세요.  
- **Styling the Caption**: 캡션은 기본 폰트를 상속합니다. 이를 변경하려면 기본 XML을 편집하거나 삽입 후 Word 스타일을 적용해야 합니다—이 가이드의 범위를 벗어나지만 Aspose.Words의 `ParagraphFormat` API로 구현 가능합니다.

---

## 전체 작업 예제

Below is the complete, ready‑to‑run Java class. Copy‑paste it into your IDE, adjust the output path, and hit **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Expected output**: After running, the console prints the save location. Opening the generated file in Word shows a button placed roughly in the middle of the page, labeled “Click Me”. Clicking it will trigger the standard ActiveX click event (you’ll need to attach a VBA macro to respond).

**예상 출력**: 실행 후 콘솔에 저장 위치가 표시됩니다. 생성된 파일을 Word에서 열면 페이지 중앙에 가깝게 배치된 “Click Me” 라벨의 버튼이 보입니다. 클릭하면 표준 ActiveX 클릭 이벤트가 발생하며, 이에 대한 응답을 위해 VBA 매크로를 연결해야 합니다.

---

## 결론

You now know **how to insert ActiveX** CommandButton controls into a Word document programmatically with Aspose.Words, and you’ve seen exactly how to **set button caption**, position, and size the control. This approach eliminates manual UI work, integrates cleanly into automated report generators, and gives you full control over the

이제 Aspose.Words를 사용해 Word 문서에 **ActiveX 삽입 방법**인 CommandButton 컨트롤을 프로그래밍 방식으로 추가하고, **버튼 캡션 설정**, 위치 및 크기 지정 방법을 정확히 알게 되었습니다. 이 접근 방식은 수동 UI 작업을 없애고 자동화된 보고서 생성기에 깔끔하게 통합되며, 컨트롤에 대한 완전한 제어권을 제공합니다.

## 다음에 배울 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 전체 작업 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET를 사용한 Word 문서에 도형 삽입](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words를 사용한 Word 문서에 인라인 이미지 삽입](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Aspose.Words for .NET를 사용한 Word 문서 헤더에 이미지 삽입](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}