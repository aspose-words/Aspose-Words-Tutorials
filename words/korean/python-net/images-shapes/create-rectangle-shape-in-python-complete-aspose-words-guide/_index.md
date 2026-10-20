---
category: general
date: 2026-06-24
description: Aspose.Words를 사용해 Python에서 사각형 모양을 만들고, 모양에 그림자를 추가하고 그림자 각도를 설정하는 방법을
  배우며, 몇 분 안에 문서를 PDF로 저장합니다.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: ko
og_description: Python에서 사각형 모양을 만들고, 모양에 그림자를 추가하고, 그림자 각도를 설정한 뒤 Aspose.Words로 문서를
  PDF로 저장하세요. 단계별 가이드를 따라 보세요.
og_title: Python에서 사각형 도형 만들기 – 전체 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Python에서 사각형 도형 만들기 – 완전한 Aspose.Words 가이드
url: /ko/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python에서 사각형 모양 만들기 – 완전한 Aspose.Words 가이드

Python을 사용해 Word 문서에 **create rectangle shape** 하는 방법이 궁금하셨나요? 굵은 콜아웃 박스가 필요하거나, 다이어그램을 위한 시각적 힌트, 혹은 보고서를 위한 멋진 사각형이 필요할 수도 있습니다. 어떤 경우든, 올바른 곳에 오셨습니다. 이 튜토리얼에서는 사각형 삽입부터 미묘한 그림자 추가, 그림자 각도 조정, 그리고 마지막으로 **save document as PDF**까지 전체 과정을 단계별로 안내합니다.

우리는 **Aspose.Words for Python via .NET**를 사용할 것입니다. 이 강력한 라이브러리를 사용하면 Word 자체를 열지 않고도 Word 파일을 조작할 수 있습니다. 이 가이드를 마치면 *“how to add shape shadow”* 질문에 자신 있게 답할 수 있게 되고, 어떤 프로젝트에든 바로 넣어 사용할 수 있는 실행 준비된 스크립트를 얻게 됩니다.

---

## 필요 사항

- **Python 3.8+**가 머신에 설치되어 있어야 합니다.  
- **Aspose.Words for Python via .NET** (`aspose-words` 패키지). 다음으로 설치합니다:

  ```bash
  pip install aspose-words
  ```

- 생성된 PDF가 저장될 쓰기 가능한 폴더.  
- (선택 사항) IDE 또는 텍스트 편집기—VS Code가 좋습니다.

이것으로 끝입니다. 추가 DLL이나 Office 설치가 필요 없으며, 단일 pip 패키지만 있으면 됩니다.

## 1단계: 문서와 빌더 설정

먼저 해야 할 일은 **create rectangle shape**에 적합한 객체, 즉 `Document`와 `DocumentBuilder`를 만드는 것입니다. 빌더를 당신의 펜이라고 생각하면 됩니다; 모든 것을 그려줍니다.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **왜 중요한가:** `Document` 객체는 전체 .docx 파일을 나타내며, `DocumentBuilder`는 `insert_shape`와 같은 메서드를 제공하여 도형 그리기를 손쉽게 합니다.

## 2단계: 사각형 모양 삽입

이제 빌더가 준비되었으니, 마침내 **create rectangle shape** 할 수 있습니다. `insert_shape` 메서드는 세 개의 인수가 필요합니다: 도형 유형, 너비, 높이. 우리는 비율이 좋은 200 pt 너비와 100 pt 높이를 사용할 것입니다.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

이 시점에서 문서에 **create rectangle shape** 를 성공적으로 수행했습니다. 생성된 DOCX를 열면(나중에 진행), 커서가 있던 위치에 단순한 사각형이 표시됩니다.

## 3단계: 그림자 서식 객체 접근

**add shadow to shape** 하려면 먼저 도형의 그림자 서식을 가져와야 합니다. Aspose.Words의 모든 도형은 그림자와 관련된 모든 설정을 노출하는 `shadow_format` 속성을 가지고 있습니다.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

`shadow` 참조를 갖게 되면 가시성, 흐림, 거리, 각도, 색상 및 투명도를 몇 줄의 코드로 토글할 수 있습니다.

## 4단계: 그림자 활성화 및 외관 설정

여기서 마법이 일어납니다. 우리는 **add shadow to shape** 하고, 약간 흐리게 만들고, 약간 오프셋을 주며, 방향을 설정(**set shadow angle** 부분)하고, 반투명 검은 색을 적용합니다.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **팁:** 더 극적인 효과가 필요하면 `blur_radius`를 늘리거나 `transparency`를 낮추세요. 반대로, `blur_radius = 0` 및 `transparency = 0`으로 날카롭고 완전 불투명한 그림자를 만들 수 있습니다.

