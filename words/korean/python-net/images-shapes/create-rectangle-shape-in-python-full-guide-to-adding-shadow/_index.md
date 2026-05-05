---
category: general
date: 2026-05-04
description: Aspose.Words for Python를 사용하여 사각형 도형을 만드는 방법, 그림자가 있는 도형을 추가하는 방법, 그림자
  색상을 변경하는 방법, 그림자 거리를 설정하는 방법 및 문서를 PDF로 저장하는 방법을 배웁니다.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: ko
og_description: Aspose.Words for Python을 사용하여 사각형 모양을 만들고, 모양 추가, 그림자 색상 변경, 그림자 거리
  설정 방법을 배우며, 문서를 PDF로 저장합니다.
og_title: 사각형 만들기 – 그림자 추가, 색상 변경 및 PDF로 저장
tags:
- Aspose.Words
- Python
- PDF generation
title: Python에서 사각형 모양 만들기 – 그림자 추가 및 PDF 저장 완전 가이드
url: /ko/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 직사각형 모양 만들기 – 파이썬 개발자를 위한 완전 튜토리얼

워드 문서에서 **직사각형 모양 만들기**가 필요했으며, 어떻게 하면 세련된 그림자를 줄 수 있을지 궁금했던 적이 있나요? 보고서 생성기를 만들고 최종 출력이 PDF인 경우 시각적 완성도가 중요할 수 있습니다. 좋은 소식은? Aspose.Words for Python을 사용하면 **shape 추가 방법**뿐만 아니라 색상부터 거리까지 모든 그림자 속성을 조정하고, **문서를 PDF로 저장**까지 한 번에 할 수 있다는 것입니다.

이 가이드에서는 전체 과정을 단계별로 자세히 살펴봅니다. 복사‑붙여넣기 할 수 있는 정확한 코드를 확인하고, 각 줄이 왜 중요한지 *왜* 이해하며, 투명 그림자나 비표준 DPI와 같은 엣지 케이스를 처리하기 위한 몇 가지 팁을 얻을 수 있습니다. 끝까지 읽으면 **직사각형 모양 만들기**, 그림자 커스터마이징, 그리고 땀 한 방울 없이 선명한 PDF 내보내기를 할 수 있게 됩니다.

## Prerequisites

- Python 3.8+이 머신에 설치되어 있어야 합니다.  
- `pip install aspose-words`를 통해 Aspose.Words for Python을 설치합니다.  
- 객체 지향 파이썬에 대한 기본적인 이해 (특별한 지식은 필요 없음).  

이미 가상 환경을 설정해 두었다면 설치 명령을 실행하기만 하면 바로 시작할 수 있습니다.

## Step 1: Initialise the Document and Builder

**shape 추가 방법**을 사용하기 전에 작업할 빈 문서가 필요합니다. `Document` 클래스는 전체 파일을 나타내고, `DocumentBuilder`는 여러분의 페인트 브러시 역할을 합니다.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Why this matters:* `Document`는 모든 섹션, 페이지 및 리소스를 보관합니다. `DocumentBuilder`는 필요한 정확한 위치에 콘텐츠를 삽입할 수 있는 유창한 API를 제공하는데, 마치 워드 프로세서의 커서와 같습니다.

## Step 2: Insert the Rectangle Shape

이제 실제로 **shape 추가 방법**을 수행합니다. `insert_shape` 메서드는 도형 유형과 크기(포인트)를 필요로 합니다. 여기서는 200 × 100 pt 직사각형을 선택하고 연한 파란색 채우기를 적용합니다.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tip:* 도형을 기존 텍스트와 정렬해야 한다면 삽입 전에 `builder.move_to`를 사용하거나, 생성 후 `left`/`top` 속성을 조정하세요.

## Step 3: Turn the Shadow On

그림자가 없는 도형은 평면적으로 보입니다. **그림자 거리 설정**을 하고 효과를 보이게 하려면 그림자 포맷을 가져와서 활성화합니다.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Why this step:* 그림자 포맷은 별도의 객체이며, `visible`을 토글하는 것이 가장 먼저 해야 할 일입니다. 그렇지 않으면 다른 모든 그림자 속성이 무시됩니다.

## Step 4: Style the Shadow – Colour, Blur, Distance, Direction

마법이 시작되는 부분입니다. **그림자 색상 변경**, 블러 반경 조정, 그림자가 직사각형에서 떨어지는 거리 설정, 그리고 45° 회전을 수행합니다.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explanation of each property:*

