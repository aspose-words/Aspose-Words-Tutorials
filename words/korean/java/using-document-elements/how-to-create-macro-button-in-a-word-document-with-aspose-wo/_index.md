---
category: general
date: 2026-11-22
description: Java를 사용하여 Word 문서에 매크로 버튼을 만들기. 명령 버튼을 삽입하고, 버튼 텍스트를 설정하며, 매크로를 버튼에
  연결하는 방법을 배워 인터랙티브한 문서를 만들세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: ko
lastmod: 2026-11-22
og_description: Java를 사용하여 Word 문서에 매크로 버튼을 만들기. 이 튜토리얼에서는 명령 버튼을 삽입하고, 버튼 텍스트를 설정하며,
  매크로를 버튼에 연결하여 완전한 상호작용을 구현하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Java로 Word 문서에 매크로 버튼 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Aspose.Words for Java를 사용하여 Word 문서에 매크로 버튼 만들기
url: /ko/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 Word 문서에 매크로 버튼 만들기

Word 파일에 **매크로 버튼을 만들** 필요가 있다면, 이 가이드는 필요한 정확한 단계들을 안내합니다. **명령 버튼 삽입**, **버튼 텍스트 설정**, 그리고 **버튼에 매크로 연결** 방법을 배우게 되어 문서를 완전히 인터랙티브하게 만들 수 있습니다.

개발자들은 종종 문서 내에서 VBA 매크로를 트리거하기 위해 OLE 컨트롤을 삽입합니다. 이 튜토리얼은 프로젝트 설정부터 .docx 파일에 **인터랙티브 버튼**을 추가하는 실행 가능한 Java 예제까지 전체 워크플로를 다룹니다. 외부 스크립트가 필요하지 않으며—모든 것이 Java 프로세스 내부에서 실행됩니다.

## 사전 요구 사항

* JDK 17 이상이 설치되어 있어야 합니다.
* Maven 3.8+ (또는 Gradle) 를 사용하여 종속성을 관리합니다.
* Aspose.Words for Java 23.9 이상 – 이 라이브러리는 `DocumentBuilder`와 OLE 컨트롤 API를 제공합니다.
* Java와 VBA 매크로에 대한 기본적인 이해가 필요합니다.

이 항목 중 하나라도 누락된 경우 먼저 설치하십시오; 나머지 튜토리얼은 모두 사용 가능하다고 가정합니다.

## Aspose.Words for Java로 매크로 버튼 만들기

솔루션의 핵심은 네 가지 작업으로 구성됩니다:

1. **명령 버튼 삽입** OLE 컨트롤을 문서에 삽입합니다.
2. **버튼 텍스트 설정** (캡션) 사용자가 보는 텍스트.
3. **버튼에 매크로 연결** 클릭 시 원하는 VBA 루틴이 실행됩니다.
4. **문서 저장** 매크로가 포함된 상태로 저장합니다.

각 작업은 아래 섹션에서 별도로 설명됩니다.

### 단계 1: 문서에 명령 버튼 삽입

`DocumentBuilder.insertForms2OleControl`은 지정된 유형의 OLE 컨트롤을 생성합니다. `Forms2OleControlType.COMMAND_BUTTON` 상수는 Aspose.Words에 매크로를 호스트할 수 있는 명령 버튼을 생성하도록 지시합니다.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**왜 중요한가:** OLE 컨트롤은 매크로를 위한 컨테이너 역할을 합니다. 이를 삽입하지 않으면 사용자가 클릭할 수 있는 시각적 요소가 없습니다.

### 단계 2: 버튼 텍스트 (캡션) 설정

캡션은 버튼에 표시되는 라벨입니다. `setCaption`을 사용하여 사용자가 보는 텍스트를 정의합니다.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**왜 중요한가:** 명확한 버튼 텍스트는 사용성을 향상시킵니다. `setCaption` 메서드는 OLE 컨트롤의 `Caption` 속성을 업데이트하며, Word는 이를 버튼 라벨로 렌더링합니다.

### 단계 3: 버튼에 매크로 연결

매크로는 이름으로 식별됩니다. 예를 들어 `MyMacro`가 있습니다. `setOnClick` 메서드는 이 이름을 버튼의 `OnClick` 이벤트 핸들러에 저장합니다.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**왜 중요한가:** 매크로를 연결하면 인터랙티브한 동작이 생성됩니다. 사용자가 Word에서 버튼을 클릭하면 연결된 VBA 루틴이 실행됩니다.

### 단계 4: Word 문서에 인터랙티브 버튼 추가

