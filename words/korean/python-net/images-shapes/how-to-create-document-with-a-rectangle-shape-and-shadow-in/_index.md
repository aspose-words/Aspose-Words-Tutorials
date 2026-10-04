---
category: general
date: 2026-10-04
description: Aspose.Words를 사용하여 Python에서 문서를 만들고 도형에 그림자를 추가하는 방법. 그림자 색상을 설정하고, 사각형
  도형을 삽입하며, 외부 그림자를 사용자 정의하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: ko
lastmod: 2026-10-04
og_description: Python에서 문서를 생성하고 도형에 그림자를 추가하는 방법. 이 가이드는 그림자 색상을 설정하고, 사각형 도형을 삽입하며,
  Aspose.Words를 사용하여 외부 그림자를 적용하는 방법을 보여줍니다.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Python으로 사각형 모양과 그림자가 있는 문서를 만드는 방법
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Python으로 사각형 모양과 그림자가 있는 문서 만들기
url: /ko/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python에서 사각형 모양과 그림자가 있는 문서 만들기

스타일이 적용된 사각형을 포함하는 **문서 만들기**가 필요하다면, 이 가이드는 완전한 솔루션을 제공합니다. **도형에 그림자 추가** 방법, 그림자 색상 설정, 오프셋 및 블러 제어 방법을 Aspose.Words for Python을 사용해 확인할 수 있습니다. 튜토리얼을 마치면 깔끔하고 배포 준비가 된 `.docx` 파일을 생성할 수 있습니다.

아래 단계에서는 라이브러리 설치부터 그림자 모양 맞춤까지 모든 과정을 다룹니다. 외부 문서는 필요 없으며, 코드는 바로 복사·실행·프로젝트에 적용할 수 있도록 준비되어 있습니다. 또한 **사각형 모양 삽입**, **외부 그림자 스타일** 선택, 그림자가 보이지 않거나 랩 설정이 잘못된 경우와 같은 일반적인 함정 처리 방법도 배울 수 있습니다.

## 사전 요구 사항

* Python 3.8 이상이 설치되어 있어야 합니다.
* 활성화된 Aspose.Words for Python 라이선스(또는 무료 평가 키)가 필요합니다.
* Python 스크립팅에 대한 기본적인 이해가 있어야 합니다.
* 생성된 문서를 저장할 파일 시스템 위치에 대한 접근 권한이 있어야 합니다.

pip으로 SDK를 설치할 수 있습니다:

```bash
pip install aspose-words
```

## 단계 1: 라이브러리 가져오기 및 새 빈 문서 만들기

