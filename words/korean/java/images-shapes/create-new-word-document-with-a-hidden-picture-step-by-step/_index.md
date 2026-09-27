---
category: general
date: 2026-09-27
description: 새 Word 문서를 만들고 숨겨진 이미지 도형을 삽입합니다. Aspose.Words for Java를 사용하여 도형을 숨기고
  숨겨진 그림을 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert image shape
- how to hide shape
- how to insert image
- add hidden picture
language: ko
lastmod: 2026-09-27
og_description: 새 Word 문서를 만들고 숨겨진 이미지 도형을 삽입합니다. Aspose.Words for Java를 사용하여 도형을
  숨기고 숨겨진 그림을 추가하는 방법을 배워보세요.
og_image_alt: Screenshot showing a Word document with a hidden picture inserted using
  Java
og_title: 숨겨진 그림이 있는 새 Word 문서 만들기 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create new Word document and insert an image shape that stays hidden.
    Learn how to hide shape and add hidden picture using Aspose.Words for Java.
  headline: Create new Word document with a hidden picture – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- hidden image
title: 숨겨진 그림이 포함된 새 Word 문서 만들기 – 단계별 가이드
url: /ko/java/images-shapes/create-new-word-document-with-a-hidden-picture-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 숨겨진 그림이 포함된 새 Word 문서 만들기 – 단계별 가이드

If you need to **create new Word document** that contains a logo but you don't want the logo to affect the page layout, this guide shows you exactly how to do it. You will learn how to **insert image shape**, understand **how to hide shape**, and finally **add hidden picture** to the file without any visual impact.

이 가이드는 프로젝트 설정부터 최종 검증 단계까지 모든 것을 다룹니다. 끝까지 진행하면 Word 파일을 만들고, 이미지 쉐이프를 삽입하고, 숨기고, 결과를 저장하는 완전한 Java 프로그램을 얻게 됩니다. Aspose.Words for Java 라이브러리 외에 추가 도구는 필요하지 않습니다.

## 전제 조건

* Java 17 (또는 최신 버전)이 설치되어 있어야 합니다.
* 의존성을 추가할 수 있는 Maven 또는 Gradle 프로젝트.
* Aspose.Words for Java 23.9 (또는 최신 버전) – 올바른 좌표는 공식 Maven 저장소를 참조하세요.
* `logo.png`와 같은 이미지 파일을 코드에서 참조할 수 있는 폴더에 배치합니다.

> **프로 팁:** 개발 중에 이미지를 소스 파일과 같은 디렉터리에 두세요; 경로 처리를 단순화합니다.

## 단계 1: 프로젝트 설정 및 Aspose.Words 가져오기

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Below is the Maven snippet:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Now create a Java class called `HiddenPictureDemo`. The first lines import the required classes and **create new Word document**:

```java
import com.aspose.words.*;

public class HiddenPictureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder
        Document doc = new Document();               // creates new Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*왜 중요한가:* `Document`는 전체 `.docx` 파일을 나타내며, `DocumentBuilder`는 단락, 표, 쉐이프와 같은 콘텐츠를 추가하기 위한 유창한 API를 제공합니다.

## 단계 2: Word 문서에 이미지 쉐이프 삽입

The next operation demonstrates **how to insert image** as a shape. Using `DocumentBuilder.insertImage` returns a `Shape` object that you can further manipulate.

```java
        // Step 2: Insert an image shape (the picture will act as a shape)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");
        // Optional: set the shape size if needed
        imageShape.setWidth(100);
        imageShape.setHeight(50);
```

*왜 쉐이프를 사용하는가:* 쉐이프로 삽입된 이미지는 가시성, 래핑, 위치 지정과 같은 레이아웃 속성에 접근할 수 있게 하며, 이는 나중에 그림을 숨길 때 필수적입니다.

## 단계 3: 쉐이프를 숨겨 레이아웃에 나타나지 않게 하기

Now we answer **how to hide shape**. Setting the `Hidden` property to `true` removes the shape from the visual layout while keeping it in the document structure.

```java
        // Step 3: Hide the shape – this is the core of "add hidden picture"
        imageShape.setHidden(true);
        // You can also set the shape's wrap type to NONE to avoid affecting surrounding text
        imageShape.setWrapType(WrapType.NONE);
