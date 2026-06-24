---
category: general
date: 2026-06-21
description: Aspose.Words를 사용하여 Python에서 사각형 모양을 만들고, 모양에 그림자를 추가하고, 채우기 색을 설정하는 방법을
  배우며, 몇 분 안에 문서를 PDF로 저장하세요.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: ko
og_description: Aspose.Words를 사용하여 Python에서 사각형 모양을 만듭니다. 이 가이드는 모양에 그림자를 추가하고, 모양
  채우기 색을 설정하며, 문서를 PDF로 저장하는 방법을 보여줍니다.
og_title: Python에서 사각형 모양 만들기 – Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Python에서 사각형 도형 만들기 – Aspose.Words 튜토리얼
url: /ko/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python에서 사각형 도형 만들기 – Aspose.Words 튜토리얼

Python으로 코딩하면서 Word 문서에 **사각형 도형을 만드는 방법**이 궁금하셨나요? 여러분만 그런 것이 아닙니다. 많은 개발자들이 색상이 있는 박스에 은은한 그림자를 넣고 이를 PDF로 내보내야 할 때 난관에 부딪히곤 합니다.  

이 가이드에서는 **사각형 도형을 만들고**, **도형 채우기 색상을 설정하고**, **도형에 그림자를 추가한 뒤**, **문서를 PDF로 저장**하는 완전하고 실행 가능한 예제를 단계별로 살펴보겠습니다. 애매한 설명이 아니라 바로 복사‑붙여넣기 해서 오늘 바로 실행할 수 있는 구체적인 코드만 제공합니다.

## 준비 사항

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- Python 3.8 이상 (우리가 사용하는 구문은 최신 버전에서 모두 동작합니다).
- 활성화된 Aspose.Words for Python 라이선스 또는 무료 체험판 (라이브러리는 순수 Python이며 COM 연동이 필요 없습니다).
- 익숙한 텍스트 편집기 또는 IDE – VS Code가 좋지만 어떤 것이든 상관없습니다.

그게 전부입니다. 무거운 프레임워크도 없고, 추가적인 OS‑레벨 의존성도 없습니다. 바로 시작해봅시다.

## 1단계: Aspose.Words for Python 설치

먼저 해야 할 일부터. 아직 설치하지 않았다면 PyPI에서 패키지를 받아옵니다:

```bash
pip install aspose-words
```

왜 이 단계가 중요한가요? Aspose.Words는 우리가 사용할 `Document`와 `DocumentBuilder` 클래스를 제공합니다. 이 라이브러리가 없으면 `insert_shape` 같은 메서드가 존재하지 않아 스크립트가 라인조차 그리기 전에 오류가 발생합니다.

> **팁:** 가상 환경을 깔끔하게 유지하세요. `python -m venv .venv && source .venv/bin/activate` 명령으로 환경을 만든 뒤 설치하면 시스템 패키지와 격리됩니다.

## 2단계: 새 Document와 DocumentBuilder 만들기