새 문서를 만드는 것은 모든 Word 자동화 시나리오의 첫 번째 작업입니다. `aw.Document()` 생성자는 텍스트, 이미지 또는 도형을 채울 수 있는 빈 파일을 제공합니다.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder` 객체는 콘텐츠 삽입을 단순화합니다. 현재 커서 위치를 추적하므로 섹션을 수동으로 관리하지 않아도 순차적으로 요소를 추가할 수 있습니다.

## 단계 2: 원하는 크기의 사각형 모양 삽입

사각형 모양은 시각적 요소를 담는 컨테이너 역할을 합니다. 너비와 높이를 포인트 단위(1 pt ≈ 1/72 in)로 정의할 수 있습니다.

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

이 시점에서는 도형에 시각적 스타일이 없으므로 단순한 외곽선으로 표시됩니다. 다음 단계에서 깊이와 색상을 부여합니다.

## 단계 3: 도형을 주변 텍스트와 인라인으로 흐르게 설정

도형이 **인라인**이면 단락의 문자처럼 동작합니다. 이를 통해 사각형이 문서 레이아웃에서 기대한 위치에 유지됩니다.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

텍스트 위에 도형을 띄우고 싶다면 `WrapType.SQUARE` 또는 `WrapType.TOP_BOTTOM`을 사용할 수 있지만, 대부분의 보고서에서는 인라인 도형이 레이아웃을 예측 가능하게 유지합니다.

## 단계 4: 그림자를 보이게 하고 색상 선택

보이지 않는 그림자는 시각적 효과가 없습니다. `visible` 플래그가 효과를 활성화하고, `color` 속성이 색조를 결정합니다. 검은색을 사용하면 클래식하고 은은한 깊이를 제공합니다.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

`aw.drawing.Color.black`을 `aw.drawing.Color.gray`와 같은 다른 색상이나 사용자 정의 RGB 값(`aw.drawing.Color.from_argb(255, 128, 128, 128)`)으로 교체할 수 있습니다.

## 단계 5: 그림자의 오프셋과 블러 정의하여 깊이 부여

오프셋은 그림자가 도형에서 얼마나 떨어져 있는지를 제어하고, 블러 반경은 가장자리를 부드럽게 합니다. 작은 값은 선명한 그림자를, 큰 값은 부드러운 그림자를 만듭니다.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

디자인 가이드라인에 맞게 숫자를 실험해 보세요. 강한 드롭 그림자를 원한다면 오프셋과 블러를 모두 늘릴 수 있습니다.

## 단계 6: 외부 그림자 스타일 선택

Aspose.Words는 `INNER`, `OUTER`, `PERSPECTIVE`와 같은 여러 그림자 스타일을 제공합니다. **외부** 스타일은 그림자를 도형 테두리 밖에 배치하므로 깔끔하고 전문적인 외관을 얻을 수 있습니다.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

더 극적인 효과가 필요하면 `ShadowStyle.PERSPECTIVE`를 시도해 보세요—3차원 기울기가 추가됩니다.

## 단계 7: 그림자가 적용된 문서 저장

저장은 파일을 최종화하고 모든 서식을 디스크에 기록합니다. 쓰기 권한이 있는 디렉터리를 선택하고 파일에 설명적인 이름을 지정하세요.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

스크립트를 실행하면 사각형과 보이는 색상 그림자가 포함된 Word 파일이 생성됩니다. Microsoft Word 또는 LibreOffice에서 파일을 열어 결과를 확인하세요.

## 전체 실행 가능한 예제

아래는 논의된 모든 단계를 포함한 완전한 스크립트입니다. 코드를 `create_shadowed_shape.py`라는 파일에 복사하고 `python create_shadowed_shape.py`로 실행하세요.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**예상 출력**

`ShapeWithShadow.docx`를 열면 페이지 중앙에 단일 사각형이 표시됩니다. 사각형은 오른쪽 아래로 약간 오프셋된 은은한 검은색 그림자를 가지고 있으며, 약간 블러 처리되어 깊이가 생깁니다. 그림자는 외부 스타일을 따르므로 사각형 내부와 겹치지 않습니다.

## 일반적인 질문 및 엣지 케이스

### 왜 그림자가 때때로 보이지 않을까요?

그림자는 `shadow.visible`이 `True` **그리고** 도형의 `wrap_type`이 표시를 허용할 때만 렌더링됩니다. 인라인 도형은 안정적으로 작동하지만, 떠 있는 도형은 추가 레이아웃 조정이 필요할 수 있습니다.

### 그림자 색상을 브랜드 팔레트에 맞게 변경하려면 어떻게 해야 하나요?

`aw.drawing.Color.black`을 사용자 정의 RGB 값으로 교체하세요:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### 도형을 텍스트 뒤에 표시하려면 어떻게 해야 하나요?

`WrapType.BEHIND`로 랩 타입을 설정하고 필요에 따라 `z_order_position`을 조정하세요. 일부 뷰어는 텍스트 뒤에 있는 도형을 다르게 렌더링할 수 있다는 점을 유념하세요.

### 동일한 그림자 설정을 여러 도형에 적용할 수 있나요?

예. 그림자를 구성하는 헬퍼 함수를 만들고 삽입하는 각 도형에 호출하면 코드 재사용이 촉진되고 스타일이 일관됩니다.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## 결론

이제 Aspose.Words for Python을 사용해 사각형 모양과 맞춤형 그림자가 포함된 **문서 만들기** 파일을 만드는 방법을 알게 되었습니다. 튜토리얼에서는 사각형 삽입, 인라인 도형 설정, 그림자 활성화, 색상·오프셋·블러·스타일 지정, 그리고 최종 저장까지 다루었습니다.

앞으로는 다른 도형 유형에 대한 **도형에 그림자 추가**, 데이터에 따라 **그림자 색상 설정** 동적 적용, 이미지와 텍스트 상자에 **그림자 추가**와 같은 관련 주제를 탐색할 수 있습니다. 다양한 크기, 색상, 그림자 스타일을 실험해 브랜드 가이드라인이나 디자인 시스템에 맞게 조정해 보세요.

더 많은 Word 문서를 자동화하고 싶나요? 다음에는 표, 머리글, 동적 콘텐츠 추가에 도전해 보세요—각 단계가 여기서 보여준 원칙을 기반으로 합니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방법을 탐색하는 데 도움이 됩니다.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}