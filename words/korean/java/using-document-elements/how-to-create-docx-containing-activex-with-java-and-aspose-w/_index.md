---
category: general
date: 2026-09-27
description: Aspose.Words를 사용하여 Java에서 ActiveX가 포함된 docx를 생성합니다. ActiveX 명령 버튼을 단계별로
  삽입하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: ko
lastmod: 2026-09-27
og_description: Aspose.Words를 사용하여 Java에서 ActiveX가 포함된 docx를 생성합니다. 이 가이드를 따라 ActiveX
  명령 버튼을 삽입하고 문서를 저장하세요.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Java에서 ActiveX를 포함한 docx 만들기 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Java와 Aspose.Words를 사용하여 ActiveX가 포함된 docx 만들기
url: /ko/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java와 Aspose.Words를 사용하여 ActiveX가 포함된 docx 만들기

ActiveX가 포함된 docx를 **생성**해야 한다면, 이 가이드는 완전한 솔루션을 제공합니다. Aspose.Words for Java를 사용하여 Word 파일에 **ActiveX 커맨드 버튼**을 삽입하는 방법을 배우고, 결과를 Microsoft Word에서 열 수 있는 .docx 파일로 저장하는 방법을 알아봅니다.

프로그램matically 워드 문서를 생성하면 수동 편집을 피할 수 있고, 보고서, 계약서 또는 양식 템플릿 전반에 걸쳐 일관성을 보장합니다. 아래 단계에서는 프로젝트 설정부터 일반적인 함정 처리까지 모든 내용을 다루므로, 이 기술을 모든 Java 애플리케이션에 통합할 수 있습니다.

## 사전 요구 사항

* Java Development Kit (JDK) 8 이상이 설치되어 있어야 합니다.
* Maven 3.6 이상 (또는 선호하는 다른 빌드 도구).
* Aspose.Words for Java 라이선스 파일 (무료 평가판을 테스트에 사용할 수 있습니다).
* ActiveX 컨트롤을 시각적으로 확인하려면 대상 컴퓨터에 Microsoft Word가 설치되어 있어야 합니다.

이 항목들은 Aspose.Words가 문서를 생성하는 API를 제공하고, Word가 ActiveX 컨트롤을 렌더링하는 데 필요하기 때문에 요구됩니다.

## 1단계: Maven 프로젝트 설정

새 Maven 프로젝트를 생성하거나 기존 `pom.xml`에 Aspose.Words 의존성을 추가합니다:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** 버그 수정 및 새로운 ActiveX 기능을 활용하려면 Aspose.Words 버전을 공식 릴리스 노트와 동기화하십시오.

## 2단계: 문서를 생성하는 Java 코드 작성

`ActiveXDocxCreator`라는 클래스를 생성합니다. 아래 코드는 필요한 모든 import, `main` 메서드, 그리고 각 작업을 설명하는 자세한 주석을 포함하고 있습니다.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### 각 라인이 중요한 이유

- `Document`는 모든 Word 콘텐츠를 담는 컨테이너입니다. 새 인스턴스를 생성하면 깨끗한 캔버스를 얻을 수 있습니다.
- `DocumentBuilder`는 요소를 삽입하기 위한 유창한 API를 제공하며, 삽입 위치를 자동으로 추적합니다.
- `insertForms2OleControl()`은 일반 OLE 컨트롤 자리표시자를 생성합니다. Aspose.Words는 이를 ActiveX 컨테이너로 처리합니다.
- `setControlType(Forms2OleControlType.COMMANDBUTTON)`은 Word에 해당 자리표시자를 CommandButton으로 렌더링하도록 지시합니다.
- `setCaption("Click Me")`는 버튼에 표시될 텍스트를 정의합니다.
- `setLeft`와 `setTop`은 페이지 여백을 기준으로 버튼을 배치합니다. 레이아웃에 맞게 값을 조정하십시오.
- `setWidth`와 `setHeight`는 선택 사항이지만, 기본 크기가 너무 작을 경우 버튼 외관을 개선합니다.
- `doc.save`는 메모리 내 구조를 실제 .docx 파일로 기록하여 Word에서 열 수 있게 합니다.