## 5단계: 문서를 PDF로 저장

우리는 **create rectangle shape** 를 수행했고, **add shadow to shape** 를 적용했으며, 이제 **save document as PDF** 하여 결과가 모든 장치에서 동일하게 보이도록 합니다. Aspose.Words는 이를 한 줄 코드로 처리합니다.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

스크립트를 실행하면 `output` 폴더에 `shadowed_rectangle.pdf`가 생성됩니다. PDF 뷰어로 열면 부드러운 45도 그림자가 있는 깔끔한 사각형을 볼 수 있습니다—우리가 설정한 그대로입니다.

## 전체 작업 예제

아래는 위의 모든 단계를 결합한 완전한 실행 가능한 스크립트입니다. `create_rectangle_with_shadow.py`라는 파일에 복사·붙여넣기하고 `python create_rectangle_with_shadow.py`를 실행하세요.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Expected output:** 부드러운 대각선 그림자가 있는 단일 사각형을 보여주는 PDF 파일입니다. 추가 페이지나 숨겨진 아티팩트 없이—우리가 만든 도형만 표시됩니다.

## 일반 질문 및 엣지 케이스

### 다른 도형이 필요하면 어떻게 하나요?

Aspose.Words는 다양한 `ShapeType` 값(타원, 별, 콜아웃 등)을 지원합니다. `aw.drawing.ShapeType.RECTANGLE`을 원하는 열거형, 예를 들어 `aw.drawing.ShapeType.ELLIPSE` 로 교체하면 됩니다.

### 여러 그림자를 추가할 수 있나요?

API는 도형당 하나의 `ShadowFormat`만 제공하지만, 도형을 복제하고 각 복제본을 오프셋하고 투명도를 조정하여 여러 그림자를 흉내낼 수 있습니다.

### 그림자 색상을 브랜드에 맞게 바꾸려면?

`shadow.color`를 원하는 `aw.drawing.Color`로 설정하면 됩니다. 브랜드 파란색의 경우 `aw.drawing.Color.from_argb(255, 0, 120, 215)`를 사용하세요.

### PDF 대신 DOCX로 저장하려면?

`document.save(pdf_path)`를 `document.save("output/shadowed_rectangle.docx")`로 바꾸면 됩니다. 그림자 렌더링은 두 형식 모두에서 유지됩니다.

### 오래된 PDF 뷰어에서도 그림자가 작동하나요?

Aspose.Words는 그림자를 벡터 효과로 렌더링하므로 대부분 지원됩니다. 그러나 매우 오래된 뷰어는 효과를 평면화할 수 있으니, 대상 사용자의 장치에서 테스트하는 것이 좋습니다.

## PDF 다듬기 팁

- **테두리 추가:** `rectangle.line_format.width = 1.5` 로 설정하고 선명한 외곽선을 위해 색상을 지정합니다.  
- **사각형 중앙 정렬:** 삽입하기 전에 `builder.move_to_document_start()`를 사용하고, 그 다음 `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`를 설정합니다.  
- **텍스트와 결합:** 사각형 뒤에 `TextFragment`를 삽입하여 라벨을 붙입니다. 예: `"Important Section"`.

이러한 작은 조정으로 평범한 사각형을 보고서, 제안서 또는 전자책에서 전문적으로 보이는 다듬어진 콜아웃 박스로 변환할 수 있습니다.

## 결론

이제 Aspose.Words를 사용해 Python에서 **create rectangle shape**, **add shadow to shape**, **set shadow angle**, 그리고 **save document as PDF** 를 수행하는 완전한 레시피를 갖추었습니다. 단계는 간단하고, 코드는 완전하게 독립적이며, 문서 초기화부터 최종 PDF 다듬기까지 각 라인의 중요성을 확인했습니다.

다음으로는 더 복잡한 도형에 **how to add shape shadow** 를 적용해 보거나, 그라디언트 채우기를 실험하거나, 도형 안에 표를 생성해 볼 수 있습니다. 라이브러리는 도형을 북마크에 연결하는 기능도 지원하므로 인터랙티브 PDF에 유용합니다.

시도해 본 독특한 방법이 있나요? 댓글로 공유하거나 남은 질문을 남겨 주세요. 즐거운 코딩 되시고, 문서에 깊이를 더하는 작업을 즐기세요! 

![그림자와 함께하는 사각형 모양 – Python에서 create rectangle shape 예시](/images/rectangle-shadow.png)


## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [Word 문서 만들기 Java – 그림자 효과가 있는 사각형 모양 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words 도형 그림자 튜토리얼 – C#에서 Word 도형에 그림자 추가](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [C#를 사용해 Word에서 사각형 모양 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}