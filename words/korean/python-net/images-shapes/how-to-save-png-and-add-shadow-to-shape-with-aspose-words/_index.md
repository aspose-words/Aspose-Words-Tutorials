---
category: general
date: 2026-08-17
description: Aspose.Words for Python을 사용하여 PNG를 저장하는 방법. 도형에 그림자를 추가하고, 문서를 PDF로 저장하며,
  Word를 PNG로 내보내는 방법을 한 가이드에서 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: ko
lastmod: 2026-08-17
og_description: Aspose.Words를 사용하여 PNG를 저장하는 방법. 이 튜토리얼에서는 도형에 그림자를 추가하고, 문서를 PDF로
  저장하며, Word를 PNG로 내보내는 과정을 보여줍니다.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Aspose.Words를 사용하여 PNG 저장 및 도형에 그림자 추가 방법
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Aspose.Words로 PNG 저장 및 도형에 그림자 추가하는 방법
url: /ko/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words로 PNG 저장 및 도형에 그림자 추가 방법

Word 파일에서 **PNG 저장 방법**이 필요하다면, 이 가이드는 완전하고 실행 가능한 솔루션을 제공합니다. 또한 **도형에 그림자 추가**, **문서를 PDF로 저장**, **Word를 PNG로 내보내기**를 Aspose.Words 환경을 떠나지 않고 수행하는 방법을 확인할 수 있습니다.

이 튜토리얼은 빈 Word 문서를 PDF와 PNG 이미지로 변환하면서 사각형 도형에 간단한 그림자 효과를 적용하는 데 필요한 모든 것을 다룹니다. 외부 도구는 필요 없으며, 코드는 Aspose.Words for Python via .NET 7 이상에서 작동합니다.

## 달성할 목표

이 문서를 끝까지 읽으면 다음을 수행할 수 있습니다:

* 프로그램을 통해 새 Word 문서를 생성합니다.  
* 사각형 도형을 삽입하고 그림자 효과를 설정합니다.  
* 같은 문서를 PDF 파일로 저장합니다.  
* 문서를 PNG 이미지로 내보냅니다.  

이 단계들은 **PNG 저장 방법**이라는 일반적인 질문에 답하면서 **도형에 그림자 추가**와 **문서를 PDF로 저장**을 하나의 워크플로우에서 처리합니다.

## 사전 요구 사항

* Python 3.9 이상.  
* Aspose.Words for Python via .NET가 설치되어 있어야 합니다 (`pip install aspose-words`).  
* 지정한 출력 디렉터리에 대한 쓰기 권한이 있어야 합니다.  

아직 Aspose.Words를 설치하지 않았다면, 다음을 실행하십시오:

```bash
pip install aspose-words
```

## Aspose.Words로 PNG 저장 방법