```

*설명:* `setHidden(true)`는 Word에게 쉐이프를 보이지 않게 처리하도록 지시합니다. 추가적인 `setWrapType(WrapType.NONE)`은 숨겨진 그림이 공간을 차지하지 않도록 하여 원래 문서 흐름을 유지합니다.

## 단계 4: 문서 저장 및 숨겨진 그림 확인

Finally, persist the file to disk. The hidden picture remains part of the document but is not displayed when the file is opened in Microsoft Word.

```java
        // Step 4: Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx");
        System.out.println("Document created successfully with a hidden picture.");
    }
}
```

When you open `HiddenShape.docx` in Word, you will see a normal, clean page with no visible logo, yet the image is stored inside the file. You can verify its presence by opening the `.docx` as a zip archive and inspecting the `word/media` folder.

`HiddenShape.docx`를 Word에서 열면 로고가 보이지 않는 일반적이고 깔끔한 페이지가 표시되지만, 이미지가 파일 내부에 저장되어 있습니다. `.docx`를 zip 아카이브로 열고 `word/media` 폴더를 확인하면 존재 여부를 검증할 수 있습니다.

### 예상 출력

Running the program prints:

```
Document created successfully with a hidden picture.
```

프로그램을 실행하면 다음과 같이 출력됩니다:

Opening the generated `HiddenShape.docx` shows an empty page (or whatever content you added elsewhere) and no visible image. If you unzip the `.docx`, you’ll find `logo.png` inside `word/media`, confirming that the picture was **add hidden picture** correctly.

생성된 `HiddenShape.docx`를 열면 빈 페이지(또는 다른 곳에 추가한 내용)가 표시되고 보이는 이미지가 없습니다. `.docx`를 압축 해제하면 `word/media` 안에 `logo.png`가 있어 **add hidden picture**가 올바르게 수행되었음을 확인할 수 있습니다.

## 다른 상황에서 이미지 삽입 방법

If you need to **insert image shape** into a specific paragraph rather than the current cursor position, you can move the builder first:

```java
builder.moveToParagraph(0, 0); // moves to the first paragraph
Shape anotherShape = builder.insertImage("YOUR_DIRECTORY/banner.jpg");
anotherShape.setHidden(true);
```

현재 커서 위치가 아니라 특정 단락에 **insert image shape**를 삽입해야 할 경우, 먼저 빌더를 이동시킬 수 있습니다:

This pattern works for headers, footers, or tables—just move the builder to the target node before calling `insertImage`.

이 패턴은 헤더, 푸터, 테이블에서도 작동합니다—`insertImage`를 호출하기 전에 빌더를 대상 노드로 이동하면 됩니다.

## 일반적인 변형 및 엣지 케이스

| 시나리오 | 조정 사항 |
|----------|----------------|
| **Multiple hidden pictures** | 각 이미지에 대해 단계 2‑3을 반복합니다. 각 `Shape`는 독립적으로 숨길 수 있습니다. |
| **Different image formats** | Aspose.Words는 PNG, JPEG, BMP, GIF, TIFF를 지원합니다. 경로에 적절한 파일 확장자를 사용하세요. |
| **Large documents** | 문서를 한 번 생성한 후 동일한 `DocumentBuilder`를 재사용하여 다양한 위치에 숨겨진 그림을 삽입합니다. |
| **Conditional visibility** | `shape.setVisible(false)`와 `shape.setHidden(true)`를 함께 사용하면 나중에 Word 매크로로 가시성을 토글할 수 있습니다. |
| **Compatibility with older Word versions** | `doc.save("file.doc", SaveFormat.DOC)`와 같이 저장하면 Word 2003‑2007을 지원해야 할 경우에도 숨겨진 쉐이프가 동일하게 동작합니다. |

## 실무 팁

* **Path handling:** `Paths.get("...").toAbsolutePath().toString()`을 사용하면 IDE에서 실행할 때와 패키징된 JAR에서 실행할 때 발생할 수 있는 상대 경로 문제를 피할 수 있습니다.
* **Performance:** 많은 대형 이미지를 삽입하면 메모리 사용량이 증가할 수 있습니다. 숨기기 전에 이미지(`setWidth`/`setHeight`)를 스케일링하는 것을 고려하세요.
* **Testing:** 저장된 문서를 로드하고 `doc.getChildNodes(NodeType.SHAPE, true).getCount()`를 호출하여 숨겨져 있더라도 예상되는 쉐이프 수가 존재하는지 자동으로 확인합니다.

## 결론

You now know how to **create new Word document**, **insert image shape**, and **how to hide shape** so that the picture remains invisible—effectively **add hidden picture** to any Word file using Aspose.Words for Java. This technique is useful for embedding watermarks, branding assets, or metadata images that should not disrupt the document layout.

이제 **create new Word document**, **insert image shape**, 그리고 **how to hide shape**를 통해 그림을 보이지 않게 유지하는 방법을 알게 되었습니다—즉 Aspose.Words for Java를 사용하여 모든 Word 파일에 **add hidden picture**를 효과적으로 추가할 수 있습니다. 이 기술은 워터마크, 브랜드 자산, 또는 문서 레이아웃을 방해하지 않아야 하는 메타데이터 이미지를 삽입할 때 유용합니다.

### 다음 단계

* 회전, 테두리, 하이퍼링크와 같은 다른 쉐이프 속성을 탐색하세요.
* 숨겨진 그림을 사용자 정의 문서 속성과 결합하여 추가 메타데이터를 저장하세요.
* **how to insert image**를 헤더나 푸터에 삽입하는 방법을 살펴보아 페이지 전반에 일관된 브랜딩을 구현하세요.

다양한 이미지 크기, 위치 및 가시성 설정을 자유롭게 실험해 보세요. 문제가 발생하면 Aspose.Words for Java 문서에서 자세한 API 레퍼런스와 샘플 프로젝트를 제공합니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [Java로 Word에서 사각형 쉐이프 만들기 – 전체 가이드](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Word에서 쉐이프에 그림자 추가 – 완전한 Aspose.Words 가이드](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용해 폼 필드 생성 및 콘텐츠 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}