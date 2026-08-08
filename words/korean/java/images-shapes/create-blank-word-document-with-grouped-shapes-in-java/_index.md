---
category: general
date: 2026-08-07
description: Aspose.Words를 사용하여 Java에서 그룹화된 도형이 포함된 빈 Word 문서를 생성합니다. 도형을 그룹화하고, 도형
  크기를 설정하며, Word에 도형을 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: ko
lastmod: 2026-08-07
og_description: Java에서 그룹화된 도형이 포함된 빈 Word 문서를 생성합니다. 이 가이드를 따라 도형 크기를 설정하고, Word에
  도형을 추가하며, 도형을 그룹화하는 방법을 마스터하세요.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: 그룹화된 도형이 포함된 빈 Word 문서 만들기 – Java 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Java에서 그룹화된 도형이 포함된 빈 Word 문서 만들기
url: /ko/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 그룹화된 도형이 포함된 빈 Word 문서 만들기

여러 도형을 하나의 단위로 배치한 **빈 Word 문서**를 만들어야 할 경우, 이 튜토리얼에서 정확한 방법을 보여드립니다. **도형 그룹화** 방법, 크기 조정, 그리고 Aspose.Words for Java를 사용한 **Word에 도형 추가**를 시연하는 완전한 실행 예제를 확인할 수 있습니다.

프로젝트 설정부터 최종 .docx 파일 저장까지 모든 단계를 자세히 안내하므로 코드를 그대로 복사해 자신의 애플리케이션에 적용할 수 있습니다. 외부 참조는 필요 없으며, 솔루션은 Aspose.Words 23.9 이상에서 동작합니다.

## 전제 조건

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 (또는 지원되는 JDK)
* Maven 또는 Gradle (의존성 관리용)
* Aspose.Words for Java 라이선스 (또는 임시 평가 키)
* 알려진 디렉터리에 위치한 샘플 이미지 파일 (예: `sample.jpg`)

위 항목 중 누락된 것이 있다면 먼저 설치하세요; 나머지 튜토리얼은 환경이 준비되었다는 전제하에 진행됩니다.

## 1단계: 프로젝트에 Aspose.Words 추가

`pom.xml` (Maven) 또는 `build.gradle` (Gradle)에 Aspose.Words 의존성을 추가합니다. 이 라이브러리는 이후에 사용할 `Document`, `DocumentBuilder`, `GroupShape`, `Shape` 클래스를 제공합니다.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**왜 중요한가:** 라이브러리가 없으면 Word‑처리 API를 사용할 수 없으며, 프로그래밍 방식으로 **빈 Word 문서**를 **생성**할 수 없습니다.

## 2단계: 빈 Word 문서 만들기

