---
category: general
date: 2026-10-04
description: 새 문서에 대한 DocumentBuilder를 초기화하고 Java에서 Aspose.Words를 사용해 ActiveX 버튼을
  추가하는 방법을 배웁니다. 전체 코드를 포함한 단계별 가이드.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: ko
lastmod: 2026-10-04
og_description: 새 문서를 위해 DocumentBuilder를 초기화하고 Aspose.Words Java API를 사용하여 ActiveX
  명령 버튼을 삽입합니다. 이 간결한 튜토리얼을 따라보세요.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: 새 문서를 위한 DocumentBuilder 초기화 – 완전한 Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Aspose.Words를 사용하여 새 문서에 대한 DocumentBuilder 초기화 방법
url: /ko/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 새 문서에 대한 DocumentBuilder 초기화 방법

Java 프로젝트에서 **initialize DocumentBuilder for new document**가 필요하다면, 이 튜토리얼은 정확한 단계를 보여줍니다. 빈 Word 파일을 만들고, ActiveX 명령 버튼을 첨부하고, 결과를 저장하는 방법을 하나의 독립적인 코드 샘플로 확인할 수 있습니다.

프로그램matically Word 문서를 다루는 것은 종종 폼 컨트롤과 같은 저수준 세부 사항을 처리하는 것을 의미합니다. 이 가이드를 끝까지 따라가면 IDE를 떠나지 않고도 ActiveX 버튼을 삽입할 수 있게 되며, 이는 템플릿 생성, 자동 보고서 또는 인터랙티브 폼에 유용합니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 이상이 설치되어 있음  
* Maven 3.8+ (또는 선호한다면 Gradle)  
* Aspose.Words for Java 라이선스(무료 체험판으로 테스트 가능)  
* Java 구문에 대한 기본적인 이해  

Aspose.Words를 처음 사용하는 경우, 이 라이브러리는 Word 문서를 생성, 편집 및 저장하기 위한 고수준 API를 제공합니다. `DocumentBuilder` 클래스는 문서 내용을 구성하기 위한 주요 진입점입니다.

## Step 1: Set up the Maven project

새 Maven 프로젝트를 만들거나(또는 기존 프로젝트에 추가) Aspose.Words 의존성을 포함합니다:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** 라이브러리 버전을 최신 상태로 유지하세요; 최신 릴리스는 추가 폼 컨트롤 지원을 추가하고 성능을 향상시킵니다.

## Step 2: Initialize `DocumentBuilder` for new document

튜토리얼의 핵심은 **initialize DocumentBuilder for new document** 작업입니다. 먼저 빈 `Document` 인스턴스를 생성한 다음 이를 `DocumentBuilder` 생성자에 전달합니다.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* `DocumentBuilder`를 초기화하면 빌더가 특정 `Document` 객체에 연결되어 해당 문서에 직접 단락, 표 또는 폼 컨트롤을 추가할 수 있습니다. 이 단계가 없으면 빌더는 작업 대상이 없습니다.

## Step 3: Insert an ActiveX command button control

Aspose.Words는 레거시 ActiveX 컨트롤을 삽입하기 위해 `Forms2OleControl` 클래스를 제공합니다. 다음 코드는 현재 커서 위치에 **Forms2OleControl 명령 버튼**을 추가합니다.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### What is an ActiveX command button?

ActiveX 명령 버튼은 사용자가 Word 문서 내에서 클릭할 때 매크로를 실행하거나 이벤트를 트리거할 수 있는 레거시 UI 요소입니다. 최신 Office 버전은 콘텐츠 컨트롤을 선호하지만, 많은 기업 템플릿은 여전히 ​​호환성을 위해 ActiveX에 의존합니다.

## Step 4: Save the document

