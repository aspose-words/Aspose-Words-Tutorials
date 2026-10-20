---
category: general
date: 2026-10-20
description: Aspose.Words for Java에서 도형을 그룹화하는 방법 – 사각형 도형을 삽입하고, 그룹화하며, 문서를 저장하는
  방법을 한 가이드에서 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: ko
lastmod: 2026-10-20
og_description: Aspose.Words for Java에서 도형을 그룹화하는 방법. 이 튜토리얼에서는 사각형 도형을 삽입하고, 그룹화한
  뒤, 결과를 내보내는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Aspose.Words for Java에서 도형을 그룹화하는 방법 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Aspose.Words for Java에서 도형을 그룹화하는 방법
url: /ko/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 도형을 그룹화하는 방법

Word 문서에서 Aspose.Words for Java를 사용해 **도형을 그룹화하는 방법**이 필요하다면, 이 가이드는 전체 워크플로를 보여줍니다. **사각형 도형 삽입**, 두 번째 사각형 추가, 두 도형을 그룹화하고 최종적으로 파일을 저장하는 과정을 명확한 실행 가능한 코드와 함께 배울 수 있습니다.

도형을 그룹화하면 여러 그림을 하나의 단위로 이동, 회전 또는 스타일링할 수 있어 편리합니다. 보고서 템플릿, 다이어그램, 맞춤형 전단지를 만들 때 그룹화를 마스터하면 시간을 절약하고 레이아웃 일관성을 유지할 수 있습니다.

이 튜토리얼에서 배우게 될 내용:

* 새 `Document`와 `DocumentBuilder`를 생성합니다.
* 정확한 크기의 **사각형 도형 삽입** 방법.
* 사각형을 `GroupShape`에 그룹화합니다.
* 문서를 저장하고 결과를 확인합니다.

> **전제 조건** – 프로젝트에 Aspose.Words for Java(v23.12 이상)가 추가되어 있어야 합니다. Maven 사용자는 아래 의존성을 포함하면 됩니다.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## 준비 사항

| 항목 | 이유 |
|------|------|
| Java 17+ | 최신 언어 기능 및 향상된 성능 |
| Aspose.Words for Java | `DocumentBuilder`, `Shape`, `GroupShape` API 제공 |
| IDE (IntelliJ IDEA, Eclipse, VS Code 등) | 예제 컴파일 및 실행 |
| 폴더에 대한 쓰기 권한 | 문서를 디스크에 저장하기 위해 필요 |

---

## 사각형 도형 삽입 방법

첫 번째 단계는 `Document`와 `DocumentBuilder`를 만드는 것입니다. 빌더를 사용하면 `insertShape`와 같은 메서드로 그림 객체를 배치할 수 있습니다.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **왜 중요한가** – `insertShape`를 사용하는 것이 Aspose.Words에서 **사각형 도형 삽입**의 표준 방법입니다. 이 메서드는 도형을 현재 단락에 자동으로 추가하므로 저수준 OpenXML을 직접 관리할 필요가 없습니다.

---

## 사각형 위치 조정 (선택 사항)

두 번째 사각형을 첫 번째 사각형에 상대적인 맞춤 위치에 두고 싶다면 `left`와 `top` 속성을 수정하면 됩니다. 이 단계는 선택 사항이지만 정밀한 다이어그램 레이아웃을 위해 자주 필요합니다.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **팁**: 모든 측정값은 포인트(1 pt ≈ 1/72 in) 단위입니다. UI 기반 계산에 픽셀 값이 필요하면 `convertPointsToPixels`를 사용하세요.

---

## 도형 그룹화 방법

이제 사각형이 준비되었으니 `GroupShape` 안에 넣을 수 있습니다. 그룹화하면 두 사각형이 하나의 객체처럼 동작하여 이동, 회전 또는 서식 지정이 동시에 적용됩니다.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **그룹화가 작동하는 이유** – `GroupShape`는 `Shape`를 상속하므로 그룹을 다른 그림 객체와 동일하게 취급할 수 있습니다. `appendChild`를 호출하면 도형이 원래 위치에서 제거되고 그룹의 자식이 됩니다.

---

## 그룹화된 도형이 포함된 문서 저장

마지막으로 문서를 디스크에 기록합니다. 파일에는 두 개의 사각형이 들어 있는 단일 `GroupShape`가 포함됩니다.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 예상 결과

Microsoft Word에서 `GroupShape.docx`를 열면:

* 나란히 배치된 파란색과 초록색 두 사각형이 보입니다.
* 어느 하나의 사각형을 선택하면 전체 그룹이 선택되어 함께 드래그하면 두 도형이 동시에 이동합니다.
* 그룹에 얇은 빨간색 테두리가 표시되어 `GroupShape` 속성이 적용된 것을 확인할 수 있습니다.

그룹을 오른쪽 클릭하고 **Group → Ungroup**을 선택하면 사각형이 독립적인 도형으로 돌아가며, 그룹화 작업이 되돌릴 수 있음을 보여줍니다.

---

## 일반적인 변형 및 예외 상황

| 상황 | 처리 방법 |
|------|-----------|
| **두 개 이상 도형** | 각 도형을 삽입한 뒤 모두 같은 `GroupShape`에 `appendChild`합니다. |
| **다른 도형 유형** (예: 타원, 그림) | `builder.insertShape(ShapeType.ELLIPSE, …)` 또는 `builder.insertImage(...)`를 사용한 뒤 그룹에 추가합니다. |
| **그룹 크기 조정** | `group.setWidth(newWidth)` 또는 `group.setHeight(newHeight)`를 호출하면 자식이 비례해서 스케일됩니다. |
| **그룹 회전** | `group.setRotationAngle(45);`를 사용하면 전체 컬렉션이 중심을 기준으로 회전합니다. |
| **원래 위치 보존** | 그룹화 전에 각 도형의 `left`/`top` 값을 저장하고, 필요 시 언그룹 후 복원합니다. |

---

## 전체 실행 가능한 예제

아래는 IDE에 복사‑붙여넣기 할 수 있는 완전한 Java 클래스입니다. 모든 import, 오류 처리 및 설명 주석이 포함되어 있습니다.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

프로그램을 실행하고 결과물인 `GroupShape.docx`를 열면 설명한 대로 그룹화된 사각형을 확인할 수 있습니다.

---

## 결론

이제 Aspose.Words for Java에서 **도형을 그룹화하는 방법**을 알게 되었습니다. 문서 생성 → 사각형 도형 삽입 → 위치 조정 → `GroupShape`로 그룹화까지의 전체 흐름을 익혔으니, 여러 그림을 하나의 엔터티로 다루어 레이아웃 조정과 시각적 일관성을 간편하게 유지할 수 있습니다.

**다음 단계**

* 다양한 채우기 패턴이나 테두리를 가진 **사각형 도형 삽입**을 탐색하세요.
* 텍스트 상자와 결합해 라벨이 있는 다이어그램을 만들어 보세요.
* 그룹을 회전하거나 스케일링해 보다 복잡한 그래픽을 구현해 보세요.

코드를 다른 도형 유형, 더 큰 그룹, 동적 문서 생성 시나리오에 맞게 자유롭게 변형해 보세요. 즐거운 코딩 되세요!


## 다음에 배울 내용은 무엇인가요?


다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 관련 주제를 깊이 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}