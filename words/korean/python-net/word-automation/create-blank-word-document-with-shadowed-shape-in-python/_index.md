---
category: general
date: 2026-10-16
description: Python을 이용해 빈 Word 문서를 생성하고, Word에 도형을 삽입한 뒤 외부 그림자를 적용하여 PDF로 저장합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: ko
lastmod: 2026-10-16
og_description: Aspose.Words for Python을 사용하여 외부 그림자 모양이 있는 빈 Word 문서를 만듭니다. 이 가이드는
  모양을 삽입하고 그림자를 적용한 다음 파일을 PDF로 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: 쉐도우가 적용된 빈 Word 문서 만들기 – Python 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Python으로 그림자 모양이 있는 빈 Word 문서 만들기
url: /ko/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python에서 그림자 효과가 있는 도형으로 빈 Word 문서 만들기

빈 Word 문서를 **생성**하고 사용자 지정 그래픽을 추가해야 하는 경우, 이 가이드가 해결책을 제공합니다. **Word에 도형 삽입**, **외부 그림자 도형 적용**, 그리고 마지막으로 **Python을 사용해 PDF로 저장**하는 과정을 단계별로 안내합니다.

Aspose.Words for Python 설정 방법, 사각형 만들기, 그림자 스타일 지정, 시각 효과를 유지한 PDF 생성까지 배울 수 있습니다. Aspose API 사용 경험이 없어도 괜찮으며, 기본적인 Python 지식과 Python 3.10 이상 설치가 필요합니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Python 3.10 이상 설치
* 활성화된 Aspose.Words for Python 라이선스(평가용 무료 체험 가능)
* `aspose-words` 패키지를 설치할 수 있는 `pip` 접근 권한
* PDF가 저장될 디렉터리에 대한 쓰기 권한

다음 한 줄 명령으로 라이브러리를 설치할 수 있습니다:

```bash
pip install aspose-words
```

## Create blank Word document – environment setup

첫 번째 단계는 도형을 배치할 캔버스로 사용할 빈 Word 파일을 만드는 것입니다.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()`는 완전히 빈 Word 파일을 나타냅니다. `DocumentBuilder`를 사용하면 `insert_shape`와 같은 메서드에 접근할 수 있으며, 이는 다음 단계에서 활용됩니다.

## Insert shape in Word and set dimensions

이제 나중에 외부 그림자를 적용할 사각형을 추가합니다. 크기는 포인트 단위로 지정됩니다(1 pt ≈ 1/72 인치).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape` 호출은 추가 커스터마이징이 가능한 `Shape` 객체를 반환합니다. 이 시점에서 문서를 Microsoft Word에서 열면 이미 보이는 사각형이 포함되어 있습니다.

## Add outer shadow shape – customizing the effect

Aspose.Words는 그림자 스타일, 블러, 거리, 색상 등을 정의할 수 있는 `ShadowEffect` 클래스를 제공합니다.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

`style`을 `OUTER`로 설정하면 그림자가 사각형 테두리 바깥쪽에 표시되어 미묘한 3‑D 효과를 줍니다. `blur`와 `distance` 값을 조정해 그림자를 더 촘촘하게 혹은 부드럽게 만들 수 있습니다.

## Save as PDF python – finalizing the document

도형 스타일링이 끝나면 문서를 바로 PDF로 저장할 수 있습니다. Aspose.Words가 내부적으로 변환을 처리해 그림자 효과를 그대로 유지합니다.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`shape_with_shadow.pdf`를 어떤 PDF 뷰어에서 열어도 Word에서 보였던 그대로의 외부 그림자 사각형을 확인할 수 있습니다.

## Full working example

아래는 모든 단계를 하나로 합친 전체 스크립트입니다. `create_word_with_shadow.py`라는 파일에 복사한 뒤 실행하세요.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Expected output**

스크립트를 실행하면 확인 메시지가 출력됩니다(예시):

```
PDF generated at: output/shape_with_shadow.pdf
```

생성된 PDF를 열면 200 pt × 100 pt 크기의 사각형에 부드러운 검은색 외부 그림자가 적용된 단일 페이지가 표시됩니다.

## Common variations and edge cases

* **그림자 색상 변경** – `aw.Color.black`을 `aw.Color.red` 또는 `aw.Color.from_argb(255, 0, 120, 215)`와 같은 다른 `aw.Color` 값으로 교체합니다.
* **다른 도형 사용** – `aw.drawing.ShapeType.RECTANGLE`을 `OVAL`, `DIAMOND` 등 지원되는 열거형 값으로 바꿉니다.
* **PDF 대신 DOCX 저장** – `doc.save("output/shape.docx")`를 호출해 Word 형식으로 저장합니다.
* **여러 도형** – `builder.insert_shape`를 다시 호출해 추가 도형을 만들 수 있으며, 각 도형마다 독립적인 `ShadowEffect`를 지정할 수 있습니다.

**Pro tip:** 도형을 특정 위치에 배치해야 할 경우, 삽입 후 `rectangle.left`와 `rectangle.top`을 설정하면 픽셀 단위의 정밀한 위치 조정이 가능합니다.

## Conclusion

이제 **빈 Word 문서 생성**, **Word에 도형 삽입**, **외부 그림자 도형 추가**, 그리고 **Python을 사용해 PDF로 저장**하는 전체 흐름을 이해했습니다. 완전한 코드 샘플은 엔드‑투‑엔드 워크플로우를 보여주며, 각 API 호출이 왜 필요한지 설명합니다.

앞으로 더 고급 스타일 옵션을 탐색하고, 도형 안에 텍스트를 넣거나 여러 도형을 결합해 복잡한 다이어그램을 만들 수 있습니다. 다양한 그림자 파라미터를 실험해 브랜드에 맞는 시각적 표현을 구현하고, 이 방식을 대규모 문서 생성 파이프라인에 통합해 보세요.

Happy coding!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 관련 주제를 심도 있게 다룹니다. 각 자료에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}