## 3단계: 생성된 문서 확인

Microsoft Word에서 `output/ActiveXCommandButton.docx` 파일을 엽니다:

1. 문서에 **Click Me** 라벨이 붙은 버튼이 페이지 왼쪽 상단 근처에 표시된 단일 페이지가 나타나야 합니다.
2. 버튼이 보이지 않으면 Word의 신뢰 센터에서 **ActiveX 컨트롤이 활성화**되어 있는지 확인하십시오(파일 → 옵션 → 신뢰 센터 → 신뢰 센터 설정 → ActiveX 설정).
3. 이 버튼은 ActiveX를 지원하는 Windows 버전의 Word에서만 작동합니다. macOS 또는 웹 기반 Word에서는 컨트롤이 정적 이미지로 표시됩니다.

## 4단계: 일반적인 엣지 케이스 처리

| 상황 | 이유 | 권장 조치 |
|-----------|--------|--------------------|
| 파일을 연 후 버튼이 누락됨 | Word 보안 설정이 ActiveX를 차단함 | 신뢰할 수 있는 위치에 대해 “제한 없이 모든 컨트롤 실행”을 활성화합니다. |
| 생성된 .docx를 열 수 없음 | 호환되지 않는 Aspose.Words 버전 | 최신 Aspose.Words 릴리스로 업그레이드하십시오; 이전 버전은 필요한 OLE 파트를 올바르게 포함하지 못할 수 있습니다. |
| 버튼이 매크로를 실행해야 함 | ActiveX만으로는 매크로 코드가 포함되지 않음 | `Click` 이벤트를 처리하는 VBA 매크로와 ActiveX 컨트롤을 결합하십시오. `DocumentBuilder.insertOleObject` 메서드를 사용하여 매크로 사용 가능한 템플릿을 삽입합니다. |
| 다른 페이지 크기에서 레이아웃이 어긋남 | 좌표가 절대 포인트값이기 때문 | 컨트롤을 배치하기 전에 `builder.getPageSetup().setPageWidth`와 `setPageHeight`를 사용하여 페이지 크기를 표준화하십시오. |

## 5단계: 솔루션 확장

`ControlType` 열거형을 변경하면 다른 ActiveX 컨트롤을 삽입할 수 있습니다:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words는 **ActiveX 텍스트 박스**, **리스트 박스**, **콤보 박스** 삽입도 지원합니다. 동일한 위치 지정 메서드(`setLeft`, `setTop`, `setWidth`, `setHeight`)를 사용할 수 있습니다.

여러 개의 컨트롤을 배치해야 하면 `builder.insertForms2OleControl()`을 반복 호출하고 각 컨트롤의 좌표를 적절히 조정하십시오.

## 전체 소스 파일

아래는 복사‑붙여넣기 할 수 있도록 준비된 전체 `ActiveXDocxCreator.java` 파일입니다:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

이 프로그램을 실행하면 **ActiveX가 포함된 docx**가 생성되며, 인터랙티브 양식이 필요한 최종 사용자에게 배포할 수 있습니다.

## 결론

이제 Java와 Aspose.Words를 사용하여 **ActiveX가 포함된 docx를 생성**하고, **ActiveX 커맨드 버튼을 프로그래밍 방식으로 삽입**하는 방법을 알게 되었습니다. 이 튜토리얼은 프로젝트 설정, 전체 소스 코드, 검증 단계, 일반적인 문제를 처리하는 전략을 다루었습니다.

다음과 같은 내용을 탐색해 볼 수 있습니다:

* 버튼 클릭에 응답하는 VBA 매크로 추가.
* 체크박스나 콤보 박스와 같은 다른 ActiveX 컨트롤 삽입.
* 동적 데이터를 사용한 다중 페이지 양식 자동 생성.

다양한 좌표, 크기, 컨트롤 유형을 실험하여 특정 문서 레이아웃에 맞추세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java에서 OLE 객체 및 ActiveX 컨트롤 사용](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용하여 양식 필드 생성 및 콘텐츠 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words로 Word에서 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}