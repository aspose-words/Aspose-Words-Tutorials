---
category: general
date: 2026-11-25
description: Python을 사용하여 Word 문서의 도형에 그림자를 추가합니다. Word에 사각형 도형을 삽입하고 Aspose.Words를
  사용해 투명 그림자를 적용하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: ko
lastmod: 2026-11-25
og_description: Python을 사용하여 Word 문서의 도형에 그림자를 추가합니다. 이 튜토리얼에서는 Word에 사각형 도형을 삽입하고
  Aspose.Words를 사용해 30 % 투명 그림자를 설정하는 방법을 보여줍니다.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Python으로 Word 문서의 도형에 그림자 추가 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Python을 사용하여 Word 문서의 도형에 그림자 추가하는 방법
url: /ko/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python을 사용하여 Word 문서에서 도형에 그림자 추가하기

Word 문서에 **도형에 그림자 추가**가 필요하다면, 이 가이드는 완전하고 실행 가능한 솔루션을 보여줍니다. Word 파일을 생성하고, 사각형 도형을 삽입한 뒤, 30 % 투명 그림자를 적용하는 과정을 Aspose.Words for Python 라이브러리를 사용해 설명합니다.

프로그래밍으로 Word 문서를 다루면 수동 포맷팅을 피할 수 있고, 보고서, 계약서, 마케팅 전단지를 대량으로 생성할 수 있습니다. 이 튜토리얼을 마치면 “**Python으로 Word 문서 만들기**” 질문에 바로 실행 가능한 코드 샘플로 답할 수 있게 됩니다.

## Prerequisites

시작하기 전에 다음을 확인하세요:

* Python 3.8 이상이 설치되어 있어야 합니다.
* 활성화된 Aspose.Words for Python 라이선스가 필요합니다(평가용 무료 체험 가능).
* `pip install aspose-words` 로 `aspose-words` 패키지를 설치합니다.
* 출력 파일을 쓸 수 있는 폴더가 있어야 합니다(코드의 `YOUR_DIRECTORY` 를 실제 경로로 교체).

추가적인 종속성은 필요하지 않습니다.

