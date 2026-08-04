---
category: general
date: 2026-08-04
description: Aspose.Words 복구 모드를 사용하여 손상된 docx 파일을 복구하고, docx를 마크다운으로 변환하며, 수식을 LaTeX로
  내보냅니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: ko
lastmod: 2026-08-04
og_description: Aspose.Words 복구 모드로 손상된 docx 파일을 복구한 다음, 수식을 LaTeX로 내보내면서 docx를 마크다운으로
  변환합니다. 이 단계별 가이드를 따라 PDF 및 TXT 출력도 생성하세요.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: 손상된 docx 복구 및 마크다운으로 변환 – Aspose 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: 손상된 docx 복구 및 Aspose를 사용한 마크다운 변환
url: /ko/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 손상된 docx 복구 및 Aspose를 사용한 마크다운 변환

손상된 docx 파일을 **복구**해야 하는 경우, Aspose.Words는 손상된 Word 문서를 자동으로 복구할 수 있는 내장 복구 모드를 제공합니다. 파일이 복원되면 **docx를 마크다운으로 변환**하고, 과학 문서에서 원활하게 사용할 수 있도록 **수식 latex를 내보내기**까지 할 수 있습니다. 이 튜토리얼에서는 Python에서 이를 정확히 수행하는 방법과 PDF 및 일반 텍스트 출력에 대한 몇 가지 추가 옵션을 보여줍니다.

다음과 같은 내용을 배웁니다:

* 복구 모드를 사용하여 잠재적으로 손상된 DOCX를 로드합니다.  
* 복구된 문서를 LaTeX 형식 수식이 포함된 Markdown으로 저장합니다.  
* LaTeX 수식이 포함된 일반 텍스트(TXT) 버전을 생성합니다.  
* 플로팅 도형을 인라인 요소로 태그하면서 PDF로 내보냅니다.  
* 도형의 그림자를 조정하고 최종 PDF를 생성합니다.

외부 도구가 필요하지 않습니다—무료 Aspose.Words for Python 라이브러리만 있으면 됩니다.

## 사전 요구 사항

| 요구 사항 | 중요한 이유 |
|-------------|----------------|
| Python 3.8+ | Aspose.Words for Python에서 필요합니다. |
| `aspose-words` package (`pip install aspose-words`) | `aw` 네임스페이스를 제공하여 코드에서 사용됩니다. |
| A DOCX file that may be damaged (e.g., `corrupted.docx`) | 손상될 수 있는 DOCX 파일 (예: `corrupted.docx`) — 복구 워크플로를 시연합니다. |
| Write permission to the output directory | 스크립트가 여러 파일(`.md`, `.txt`, `.pdf`)을 작성합니다. |

평가 제한을 초과하는 경우, Aspose.Words 라이선스(무료 평가판 또는 구매)를 올바르게 구성했는지 확인하십시오.

## Aspose.Words를 사용한 손상된 docx 복구

첫 번째 단계는 Aspose.Words에 입력 파일을 잠재적으로 손상된 것으로 처리하도록 지시하는 것입니다. 이는 `LoadOptions.recovery_mode`를 사용하여 수행합니다.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**이 동작의 이유:**  
`RecoveryMode.RECOVER`는 로더가 구조적 오류를 무시하고 문서 트리를 재구성하도록 강제합니다. 파일이 부분적으로만 손상된 경우, 텍스트, 이미지 및 수식을 포함한 대부분의 내용이 복원됩니다.

**팁:** 문서를 복구하지 않고 검증만 하려면 `RecoveryMode.NO_RECOVERY`를 사용하십시오. 전체 복구를 위해서는 표시된 설정을 유지하십시오.

## LaTeX 수식이 포함된 docx를 마크다운으로 변환

문서가 메모리에 로드되면, 이를 Markdown으로 저장할 수 있습니다. `office_math_export_mode`를 `LATEX`로 설정하면 Aspose.Words가 각 Word 수식을 LaTeX 문자열로 렌더링합니다.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

결과 `output.md`는 일반 Markdown 파일처럼 보이지만, 모든 수식이 `$...$`(인라인) 또는 `$$...$$`(디스플레이) LaTeX 코드로 나타납니다. 이는 LaTeX 구문을 이해하는 Pandoc이나 Jupyter 노트북과 같은 하위 도구에 필수적입니다.

## 손상된 파일에 복구 모드 사용 방법

복구 모드는 모든 로드 작업에 재사용할 수 있습니다. 아래는 다른 스크립트에 복사하여 사용할 수 있는 간결한 패턴입니다:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

`load_with_recovery("myfile.docx")`를 호출하면 Aspose.Words가 이미 복구를 시도한 `Document` 객체가 반환됩니다. 이 함수는 프로젝트 전반에 걸쳐 **복구 모드 사용 방법**을 안전하게 구현합니다.

## 마크다운 및 txt 저장 시 수식 latex 내보내기

일반 텍스트 버전도 필요하다면, 동일한 `office_math_export_mode` 플래그를 `TxtSaveOptions`와 함께 사용할 수 있습니다.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

`.txt` 파일에는 Word 문서의 원시 텍스트가 포함되며, 모든 수식이 LaTeX 코드로 표시됩니다. 이 형식은 인덱싱이나 LaTeX를 이해하는 검색 엔진에 콘텐츠를 제공할 때 유용합니다.

## 추가 옵션: 인라인 도형 및 도형 그림자가 있는 PDF

### 플로팅 도형을 인라인 태그로 내보내기

플로팅 이미지나 텍스트 상자는 PDF 변환 시 레이아웃 문제를 일으킬 수 있습니다. `export_floating_shapes_as_inline_tag`를 설정하면 Aspose.Words가 해당 도형을 일반 인라인 요소로 처리하도록 강제하여 시각적 흐름을 유지합니다.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### 첫 번째 도형의 그림자 조정

최종 PDF를 저장하기 전에 특정 도형의 외관을 향상시키고 싶을 수 있습니다. 아래 코드는 첫 번째 `Shape` 노드에 접근하여 그림자를 활성화하고 시각적 매개변수를 조정합니다.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Result:** `shadowed.pdf`는 `output.pdf`와 동일하게 보이지만, 첫 번째 도형에 미묘한 검은 그림자가 추가되어 프레젠테이션에서 가독성을 향상시킬 수 있습니다.

## 전체 실행 가능한 스크립트

아래는 모든 단계를 결합한 전체 스크립트입니다. `recover_and_convert.py`라는 파일에 복사하고, `YOUR_DIRECTORY`를 실제 경로로 교체한 뒤 `python recover_and_convert.py`를 실행하십시오.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### 예상 출력

| 파일 | 설명 |
|------|-------------|
| `output.md` | 원본 DOCX의 Markdown 버전. 모든 수식이 LaTeX(`$...$` 또는 `$$...$$`)로 표시됩니다. |
| `output.txt` | 일반 텍스트 덤프 |

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [마크다운 사용 방법: DOCX를 LaTeX 수식이 포함된 마크다운으로 변환](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [Aspose.Words로 docx 복구하기 – 단계별](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [손상된 DOCX 복구 및 Word를 마크다운으로 변환](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}