OLE 컨트롤을 구성한 후에는 위치를 지정하거나 크기를 조정하거나 주변 텍스트를 추가하고 싶을 수 있습니다. `DocumentBuilder`는 문서 작업을 계속하므로 버튼 앞이나 뒤에 단락을 삽입할 수 있습니다.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**왜 중요한가:** `.docm` 형식으로 저장하면 매크로 코드가 보존됩니다. `.docx`로 저장하면 매크로 참조가 사라집니다.

## 전체 실행 가능한 예제

아래는 전체 Java 프로그램으로, import, 예외 처리 및 각 단계를 설명하는 주석이 포함되어 있습니다. 코드를 Aspose.Words 의존성을 포함한 Maven 프로젝트에 복사하고 실행하십시오.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### 예상 출력

프로그램을 실행하면 `MacroButtonDemo.docm`이 생성됩니다. Microsoft Word에서 파일을 열면 다음과 같이 표시됩니다:

* *“매크로를 실행하려면 버튼을 누르세요:”* 라는 문단이 표시됩니다.
* **Run Report** 라는 라벨이 붙은 버튼이 해당 문단 바로 아래에 표시됩니다.
* 버튼을 클릭하면 Word가 매크로 `MyMacro`를 실행하려고 시도합니다. (실제 VBA 코드는 문서에 수동으로 또는 다른 자동화 단계로 추가해야 합니다.)

매크로가 존재하지 않으면 Word는 보안 경고를 표시합니다. 이는 매크로 사용 문서에서 표준 동작입니다.

## 일반적인 변형 및 엣지 케이스

| 시나리오 | 코드 적용 방법 |
|----------|-----------------------|
| **다른 버튼 캡션** | `setCaption`에 전달되는 문자열을 변경합니다. |
| **여러 버튼** | `insertForms2OleControl`을 반복 호출하고 각각에 `setCaption` 및 `setOnClick`을 설정합니다. |
| **사용자 정의 매크로 이름** | `"MyMacro"`를 유효한 VBA 프로시저 이름으로 교체합니다. 예: `"ExportToExcel"` |
| **버튼 크기 제한** | `setWidth`와 `setHeight` 값을 조정합니다; Word는 지정한 포인트 값을 그대로 적용합니다. |
| **프로그램matically 매크로 삽입** | `Document.getBuiltInDocumentProperties().add("Macros", …)`를 사용하거나 별도의 VBA 삽입 단계를 수행합니다; Aspose.Words는 자체적으로 VBA 코드를 작성하지 않습니다. |

**Pro tip:** 개발 단계에서는 매크로 보안이 *모든 매크로 사용*으로 설정된 머신에서 생성된 `.docm`을 항상 테스트하십시오. 운영 환경에서는 신뢰할 수 있는 인증서로 매크로에 서명하여 보안 프롬프트를 피하십시오.

## 문제 해결 체크리스트

* **버튼이 표시되지 않음** – 문서가 `.docm`으로 저장되고 OLE 컨트롤을 지원하는 Word 버전에서 열렸는지 확인하십시오.
* **매크로가 실행되지 않음** – 매크로 이름이 정확히 일치하는지(대소문자 포함) 확인하고, 매크로가 문서의 VBA 프로젝트에 존재하는지 확인하십시오.
* **버튼 캡션이 잘림** – `setWidth`를 사용하여 버튼 너비를 늘려 긴 텍스트를 수용하십시오.
* **예상치 못한 레이아웃 이동** – 컨트롤을 삽입하기 전에 `builder.moveTo`를 사용해 커서를 정확히 위치시키십시오.

## 결론

이제 Java를 사용하여 Word 문서에 **매크로 버튼을 만들**, **명령 버튼을 삽입**, **버튼 텍스트를 설정**, 그리고 **버튼에 매크로를 연결**하여 완전한 인터랙티브 기능을 구현하는 방법을 알게 되었습니다. 전체 예제는 필요한 모든 API 호출을 보여주고, 각 단계가 중요한 이유를 설명하며, 일반적인 변형에 대한 가이드를 제공합니다.

다음에 배워야 할 내용은?

* **인터랙티브 버튼 추가**를 새 문서가 아니라 기존 템플릿에 적용합니다.
* **프로그램적으로 VBA 코드를 삽입**은 Open XML SDK 또는 다른 자동화 도구를 사용합니다.
* **여러 OLE 컨트롤 결합** (체크박스, 리스트 박스)하여 풍부한 양식을 만듭니다.

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 전체 작업 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}