## Step 1: Create a new Word document

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 상의 전체 .docx 파일을 나타냅니다.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder`는 가상의 커서처럼 동작합니다. 메서드를 호출하면 라이브러리가 현재 커서 위치에 해당 요소를 삽입합니다.

## Step 2: Insert rectangle shape word

다음으로 **insert rectangle shape word** 를 builder의 `insert_shape` 메서드로 삽입합니다. 이 메서드는 도형 유형과 크기(포인트 단위, 1 포인트 = 1/72 인치)를 요구합니다.

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

디자인에 맞게 크기를 조정할 수 있습니다. 사각형은 문서의 드로잉 레이어에 포함되므로 이후에 채우기, 외곽선, 그림자 등을 수정할 수 있습니다.

## Step 3: Access the shape’s shadow format

모든 드로잉 객체는 그림자 모양을 제어하는 `shadow_format` 속성을 제공합니다. 투명도, 오프셋, 블러, 색상을 조정하려면 이 속성을 가져오세요.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

이 시점에서 도형은 기본 그림자(그림자 없음)를 가지고 있습니다. `ShadowFormat` 객체에 현실적인 효과를 만들기 위한 모든 매개변수가 들어 있습니다.

## Step 4: Make the shadow 30 % transparent

투명도는 `0`(완전 불투명)과 `1`(완전 투명) 사이의 값으로 표현됩니다. `0.3` 으로 설정하면 30 % 투명 그림자가 적용되어 텍스트를 압도하지 않으면서 깊이를 더합니다.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

추가 속성은 필수는 아니지만 효과를 미세 조정하는 방법을 보여줍니다. `visible` 플래그는 반드시 설정해야 합니다; 이를 빼면 다른 설정이 모두 올바르게 되어 있어도 그림자가 표시되지 않습니다.

## Step 5: Save the document to view the result

마지막으로 문서를 디스크에 저장합니다. 생성된 `.docx` 파일을 Microsoft Word 또는 호환 뷰어에서 열면 투명 그림자가 적용된 사각형을 확인할 수 있습니다.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`output.docx` 를 열면 오른쪽 아래로 살짝 오프셋된 회색 그림자가 있는 단순 사각형이 보입니다. 그림자의 30 % 투명도 덕분에 도형이 페이지에서 살짝 떠 있는 듯한 효과를 줍니다.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Python으로 만든 Word 문서에서 도형에 그림자 추가 예시"}

## Full, runnable script

모든 부분을 합치면 바로 복사·붙여넣기·실행할 수 있는 독립형 스크립트가 됩니다.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Expected output:** 생성된 `output.docx` 를 열면 사각형이 가벼운 반투명 그림자를 드리운 채 단일 페이지에 표시됩니다. 추가 포맷팅은 필요하지 않습니다.

## Common variations and edge cases

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different shape type** (e.g., ellipse) | `aw.drawing.ShapeType.RECTANGLE` 를 `aw.drawing.ShapeType.ELLIPSE` 로 변경합니다. |
| **Custom shadow color** | `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` 로 붉은색 그림자를 설정합니다. |
| **Multiple shapes** | `builder.insert_shape` 를 여러 번 호출합니다; 각 호출은 독립적인 `Shape` 객체를 반환하므로 개별적으로 스타일을 지정할 수 있습니다. |
| **Saving as PDF** | `doc.save(output_path)` 를 `doc.save(output_path.replace('.docx', '.pdf'))` 로 바꾸고 확장자를 `.pdf` 로 지정합니다. |
| **Running without a license** | 무료 체험판은 첫 페이지에 워터마크를 추가합니다. 프로덕션 사용을 위해서는 라이선스를 구매해 워터마크를 제거하세요. |

이러한 변형은 동일한 패턴—문서 생성, 도형 삽입, `shadow_format` 조정, 저장—이 대부분의 자동화 시나리오를 포괄한다는 것을 보여줍니다.

## Tips and best practices

* **Reuse the builder**: 전체 문서에 대해 하나의 `DocumentBuilder` 인스턴스를 유지해 불필요한 객체 생성을 방지합니다.
* **Dispose resources**: 장시간 실행되는 서비스에서는 저장 후 `doc.dispose()` 를 호출해 네이티브 메모리를 해제합니다.
* **Validate output**: Open XML 표준 준수를 확인하려면 저장 전에 `doc.validate(aw.ValidationType.FULL_VALIDATION)` 을 사용합니다.
* **Version compatibility**: 코드는 Aspose.Words for Python ≥ 22.9 에서 동작합니다. `pip install --upgrade aspose-words` 로 패키지를 최신 상태로 유지하세요.

## Conclusion

이제 Python을 사용해 Word 문서의 **도형에 그림자 추가** 방법을 알게 되었습니다. 다섯 단계—문서 생성, **insert rectangle shape word**, 그림자 설정, 저장—를 따라 하면 보고서, 인보이스, 마케팅 자료 등에서 깔끔한 문서 자동화를 구현할 수 있습니다.

다음 단계로는 그라디언트 채우기, 텍스트 래핑, PDF 변환 등 다른 포맷 옵션을 탐색해 보세요. 이 모든 주제는 이번 튜토리얼에서 소개한 `DocumentBuilder` 와 도형 포맷팅 개념을 기반으로 합니다.

즐거운 코딩 되시고, 간단한 그림자가 자동 생성 Word 문서에 가져다 주는 시각적 깊이를 경험해 보세요!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하는 내용으로, 단계별 코드 예제와 설명을 포함하고 있어 추가 API 기능을 마스터하고 다양한 구현 방식을 탐구하는 데 도움이 됩니다.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}