컨트롤을 삽입한 후에는 간단히 `save`를 호출하면 됩니다. 파일에는 ActiveX 버튼이 포함되며 Microsoft Word에서 열 수 있습니다.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`ActiveXButton.docx`를 Word에서 열면 **Click Me**라는 레이블이 붙은 버튼이 표시됩니다. 매크로를 연결하지 않으면 버튼을 클릭해도 아무 동작을 하지 않지만, 컨트롤 자체는 완전히 작동합니다.

## Full, runnable example

아래는 `src/main/java/com/example/ActiveXButtonDemo.java`에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 빠른 테스트에 필요한 모든 import와 오류 처리를 포함합니다.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document saved to output/ActiveXButton.docx
```

생성된 파일을 Microsoft Word 2016 이상에서 열면 첫 페이지 상단에 *Click Me*라는 레이블이 붙은 버튼이 표시됩니다.

## Common variations and edge cases

| 시나리오 | 조정 |
|----------|------|
| **특정 단락에 버튼 추가** | `insertForms2OleControl`을 호출하기 전에 `builder.moveToParagraph(index, NodeType.PARAGRAPH);` 로 빌더의 커서를 이동합니다. |
| **버튼 크기 설정** | 포인트 단위로 크기를 정의하려면 `commandButton.setWidth(100);` 및 `commandButton.setHeight(30);` 를 사용합니다. |
| **버튼에 매크로 추가** | 문서를 저장한 후 Word에서 열어 개발자 탭을 활성화하고 버튼에 VBA 매크로를 수동으로 연결합니다 (ActiveX 컨트롤은 Aspose.Words에서 직접 스크립팅할 수 없습니다). |
| **.doc (바이너리) 형식 대상** | 레거시 Word 97‑2003 파일을 만들려면 `doc.save(outputPath, SaveFormat.DOC);` 로 변경합니다. |
| **Android에서 실행** | Java API를 통해 Aspose.Words for Android를 사용하세요; 라이브러리가 APK에 포함되어 있는 한 동일한 코드가 작동합니다. |

## Troubleshooting tips

* **`java.lang.NoClassDefFoundError`** – Aspose.Words JAR가 클래스패스에 있는지 확인하세요. Maven은 자동으로 추가합니다; 수동 빌드의 경우 JAR를 `libs/`에 두고 IDE 라이브러리에 추가합니다.  
* **Button does not appear in Word** – Word의 신뢰 센터(`File → Options → Trust Center → Trust Center Settings → Macro Settings`)에서 *Show legacy forms* 옵션이 활성화되어 있는지 확인하세요.  
* **License exception** – 유효한 라이선스 없이 코드를 실행하면 Aspose.Words가 워터마크를 삽입합니다. 무료 체험을 등록하거나 라이선스를 구매하여 제거하세요.

## Conclusion

이제 **initialize DocumentBuilder for new document** 방법, ActiveX 명령 버튼 삽입, 그리고 Aspose.Words for Java로 결과를 저장하는 방법을 알게 되었습니다. 이 패턴을 사용하면 프로그램matically 인터랙티브 Word 템플릿을 생성할 수 있어 자동 보고서 작성이나 폼 기반 워크플로에 특히 유용합니다.

여기서부터는 추가 폼 컨트롤(`Forms2OleControlType.CHECKBOX`, `COMBOBOX` 등)을 탐색하고, 버튼을 사용자 정의 VBA 매크로와 결합하거나, 표, 이미지, 스타일링을 포함한 완전한 문서를 생성할 수 있습니다—모두 동일한 `DocumentBuilder` 워크플로를 사용합니다.

---

*보다 복잡한 Word 자동화를 구축할 준비가 되셨나요? **DocumentBuilder로 표 삽입**, **프로그램matically 스타일 적용**, 그리고 **Aspose.Words로 PDF 내보내기**에 대한 가이드를 확인하세요.*

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java에서 DocumentBuilder를 사용하여 폼 필드 생성 및 콘텐츠 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java로 문서를 PDF로 저장하는 방법](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java를 사용하여 문서에 워터마크 추가하기](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}