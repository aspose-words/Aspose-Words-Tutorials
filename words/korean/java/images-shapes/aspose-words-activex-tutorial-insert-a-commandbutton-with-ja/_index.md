---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX 튜토리얼에서는 Java를 사용하여 Word 문서에 CommandButton 컨트롤을 추가하는
  방법을 보여줍니다. 전체 코드, 구성 및 저장 단계에 대해 알아보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: ko
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX 튜토리얼은 Java를 사용하여 Word 문서에 CommandButton ActiveX
  컨트롤을 삽입하는 방법을 설명합니다. 전체 예제를 따라 문서를 생성, 구성 및 저장하세요.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX 튜토리얼 – Java 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX 튜토리얼 – Java로 CommandButton 삽입
url: /ko/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX 튜토리얼 – Java로 CommandButton 삽입

Word 파일에 ActiveX 컨트롤을 삽입해야 하는 경우, 이 **Aspose.Words ActiveX 튜토리얼**은 전체 과정을 안내합니다. 빈 문서를 만들고, CommandButton을 삽입하고, 속성을 설정하고, 결과를 저장하는 과정을 순수 Java 코드로 확인할 수 있습니다.

예제는 Aspose.Words for Java API를 사용하므로 빌드 서버에 Microsoft Office가 필요하지 않습니다. 이 가이드를 마치면 Windows 환경에서 사용할 수 있는 완전한 기능의 CommandButton 컨트롤이 포함된 .docx 파일을 생성할 수 있습니다.

## 필수 조건

- Java Development Kit (JDK) 8 이상이 설치되어 있어야 합니다.
- Maven 또는 기타 빌드 도구를 사용해 종속성을 관리합니다.
- Aspose.Words for Java 라이선스(또는 임시 평가 키)를 사용해 평가 워터마크를 방지합니다.
- Java 구문 및 객체 지향 프로그래밍에 대한 기본적인 이해가 필요합니다.

> **Pro tip:** `pom.xml`에 Aspose.Words Maven 종속성을 추가하면 IDE가 클래스를 자동으로 해결합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## 1단계: 새 빈 문서와 `DocumentBuilder` 만들기

`Document` 클래스는 메모리 내의 Word 파일을 나타내며, `DocumentBuilder`는 문서를 편집하기 위한 유창한 API를 제공합니다. 두 객체를 초기화하면 문서를 추가 수정할 준비가 됩니다.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**왜 중요한가:**  
`DocumentBuilder`는 현재 커서 위치를 추적하므로, 이후에 수행되는 삽입 작업(예: 컨트롤 추가)이 정확히 원하는 위치에 나타납니다.

## 2단계: CommandButton ActiveX 컨트롤 삽입

Aspose.Words는 ActiveX 객체를 위해 `Forms2OleControl`을 제공합니다. `insertForms2OleControl` 메서드는 컨트롤 유형을 필요로 하며, 이는 `Forms2OleControlType` 열거형을 통해 지정합니다.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**설명:**  
삽입된 컨트롤은 COM 기반 객체이며, 문서를 Windows 환경의 Word에서 열면 클릭 가능한 버튼으로 렌더링됩니다.

## 3단계: 버튼 속성 구성

삽입 후에는 버튼의 이름, 캡션, 크기 및 위치를 조정할 수 있습니다. 이러한 속성은 Word 내부에서 컨트롤의 모양과 동작에 영향을 줍니다.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**이 설정이 중요한 이유:**  

