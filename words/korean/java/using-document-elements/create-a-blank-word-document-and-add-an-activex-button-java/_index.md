---
category: general
date: 2026-10-16
description: Java로 빈 Word 문서를 만든 다음, Aspose.Words를 사용하여 ActiveX 버튼을 추가하고 캡션을 설정하며
  크기를 조정하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: ko
lastmod: 2026-10-16
og_description: Java로 빈 Word 문서를 만든 다음, ActiveX 버튼을 추가하고 캡션을 설정하며 Aspose.Words를 사용하여
  크기를 정의합니다.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: 빈 Word 문서를 만들고 ActiveX 버튼 삽입 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: 빈 Word 문서를 만들고 ActiveX 버튼을 추가하기 (Java)
url: /ko/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서를 만들고 ActiveX 버튼을 추가하기 (Java)

프로그램matically **빈 Word 문서를 만들** 필요가 있다면, 이 가이드는 Java와 Aspose.Words를 사용하여 이를 수행하는 방법을 보여줍니다. 또한 **ActiveX 버튼을 추가**, **버튼 캡션 설정**, **버튼 크기 설정** 방법을 배워서 컨트롤이 기대한 대로 보이도록 할 수 있습니다.

이 튜토리얼에서는 다음을 다룹니다:

* Aspose.Words for Java를 사용하여 빈 Word 파일 초기화하기.  
* ActiveX `CommandButton` 컨트롤 삽입하기.  
* 버튼의 캡션과 크기 구성하기.  
* 최종 `.docx` 파일 저장하기.

Java에 대한 기본 지식과 최신 버전의 Aspose.Words for Java 라이브러리(코드는 23.9 이상에서 작동)를 가지고 있어야 합니다. 추가 종속성은 필요하지 않습니다.

![ActiveX 버튼이 포함된 빈 Word 문서 만들기](/images/activex-button-example.png){: .align-center alt="ActiveX 버튼이 포함된 빈 Word 문서 만들기"}

## Aspose.Words로 빈 Word 문서 만들기

첫 번째 단계는 빈 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내 전체 Word 파일을 나타내며 편집을 위한 `DocumentBuilder` 클래스를 제공합니다.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**왜 중요한가:**  
빈 문서를 만들면 숨겨진 스타일이나 섹션이 없어진 깨끗한 캔버스를 얻을 수 있어 이후 레이아웃 계산에 방해가 되는 요소를 피할 수 있습니다.

## 문서에 ActiveX 버튼 추가하기

Aspose.Words는 `Forms2OleControl` 클래스를 통해 레거시 ActiveX 컨트롤을 삽입할 수 있습니다. 다음 코드는 현재 커서 위치에 `CommandButton` 컨트롤을 삽입합니다.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**팁:** `setOleClassName` 값 `"Forms.CommandButton.1"`은 표준 Microsoft Forms 버튼의 ProgID입니다. 다른 ProgID(예: `"Forms.CheckBox.1"`)를 사용하면 다른 종류의 컨트롤이 삽입됩니다.

## 버튼 캡션 설정

캡션은 버튼 표면에 표시되는 텍스트입니다. 문서를 저장하기 전 언제든지 변경할 수 있습니다.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**왜 필요한가:** 사용자는 컨트롤의 목적이 명확할 때만 이해합니다. 의미 있는 캡션을 설정하면 특히 Windows에서 Word로 문서를 열 때 사용성이 향상됩니다.

## 버튼 크기 설정

위치와 크기는 포인트 단위로 지정됩니다(1 포인트 = 1/72 인치). 레이아웃에 맞게 값을 조정하세요.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**일반적인 변형:**

| 시나리오 | 조정 |
|----------|------------|
| 터치 스크린용 큰 버튼 | `setWidth`와 `setHeight`를 비례적으로 증가시킵니다 |
| 페이지 중앙에 배치된 버튼 | `left = (pageWidth - width) / 2` 계산 |
| 열에 여러 버튼 | 각 새 버튼마다 `setTop`을 증가시킵니다 |

## ActiveX 버튼이 포함된 문서 저장하기

마지막으로 문서를 디스크에 기록합니다. `.docx` 형식은 Windows 버전 Microsoft Word에서 ActiveX 컨트롤을 보존합니다.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**예상 결과:** Windows에서 Word로 `ActiveXCommandButton.docx`를 열면 왼쪽 여백에서 100 pt, 위쪽 여백에서 200 pt 떨어진 위치에 **Click Me** 라는 레이블이 붙은 클릭 가능한 버튼이 있는 빈 페이지가 표시됩니다.

## 전체 실행 가능한 예제

아래 전체 클래스를 IDE에 복사하고, 프로젝트 클래스패스에 Aspose.Words for Java JAR를 추가한 뒤 실행하세요.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

프로그램을 실행하면 작업 디렉터리에 `ActiveXCommandButton.docx`가 생성됩니다. Windows용 Microsoft Word로 열어 버튼이 설정대로 정확히 표시되는지 확인하세요.

## 이 접근 방식이 권장되는 이유

* **Simplicity:** 핵심 Aspose.Words API만 사용하므로 COM 인터옵이나 추가 라이브러리가 필요하지 않습니다.  
* **Portability:** 코드는 Java를 지원하는 모든 플랫폼에서 실행되지만, ActiveX 컨트롤 자체는 Windows 버전 Word에서만 작동합니다.  
* **Maintainability:** 모든 속성(캡션, 크기, 위치)이 명확하고 자체 문서화된 메서드를 통해 설정되므로 향후 조정이 간단합니다.

## 흔히 발생하는 문제와 해결 방법

| 문제점 | 해결책 |
|---------|------------|
| macOS 또는 Linux의 Word에서 버튼이 표시되지 않음 | ActiveX 컨트롤은 Windows 전용입니다. 크로스 플랫폼 문서를 위해 다른 컨트롤(예: 콘텐츠 컨트롤)을 사용하십시오. |
| 캡션이 잘림 | 버튼 너비가 텍스트를 담을 만큼 충분히 넓은지 확인하고, `setWidth`를 늘리거나 짧은 캡션을 사용하십시오. |
| 버튼이 다른 콘텐츠와 겹침 | `setTop` 및 `setLeft` 값을 조정하거나, 컨트롤 앞에 새 단락을 삽입하여 자체 공간을 확보하십시오. |

## 다음 단계

이제 **빈 Word 문서를 만들고**, **ActiveX 버튼을 추가하고**, **버튼 캡션을 설정하고**, **버튼 크기를 지정**할 수 있게 되었으니 다음을 탐색해 볼 수 있습니다:

* VBA 매크로를 통한 이벤트 처리 코드 추가(매크로 모듈 삽입 필요).  
* 테이블 레이아웃에 여러 컨트롤을 삽입하여 양식과 같은 문서 만들기.  
* Aspose.Words의 **FormField** API를 사용하여 크로스 플랫폼 양식 솔루션 구현하기.

다양한 크기, 위치, 캡션을 실험하여 특정 문서 디자인에 맞게 조정해 보세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 완전한 작동 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Java로 Word 문서 만들기 – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용하여 양식 필드 만들기 및 콘텐츠 추가](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java를 사용하여 문서에 워터마크 추가](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}