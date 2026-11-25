---
category: general
date: 2026-11-25
description: Aspose.Words for Python을 사용하여 손상된 docx 파일을 복구하고 markdown으로 변환합니다. PDF를
  인라인으로 저장하는 방법도 포함된 단계별 가이드를 따라보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to recover word
- how to convert word pdf
- how to save pdf inline
language: ko
lastmod: 2026-11-25
og_description: Aspose.Words for Python을 사용하여 손상된 docx 파일을 복구하고 마크다운으로 변환합니다. 이 튜토리얼에서는
  PDF 인라인 저장 및 도형 스타일링도 다룹니다.
og_image_alt: Diagram showing the recover corrupted docx workflow and conversion steps
og_title: 손상된 docx 복구 및 마크다운 변환 – 전체 파이썬 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Recover corrupted docx files and convert them to markdown using Aspose.Words
    for Python. Follow a step‑by‑step guide that also shows how to save PDF inline.
  headline: How to recover corrupted docx and convert to markdown
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document conversion
title: 손상된 docx 복구 및 마크다운으로 변환하는 방법
url: /ko/python/document-conversion/how-to-recover-corrupted-docx-and-convert-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 손상된 docx 복구 및 마크다운으로 변환하는 방법

손상된 **docx** 파일을 **복구**해야 하는 경우, 이 가이드는 Aspose.Words for Python을 사용한 신뢰할 수 있는 방법을 보여줍니다. 또한 **docx를 마크다운으로 변환**하고, 인라인 도형이 포함된 PDF를 생성하며, 첫 번째 도형의 외관을 미세 조정하는 방법도 배울 수 있습니다.

깨진 Word 문서를 복구하는 일은 막다른 길처럼 느껴질 수 있지만, Aspose.Words는 문서 구조를 재구성하려는 내장 복구 모드를 제공합니다. 파일을 읽을 수 있게 되면 Markdown 및 PDF를 포함한 다양한 형식으로 내용을 내보낼 수 있습니다.

이 튜토리얼에서 수행할 내용:

* 복구 모드를 사용하여 잠재적으로 손상된 `.docx` 로드하기.  
* Markdown 파일 내부에 LaTeX 형식으로 Office Math 수식을 내보내기 (`docx를 마크다운으로 변환`).  
* 부동 도형을 인라인 요소로 태그하는 PDF 저장하기 (`PDF를 인라인으로 저장하는 방법`).  
* 첫 번째 도형의 그림자를 조정하여 시각적 품질 향상하기.  
* 수정된 문서를 Word 파일로 다시 저장하기 (`Word 복구 방법`).

예제는 Python 3와 Aspose.Words 23.10을 사용하지만, 개념은 최신 버전의 라이브러리에도 적용됩니다.

## Prerequisites

| Requirement | Reason |
|-------------|--------|
| Python 3.8+ | Aspose.Words for Python이 요구하는 버전 |
| `aspose-words` package (`pip install aspose-words`) | 코드에서 사용되는 API 제공 |
| Microsoft Word에서 열리지 않는 `.docx` 파일 (선택 사항) | 복구 워크플로우 시연 |
| Python 스크립팅에 대한 기본 지식 | 예제를 프로젝트에 적용하기 용이 |

> **Pro tip:** 시작하기 전에 `pip show aspose-words`를 실행해 설치된 버전을 확인하세요.

## Recover corrupted docx and prepare for conversion

첫 번째 단계는 **복구 모드**로 문서를 여는 것입니다. Aspose.Words는 가능한 많은 데이터를 읽어 누락된 부분을 재구성하여 파이프라인의 나머지 작업이 진행될 수 있게 합니다.

```python
import aspose.words as aw

# Load a potentially corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/sample_corrupted.docx", load_options)
```

**Why this matters:**  
`recovery_mode`를 `RECOVER`로 설정하면 라이브러리는 비핵심 오류(예: 깨진 관계, 누락된 파트)를 무시하고 원본 문서의 최선 표현을 구성합니다. 이 플래그가 없으면 `Document` 생성자가 예외를 발생시켜 변환 파이프라인이 중단됩니다.

문서가 정상적으로 로드되면 다른 `Document` 객체와 마찬가지로 단락, 이미지, 도형 등을 검사하고 다음 단계로 진행할 수 있습니다.

## Convert docx to markdown

Aspose.Words는 Word 파일을 Markdown으로 렌더링할 수 있으며, 대부분의 서식을 유지하고 Office Math 수식을 선택적으로 LaTeX로 내보낼 수 있습니다. 이는 **docx를 마크다운으로 변환** 요구 사항을 충족합니다.

```python
# Export Office Math equations as LaTeX within a Markdown file
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/sample.md", markdown_options)
```

