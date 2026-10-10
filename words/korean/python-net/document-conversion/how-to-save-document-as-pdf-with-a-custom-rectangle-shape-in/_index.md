---
category: general
date: 2026-10-07
description: Aspose.Words for Python을 사용하여 사각형 모양과 사용자 지정 그림자를 추가하면서 문서를 PDF로 저장하는
  방법을 배웁니다. 단계별 코드가 포함되어 있습니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: ko
lastmod: 2026-10-07
og_description: Aspose.Words for Python을 사용하여 사용자 정의 사각형 모양으로 문서를 PDF로 저장합니다. 그리기,
  스타일 지정 및 Word를 PDF로 내보내는 전체 예제를 따라 보세요.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: 문서를 사각형 모양으로 PDF에 저장 – 완전한 파이썬 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Python에서 사용자 지정 사각형 모양으로 문서를 PDF로 저장하는 방법
url: /ko/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python에서 사용자 정의 사각형 모양으로 문서를 PDF로 저장하는 방법

맞춤 그래픽을 추가하면서 **save document as PDF**가 필요하다면, 이 가이드가 방법을 보여줍니다. 빈 Word 파일을 만들고, **drawing a rectangle shape**을 그리고, 크기를 설정하고, 보이는 그림자를 적용한 뒤, 마지막으로 Aspose.Words for Python 라이브러리를 사용해 **export Word to PDF**를 수행하는 과정을 단계별로 안내합니다.

여러분은 보고서, 청구서 또는 모든 문서 자동화 시나리오에 적합한 완벽하게 배치된 사각형이 포함된 PDF를 얻게 됩니다. 외부 도구는 필요 없으며, Python과 Aspose.Words 패키지만 있으면 됩니다.

## 필요 사항

| 요건 | 중요한 이유 |
|------|--------------|
| Python 3.8+ | Aspose.Words for Python API는 최신 인터프리터를 대상으로 합니다. |
| `aspose-words` package (`pip install aspose-words`) | `aw` 네임스페이스를 코드 예제에서 사용하도록 제공합니다. |
| Basic familiarity with Python and object‑oriented programming | 튜토리얼에서는 `Document`와 `Shape` 같은 객체를 조작합니다. |
| Write permission to a folder where the PDF will be saved | `save document as pdf` 단계에서 파일을 디스크에 씁니다. |

> **Pro tip:** 의존성을 격리하기 위해 가상 환경(`python -m venv venv`)을 사용하세요.

## 사각형 모양으로 문서를 PDF로 저장하는 방법

아래는 완전하고 실행 가능한 예제입니다. 각 단계마다 **왜** 해당 작업을 수행하는지, **무엇을** 하는지 설명합니다.

### 단계 1: 새 빈 문서 초기화

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

`Document` 객체를 새로 생성하면 깨끗한 페이지 컬렉션을 얻을 수 있습니다. 나중에 **export Word to PDF**를 원한다면 기존 *.docx* 파일을 로드할 수도 있지만, 빈 상태에서 시작하면 예제가 집중됩니다.

### 단계 2: 문서에 사각형 모양 추가

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape` 단계에서는 `ShapeType.RECTANGLE`을 사용합니다. 모양을 단락에 추가하면 Aspose.Words가 최종 PDF에서 어디에 렌더링할지 알게 됩니다.

### 단계 3: 사각형 크기 설정

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

명시적인 **rectangle dimensions**를 설정하면 플랫폼 간에 모양이 일관되게 보장됩니다. 인치 단위를 선호한다면 `convert_to_inches` 도우미를 사용할 수도 있습니다.

### 단계 4: (선택) 보이는 사용자 정의 그림자 적용

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

그림자는 PDF에서 사각형을 돋보이게 합니다. `shadow.visible` 플래그가 필요하며, 이 플래그가 없으면 다른 속성은 효과가 없습니다.

### 단계 5: 문서를 PDF로 저장

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

`document.save`를 **.pdf** 확장자로 호출하면 Aspose.Words의 내장 PDF 렌더러를 사용해 자동으로 **save document as pdf**가 수행됩니다. 추가 변환 단계가 필요 없으며, 따라서 이 방법이 **export Word to PDF**에 권장되는 방식입니다.

> **Why this works:** Aspose.Words는 사각형과 그림자를 포함한 문서 레이아웃을 PDF 스트림에 직접 기록합니다. 이 과정은 무손실이며 벡터 품질을 유지합니다.

## 전체 소스 코드 (단일 스크립트)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

이 스크립트를 실행하면 다음과 같은 `shadow_rectangle.pdf`가 생성됩니다:

![PDF 저장 후 사각형 모양을 보여주는 생성된 PDF 다이어그램](placeholder-image.png)

*PDF는 문서 중앙에 검은 그림자 사각형이 있는 단일 페이지를 포함합니다.*

## 일반적인 질문 및 엣지 케이스

| 질문 | 답변 |
|------|------|
| **특정 위치에 사각형을 배치할 수 있나요?** | 예. 저장하기 전에 `rectangle.left`와 `rectangle.top`을 (포인트 단위) 설정하면 됩니다. |
| **여러 개의 모양이 필요하면 어떻게 하나요?** | 추가 `Shape` 객체를 만들고 각각을 구성한 뒤, 동일하거나 다른 단락에 추가하면 됩니다. |
| **그림자가 PDF 크기에 영향을 줍니까?** | 거의 영향을 주지 않습니다; 그림자는 래스터 이미지가 아니라 벡터 메타데이터로 저장됩니다. |
| **기존 *.docx* 파일을 변환하는 데 사용할 수 있나요?** | 물론 가능합니다. `aw.Document()`를 `aw.Document("input.docx")`로 교체하면 나머지 단계는 그대로 유지됩니다. |
| **사각형의 채우기 색을 변경할 수 있나요?** | `rectangle.fill_color = aw.drawing.Color.light_blue`(또는 원하는 `Color`로) 설정합니다. |

## 다음 단계

이제 **save document as PDF**를 사용자 정의 사각형과 함께 수행하는 방법을 알았으니, 다음을 탐색해 볼 수 있습니다:

* **Export Word to PDF**에 헤더, 푸터 및 페이지 번호 포함.  
* 동일한 `Shape` 클래스를 사용해 다른 그리기 객체(`Ellipse`, `Polygon`) 추가.  
* Word 파일이 들어 있는 폴더를 **Batch process**하여 각 파일에 동일한 사각형 오버레이 적용.  

이러한 확장은 동일한 패턴을 따릅니다: 모양을 만들고, 속성을 구성한 뒤 **save document as pdf**를 수행합니다.

---

**Summary:** 이 튜토리얼에서는 Aspose.Words for Python을 사용해 **save document as PDF**하면서 **add rectangle shape**, **set rectangle dimensions**를 수행하고 사용자 정의 그림자를 적용하는 방법을 보여주었습니다. 전체 스크립트는 복사하고 실행하여 자체 문서 자동화 파이프라인에 맞게 적용할 준비가 되어 있습니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [사각형 모양 만들기, 그림자 추가 및 PDF 저장](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words로 PDF에 사각형 추가 – 단계별 가이드](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Aspose.Words로 문서를 PDF로 저장 – 완전한 C# 가이드](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}