첫 번째 주요 단계는 문서와 `DocumentBuilder`를 만드는 것입니다. 빌더는 도형, 표, 텍스트 등 콘텐츠를 삽입하기 위한 유창한 API를 제공합니다.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()`는 메모리 내 전체 Word 파일을 나타냅니다. `aw.DocumentBuilder`는 현재 삽입 위치를 가리키며, 처음에는 첫 번째(그리고 유일한) 섹션의 시작점입니다.

## 내보내기 전에 도형에 그림자 추가

도형은 사각형, 타원, 사용자 정의 다각형 등 모든 그리기 객체가 될 수 있습니다. 여기서는 100 × 100 포인트 사각형을 만들고 부드러운 그림자를 적용합니다.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

왜 저장하기 전에 그림자를 설정하나요? Aspose.Words는 PDF와 PNG 내보내기 단계에서 그림자를 렌더링하므로 두 출력 형식 모두에서 시각 효과가 유지됩니다.

### 전문가 팁
더 선명한 그림자가 필요하면 `blur`를 줄이세요. 더 큰 오프셋이 필요하면 `distance`를 늘리세요. `Shadow` 클래스는 `angle`과 `transparency`도 제공하여 세밀한 제어가 가능합니다.

## 문서를 PDF로 저장

내용이 준비되면 Word 문서를 PDF로 저장하는 코드는 한 줄이면 됩니다. `SaveFormat.PDF` 상수는 Aspose.Words에 변환을 수행하도록 지시합니다.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

결과 PDF에는 정의한 정확한 그림자를 가진 사각형이 포함됩니다. Aspose.Words는 벡터 그래픽을 처리하므로 PDF 파일 크기가 크게 증가하지 않습니다.

## Word를 PNG로 내보내기

PNG로 내보내면 각 페이지가 래스터 이미지로 생성됩니다. 기본적으로 Aspose.Words는 96 DPI를 사용하며, `PngSaveOptions` 객체를 제공하여 더 높은 해상도로 늘릴 수 있습니다.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

**Word를 PNG로 내보낼 때** 각 페이지가 별도의 PNG 파일로 저장됩니다. 예제 문서가 한 페이지만 포함하고 있기 때문에 단일 PNG 파일만 생성됩니다.

### 선택 사항: 고해상도 PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

높은 DPI는 PNG를 인쇄에 사용하거나 선명한 썸네일이 필요할 때 유용합니다.

## 전체 스크립트 – 복사, 붙여넣기, 실행

아래는 위에서 설명한 모든 단계를 구현한 완전하고 독립적인 스크립트입니다. `generate_assets.py`라는 이름으로 저장하고 명령줄에서 실행하십시오.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### 예상 출력

스크립트를 실행하면 세 개의 파일이 생성됩니다:

* `output/output.pdf` – 검은 그림자를 드리운 사각형이 포함된 PDF.  
* `output/output.png` – 동일 페이지를 96 DPI로 렌더링한 PNG.  
* `output/high_res_output.png` – 고품질을 위한 300 DPI PNG.

선호하는 뷰어로 파일을 열어 그림자가 정의한 대로 정확히 표시되는지 확인하십시오.

## 일반적인 질문 및 예외 상황

**출력 디렉터리가 존재하지 않으면 어떻게 하나요?**  
스크립트는 `os.makedirs(output_dir, exist_ok=True)`를 호출하여 폴더를 자동으로 생성합니다. 이렇게 하면 저장 작업 중 `FileNotFoundError`가 발생하지 않습니다.

**다른 그림자와 함께 여러 도형을 추가할 수 있나요?**  
가능합니다. 추가 `Shape` 객체를 만들고 각 `shadow` 속성을 독립적으로 설정한 뒤 `builder.insert_node(shape)`로 삽입하면 됩니다.

**다른 래스터 형식(예: JPEG)으로 변환할 때 그림자가 유지되나요?**  
Aspose.Words는 `SaveFormat`이 지원하는 모든 래스터 형식에 대해 그림자를 렌더링합니다. `aw.SaveFormat.PNG`를 `aw.SaveFormat.JPEG`로 바꾸면 그림자가 그대로 표시됩니다.

**“convert word to pdf”와는 어떻게 다른가요?**  
`convert word to pdf`는 4단계에서 수행되는 작업과 본질적으로 동일합니다. `doc.save` 호출에 `SaveFormat.PDF`를 지정하면 내부적으로 변환이 이루어지며 레이아웃, 폰트, 그림자와 같은 그래픽이 그대로 유지됩니다.

**도형 크기에 제한이 있나요?**  
도형은 포인트(1 pt ≈ 1/72 인치) 단위로 측정됩니다. 매우 큰 크기는 파일 크기를 증가시킬 수 있지만 Aspose.Words에 강제적인 제한은 없습니다. `aw.Shape`를 생성할 때 `width`와 `height` 인수를 조정하여 레이아웃에 맞게 설정하십시오.

## 결론

이제 Aspose.Words for Python을 사용해 Word 문서에서 **PNG 저장 방법**을 배우고, **도형에 그림자 추가**, **문서를 PDF로 저장**, **Word를 PNG로 내보내기**까지 한 번에 수행할 수 있습니다. 완전한 스크립트는 더 큰 문서, 여러 페이지 또는 복잡한 그래픽 효과에 맞게 쉽게 확장할 수 있는 깔끔하고 재현 가능한 패턴을 보여줍니다.

다음 단계로는 다음을 시도해 볼 수 있습니다:

* `ShapeType`의 다른 값(타원, 구름 등)을 실험해 보기.  
* Using `

## 다음에 배울 내용은 무엇인가요?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하며, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 되는 완전한 코드 예제와 단계별 설명을 제공합니다.

- [Aspose.Words 도형 그림자 튜토리얼 – C#에서 Word 도형에 그림자 추가](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Java에서 DOCX를 PNG로 변환하는 방법 – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Python에서 Aspose.Words를 사용해 Word 문서를 PostScript로 저장하기: 종합 가이드](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}