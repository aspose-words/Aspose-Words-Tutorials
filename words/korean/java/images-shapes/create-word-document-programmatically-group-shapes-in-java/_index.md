---
category: general
date: 2026-09-21
description: Java를 사용하여 프로그래밍 방식으로 워드 문서를 생성합니다. 워드에서 도형을 그룹화하는 방법, 사각형 도형 삽입, 도형
  크기 설정 및 도형을 워드 문서에 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: ko
lastmod: 2026-09-21
og_description: 'Java로 워드 문서를 프로그래밍 방식으로 생성하기: 이 가이드는 워드에서 도형을 그룹화하고, 사각형 도형을 삽입하며,
  도형 크기를 설정하고, 워드 문서에 도형을 추가하는 방법을 보여줍니다.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: 프로그램으로 워드 문서 만들기, Java에서 도형 그룹화
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: 프로그래밍으로 워드 문서 만들기, Java에서 도형 그룹화
url: /ko/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 프로그래밍으로 워드 문서 만들기, 도형 그룹화

프로그래밍으로 워드 문서를 **생성**해야 한다면, 이 가이드는 전체 솔루션을 단계별로 안내합니다. **Word에서 도형을 그룹화**하고, 사각형을 삽입하고, 크기를 설정하며, 다른 도형을 추가하는 방법을 Java와 Aspose.Words for Java 라이브러리를 사용하여 보여줍니다.

이 튜토리얼은 프로젝트 설정부터 최종 .docx 파일 저장까지 모든 단계를 다룹니다. 끝까지 따라오면 사각형과 이미지가 하나의 그룹으로 묶인 Word 문서를 생성할 수 있게 되며, 이를 통해 두 객체를 함께 이동하거나 크기를 조정할 수 있습니다. Aspose.Words API에 대한 사전 경험은 필요 없으며, 기본적인 Java 개발 환경만 있으면 됩니다.

## Prerequisites

* Java Development Kit (JDK) 8 이상  
* Maven 또는 Gradle(의존성 관리용)  
* Aspose.Words for Java 23.9(또는 최신 버전) – 라이브러리는 평가용으로 무료  
* 이미지 파일(예: `sample.jpg`)을 알려진 디렉터리에 배치  

이 항목들을 미리 준비하면 추가 설정 없이 코드를 실행할 수 있습니다.

## Step 1: Set up the project and import Aspose.Words

Maven 프로젝트를 생성하거나 기존 `pom.xml`에 종속성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Gradle을 선호한다면 `build.gradle`에 다음을 추가합니다:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

종속성이 해결된 후, Java 소스 파일에 필요한 클래스를 import 합니다:

```java
import com.aspose.words.*;
import java.io.File;
```

## Step 2: Create the Word document programmatically

자동화 시나리오에서 첫 번째 작업은 `Document` 객체와 `DocumentBuilder`를 인스턴스화하는 것입니다. Builder를 사용하면 텍스트, 이미지, 도형 삽입이 간편해집니다.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

이 시점에서 문서는 메모리 상에만 존재합니다. 이제 도형을 추가할 수 있습니다.

## Step 3: Insert a rectangle shape – how to insert rectangle shape

사각형은 `ShapeType.RECTANGLE`을 가진 기본 `Shape`입니다. `setWidth`, `setHeight`로 크기를 제어하고 `setTop`, `setLeft`로 위치를 지정합니다.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Why this matters:** 크기와 위치를 명시적으로 설정(`set shape size word`)하면 문서의 기본 레이아웃에 관계없이 사각형이 정확히 원하는 위치에 표시됩니다.

## Step 4: Insert an image – add shapes to word document

`DocumentBuilder`는 파일 경로에서 직접 이미지를 삽입할 수 있습니다. 삽입 후에는 다른 도형처럼 사진의 위치를 다시 지정할 수 있습니다.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

이제 사각형과 그림은 문서 안에서 독립적인 도형으로 존재합니다.

## Step 5: Group the shapes – how to group shapes in word

도형을 그룹화하면 하나의 단위로 이동하거나 크기를 조정할 수 있어 편리합니다. Aspose.Words는 이를 위해 `GroupShape` 컨테이너를 제공합니다.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

그룹을 저장하면 Word는 두 자식을 하나의 논리 객체로 취급합니다. 이후 그룹을 선택해 드래그하면 사각형과 이미지가 함께 움직입니다.

## Step 6: Save the document

마지막으로 문서를 디스크에 기록합니다. 경로는 Java 프로세스가 쓰기 가능한 위치여야 합니다.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`main` 메서드를 실행하면 **GroupShapeExample.docx** 파일이 생성됩니다. Microsoft Word에서 열어 보면 사각형과 이미지가 하나의 그룹 안에 고정되어 있는 것을 확인할 수 있습니다. 그룹을 선택하면 두 객체가 동시에 이동하여 그룹화가 성공했음을 증명합니다.

## Expected output

* 지정한 디렉터리에 생성된 Word 파일(`GroupShapeExample.docx`).  
* 파일 내부에, 연한 회색 채우기의 사각형이 좌상단에 표시되고, 이미지가 바로 아래에 배치됩니다.  
* 두 객체가 하나의 그룹에 포함되어 있어, 하나를 드래그하면 다른 객체도 함께 이동합니다.

## Common variations and edge cases

| 상황 | 권장 사항 |
|-----------|----------------|
| **다양한 이미지 포맷** | Aspose.Words는 PNG, BMP, GIF, TIFF를 지원합니다. `insertImage`에 적절한 파일 확장자를 사용하세요. |
| **음수 크기** | API가 `ArgumentException`을 발생시킵니다. `setWidth`/`setHeight` 호출 전에 항상 너비와 높이를 검증하세요. |
| **대용량 문서** | 많은 도형을 그룹화하면 파일 크기가 증가할 수 있습니다. 성능이 중요한 경우 도형을 하나의 그림으로 병합하는 것을 고려하세요. |
| **Word 버전 호환성** | GroupShape는 Word 2007(`.docx`) 이후 버전에서 작동합니다. 오래된 `.doc` 파일에서는 그룹이 평면화됩니다. |
| **동적 위치 지정** | 페이지 크기(`doc.getFirstSection().getPageSetup().getPageWidth()`)를 기반으로 계산하여 적응형 배치를 구현하세요. |

**Pro tip:** 그룹을 만든 후, 변경할 수 있습니다

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Word 문서 생성 Java – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java로 Word에서 사각형 도형 만들기 – 전체 가이드](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [.NET용 Aspose.Words를 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}