이제 실제로 **사각형 도형을 만들** 차례지만, 먼저 빈 캔버스가 필요합니다.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document` 객체는 전체 파일을 나타내고, `DocumentBuilder`는 현재 커서 위치를 알고 그 지점에 요소를 삽입할 수 있는 편리한 도구입니다. 빌더를 페이지에 글을 쓰는 펜이라고 생각하면 됩니다.

## 3단계: 사각형 도형 삽입

본격적인 작업이 시작되는 부분입니다. 고정된 너비와 높이를 가진 **사각형 도형**을 만들고 페이지에 배치합니다.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

왜 사각형인가요? 가장 단순하면서도 채우기 색상과 그림자를 보여줄 수 있는 형태이기 때문입니다. 나중에 원이나 별이 필요하면 `ShapeType.RECTANGLE`을 다른 열거값으로 바꾸면 됩니다.

## 4단계: 도형 채우기 색상 설정

흰색 박스만으로는 재미가 없으니 **도형 채우기 색상**을 부드러운 색으로 지정해봅시다—연한 파란색이 보고서에 잘 어울립니다.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

미리 정의된 `aw.Color` 멤버(`red`, `green`, `dark_gray` 등)를 사용하거나 RGB 튜플(`aw.Color.from_argb(255, 30, 144, 255)`)을 전달할 수 있습니다. 채우기 색상은 그림자나 테두리가 적용되기 전 사용자가 보는 색입니다.

## 5단계: 도형에 그림자 추가

시각적인 마무리 단계: **도형에 그림자 추가**. 그림자는 깊이감을 주어 사각형이 페이지에서 돋보이게 합니다.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**그림자를 추가하는 방법**? 위 코드가 바로 그 역할을 하지만 각 속성이 왜 중요한지 살펴보겠습니다:

- `visible` – 효과를 켜거나 끕니다.
- `color` – 색상을 정의합니다; 어두운 회색이 자연광을 흉내냅니다.
- `blur` – 값이 클수록 가장자리가 부드러워집니다.
- `offset_x` / `offset_y` – 그림자를 도형에서 떨어뜨려 위치를 조정합니다; 빛의 각도에 따라 조절하세요.
- `transparency` – 0은 불투명, 1은 투명; 0.2는 은은한 느낌을 줍니다.
- `type` – `OUTER`는 도형 외부에 그림자를 만들고, `INNER`는 내부에 그림자를 만듭니다.

극적인 드롭 섀도우가 필요하면 `blur`를 10‑15로 높이고 `offset_x`/`offset_y`를 6‑8로 늘려보세요.

## 6단계: 문서를 PDF로 저장

이 모든 작업은 **문서를 PDF로 저장**하고 공유하지 않으면 의미가 없습니다. Aspose.Words는 한 줄 코드로 해결합니다:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

왜 PDF인가요? PDF는 플랫폼 간 레이아웃을 그대로 유지해 보고서, 청구서, 인쇄물 등에 최적입니다. `save` 메서드는 파일 확장자를 자동으로 인식해 적절한 포맷을 선택합니다—경로가 `.pdf`로 끝나는지 확인만 하면 됩니다.

### 기대 결과

생성된 `ShapeWithShadow.pdf`를 열면 첫 페이지 상단 근처에 연한 파란색 사각형이 중앙에 배치되고, 오른쪽 아래로 약간 이동된 부드러운 어두운 회색 그림자가 보일 것입니다. 도형 가장자는 선명하고, 그림자는 은은하며 파일 크기는 보통 100 KB 이하입니다.

## 보너스: 그림자 미세 조정 – “그림자 추가”에 대한 답변

*“도형을 움직이지 않고 그림자 방향만 바꿀 수 있나요?”* 물론 가능합니다. 그림자 위치는 도형 좌표와 독립적이므로 `offset_x`와 `offset_y`만 조정하면 됩니다. 양수 값은 그림자를 오른쪽/아래로 이동시키고, 음수 값은 왼쪽/위로 이동시킵니다. 왼쪽 위에서 빛이 오는 경우 `offset_x = -3`, `offset_y = -3`을 사용하세요.

또 다른 자주 묻는 질문: *“같은 도형에 여러 개의 그림자를 적용할 수 있나요?”* Aspose.Words는 도형당 하나의 그림자만 지원합니다. 레이어드 효과가 필요하면 도형을 복제하고 약간씩 오프셋을 준 뒤 각각 다른 그림자를 적용하면 됩니다. 약간의 트릭이지만 동작합니다.

## 전체 스크립트 – 바로 실행 가능

아래는 완전하고 독립적인 스크립트입니다. `create_rectangle_with_shadow.py`라는 파일에 복사하고 `python create_rectangle_with_shadow.py`로 실행하세요.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **주의:** `YOUR_DIRECTORY`를 실제 존재하는 절대 경로나 상대 경로로 바꾸세요. 폴더가 없으면 Python이 `FileNotFoundError`를 발생시킵니다.

## 흔히 겪는 문제와 해결 방법

| 문제 | 발생 원인 | 해결 방법 |
|------|-----------|-----------|
| 그림자가 보이지 않음 | `shadow.visible`이 기본값 `False`인 상태 | `shadow.visible = True` 로 설정 |
| 도형이 보이지 않음 | 채우기 색상이 `aw.Color.transparent` 또는 `None` | `aw.Color.light_blue` 등 실색 사용 |
| PDF가 비어 있음 | `doc.save` 호출을 빼먹었거나 확장자를 잘못 지정 | `doc.save("output.pdf")` 호출 및 경로 확인 |
| 런타임 오류 `ImportError` | Aspose.Words가 설치되지 않았거나 잘못된 가상 환경 | 활성화된 venv에서 `pip install aspose-words` 실행 |

## 다음 단계 – 더 많은 도형과 서식 탐색

이제 **사각형 도형 만들기**를 마스터했으니 다음을 시도해볼 수 있습니다:

- `ShapeType.RECTANGLE`을 `ShapeType.ELLIPSE` 혹은 `ShapeType.PENTAGON`으로 바꿔 다른 기하학 형태 실험
- `builder.move_to(rectangle.absolute_position)` 후 `builder.writeln("Hello World")`를 사용해 도형 안에 텍스트 삽입
- `group = aw.drawing.GroupShape(doc)` 로 여러 도형을 그룹화해 복잡한 다이어그램 만들기
- `doc.save("output.docx")` 혹은 `doc.save("output.html")` 로 다른 포맷으로 내보내어 그림자가 어떻게 변하는지 확인

이 모든 확장은 동일한 핵심 개념에 기반합니다: **도형에 그림자 추가**, **도형 채우기 색상 설정**, 그리고 **문서를 PDF(또는 다른 포맷)로 저장**.

---

### 이미지 미리보기 *(옵션)*

![Python에서 그림자와 함께 사각형 도형 만들기](https://example.com/rectangle-shadow.png "Python에서 그림자와 함께 사각형 도형 만들기")

*스크린샷은 연한 파란색 사각형과 은은한 외부 그림자가 적용된 최종 PDF 출력을 보여줍니다.*

---

## 결론

우리는 Python에서 **사각형 도형을 만들고**, 사용자 정의 채우기를 적용하고, **도형에 그림자를 추가**한 뒤 **문서를 PDF로 저장**하는 모든 단계를 차근차근 살펴보았습니다. 코드는 바로 실행 가능하고, 각 속성 뒤에 숨은 이유를 설명했으며, 흔히 발생하는 문제와 다음에 배울 내용까지 다루었습니다.

## 다음에 배워야 할 내용은?


다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하여 관련 주제를 심도 있게 다룹니다. 각 자료는 완전한 코드 예제와 단계별 설명을 포함해 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 도와줍니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}