**What you get:**  
`sample.md`에는 원본 문서의 텍스트 내용이 들어 있습니다. 삽입된 수식은 LaTeX 블록으로 표시되며, *pandoc*이나 *GitHub* 같은 Markdown 프로세서가 올바르게 렌더링합니다.

> **Common question:** *Will images be included?*  
> Yes. Images are saved as separate files in the same directory and referenced with relative paths in the Markdown output.

## How to convert word pdf and save PDF inline

다음으로 복구된 문서의 PDF 버전을 생성합니다. `PdfSaveOptions` 클래스를 사용하면 부동 도형이 처리되는 방식을 제어할 수 있습니다. `export_floating_shapes_as_inline_tag`를 `True`로 설정하면 해당 도형이 PDF 내부 구조에서 인라인 요소로 태그됩니다 (`PDF를 인라인으로 저장하는 방법`).

```python
# Save the same document as PDF, tagging floating shapes as inline elements
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/sample.pdf", pdf_options)
```

**Why you might need this:**  
일부 다운스트림 PDF 처리기(예: OCR 도구)는 인라인 태그를 사용해 도형 경계를 정확히 찾습니다. 도형을 인라인으로 태깅하면 접근성이 향상되고 나중에 추출하기도 쉬워집니다.

## Fine‑tune the visual appearance of the first shape

복구된 문서에 부동 도형(예: 사진, 그림)이 포함된 경우, 최종 저장 전에 시각적 속성을 조정할 수 있습니다. 아래 예제는 첫 번째 도형의 그림자를 수정합니다.

```python
# Retrieve the first shape in the document
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Access and configure the shape's shadow format
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.color = aw.drawing.Color.black
shape_shadow.offset_x = 5          # Horizontal offset in points
shape_shadow.offset_y = 5          # Vertical offset in points
shape_shadow.blur = 8
shape_shadow.transparency = 0.2    # 20 % transparent
```

**Practical tip:**  
문서에 도형이 많이 있다면 `doc.get_child_nodes(aw.NodeType.SHAPE, True)`를 사용해 반복하고 조건에 따라 동일한 스타일을 적용하세요.

## Save the modified document (how to recover word)

도형을 조정한 뒤 변경 사항을 Word 파일에 저장합니다. 이는 **Word 복구 방법**을 보여주며, 프로그램matically 복구 및 편집된 문서를 다시 저장하는 과정을 나타냅니다.

```python
# Save the document with the modified shape
doc.save("YOUR_DIRECTORY/sample_modified.docx")
```

이제 세 가지 활용 가능한 결과물이 생성되었습니다:

| File | Purpose |
|------|---------|
| `sample.md` | LaTeX 수식이 포함된 Markdown 소스 (`docx를 마크다운으로 변환`). |
| `sample.pdf` | 인라인‑태그된 도형이 포함된 PDF (`PDF를 인라인으로 저장하는 방법`). |
| `sample_modified.docx` | 복구 및 향상된 Word 문서 (`Word 복구 방법`). |

## Verify the results

각 출력 파일을 열어 작업이 성공했는지 확인하세요:

* **Markdown:** `sample.md`를 텍스트 편집기로 열고 `$$ … $$` 로 감싼 LaTeX 블록을 찾습니다.  
* **PDF:** Adobe Reader로 `sample.pdf`를 열고 *Content* 패널에서 부동 도형이 **Figure (Inline)** 로 표시되는지 확인합니다.  
* **Word:** Microsoft Word에서 `sample_modified.docx`를 열고 첫 번째 도형에 부드러운 그림자가 적용됐는지 확인합니다.

파일이 열리지 않으면 `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER_WITH_EXCEPTIONS`로 스크립트를 다시 실행해 자세한 오류 메시지를 확인하세요.

## Common edge cases and how to handle them

| Situation | Recommended approach |
|-----------|----------------------|
| 파일이 **완전히 읽을 수 없음** (XML 파트가 없음) | `RecoveryMode.RECOVER_WITH_EXCEPTIONS`를 사용해 정확한 실패 원인을 캡처한 뒤, 문서를 처음부터 재구성하는 것을 고려합니다. |
| **대용량 문서** (> 100 MB) 로 인해 메모리 압박 발생 | `DocumentBuilder`를 이용해 섹션별로 처리하거나, 증분 저장을 지원하는 `SaveOptions`로 스트리밍 출력합니다. |
| 변환 후 **이미지 누락** | 원본 `.docx`에 이미지 파트가 포함되어 있는지 확인하고, 누락된 경우 저장 전에 자리표시자로 교체합니다. |
| **수식 내보내기**가 LaTeX 대신 원시 MathML로 표시 |  |

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [How to recover corrupted docx files using Aspose.Words for Python](/words/english/python-net/document-operations/how-to-recover-corrupted-docx-files-using-aspose-words-for-p/)
- [How to convert DOCX to PDF in Python using Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)
- [How to save Word as PDF and convert DOCX to Markdown](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}