| Property | What it does | Typical values |
|----------|--------------|----------------|
| `style` | 그림자가 *inner*인지 *outer*인지 결정합니다. | `OUTER` (가장 일반적) |
| `blur_radius` | 부드러움을 제어합니다; 값이 클수록 가장자리가 흐릿해집니다. | 보통 0–20 px |
| `distance` | 그림자가 도형에서 얼마나 떨어져 있는지 지정합니다. | 미묘하게는 0–10 pt, 강하게는 10 pt 이상 |
| `direction` | 빛의 방향을 나타내며, x축을 기준으로 시계 방향으로 측정합니다. | 0‑360° |
| `color` | 그림자 색조입니다. | 任意 `aw.Color` (예: `gray`, `dark_red`) |

*Edge case:* `distance`를 `0`으로 설정하면 그림자가 도형 바로 아래에 놓여 도형의 채우기가 사실상 가려집니다. 보이는 오프셋을 위해 `0`보다 크게 유지하세요.

## Step 5: Save the Document as a PDF

마지막으로 **문서를 PDF로 저장**합니다. Aspose.Words는 그림자를 자동으로 래스터화하므로 PDF가 워드 뷰와 정확히 동일하게 보입니다.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Why PDF?* PDF는 플랫폼 간 레이아웃을 보존하므로 보고서, 청구서 또는 인쇄 가능한 모든 아티팩트에 이상적입니다.

---

![그림자가 있는 직사각형 모양 만들기](https://example.com/images/rectangle-shadow.png){: .align-center alt="그림자 예시가 있는 직사각형 모양 만들기"}

*위 이미지는 최종 PDF 출력물을 보여줍니다 – 연한 파란색 직사각형에 부드러운 회색 외부 그림자가 적용된 모습이며, 우리가 설정한 대로 정확히 표시됩니다.*

## Common Questions & Variations

### 투명한 그림자가 필요하면 어떻게 하나요?

그림자 색상의 알파 채널을 설정합니다:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### 여러 도형에 동일한 그림자를 적용할 수 있나요?

예. 한 도형에서 `ShadowFormat`을 추출한 뒤 다른 도형에 할당하면 됩니다:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### 다른 도형 유형에 그림자를 바꾸려면 어떻게 하나요?

모든 도형 유형은 동일한 `ShadowFormat` 속성을 공유하므로 같은 설정 블록을 재사용할 수 있습니다—단지 `ShapeType.RECTANGLE`을 `ShapeType.OVAL`, `ShapeType.TRIANGLE` 등으로 교체하면 됩니다.

### 인쇄용 **고해상도 PDF**는 어떻게 만들나요?

`PdfSaveOptions`에 더 높은 DPI를 지정합니다:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Recap

우리는 **직사각형 모양 만들기**, **shape 추가 방법**, 그림자 **색상 커스터마이징**, **그림자 거리 설정**, 그리고 최종적으로 **문서를 PDF로 저장**하는 모든 과정을 다루었습니다. 전체 실행 가능한 스크립트는 다음과 같습니다:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

스크립트를 실행하고 생성된 `ShadowedShape.pdf`를 열면, 섬세한 회색 그림자가 있는 선명한 직사각형을 확인할 수 있습니다—전문적으로 포맷된 보고서에서 기대할 수 있는 바로 그 모습입니다.

## What Next?

- **다른 도형 유형 탐색** (`ShapeType.OVAL`, `ShapeType.LINE`)을 통해 문서를 풍부하게 만들 수 있습니다.  
- **여러 그림자 결합**: 도형을 겹쳐 레이어링하면 내부 그림자와 밝은 색을 사용해 “글로우” 효과도 만들 수 있습니다.  
- **배치 처리 자동화**: 데이터 행 컬렉션을 순회하면서 행당 하나씩 도형을 생성하고, 모든 결과를 하나의 PDF로 병합합니다.  
- **다른 Aspose 라이브러리와 통합** (예: Aspose.Slides)하면 동일한 시각을 파워포인트로도 내보낼 수 있습니다.

실험을 두려워하지 마세요—`blur_radius`를 바꾸고, `direction`을 조정하거나, `gray`를 브랜드 고유 색상으로 교체해 보세요. API가 충분히 유연해 몇 가지 조정만으로도 시각적 효과가 크게 달라집니다.

질문이나 까다로운 상황이 있나요? 아래에 댓글을 남기거나 Aspose 커뮤니티 포럼에 문의하세요. 즐거운 코딩 되시고, 아름답게 그림자가 들어간 직사각형을 마음껏 활용하세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}