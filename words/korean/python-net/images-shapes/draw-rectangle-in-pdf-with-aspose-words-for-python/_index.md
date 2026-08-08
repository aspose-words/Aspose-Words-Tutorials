---
category: general
date: 2026-08-07
description: Aspose.Words for Python을 사용하여 PDF에 사각형을 그리며, 도형에 그림자를 추가하고 그림자 설정을 구성하는
  방법 및 문서를 PDF로 저장하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: ko
lastmod: 2026-08-07
og_description: Aspose.Words for Python을 사용하여 PDF에 사각형을 그립니다. 이 튜토리얼에서는 도형에 그림자를 추가하고,
  그림자 설정을 구성하며, 전문 문서 생성을 위해 문서를 PDF로 저장하는 방법을 보여줍니다.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Aspose.Words for Python을 사용하여 PDF에 사각형 그리기 – 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Aspose.Words for Python을 사용하여 PDF에 사각형 그리기
url: /ko/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python을 사용하여 PDF에 사각형 그리기

Python으로 작업하면서 **draw rectangle in PDF**가 필요하다면, 이 가이드는 완전하고 바로 실행할 수 있는 솔루션을 제공합니다. **add shadow to shape**를 정확히 수행하고, 그림자를 구성하며, 마지막으로 **save document as PDF**를 통해 배포 또는 보관용으로 저장하는 방법을 확인할 수 있습니다.

그림자가 있는 사각형을 만드는 것은 보고서, 청구서 또는 시각적 주석에 흔히 필요한 작업입니다. 이 튜토리얼을 마치면 현실적인 그림자가 적용된 사각형을 포함하는 PDF를 생성하는 단일 스크립트를 얻게 되며, 크기, 색상 및 오프셋을 조정하여 어떤 디자인에도 맞출 수 있는 방법을 이해하게 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Python 3.8+ 설치
* Aspose.Words for Python via .NET 패키지(`aspose-words`) – 다음 명령으로 설치:

```bash
pip install aspose-words
```

* PDF를 저장하려는 폴더에 대한 쓰기 권한

추가 라이브러리는 필요하지 않습니다; Aspose.Words가 도형 생성, 그림자 구성 및 PDF 내보내기를 내부적으로 처리합니다.

## Step 1: Create a new blank document (draw rectangle in PDF – initialize)

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 전체 PDF 파일을 나타내며 섹션, 단락 및 도형을 담는 컨테이너 역할을 합니다.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**왜 중요한가:** Aspose.Words는 PDF 생성을 Word 문서 모델에서의 변환으로 처리하므로 최종 출력이 PDF이더라도 `Document`부터 시작합니다.

## Step 2: Insert a rectangle shape into the document body

사각형은 특정 `ShapeType`입니다. 첫 번째 섹션의 본문에 추가하면 PDF로 저장될 때 자동으로 새 페이지가 생성됩니다.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**설명:** `width`와 `height` 속성은 PDF에서 도형의 시각적 크기를 제어합니다. 텍스트를 추가하면 테스트 중에 사각형을 쉽게 확인할 수 있습니다.

## Step 3: Add shadow to shape – enable and customize

이제 그림자 효과를 켜고 외관을 미세 조정합니다. 여기서 **add shadow to shape** 키워드가 사용됩니다.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**왜 도형 그림자를 구성해야 할까?** `blur`, `distance`, `angle`을 조정하면 현실적인 조명을 시뮬레이션할 수 있어 생성된 PDF의 가독성과 시각적 계층 구조가 향상됩니다.

## Step 4: Save document as PDF – final output

사각형과 그림자가 정의되었으므로 마지막 단계는 Word 문서를 PDF로 내보내는 것입니다. 이는 **save document as pdf** 요구 사항을 충족합니다.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

`shadow_rectangle.pdf`를 열면 “Shadow demo”라는 제목이 붙은 회색 테두리 사각형과 선명한 대각선 그림자가 있는 단일 페이지를 확인할 수 있습니다.

### Expected output

* `shadow_rectangle.pdf`라는 이름의 PDF 파일
* 200 pt × 100 pt 사각형이 한 페이지에 포함
* 45° 각도에서 5 pt 오프셋, 8 pt 블러가 적용된 그림자 표시

## Step 5: Explore variations and edge cases (optional)

실제 프로젝트에서 자주 필요할 수 있는 일반적인 변형을 아래에 정리했습니다:

| Variation | Code snippet | When to use |
|-----------|--------------|-------------|
| **Different shape type** (e.g., ellipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | 둥근 그래픽이나 배지를 만들 때 |
| **Custom shadow color** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | 회색 또는 브랜드 전용 그림자 색상이 필요할 때 |
| **Multiple shapes** | Repeat the shape‑creation block and adjust `left`/`top` properties | 복잡한 다이어그램을 구성할 때 |
| **No text inside shape** | Omit `rectangle.text = "..."` | 도형이 순수히 장식용일 때 |
| **Higher DPI output** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | 인쇄용 PDF를 만들 때 |

**Pro tip:** 다른 속성을 조정하기 전에 항상 `shadow.visible = True`를 설정하세요. 그렇지 않으면 변경 사항이 조용히 무시됩니다.

## Full script – copy, paste, and run

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

터미널이나 IDE에서 스크립트를 실행하세요. `YOUR_DIRECTORY`를 실제 폴더 경로(예: `"/tmp"` 또는 `"C:\\Users\\Me\\Documents"`)로 교체하면 됩니다.

## Conclusion

이제 Aspose.Words for Python을 사용하여 **draw rectangle in PDF**, **add shadow to shape**, **configure shape shadow**, 그리고 **save document as PDF**하는 방법을 알게 되었습니다. 전체 예제는 문서 생성부터 최종 내보내기까지 모든 단계를 보여주며, 선택적인 변형을 통해 보다 복잡한 시나리오에 코드를 적용하는 방법도 제시합니다.

다음 단계로는:

* 다른 도형 유형(`ShapeType.LINE`, `ShapeType.ELLIPSE`) 추가
* 그라디언트 채우기 또는 테두리 적용으로 시각적 매력 강화
* `PdfSaveOptions`를 사용해 글꼴을 포함하거나 이미지 압축 제어

파라미터를 실험하여 브랜드나 디자인 가이드라인에 맞게 조정해 보세요. 즐거운 PDF 스크립팅 되시길 바랍니다!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하며, 관련 주제를 깊이 있게 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 돕습니다.

- [Aspose.Words for Python을 사용한 PDF 책갈피 최적화](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Python Aspose Words에서 이미지 건너뛰기로 PDF 로드 최적화](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF 조작](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}