첫 번째 실질적인 작업은 메모리 상의 **빈 Word 문서**를 나타내는 `Document` 객체를 인스턴스화하는 것입니다.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`*는 기본 설정(A4 페이지, 기본 여백)으로 **빈 Word 문서**를 생성합니다. 함께 제공되는 `DocumentBuilder`를 사용하면 현재 커서 위치에 콘텐츠를 삽입할 수 있습니다.

## 3단계: 그룹 도형 삽입 (도형 그룹화 방법)

*그룹 도형*은 다른 도형들을 담는 컨테이너 역할을 합니다. 이 단계에서는 **도형을 그룹화**하여 함께 이동하도록 하는 방법을 배웁니다.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

`insertGroupShape` 메서드는 빌더의 커서 위치에 컨테이너를 배치합니다. 여러 그림을 하나의 엔터티로 취급하고 싶을 때 그룹화는 필수이며, 이는 **그룹 도형 Word** 기능의 핵심입니다.

## 4단계: 사각형 만들고 크기 설정

이제 그룹에 사각형을 추가합니다. 이는 **도형 크기 설정**을 보여주며, 정확한 레이아웃을 위해 필요합니다.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*왜 차원을 설정하나요?* `setWidth`와 `setHeight`를 명시적으로 호출하면 문서의 기본 도형 스타일에 관계없이 사각형이 정확히 원하는 크기로 표시됩니다.

## 5단계: 이미지 삽입 및 그룹에 추가

이미지를 추가하면 **Word에 도형 추가**의 또 다른 일반적인 사용 사례를 확인할 수 있습니다. 이미지 역시 같은 그룹에 포함되어 사각형과 함께 이동합니다.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

이미지 파일이 없으면 Aspose.Words가 예외를 발생시킵니다. 실용적인 팁은 미리 경로를 확인하는 것입니다:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## 6단계: 그룹화된 도형이 포함된 문서 저장

마지막으로 **빈 Word 문서**(이제 그룹화된 도형이 포함됨)를 디스크에 저장합니다.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

`GroupShapeDemo.docx`를 Microsoft Word에서 열면 사각형과 이미지가 포함된 단일 그룹 객체가 보입니다. 그룹의 어느 부분을 선택해도 전체 컨테이너가 이동하여 도형이 올바르게 **그룹화**되었음을 확인할 수 있습니다.

### 예상 출력

* 지정된 디렉터리에 `GroupShapeDemo.docx` 파일이 생성됩니다.
* 파일을 열면 300 × 200 포인트 컨테이너 안에 다음이 표시됩니다:
  * (20, 20) 위치에 100 × 50 포인트 사각형
  * 같은 컨테이너 안 (150, 30) 위치에 이미지

## 엣지 케이스 및 변형

| 상황 | 처리 방법 |
|-----------|-----------------|
| **다른 페이지 크기** | 그룹을 삽입하기 전에 `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` 를 호출합니다. |
| **여러 그룹** | 새 `GroupShape` 인스턴스로 3‑5단계를 반복합니다; 각 그룹은 독립적으로 배치할 수 있습니다. |
| **도형 회전** | 그룹에 추가하기 전에 `shape.setRotationAngle(45.0);` 로 사각형이나 그림을 회전합니다. |
| **이미지가 아닌 도형** | `ShapeType.ELLIPSE`, `ShapeType.LINE` 등 타입의 `Shape` 객체를 생성하고 사각형과 동일하게 추가합니다. |
| **큰 이미지** | `picture.setWidth(80.0); picture.setHeight(60.0);` 로 크기를 조정해 그룹이 원래 경계를 넘지 않게 합니다. |

이러한 변형을 통해 핵심 패턴을 다양한 문서 생성 시나리오에 적용할 수 있습니다.

## 실전 팁

* **프로 팁:** 그룹을 페이지에 고정하고 싶다면 `RelativeHorizontalPosition`과 `RelativeVerticalPosition`을 각각 `RelativeHorizontalPosition.PAGE`, `RelativeVerticalPosition.PAGE` 로 설정합니다.
* **주의점:** 그룹 크기를 초과하는 도형을 추가하면 Word에서 해당 도형이 잘려 보입니다. `group.setWidth()`와 `group.setHeight()` 로 그룹 크기를 적절히 조정하세요.
* **성능 참고:** 루프에서 다수의 문서를 생성할 경우, 단일 `DocumentBuilder` 인스턴스를 재사용하고 `doc.clone()`을 호출해 객체 생성 오버헤드를 줄입니다.

## 결론

이제 Aspose.Words for Java를 사용해 **그룹화된 도형 컬렉션**이 포함된 **빈 Word 문서**를 **생성**하는 방법을 알게 되었습니다. 라이브러리 설정, 문서 생성, 그룹 삽입, **도형 크기 설정**, **Word에 도형 추가**, 저장까지 전체 워크플로를 다루었습니다.

다음 단계에서는 차트 그룹화, 개별 도형 스타일 적용, PDF로 내보내기 등 고급 기능을 탐색해 보세요. 이 모든 주제는 본 가이드에서 시연한 원리를 기반으로 합니다.

---


## 다음에 배워야 할 내용은?


아래 튜토리얼은 본 가이드에서 시연한 기술을 확장하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하므로, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}