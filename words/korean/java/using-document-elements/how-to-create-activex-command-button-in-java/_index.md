---
category: general
date: 2026-10-07
description: Java에서 ActiveX 명령 버튼을 생성하고 프로그래밍 방식으로 Word 문서에 명령 버튼을 추가합니다. 버튼의 왼쪽 상단
  위치를 설정하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: ko
lastmod: 2026-10-07
og_description: Java에서 ActiveX 명령 버튼을 만들어 Word 문서에 인터랙티브 컨트롤을 삽입하세요. 프로그래밍 방식으로 명령
  버튼을 추가하고, 위치를 설정하며, 외관을 맞춤 설정하는 방법을 배워보세요.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Java에서 ActiveX 명령 버튼 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Java에서 ActiveX 명령 버튼을 만드는 방법
url: /ko/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 ActiveX 명령 버튼 만들기

Java를 사용하여 Word 문서에 **ActiveX 명령 버튼**을 **생성**해야 하는 경우, 이 가이드는 정확한 방법을 보여줍니다. **프로그램matically 명령 버튼을 추가하고**, `setLeft`와 `setTop`으로 위치를 지정한 뒤, 결과를 `.docx` 파일로 저장하는 완전한 실행 예제를 확인할 수 있습니다.

대화형 버튼을 삽입하면 폼을 만들거나, 워크플로를 자동화하거나, Word 파일 내부에서 직접 사용자 입력을 수집할 수 있습니다. 아래 단계에서는 프로젝트 설정부터 최종 검증까지 모든 과정을 다루므로, 코드를 그대로 복사해 자신의 프로젝트에 적용해도 상세 내용이 빠지지 않습니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- JDK 17 이상 설치  
- Maven 3.8+ (또는 선호하는 빌드 도구)  
- Aspose.Words for Java 23.9 이상 – `DocumentBuilder`와 OLE 제어 지원을 제공하는 라이브러리  
- Java 문법 및 객체‑지향 개념에 대한 기본 지식  

Maven을 사용하는 경우 `pom.xml`에 다음 의존성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **팁:** 최신 Aspose.Words 버전을 사용하면 버그 수정 및 새로운 OLE 기능을 활용할 수 있습니다.

## 1단계: 빈 문서와 DocumentBuilder 생성

**ActiveX 명령 버튼을 생성**하기 위한 첫 번째 단계는 빈 `Document`와 `DocumentBuilder`를 인스턴스화하는 것입니다. Builder는 콘텐츠 삽입을 위한 유창한 API를 제공하며, OLE 제어도 포함됩니다.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`는 메모리상의 Word 파일을 나타내고, `DocumentBuilder`는 요소를 정확히 원하는 위치에 배치할 수 있는 커서 역할을 합니다.

## 2단계: OLE 명령 버튼 제어 삽입

ActiveX 제어는 OLE 객체로 삽입됩니다. 이를 위해 Aspose.Words는 `Forms2OleControl` 클래스를 제공합니다.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

`insertForms2OleControl()`을 호출하면 Aspose가 자동으로 ActiveX 버튼을 호스트할 자리 표시자 도형을 생성합니다.

## 3단계: 버튼 속성 구성

이제 **프로그램matically 명령 버튼**의 ProgID, 캡션, 크기 등을 추가합니다. 명령 버튼의 가장 일반적인 ProgID는 `"Forms.CommandButton.1"`입니다.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### 버튼 left top 설정 방법

버튼 위치 지정은 **how to set button left top**이라는 보조 키워드와 관련이 있습니다. `setLeft`와 `setTop` 메서드는 포인트 단위(1 포인트 = 1/72 인치)의 값을 받습니다.

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

레이아웃에 맞게 숫자를 조정하세요. 예를 들어 버튼을 표 셀에 맞추려면 셀 좌표를 계산해 `setLeft`/`setTop`에 전달하면 됩니다.

## 4단계: 문서 저장

마지막으로 문서를 디스크에 씁니다. 파일에는 Microsoft Word에서 열었을 때 상호 작용 가능한 ActiveX 버튼이 포함됩니다.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`main` 메서드를 실행하면 `CommandButton.docx`가 생성됩니다. Word에서 파일을 열고, 필요 시 콘텐츠 사용을 허용하면 **Click Me**라는 레이블이 지정된 클릭 가능한 버튼이 지정한 좌표에 표시됩니다.

![Java에서 ActiveX 명령 버튼 만들기](/images/activex-button-screenshot.png){.center width=600 alt="Java에서 ActiveX 명령 버튼을 만든 스크린샷으로, Word 문서 내부에 버튼이 표시된 모습"}

## 일반적인 변형 및 예외 상황

### 여러 버튼 추가

여러 개의 버튼이 필요하면 **2단계**와 **3단계**를 각 제어마다 반복합니다. 버튼이 겹치지 않도록 `setLeft`와 `setTop`을 조정하세요.

### 버튼 동작 변경

ActiveX 버튼은 클릭 시 VBA 매크로를 실행할 수 있습니다. 매크로를 연결하려면 `setOnAction` 속성에 매크로 이름을 설정합니다:

```java
commandButton.setOnAction("MyMacro");
```

대상 문서에 해당 VBA 모듈이 포함되어 있어야 합니다. 그렇지 않으면 Word에서 오류가 표시됩니다.

### 호환성 참고 사항

- 이 버튼은 ActiveX를 지원하는 데스크톱 버전 Word(예: Windows용 Word)에서만 작동합니다. Mac용 Word이나 온라인 편집기에서는 정적 이미지로 표시됩니다.  
- 혼합 환경을 대상으로 한다면 ActiveX 대신 **콘텐츠 컨트롤**(`RichTextContentControl`) 사용을 고려하세요.

## 전체 소스 코드 (참고용)

아래는 새 Maven 프로젝트에 복사해 바로 실행할 수 있는 완전한 예제입니다.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**예상 출력:** 실행 후 프로젝트 작업 디렉터리에 `CommandButton.docx`가 생성됩니다. Microsoft Word에서 파일을 열면 지정한 위치에 “Click Me” 캡션이 표시된 버튼이 나타납니다.

## 결론

이제 Java에서 **ActiveX 명령 버튼을 생성**하고, Word 문서에 **프로그램matically 명령 버튼을 추가**하며, **how to set button left top** 메서드를 사용해 레이아웃을 정확히 제어하는 방법을 알게 되었습니다. 이 기술을 활용하면 매크로를 트리거하거나 외부 애플리케이션을 실행하거나 문서 내부에서 직접 사용자 입력을 수집하는 풍부하고 대화형인 Word 폼을 만들 수 있습니다.

### 다음 단계

- `Forms.TextBox.1` 또는 `Forms.CheckBox.1`과 같은 다른 ActiveX 제어 탐색  
- VBA 모듈과 결합해 다중 제어를 이용한 완전한 폼 구현  
- 크로스 플랫폼 호환성을 위해 ActiveX 대신 콘텐츠 컨트롤 사용  

크기, 캡션, 위치 등을 자유롭게 실험해 UI 디자인에 맞추세요. 문제가 발생하면 사용 중인 Aspose.Words 버전이 OLE 제어를 지원하는지, Word 보안 설정이 ActiveX 실행을 허용하는지 다시 확인하십시오. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하며, 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Word 문서에 OLE 객체 및 ActiveX 컨트롤 삽입](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용해 폼 필드 및 콘텐츠 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Java로 Word에서 사각형 도형 만들기 – 전체 가이드](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}