---
category: general
date: 2026-09-30
description: Aspose.Words for Python을 사용하여 사각형 모양을 만들고, 모양에 그림자를 적용하며, 모양이 포함된 Word
  문서를 저장하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: ko
lastmod: 2026-09-30
og_description: Word 문서에 사각형 도형을 빠르게 만들기. 이 튜토리얼에서는 도형을 추가하고, 도형에 그림자를 적용하며, 그림자 흐림을
  설정하고, 도형이 포함된 Word 파일을 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Python으로 Word에서 사각형 도형 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Python을 사용하여 Word 문서에 사각형 도형 만들기
url: /ko/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python을 사용하여 Word 문서에 사각형 도형 만들기

Word 파일에 **사각형 도형**을 만들어야 한다면, 이 가이드는 완전하고 실행 가능한 솔루션을 제공합니다. 도형을 추가하고, 그림자 효과를 적용하고, 블러를 조정한 뒤 **도형이 포함된 Word 저장** 방법을 보여줍니다. 결과 파일은 Microsoft Word 또는 호환 뷰어에서 열 수 있습니다.

예제는 **Aspose.Words for Python via .NET**를 사용합니다. 이 라이브러리를 통해 Microsoft Office 없이 Word 문서를 조작할 수 있습니다. API 사용 경험이 없어도 기본적인 Python 지식만 있으면 됩니다.

## 달성할 내용

- 새 문서의 첫 번째 섹션에 사각형을 삽입합니다.  
- 블러, 오프셋, 색상을 설정하여 부드러운 그림자를 구성합니다.  
- 문서를 디스크에 저장하고 시각적 결과를 확인합니다.

## 사전 요구 사항

- Python 3.8 이상.  
- `aspose-words` 패키지 설치 (`pip install aspose-words`).  
- 출력 디렉터리에 대한 쓰기 권한.

## 사각형 도형 생성 및 외관 설정

첫 번째 단계는 빈 문서를 인스턴스화하고 그 안에 사각형 도형을 추가하는 것입니다. 이 도형이 그림자 효과의 캔버스 역할을 합니다.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**왜 중요한가:**  
사각형을 만들면 나중에 스타일을 적용할 수 있는 구체적인 객체(`shape`)가 생깁니다. 명시적인 크기를 지정하면 모든 플랫폼에서 도형이 동일하게 보입니다.

## Word 문서에 도형 추가하기

위 코드가 이미 사각형을 추가하지만, 이후에 원형이나 화살표 등 다른 도형을 추가해야 할 수도 있습니다. 동일한 패턴을 사용합니다: 문서 본문에 `append_child`를 호출하고 원하는 `ShapeType`을 전달합니다.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**팁:** `ShapeType` 열거형을 사용해 지원되는 모든 도형을 탐색하세요. 이렇게 하면 코드 가독성이 높아지고 매직 넘버를 피할 수 있습니다.

## 도형에 그림자 적용 및 그림자 블러 설정

그림자는 깊이감과 시각적 흥미를 더합니다. `ShadowEffect` 클래스를 사용하면 블러, 오프셋, 색상을 제어할 수 있습니다. 아래 예제에서는 사각형에 부드러운 검은색 그림자를 적용합니다.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**왜 블러를 설정하나요?**  
`blur`는 그림자가 얼마나 퍼지는지를 결정합니다. 낮은 값(예: 1.0)은 선명한 가장자리를 만들고, 높은 값(예: 5.0)은 부드러운 페이드 효과를 제공해 시각적으로 더 아름답습니다.

**예외 상황:** `blur`를 0으로 설정하면 그림자가 실루엣처럼 고형이 됩니다. 일부 뷰어에서는 앨리어싱 아티팩트가 발생할 수 있으니, 부드러운 출력을 위해 0보다 큰 값을 선택하세요.

## 도형이 포함된 Word 저장

문서를 저장하면 모든 변경 사항이 최종화됩니다. `save` 메서드는 현대적인 워드 프로세서가 열 수 있는 `.docx` 파일을 작성합니다.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`output.docx`를 열면 사각형이 왼쪽 위 모서리에서 1인치 떨어진 위치에 배치되고, 오른쪽과 아래로 각각 2포인트 이동된 부드러운 검은색 그림자가 적용된 것을 확인할 수 있습니다. 그림자의 블러 덕분에 도형이 페이지에서 떠 있는 듯한 느낌을 줍니다.

**프로 팁:** 루프에서 다수의 문서를 생성해야 한다면 동일한 `Document` 인스턴스를 재사용하고 반복마다 본문을 비워 메모리 사용량을 줄이세요.

## 일반적인 변형 및 문제 해결

| 상황 | 변경 내용 | 이유 |
|-----------|----------------|--------|
| 다른 그림자 색상 | `shadow.color = aw.Color.red` | 브랜드 색상 사용 또는 중요한 도형 강조 |
| 더 큰 그림자 오프셋 | `shadow.offset_x`/`offset_y` 증가 | UI 목업에서 깊이감 강조 |
| 그림자 없이 | `shape.shadow = shadow` 라인 삭제 | 미니멀리스트 보고서에 적합 |
| DOCX 대신 PDF로 내보내기 | `doc.save("output.pdf")` | 읽기 전용 배포에 PDF가 이상적 |

도형이 보이지 않을 경우, 올바른 섹션(`get_first_section()`)에 추가했는지와 수정 후 문서를 저장했는지 확인하세요.

## 전체 실행 가능한 예제

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

스크립트를 실행하면 부드러운 그림자가 적용된 사각형이 포함된 `output.docx`가 생성됩니다. Microsoft Word에서 파일을 열어 시각 효과가 설명과 일치하는지 확인하세요.

## 결론

이제 **사각형 도형 만들기**, **Word 문서에 도형 추가하기**, **도형에 그림자 적용하기**, **그림자 블러 설정하기**, 그리고 **도형이 포함된 Word 저장하기**를 Aspose.Words for Python을 사용해 수행하는 방법을 알게 되었습니다. 동일한 패턴을 다른 도형 유형, 색상, 효과에도 확장할 수 있어 Office 자동화에 의존하지 않고 문서 그래픽을 완벽히 제어할 수 있습니다.

**다음 단계**

- `Shape.fill`을 사용해 그라디언트 또는 이미지 배경을 추가해 보세요.  
- `Paragraph` 객체를 이용해 사각형 안에 텍스트를 배치하세요.  
- 여러 도형을 결합해 복잡한 다이어그램을 만든 뒤 PDF로 내보내 배포하세요.  

코드를 자신의 보고서나 템플릿에 맞게 자유롭게 변형하고, 결과를 댓글에 공유해 주세요!

## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}