- **Name** – VBA 매크로가 컨트롤을 참조할 수 있게 합니다 (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – 사용자가 클릭하는 표시 라벨을 결정합니다.
- **Left / Top** – 페이지 여백을 기준으로 배치를 제어합니다.
- **Width / Height** – 다양한 화면 해상도에서도 일관된 시각적 크기를 보장합니다.

## 4단계: 문서 저장

`save` 메서드를 호출하면 메모리 내 표현이 실제 파일로 기록됩니다. 지원되는 형식(`.docx`, `.doc`, `.pdf` 등) 중 원하는 형식을 선택할 수 있습니다. 이 튜토리얼에서는 기본 Word 형식을 유지합니다.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**결과:**  
Microsoft Word에서 `ActiveXDemo.docx`를 열면 지정된 좌표에 **Submit**이라는 레이블이 붙은 CommandButton이 표시됩니다. 버튼을 클릭하면 기본 동작이 실행되며(기본적으로 VBA 코드가 연결되어 있지 않음) 동작합니다.

## 전체 소스 코드

조각들을 합치면 완전하고 실행 가능한 프로그램은 다음과 같습니다:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### 예상 출력

- `output` 폴더에 **ActiveXDemo.docx** 파일이 생성됩니다.
- Microsoft Word(Windows)에서 열면 문서에 정의된 위치에 클릭 가능한 **Submit** 버튼이 표시됩니다.
- 버튼을 선택, 이동하거나 Word UI(Developer → Properties)를 통해 VBA 코드에 연결할 수 있습니다.

## 일반적인 변형 처리

| Scenario | Adjustment |
|----------|------------|
| **.doc 형식으로 저장** (레거시 포맷) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **이벤트 핸들러 추가** | Word는 Aspose.Words를 통해 ActiveX 이벤트를 노출하지 않습니다. 문서가 생성된 후 VBA 코드를 수동으로 추가해야 합니다. |
| **여러 컨트롤** | 다른 `setName` 및 `setCaption` 값을 사용해 삽입/구성 블록을 반복합니다. |
| **다른 컨트롤 유형 (예: CheckBox)** | `insertForms2OleControl` 호출에서 `Forms2OleControlType.CHECKBOX`를 사용합니다. |
| **비 Windows 플랫폼** | ActiveX 컨트롤은 Windows Word에서만 렌더링됩니다. 크로스 플랫폼 솔루션이 필요하면 콘텐츠 컨트롤(`StructuredDocumentTag`)을 고려하세요. |

## 모범 사례 및 함정

- **License early** – `Document`를 생성하기 전에 Aspose.Words 라이선스를 등록하여 평가 프롬프트를 방지합니다.
- **Coordinate system** – 위치는 포인트 단위(1 pt = 1/72 in)로 측정됩니다. UI 디자인이 픽셀이나 센티미터 단위를 사용한다면 변환이 필요합니다.
- **File paths** – 출력 디렉터리가 존재하지 않을 경우 `FileNotFoundException`을 방지하기 위해 절대 경로나 Java의 `Paths` API를 사용합니다.
- **Thread safety** – `Document`와 `DocumentBuilder`는 스레드 안전하지 않습니다. 병렬로 문서를 생성한다면 스레드당 별도 인스턴스를 생성하세요.
- **Testing** – 대상 Word 버전(예: Word 2016, Word 365)에서 생성된 문서를 확인하세요. 오래된 버전에서는 ActiveX 컨트롤이 다르게 표시될 수 있습니다.

## 결론

이 **Aspose.Words ActiveX 튜토리얼**은 Java를 사용해 Word 문서에 CommandButton 컨트롤을 프로그래밍 방식으로 추가하는 방법을 보여줍니다. 다음을 배웠습니다:

1. `Document`와 `DocumentBuilder` 초기화
2. `COMMAND_BUTTON` 유형의 `Forms2OleControl` 삽입
3. 버튼의 이름, 캡션, 크기 및 위치 설정
4. ActiveX 컨트롤이 포함된 .docx 파일 저장

이제 추가 컨트롤 유형을 탐색하거나 VBA 매크로 주입을 자동화하거나 ActiveX 컨트롤을 메일 머지 및 콘텐츠 컨트롤과 같은 다른 Aspose.Words 기능과 결합할 수 있습니다. 다양한 레이아웃을 실험하고 생성된 문서를 더 큰 Java 기반 보고 파이프라인에 통합해 보세요.

---


## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하며, 관련 주제를 자세히 다룹니다. 각 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for Java에서 OLE 객체 및 ActiveX 컨트롤 사용](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용해 양식 필드 생성 및 콘텐츠 추가](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java 튜토리얼: Word를 RTF로 변환](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}